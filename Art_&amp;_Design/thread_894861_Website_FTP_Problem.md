---
title: "Website FTP Problem"
date: 2008-08-19
forum: Art &amp; Design
---

### Post by adewale on 2008-08-19
I need to upload some files onto a website which is only possible through FTP. Now my ISP put me behind a proxy, i've tried all ftp managers i know the simply can't establish connection maybe its my proxy. Please i'd really love to upload the files now cause am behind deadline already.
Thanks

---

### Post by Genius314 on 2008-08-19
You could try a web service that lets you upload files via FTP:

[http://www.net2ftp.com/](http://www.net2ftp.com/) (WARNING: I've never used this one. Maybe get a second opinion on this before trying it out.)
[http://www.web2ftp.com/](http://www.web2ftp.com/) (I used to use this one, and it seemed safe. Unfortunately they seem to have been down for quite a while.)

Those are just two examples. There might be a better one out there.

---

### Post by Cheesehead on 2008-08-19
I've had good luck with the 'curl' package.

```
curl -v -T localpath/localfile -u username:password ftp://ftp.ftpsite.com/path/
```

Since it's easy to script, I can maintain a lot of pages easily without all that tedious *remembering*.


Alternate plan: If it's your ISP, put it on a USB stick and head to a local internet cafe, or invite a friend with a wireless laptop to coffee.

---

