# -app-app
将网站封装成苹果免签app +安卓app
目前仅支持api调用

分为两步:提交 查询

提交:

请求地址ַ:https://xujimu.wlznsb.cn/ioss/submit.php
请求方式ʽ:post
请求参数
appname(软件名称)
url(打包网址)
name(名称)
jigou(机构)
miaoshu(描述)
touyi(ͬ同意信息)
img(经过base64编码后的桌面图标)
public(服务器证书)
root(根证书)
key(秘钥)
sign(签名){appname + url + name + jigou + miaoshu + touyi + img + public + root +key 的md5}

完整请求参数
appname=淘宝&url=https://main.m.taobao.com&name=淘宝&jigou=淘宝机构&miaoshu=淘宝安装程序&touyi=无&img=base64编码的字符串&public=服务器证书&root=根证书&key=秘钥&sign=签名
服务器返回:{"err":1,"mess":"C32907342F9D958709FFA04DAEA2EBA2"} 参数说明:err为1则提交成功否则失败,mess为查询编号

查询:

请求地址ַ:https://xujimu.wlznsb.cn/ioss/select.php
请求方式ʽ:post
请求参数
uuid=返回的mess

服务器返回:
{"ios_id":"427","ios_appname":"淘宝","ios_url":"https://main.m.taobao.com","ios_name":"淘宝","ios_jigou":"淘宝机构","ios_miaoshu":"淘宝安装程序","ios_tongyi":"无","ios_img":"temp/9F00F96E161F2C1BCB7757A85A94C8FA/android/temp/icon.png","ios_public":"static/cert/public.crt","ios_root":"static/cert/root.crt","ios_key":"static/cert/key.key","ios_sign":"1a6da74c578747cf2636213961021598","ios_uuid":"9F00F96E161F2C1BCB7757A85A94C8FA","ios_time":"2020-05-11 22:56:34","ios_status":"打包成功","ios_index":"暂未开放","ios_down":"https://xujimu.wlznsb.cn/ioss/temp/9F00F96E161F2C1BCB7757A85A94C8FA/down.zip"}
参数很多不一一说明,请根据字段意思自己判别

注意:
1.提交的请求参数内容不允许有+,如果有+请替换成%2B,建议每个字段都进行替换一下
2.签名的md5必须是utf8编码后的md5
3.证书要么不全部不填,要么全部填写正确,否则必定打包失败
