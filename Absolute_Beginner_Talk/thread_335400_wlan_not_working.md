---
title: "wlan not working"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by EAkrish on 2007-01-10
I am pretty sure someone has answered this, however i have done everything that prople say to do. i have a dell inspiron e1405, it has the 1390 chipset in it. i uploaded the diswrapper **** with no luck! please help me.....

---

### Post by EAkrish on 2007-01-10
no help?????

---

### Post by sailor2001 on 2007-01-10
> **EAkrish said:**
> I am pretty sure someone has answered this, however i have done everything that prople say to do. i have a dell inspiron e1405, it has the 1390 chipset in it. i uploaded the diswrapper **** with no luck! please help me.....

ndiswrapper.............check dark ox's tutorial   [http://ubuntuforums.org/showthread.php?t=198521](http://ubuntuforums.org/showthread.php?t=198521)

---

### Post by EAkrish on 2007-01-10
ok this did not work, it says i have the wrong driver installed. please help

---

### Post by EAkrish on 2007-01-10
this is from terminal

eric@eric-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
bcmwl5a         driver installed

---

### Post by EAkrish on 2007-01-10
help me.....

---

### Post by Papa-san on 2007-01-10
Hi,

I had a lot of trouble with mine, so I added some links in my signature line.

The first thing you need to do is get the right driver. Also, which Ubuntu version are you using? Dapper LTS or edgy?

I'll see if I can help you walk through this! [:-)]

---

### Post by EAkrish on 2007-01-10
i got edgy

---

### Post by EAkrish on 2007-01-10
help

---

### Post by Papa-san on 2007-01-11
OK, did you try the 'ndiswrapper help' link in my signature?
You should follow it, step by step, and report thr output of the commands if and when you fail to get it set up. 

I don't want you to get too discouraged, it sounds like you have it nailed down pretty well, except for which driver you have installed. That tutorial goes through the process of discovering what you need to know to get the right driver. You need to get the actual wireless card name and its revision number.

For example, mine is a: 'Broadcom 4306 (Rev 03)'

Start by posting the output of:
```
sudo lshw -C network
```

then:```
sudo lspci -n
```
This will give you several different lines of information which you will compare to drivers you will browse through here:  [http://ndiswrapper.sourceforge.net/mediawiki/index.php/list](http://ndiswrapper.sourceforge.net/mediawiki/index.php/list)

---

