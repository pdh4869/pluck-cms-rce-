# CVE-2026-117426: Pluck CMS Authenticated Remote Code Execution (RCE)

## Affected Product
- Product: Pluck CMS
- Version: 4.7.21 dev

## Vulnerability Type
Remote Code Execution (RCE) / Arbitrary File Upload

## Description
Pluck CMS 4.7.21 dev allows authenticated remote code execution via the module installation functionality. An administrator can upload a crafted `.tar.gz` archive containing a PHP webshell, which is extracted to `data/modules/` — a directory that lacks PHP execution restrictions in its `.htaccess` file — resulting in remote code execution.

## Impact
Allows an authenticated administrator to execute arbitrary PHP code on the server.

## PoC
1) approach manage modules menu and click "install a module"
<img width="1919" height="515" alt="1__install a module" src="https://github.com/user-attachments/assets/9e8802db-5250-43e2-bb0e-0b7c78ed2923" />

2) click "select file"
<img width="1919" height="515" alt="2__select file" src="https://github.com/user-attachments/assets/122ca740-4282-45f2-bc74-da1be91daee9" />

3) make shell file (tar.gz)
<img width="620" height="531" alt="3__make tar" src="https://github.com/user-attachments/assets/26271e67-45e2-4674-aa66-2d1868b9115c" />

<img width="497" height="74" alt="4__make tar2" src="https://github.com/user-attachments/assets/be7feb2e-5e07-4f5d-9481-e8f84ea1c0f0" />

4) open tar.gz file
<img width="762" height="448" alt="5__open" src="https://github.com/user-attachments/assets/ff842cb0-c231-4879-ac14-b4ec6745b92b" />

5) click "Upload" button
<img width="1923" height="455" alt="6__upload" src="https://github.com/user-attachments/assets/632caccc-6f99-46f2-ae53-d76f06813d2e" />

6) installed successfully
<img width="1923" height="536" alt="7__successfully" src="https://github.com/user-attachments/assets/b2a3e207-faa2-498c-8539-b4c5ef872381" />

7) Result of cmd=id 
<img width="1923" height="536" alt="8__cmd id" src="https://github.com/user-attachments/assets/41017912-ffa5-466c-9eec-eefeeac10e47" />

8) Result of cmd=cat /etc/passwd
<img width="1923" height="536" alt="9__cmd cat etc passwd" src="https://github.com/user-attachments/assets/9cd23f68-adf2-4ac8-b028-bb306a30663c" />
