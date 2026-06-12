---
title: "Need a walkthrough on creating user website"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by sgg on 2007-05-07
Hello,

Here's what I'm trying to  do. 

I've created a new user. I would like the
user to have a website which also allows ftp access.
I'm assuming the url would be: 
localhost/newuser/newpage

currenly, only contents of my /var/www folder are
visible via browser.

Here's what I've done so far:

I've setup a 6.06 lamp server.
I've installed vsftpd.
I've enabled usermod (but don't know how to use it or know what it does)

I've created a folder called public_html within my
new user's home flolder ie. /home/newuser/public_html

I've run chmod 775 public_html

I need  a bit of a walkthrough here please.

On a side note. I'm enjoying Ubuntu very much.

---

### Post by linux_kid on 2007-05-07
/var/www is currently the only place on your computer that is being hosted.  This is the apache default.  I am not sure what you want, do you want home/newuser/publc_html to be hosted?

On a side note, I'm glad your enjoying ubuntu

---

### Post by sgg on 2007-05-07
yes, /home/newuser/public_html should be  hosted
as well as have ftp access.

I know this is basic but i'm in the dark here.

---

### Post by linux_kid on 2007-05-09
This will get you to the apache config document
```
sudo gedit /etc/apache2/sites-available/default
```
On the fifth line, you will see the following code:
```
***
DocumentRoot /var/www
***
```
Change /var/www to the location you want to hosted.

I'm not very fluent with FTP, sorry

---

### Post by opus on 2007-05-09
If you have enabled the userdir module, then the users public_html folder will be viewable at [http://hostname/~username/](http://hostname/~username/)

The '~' character is the key.

Hopefully you enabled the module by using "a2enmod userdir"

Aaron

---

