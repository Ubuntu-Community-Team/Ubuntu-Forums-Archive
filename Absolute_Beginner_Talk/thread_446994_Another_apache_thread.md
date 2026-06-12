---
title: "Another apache thread"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by nikomax on 2007-05-17
Hi there :)

iI have just installed Apache, php5, mysql via synaptic package manager and to be honest its looking good.
but I wondering if i could change the location of the /www/ folder to my home folder. The reason being is that my home folder is on a separate hard drive. I have googled and tried tried looking but no luck so far.

Thanks

---

### Post by Bachstelze on 2007-05-17
This can be done in your /etc/apache2/sites-enabled/default file. If you paste the file here, I might be able to tell you what you need to change. Not sure though, I have very little experience with Apache 2.x...

---

### Post by CorranH on 2007-05-18
You'd need to change both instances of /var/www/ to /home/. 

The two lines you need to change are:
DocumentRoot /var/www
and
<Directory /var/www/>

They appear on lines 5 and 10, for me atleast.

That should be all you need to change.

---

### Post by esoterica on 2007-05-18
Just got done installing this myself (thanks again Hymn ToLife). The documents that tell you how to do this step by step and easy to read are here...

[https://help.ubuntu.com/7.04/server/C/httpd.html](https://help.ubuntu.com/7.04/server/C/httpd.html)

It's very well documented, I'm just loving Ubuntu because the documentation is so great!

---

### Post by nikomax on 2007-05-19
Thank you so much!!
The community is half the reason I'm loving ubuntu so much :D:D
I really wish I found out about ubuntu earlier :)

---

