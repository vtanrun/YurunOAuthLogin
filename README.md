# YurunOAuthLogin
PHP封装集成的QQ、微信登录SDK，测试代码可看test目录

## 代码实例

自v1.2起所有方法统一参数调用，如果需要额外参数的可使用对象属性赋值，具体参考test目录下的测试代码。

下面代码以QQ接口举例，完全可以把QQ字样改为其它任意接口字样使用。

### 实例化

```php
$qqOAuth = new \Yurun\OAuthLogin\QQ\OAuth2('appid', 'appkey', 'callbackUrl');
```

### 登录

```php
$url = $qqOAuth->getAuthUrl();
$_SESSION['YURUN_QQ_STATE'] = $qqOAuth->state;
header('location:' . $url);
```

### 回调处理

```php
// 获取accessToken
$accessToken = $qqOAuth->getAccessToken($_SESSION['YURUN_QQ_STATE']);

// 调用过getAccessToken方法后也可这么获取
// $accessToken = $qqOAuth->accessToken;
// 这是getAccessToken的api请求返回结果
// $result = $qqOAuth->result;

// 用户资料
$userInfo = $qqOAuth->getUserInfo();

// 这是getAccessToken的api请求返回结果
// $result = $qqOAuth->result;

// 用户唯一标识
$openid = $qqOAuth->openid;
```