---
title: "Web cam"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by maliboy1 on 2008-02-17
Ok I've done searching and experimentation but I can't get my webcam to work. I have camorama installed, I'm using a nexxtech webcam. when I launch camorama all I get is error could not connect with video device /dev/video0 please check connection. It is connected and I've tried unplugging the cam and plugging back in and that doen't work. Help!

Thanks
Randy

---

### Post by linuxwizard on 2008-02-17
Post results of the command >> lsusb.  Have you tried to install any drivers for the cam ?

---

### Post by maliboy1 on 2008-02-17
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 093a:2600 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  

no I havent tried to install drivers

---

### Post by linuxwizard on 2008-02-17
Have you tried using Ekiga to see if webcam works/detected ? You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

On this page shows your wecam as >>Typhoon  236    0x093a  0x2600  Typhon
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by maliboy1 on 2008-02-17
I tried to install the driver but had no luck. I also tried to configure with Ekiga and played with all of the settings and had no luck.

---

### Post by linuxwizard on 2008-02-17
Are you getting any error messages ? When you open Ekiga along the left side there should be 6 icons click on the 4th icon down. Anything ?

---

### Post by maliboy1 on 2008-02-17
Nothing happens I just get an orange ball moving around the screen and tells me to stand by. at the bottom it says registration unacceptable.

---

### Post by linuxwizard on 2008-02-17
When you first opened Ekiga did you go through the 10 step Configuration druid that will help you to correctly configure Ekiga ? Or did you skip it ? If you skipped it you can open Ekiga > Edit > Configuration druid. If that doesn't work, than the only thing I can think of is you are going to have to install new driver which could be a newer version than already installed.

---

### Post by maliboy1 on 2008-02-19
I guess the only thing I can do is install a newer driver, I've tried everything else.
The only problem is I don't know how to install another driver, so I need help in that department.

---

