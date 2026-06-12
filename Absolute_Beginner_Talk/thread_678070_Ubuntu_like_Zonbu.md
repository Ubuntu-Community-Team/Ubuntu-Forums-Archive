---
title: "Ubuntu like Zonbu"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Rhonie on 2008-01-25
I have my own web space on the internet and was wondering if there is a way that I can find a program that can be used with Ubuntu that will use my web space like they are doing with [www.zonbu.com](www.zonbu.com).  I am looking for an easy to load application/program that works like xdrive.

---

### Post by Het Irv on 2008-01-25
Just for clarification, you want to be able to store data in a drive on a web server somewhere, right?  How would this program connect to the drive?

---

### Post by ugm6hr on 2008-01-25
> **Rhonie said:**
> I have my own web space on the internet and was wondering if there is a way that I can find a program that can be used with Ubuntu that will use my web space like they are doing with [www.zonbu.com](www.zonbu.com).  I am looking for an easy to load application/program that works like xdrive.

The program would most likely have to be provided by your webspace provider.  Given that Linux support for such things is generally poor - I suspect you are going to be out of luck.

Linux Mint now offers a paid-for data storage option (I think), in a similar vein to Zonbu.

---

### Post by Rhonie on 2008-01-26
I want to do it over the internet to my own web space.  In other words just to set up somekind of ftp program under a folder.  So what ever I save into this folder goes directly to my web host and saves it as a file name.  Seems to me that someone should have already written a program to do this.

---

### Post by gvartser on 2008-01-26
maby wput is the thing for you

Install:
```
sudo apt-get install wput
```

Usage:
```
wput <filename> ftp://username:password@<remote file address>
```

Schedule, use crontab.

/G

---

### Post by Rhonie on 2008-01-26
I'll give it a try.
Thank you,

---

### Post by gvartser on 2008-01-26
cool, post a msg if it worked for you.. 

/g

---

