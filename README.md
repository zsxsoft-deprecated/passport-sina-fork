# passport-sina
**此项目作者已消失，本项目仅为该项目的从npm上下载的Fork!!!!**


用于 [passport](http://passportjs.org/)，基于 [passport-oauth](https://github.com/jaredhanson/passport-oauth) 的新浪微博 OAuth2 Strategy 。

## Installation

```bash
$ npm install passport-sina
```

## Usage

### 配置

```
passport.use(new passport_sina({
    clientID: 'your app key here'
  , clientSecret: 'your app secret here'
  , callbackURL: 'your callback url here'
//  , requireState: true // for csrf, default: true
//  , scope: ['statuses_to_me_read'
//          , 'follow_app_official_microblog']
},
function(accessToken, refreshToken, profile, callback) {
    // verify
    process.nextTick(function () {
        return callback(null, profile);
    });
}));
```

### 验证

```
// Auth
app.get('/auth/sina', passport.authenticate('sina'));
// Callback
app.get('/auth/sina/callback', passport.authenticate('sina', { failureRedirect: '/aaa', successRedirect: '/' }));
```

### Express and Session

需要注意的是，由于默认启用 `state` 特性(防CSRF)，你需要启用 express 或 connect 的 session 中间件；

## Example

一个完整的例子可见 [example/app.js](https://github.com/kfll/passport-sina/tree/master/example/app.js)

## Tests

```
$ npm install
$ make test
```
