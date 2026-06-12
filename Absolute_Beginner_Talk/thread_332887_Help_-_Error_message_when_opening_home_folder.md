---
title: "Help - Error message when opening home folder"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by cingh on 2007-01-06
hi whenver i try to open the home folder i get this error message 

[http://s1.upload.sc/request/e3b9927813a0cbcebe3c0176223d501e/owner](http://s1.upload.sc/request/e3b9927813a0cbcebe3c0176223d501e/owner)

---

### Post by cingh on 2007-01-06
hi whenver i try to open the home folder i get this error message 


[http://s1.upload.sc/request/e3b9927813a0cbcebe3c0176223d501e/owner](http://s1.upload.sc/request/e3b9927813a0cbcebe3c0176223d501e/owner)

thanks 
Cingh

---

### Post by vijayanand_sodadasi on 2007-01-06
Hi,
The link you gave doesn't seem to work.

---

### Post by Ripfox on 2007-01-06
That link is expired?

---

### Post by cingh on 2007-01-06
lol no ijust typed up the direct link 

Cingh

---

### Post by tbroderick on 2007-01-06
> **cingh said:**
> hi whenver i try to open the home folder i get this error message 

[http://s1.upload.sc/request/e3b9927813a0cbcebe3c0176223d501e/owner](http://s1.upload.sc/request/e3b9927813a0cbcebe3c0176223d501e/owner)

What is that? Can you just post the error message?

---

### Post by Bachstelze on 2007-01-06
a .bin file for an error message, that looks very much like something nasty...

---

### Post by MasterPatricko on 2007-01-06
Looks like you dont have the required permissions. Check the permissions of /home/cingh - it should belong to you and have read, write, execute access (for you) and read, execute for others. It should not belong to root. Opening the file manager as root (sudo nautilus) and fixing the permissions or a simple chmod/chown (with a -R for recursive) will probably solve the problem. If you need detailed steps post and i'll be happy to help.

---

### Post by cingh on 2007-01-06
> **MasterPatricko said:**
> Looks like you dont have the required permissions. Check the permissions of /home/cingh - it should belong to you and have read, write, execute access (for you) and read, execute for others. It should not belong to root. Opening the file manager as root (sudo nautilus) and fixing the permissions or a simple chmod/chown (with a -R for recursive) will probably solve the problem. If you need detailed steps post and i'll be happy to help.

if you could that would be great thanks 

Cingh

---

