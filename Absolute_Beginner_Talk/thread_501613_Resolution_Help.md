---
title: "Resolution Help?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by sanzy on 2007-07-15
Hey i have installed Ubuntu 7.04 and it only allows me to choose the following resolutions :

1024 x 768
800 x 600
640 x 480

Now my native resolution on my laptop = 1280 x 800 yet i can not choose this :(

I have the following graphics if this makes a differnce : 128MB Intel UMA Integrated graphcis

Could anybody help my get my native resolution as i am a total n00b and have only tryed ubuntu 5mins ago.

---

### Post by w4ett on 2007-07-15
From the terminal type:

sudo dpkg-reconfigure -phigh xerver-xorg

This will give you a graphical interface to change your resolution and refresh rates.

---

### Post by freebird54 on 2007-07-15
Basically your monitor's capabilities were not quite correctly determined.  If you open an Applications->Accessories->Terminal and enter

```
sudo dpkg-reconfigure xserver-xorg
```

and follow along on this [guide](http://users.bigpond.net.au/hermanzone/p7.html), you will get the rest of the options you need.

---

