---
title: "Webcam woes with Skype 2.0 BETA"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2008-03-01
I have a PC-Line 300K webcam (0.3MP); cheap, I know, but it works. The problem is that Skype can't see it, Camorama can't see it and Ubuntu can't see it. I don't know what driver it needs. Does anyone know what to do?

Thanks :D

---

### Post by spiderbatdad on 2008-03-01
Most webcams can be made to work: [http://www.linux.com/base/ldp/howto/Webcam-HOWTO/hardware.html](http://www.linux.com/base/ldp/howto/Webcam-HOWTO/hardware.html)

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by eoghanmurray on 2008-03-01
I'll try that - thanks.

---

### Post by eoghanmurray on 2008-03-01
Nope - no luck :(

---

### Post by eoghanmurray on 2008-03-02
anything?
Thanks :D

---

### Post by TeoBigusGeekus on 2008-03-02
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by spiderbatdad on 2008-03-02
Have you looked into  easycam? [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by eoghanmurray on 2008-03-02
I've tried Easycam - it can;t find the camera. I'll look at that skypewebcams thing - thanks.

---

### Post by eoghanmurray on 2008-03-02
Nope - can't get it to work :(

If anyone knows of a fix, i'd appreciate.
Webcam is **PC-Line 300K**.

Thanks :D

---

### Post by eoghanmurray on 2008-03-03
anything at all?
Thanks :D

---

### Post by Technoviking on 2008-03-03
Is it a USB cam,  type
```
lsusb
```
And post what you see.

---

### Post by eoghanmurray on 2008-03-04
```
eoghan@ubuntu-feisty-desktop:~$ lsusb
Bus 005 Device 002: ID 093a:262a Pixart Imaging, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 056a:0062 Wacom Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04a9:108d Canon, Inc. 
Bus 002 Device 003: ID 04f3:0212 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. 
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 04e8:5055 Samsung Electronics Co., Ltd 
Bus 001 Device 005: ID 13b1:000d Linksys 
```

Thats the output of ```
lsusb
```

I guess "**Bus 005 Device 002: ID 093a:262a Pixart Imaging, Inc. **" is my webcam?

---

### Post by eoghanmurray on 2008-03-05
bump :D

---

