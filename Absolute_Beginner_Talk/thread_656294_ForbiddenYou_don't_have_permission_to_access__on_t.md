---
title: "Forbidden/You don't have permission to access / on this server"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by guitarman on 2008-01-02
Hi Folks and Happy New year,
I have set up my Apache server and copied my 4 web site files into both /var/www and /var/www/mysite.com directories have restarted Apache2 successfully, but when I try to access my server with 192.168.2.10 (Ubuntu IP address on my local line) I get:


Forbidden
You don't have permission to access /index.html on this server.

I found info on the Apache.org FAQs and did a chmod -x /var/www and chmod -x /var/www/mysite.com, but I still get the same error. 

Also did the following as per Apache.org
"Search your conf/httpd.conf file for this exact string: <Files ~>. If you find it, that's your problem -- that particular <Files>  container is malformed. Delete it or replace it with <Files ~ "^\.ht"> and restart your server and things should work as expected."

But still no success.  Any ideas would be greatly appreciated.

Thanks again,

---

### Post by foolsh on 2008-01-02
sudo nautilus
then browse to the /var/www/ folder and right click /mysite then choose proberties 
next go to the permissions tab and make Folder Access on Others read "Access Files"
if your using kubuntu instead of "sudo nautilus" use "sudo konqueror"

atleast that sounds like the problem to me
hope this helps

---

### Post by cecure on 2008-01-02
> **guitarman said:**
> Hi Folks and Happy New year,
I have set up my Apache server and copied my 4 web site files into both /var/www and /var/www/mysite.com directories have restarted Apache2 successfully, but when I try to access my server with 192.168.2.10 (Ubuntu IP address on my local line) I get:


Forbidden
You don't have permission to access /index.html on this server.

I found info on the Apache.org FAQs and did a chmod -x /var/www and chmod -x /var/www/mysite.com, but I still get the same error. 

Also did the following as per Apache.org
"Search your conf/httpd.conf file for this exact string: <Files ~>. If you find it, that's your problem -- that particular <Files>  container is malformed. Delete it or replace it with <Files ~ "^\.ht"> and restart your server and things should work as expected."

But still no success.  Any ideas would be greatly appreciated.

Thanks again,

First, does it work when you access it as localhost?


Second, try making the files readable and executable by everyone, if you only want users to access your mainpage try:
```
sudo chmod a=rx /var/www/index.html 
```

or if you want all files readable by everyone
```
sudo chmod -R a=rx /var/www
```

hope that helps

---

### Post by foolsh on 2008-01-04
> **cecure said:**
> First, does it work when you access it as localhost?


Second, try making the files readable and executable by everyone, if you only want users to access your mainpage try:
```
sudo chmod a=rx /var/www/index.html 
```

or if you want all files readable by everyone
```
sudo chmod -R a=rx /var/www
```

hope that helps

if this is a web page open to the public please don't make the files executable by anyone that could lead to big problems
read permissions should more than enough

---

### Post by rybaxs on 2008-05-07
who created this post? i greatly fully thank you,,! yeah! my boss will never kill me again.. :guitar:  when i set to chmod 666 Forbidden appear, then when i sudo chmod -R a=rx /var/www at the root. my virtual host works!..

---

### Post by lordadi on 2008-05-08
Thank you So so sooooo much. This totally took care of my problems. YAY!!:)

---

