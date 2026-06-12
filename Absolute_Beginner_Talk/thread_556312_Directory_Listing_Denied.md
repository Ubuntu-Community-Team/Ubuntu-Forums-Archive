---
title: "Directory Listing Denied"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by veinless on 2007-09-21
Hello there,

I have apache 2 on ubuntu and I host a website. The problem is that anyone can see the directory list of my page but I want someone, who tries to view the directory list, to get the message:
Directory Listing Denied
This Virtual Directory does not allow contents to be listed.

I would appreciate if you were comprehensive because I'm a newnewnewbie.:(

Thanks and sorry for my English...:oops:

---

### Post by ukripper on 2007-09-21
Apply appropriate security to your /var/www/*sharename* with chmod command

---

### Post by hyper_ch on 2007-09-21
[http://www.linuxassassin.com/2007/06/16/disable-directory-listing-on-apache/](http://www.linuxassassin.com/2007/06/16/disable-directory-listing-on-apache/)

---

### Post by ukripper on 2007-09-21
Taken from  [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server)

"[I]Apache will display Web page files as long as they are world readable. You have to make sure you make all the files and subdirectories in your DocumentRoot have the correct permissions.

It is a good idea to have the files owned by a nonprivileged user so that Web developers can update the files using FTP or SCP without requiring the root password.

 [/I]"

---

### Post by veinless on 2007-09-21
Hello again,

I probably didn't make myself clear.  But its ok because I found the solution. I just had to replace "Indexes" with "-Indexes" in the configuration file of the website (/etc/apache2/sites-available/default) and restart!

Thanks for your time

---

### Post by ukripper on 2007-09-21
Glad it's working now!! :)

---

