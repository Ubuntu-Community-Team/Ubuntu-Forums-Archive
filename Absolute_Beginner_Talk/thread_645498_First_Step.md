---
title: "First Step"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by rodney ford on 2007-12-20
How do I reset the Username & Password as I cant even open the  program anymore. I have tried everyway possible to spell my name, with capital letters, without, with a space between the 2 names, without, all in lowercase,  all in higher case.   HELP

---

### Post by forestpixie on 2007-12-20
[https://help.ubuntu.com/community/LostPassword?highlight=(password](https://help.ubuntu.com/community/LostPassword?highlight=(password))

have a look at that

---

### Post by forestpixie on 2007-12-20
further - thanks to frank05 on an old thread
> 
if you don't know your user name, you can look for it by typing
cat /etc/passwd | grep [some-or-all-of-your-real-name]

change the [text] bit to start with you username

eg - I did cat /etc/passwd |grep k*

passwd [username] - change to the new password

got me - then you can do your passwd from the earlier reference

---

