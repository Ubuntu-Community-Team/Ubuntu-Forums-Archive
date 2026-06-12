---
title: "No WiFi connection"
date: 2008-06-29
forum: Apple Hardware Users
---

### Post by ianoreo on 2008-06-29
I just installed Ubuntu but I've noticed that I have no connection to my WiFi. I have a MacBook and I tried the sudo apt-get install build-essential autoconf automake command thing but it says couldnt find the package.

What do I do?


EDIT: I also don't see any sort of WiFi icon in the Wired network manager. Nor is there a driver listed under the Hardware Drivers list.

---

### Post by cyberdork33 on 2008-06-29
> **ianoreo said:**
> I just installed Ubuntu but I've noticed that I have no connection to my WiFi. I have a MacBook and I tried the sudo apt-get install build-essential autoconf automake command thing but it says couldnt find the package.

What do I do?


EDIT: I also don't see any sort of WiFi icon in the Wired network manager. Nor is there a driver listed under the Hardware Drivers list.
because you haven't installed any drivers, your wifi will not work. do not install packages that do not work. but continue to follow the wiki page.

---

### Post by ianoreo on 2008-06-29
I've also just noticed that I keep seeing a lot of errors? I have a "-" sign in the top bar. When I do what it says (open package manager), I get an error: 
"E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem.
E: _cache->open() failed, please report.

I'm getting really confused....because when I try that command it says I need superuser privileges?

---

### Post by ianoreo on 2008-06-29
Okay I just managed to install ndiswrapper. After executing the first command (sudo ndiswrapper -i bcmwl5.inf)


 on the list, I got this:

couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.


What should I do?

---

### Post by ianoreo on 2008-06-30
Please I really want to get this Wifi working. I don't understand this error. I don't know how to fix it either.

---

### Post by cyberdork33 on 2008-06-30
you are mixing how tos for two different hardware types. What Mac version do you have?

An update was interrupted it seems and has messed up the apt database. You need to run the command stated. If you need to have "superuser" privs, then put a 'sudo' before the command... (It literally means, '_s_uper_u_ser _do_')

---

### Post by ianoreo on 2008-06-30
Yeah I feel dumb I got the error fixed by using sudo. But I am still stuck on the ndiswrapper error. I don't know what type of Macbook I have is there a way to find out?

---

### Post by cyberdork33 on 2008-06-30
```
sudo dmidecode| grep Product
```

Depending on the version number returned, you need to follow the appropriate guide:
MacBook1,1 and MacBook2,1
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

MacBook3,1 and MacBook4,1
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

