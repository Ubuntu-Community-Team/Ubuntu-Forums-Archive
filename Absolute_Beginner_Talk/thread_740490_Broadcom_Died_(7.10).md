---
title: "Broadcom Died (7.10)"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by dr.silly on 2008-03-30
I have been working happily with a Broadcom Wireless card for the past few days. Then, suddenly it seemed to die.

I first got it to work by installing the drivers through Restricted Drivers Manager.

Now no networks show up and when I try and connect to it as "Other Network" the password never goes through.

I've used bcm43xx-fwcutter a dozen times, too.

---

### Post by uberlube on 2008-03-30
Use the howto in my sig :)

---

### Post by dr.silly on 2008-03-31
That didn't work for me, or at least i don't think so. It shows up in iwconfig fine, but not in NM.

---

### Post by dicecca112 on 2008-03-31
I've noticed that the firmware always dies after a while, the only way I have gotten Broadcom to work consistently was via ndiswrapper

---

### Post by dr.silly on 2008-03-31
that's funny... still i used the ndiswrapper way from uberlube's howto

---

### Post by mattman059 on 2008-03-31
I posted a how-to for the bcm-43xx a few days ago, if you search the forums for my username you should find it. I dont have the link at the moment.


EDIT:

 Here you go
[http://ubuntuforums.org/showthread.php?t=734256]("http://ubuntuforums.org/showthread.php?t=734256")

---

### Post by dr.silly on 2008-03-31
I'm beginning to think that the ndiswrapper driver is installed correctly because lshw -C network it shows up with the driver=ndiswrapper+bcmwl5

---

### Post by dr.silly on 2008-04-01
bump

---

