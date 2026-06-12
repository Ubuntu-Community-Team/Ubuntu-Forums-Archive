---
title: "Require network help asap"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by DaveGiant on 2008-02-21
I have posted this in the networking forum and have received no replies what so ever. 

The thread can be found here.
[http://ubuntuforums.org/showthread.php?t=702516](http://ubuntuforums.org/showthread.php?t=702516)

I attempted to do what was said in the broadcom sticky and have now lost wireless functionality all together. I am no longer concerned about connecting to secured networks. What is critical is that I restore the functionality I have lost.

Can someone tell me how I can remove what was installed by the package in the sticky so that my restricted driver will be able to function again.

This is now critical as I am leaving for a wireless environment tonight and my laptop will be left unable to connect to anything if this is not fixed before then.

---

### Post by dje on 2008-02-21
1. Are you using gutsy?
2. Was it [this sticky]("http://ubuntuforums.org/showthread.php?t=405990")?

> This method is no longer supported and could possibly cause more problems than it fixes. I'm going to leave it up, but just remember - use it at your own risk.

> Also be advised that the offline installer will not work with Gutsy Gibbon. The online installer may or may not, I haven't tried it.

A note for anyone wanting to install these drivers: If you are using Gutsy Gibbon, it is recommended that you either use the restricted drivers manager to install the firmware or install ndiswrapper yourself. This installation method has already outlived its intended life cycle.

You could try [this guide]("http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html"), that worked for me and my Inspiron 1501 which has a broadcom 1390 wireless card. please post the output of:

```
lspci
```

dje

---

