---
title: "Getting Webcams to Work"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by drndrw on 2008-01-06
Hey guys. I am trying to get my webcam to work on my Linux box, mainly for use on instant messaging (Like PIdgin. Would a webcam work on Pidgin?). I've already read [this]("http://ubuntuforums.org/showthread.php?t=651919") post, and I've installed Canorama, but I got this error:

> Could not connect to video device (/dev/video0). Please check connection.

I am using a old Digital Blue camera thing, which has worked for me as a webcam in the past. DOes anyone know what I can do? And if I cannot use it as a webcam on PIdgin, what other IM clients can I use? Does AMSN work? Thanks.

---

### Post by icheyne on 2008-01-06
You need to load the drivers - IF your webcam is supported.
AMSN, Ekiga, Skype and Kopete all work.

This should put you on the right path.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by philinux on 2008-01-06
> **drndrw said:**
> Hey guys. I am trying to get my webcam to work on my Linux box, mainly for use on instant messaging (Like PIdgin. Would a webcam work on Pidgin?). I've already read [this]("http://ubuntuforums.org/showthread.php?t=651919") post, and I've installed Canorama, but I got this error:



I am using a old Digital Blue camera thing, which has worked for me as a webcam in the past. DOes anyone know what I can do? And if I cannot use it as a webcam on PIdgin, what other IM clients can I use? Does AMSN work? Thanks.

Post the output of 

[FONT="Times New Roman"]```
lsusb
```[/FONT]

---

### Post by drndrw on 2008-01-06
This is what I got:

```
Bus 003 Device 002: ID 0471:0831 Philips 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 8086:0510 Intel Corp. Digital Movie Creator
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

---

