---
title: "video resolution is  800x600  since upgrade 7.01"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by probachlor on 2008-01-18
Help!!

I am very new to ubuntu and quite intimidated by the conventions and and concepts.

I have created a linux exclusive machine to learn on.  I have been involved with computers from the days when you had to be able to read to use them.  (GUI, please!)

My video resolution (which was fine) has been reduced to 800x600 since upgrading to GIBON 7.xx

Video card is mother board mounted and is detected as VESA generic.  

Please note that it resolution was 1200+ before the upgrade.

My name is Freeman.  I am in Baltimore.  My emai address is [email]Probachlor@Gmail.com[/email].

Thank you for any help you may offer.

---

### Post by stump138 on 2008-01-18
First thing I would do is make a copy of your xorg file :) open a terminal and:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then you can try and reconfigure X
```
sudo dpkg-reconfigure xserver-xorg
```

If anything goes wrong, you can simply put the xorg.conf you have now back in place and be back at 800x600 while we work at other solutions

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

