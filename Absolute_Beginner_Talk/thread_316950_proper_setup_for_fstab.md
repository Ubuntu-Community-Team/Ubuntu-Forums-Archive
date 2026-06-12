---
title: "proper setup for fstab?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by tmeier on 2006-12-11
I am running Edgy on an IBM X41T tablet PC in a public school environment.  We have a Windows 2003 Server for File storage and a Mac OS X web server with windows sharing turned on.  I can manually mount to these servers with the following command : 

sudo mount -t cifs //10.1.0.2/District\ JMC /mnt/jmc -o user=xxx,password=xxxxxx,domain=xxxx

and this works fine.  I would like to automount this and a few other folders with entries in fstab.  I have tried some things found on this forum and others but keep running into errors.  The latest one is an error 11 = resource unavailable.  any help here is appreciated.

---

### Post by adaptr on 2006-12-11
What have you tried ?
The fstab format is slightly different from the mount format.

---

### Post by tmeier on 2006-12-12
Most recently I tried this from a howto for cifs on the ubuntu forums :

```
 //10.1.0.2/Crisis /mnt/safety cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_ mode=0777 0 0
```

This is what gave me the error 11 = resource unavailable.
I have also tried it without the .smbcrdentials and just inserted username=xxx,password=xxx,domain=xxx.

---

### Post by xyz on 2006-12-12
How about this great HowTo:
[How to fstab]("http://www.ubuntuforums.org/showthread.php?t=283131&highlight=fstab+howto")

---

### Post by tmeier on 2006-12-13
The how to helped.  Thanks.  I also had to look up how to deal with a space in the sharename in the fstab.  It works something like this in case others are wondering:

//10.1.0.2/District\040JMC

the \040 is apparently a place holder for the space and makes it work in fstab.  You guys are great in this community, wouldn't want to be on any other distribution of Linux.

---

### Post by xyz on 2006-12-13
That's nice to hear...and of course big thanks to **bodhi.zazen** for the HowTo...(that's a 'light' word for it).

---

### Post by bodhi.zazen on 2006-12-13
:redface: Thanks xyz

xpod calls 'em "how-longs" :roll:

---

### Post by xyz on 2006-12-14
Can't wait for the next "how-long"! ;)

---

