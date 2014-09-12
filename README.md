#Url Checker API Documentation
### Update Sep 12th, 2014

---------
URL:http://urlchecker.net/#api

### Description :
Urlchecker.net is a website tools to help you find out the link want to download still A Live or Dead
and get file name,file size

### Required parameters
- link :Single Link need check ( see list host support from http://urlchecker.net/#hosts)
- url : website or folder need extract
- decodelink : Decode single link only ( adf.ly,bit.ly....)
- decodelinks : Decode multi link or website 

*Chose one of parameter only*

### Method : POST OR GET

Optional Parameters
response_format : 'xml' ,'txt' or 'json' (default 'xml')

And response
Result of querry: "Success" OR "Error"
Status of file : "working", "dead" or "unknown" 
Size of file : "KB", "MB" "GB" or "TB" 
current_api_version: API version

----------------------------------------------------------------------------------------
### Extract website or folder
Example: with php
*Demo worked with example link only*
*Direct query http://api.urlchecker.net/?url=http://pastebin.com/raw.php?i=DUfzyeXn*
```php
   <?php
    $response_format="xml";
    $link="http://pastebin.com/raw.php?i=DUfzyeXn";
    $url = 'http://api.urlchecker.net/';
    $ch = curl_init($url);

    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, "response_format=$response_format&url=$link");
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_VERBOSE, 1);
    curl_setopt($ch, CURLOPT_NOBODY, 0);

    $response = curl_exec($ch);
    echo $response;
    ?>
```
 Out put 'xml'
 
 

```xml


        <response>
                    <title>Checked by urlchecker version 1.0</title>
                    <url></url>
                    <api_query>8</api_query>
                    <daily_limited>250</daily_limited>
                    <api_member_pack>Free</api_member_pack>
                    <api_version>1.0</api_version>
                    <webMaster>thomanphan@gmail.com</webMaster>
           <item>
                <link>http://letitbit.net/download/94986.9b8ca37e93a0f879e3a1c89ca909/Paname_FY.rar.html</link>
                <result>Success</result> 
                <status>working</status> 
                <filename>Paname_FY.rar</filename>
                <filesize>3.45</filesize>
                <filesize_mb>3.45</filesize_mb>
           </item>
           <item>
                <link>http://rapidgator.net/file/007a0d220430bde47d342dfb67b948b3/Paname_FY.rar.html</link>
                <result>Success</result> 
                <status>working</status> 
                <filename>Paname_FY.rar</filename>
                <filesize>3.29</filesize>
                <filesize_mb>3.29</filesize_mb>
           </item>
        </response>
```
### Decode multi link or website container encode links
Example: with php
*Demo worked with example link only*
*Direct query http://api.urlchecker.net/?decodelinks=http://pastebin.com/raw.php?i=A1K3TxXE*
```php
   <?php
    $response_format="xml";
    $decodelinks="http://pastebin.com/raw.php?i=DUfzyeXn";
    $api = 'http://api.urlchecker.net/';
    $ch = curl_init($api);

    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, "response_format=$response_format&decodelinks=$decodelinks");
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_VERBOSE, 1);
    curl_setopt($ch, CURLOPT_NOBODY, 0);

    $response = curl_exec($ch);
    echo $response;
    ?>
```
 Out put 'xml'
 
 

```xml


        <response>
                    <title>Checked by urlchecker version 1.0</title>
                    <url>http://pastebin.com/raw.php?i=A1K3TxXE</url>
                    <api_query>59</api_query>
                    <daily_limited>250</daily_limited>
                    <api_member_pack>Free</api_member_pack>
                    <api_version>1.0</api_version>
                    <webMaster>thomanphan@gmail.com</webMaster>
                <item>
                     <link>https://adf.ly/j24Fg</link>
                     <result>Success</result> 
                     <status>decoded</status> 
                     <decoded_link>http://billionuploads.com/fqc70c48t6b6</decoded_link>
                </item>
                <item>
                     <link>http://adf.ly/rz625</link>
                     <result>Success</result> 
                     <status>decoded</status> 
                     <decoded_link>https://github.com/Thomanphan/urlchecker</decoded_link>
                </item>
                <item>
                     <link>http://adf.ly/rz645</link>
                     <result>Success</result> 
                     <status>decoded</status> 
                     <decoded_link>http://urlchecker.org/</decoded_link>
                </item>
                <item>
                     <link>http://adf.ly/rz654</link>
                     <result>Success</result> 
                     <status>decoded</status> 
                     <decoded_link>http://urlchecker.org/member/</decoded_link>
                </item>
        </response>
```

### Check single link
Example: with php

  Out put xml
  
  

```php
   <?php
    $response_format="xml";
    $link="http://www.mediafire.com/?wfghxg5x7d159x8";
    $url = 'http://api.urlchecker.net/';
    $ch = curl_init($url);

    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, "response_format=$response_format&link=$link");
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_VERBOSE, 1);
    curl_setopt($ch, CURLOPT_NOBODY, 0);

    $response = curl_exec($ch);
    echo $response;
    ?>
```
And response
OUTPUT


```php
       <response>
        <link>http://www.mediafire.com/?wfghxg5x7d159x8</link>
        <result>Success</result>
        <status>working</status>
        <filesize>167.53 kB</filesize>
        <filesize_mb>0.164</filesize_mb>
        <api_query>5</api_query>
        <daily_limited>10</daily_limited>
        <api_member_pack>Free</api_member_pack>
        <current_api_version>0.9</current_api_version>
        </response>
```





 Out put json

Example: php

Request url

```php
<?php
$response_format="json";
$link="http://www.mediafire.com/?wfghxg5x7d159x8";
$url = 'http://api.urlchecker.net/';
$ch = curl_init($url);

curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, "response_format=$response_format&link=$link");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_VERBOSE, 1);
curl_setopt($ch, CURLOPT_NOBODY, 0);

$response  = curl_exec($ch);
echo $response;
?>
```



OUTPUT



```php
    {"link":"http:\/\/www.mediafire.com\/?wfghxg5x7d159x8","result":"Success","status":"working","current_api_version":"0.1"}

```



Out put txt

Example: php

Request url



```php
<?php
$response_format="txt";
$link="http://www.mediafire.com/?wfghxg5x7d159x8";
$url = 'http://api.urlchecker.net/';
$ch = curl_init($url);

curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, "response_format=$response_format&link=$link");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_VERBOSE, 1);
curl_setopt($ch, CURLOPT_NOBODY, 0);

$response  = curl_exec($ch);
echo $response;
?>
```


OUTPUT



```php
link:http://www.mediafire.com/?wfghxg5x7d159x8|result:Success|status:working|api_query:1|current_api_version:0.2

```
