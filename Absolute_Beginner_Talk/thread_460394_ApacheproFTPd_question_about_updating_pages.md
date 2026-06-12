---
title: "Apache/proFTPd question about updating pages"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Nathan_Scott_Grey on 2007-05-31
I have set up apache to run on my Ubuntu Feisty server. I have my default directory set. I also have a proFTPd directory set to update to a user's directory. How do I allow FTP only to the directory that is my default in apache for uploading files/pics/and whatnot so I can upload directly to a place that lets web users see them?

---

### Post by pbw on 2007-05-31
It sounds like you answered your own question

> 
I have my default directory set. I also have a proFTPd directory set to update to a user's directory.

Just change that to point to your public html rather than a user's directory.. 

Or you can jail a certain user to your web url, and have the others login going to their home as you already setup, do this for example like so:

```
DefaultRoot /var/www/ pbw
```
Replacing pbw with your username of course, and restart proftpd.

---

### Post by Nathan_Scott_Grey on 2007-06-04
It worked perfectly, thank you.

---

