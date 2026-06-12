---
title: "change apache2 directory"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by rickdog on 2007-04-07
Can anyone tell me how to change the location of where apache2 directs web requests? I would like it to point to a directory on a different hard drive rather than the default /var/www

Thanks.

---

### Post by chamberlain2006 on 2007-04-07
You can change the configuration file "/etc/apache2/apache2.conf".  Change the DocumentRoot to whatever the directory is.  IE: /home/username/web

---

### Post by rickdog on 2007-04-07
Thanks for getting back. Unfortunately, I can't seem to find the DocumentRoot statement in my apache2.conf file. There is a ServerRoot, however, is that the path I change? Will that affect any of the other log file locations and such? I have the sight up, but I'd just like to keep the files on another disk. Thanks.

---

### Post by chamberlain2006 on 2007-04-08
The other place it might be is in the /etc/apache2/sites-available/default.conf file.  If it isn't there, you can safely add it to the file.

---

### Post by rickdog on 2007-04-10
Thanks, got it. I had had an earlier Apache server installed when I had XP and the configuration was located in the httpd.conf file, so that's what I was used to. Now, it's all set up!

[http://watershed.servehttp.com](http://watershed.servehttp.com)

---

