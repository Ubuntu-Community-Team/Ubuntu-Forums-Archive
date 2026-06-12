---
title: "[SOLVED] OK I just installed linux"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by HenvY on 2008-02-14
and I need to add drivers for my wireless usb adapater but I don't know how. The website has instructions but I don't understand anything it says. Can you translate it for me?
[http://safecom.cn/code/product/WLAN/SWMULZ-5400/manual/SWMULZ-5400-Linux-UserGuide.pdf](http://safecom.cn/code/product/WLAN/SWMULZ-5400/manual/SWMULZ-5400-Linux-UserGuide.pdf)

---

### Post by randy78 on 2008-02-14
> **HenvY said:**
> and I need to add drivers for my wireless usb adapater but I don't know how. The website has instructions but I don't understand anything it says. Can you translate it for me?
[http://safecom.cn/code/product/WLAN/SWMULZ-5400/manual/SWMULZ-5400-Linux-UserGuide.pdf](http://safecom.cn/code/product/WLAN/SWMULZ-5400/manual/SWMULZ-5400-Linux-UserGuide.pdf)

How about posting the make of the card and the drivers you are trying to install?

---

### Post by stevejesus on 2008-02-14
First, see if this is supported in Ubuntu's restricted modules.

```
sudo apt-get install linux-restricted-modules
```

If you are using gnome, I know that if it works, it will be obvious...  There is a network manager in the panel, and from there it will either start off in roaming made and try to connect to something, or you can click on it and choose a network.  GOOD LUCK!

---

### Post by KCormier on 2008-02-14
Howdy.  I'm not too familiar with the command line stuff but assuming you're running 7.10, have you tried the restricted driver manager?  do system -> admin -> package sources or something like that (not on a linux machine at the moment).  Make sure you check off the third check box (for restricted/3'rd party drivers or something similar).  Then system -> admin -> restricted driver manager....see if that has the drivers automatically for you.  If not, someone w/ more experience can help you w/ those directions...

---

### Post by jonnywombat on 2008-02-14
[https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211](https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211)

According to link above if your using gutsy then it will work straight out the box

---

### Post by HenvY on 2008-02-14
Guys, i'm so dumb, I didn't need a driver as you said. Thanks for your help. :D

---

### Post by jan quark on 2008-02-14
would be nice if you mark this thread as solved

thank you

---

