---
title: "Screen resolution"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by nilesh892003 on 2007-01-31
hello friends 
i had recently installed ubuntu dapper drake in my dell gx110 ,
my pc configuration is 256 ram ,1 ghz motherboard ,
but my deault screen solution is 640*480,
i want to switch to 800*600 but it dosn`t have any other option plz suggest me how to set the screen in my pc,

---

### Post by taurus on 2007-01-31
Open a terminal, Applications -> Accessories -> Terminal, and reconfigure your X with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by nilesh892003 on 2007-01-31
sudo dpkg-reconfigure -phigh xserver-xorg

the above method shows server-xorg postinst warning: overwriting possibly-customised configuration   file; backup in /etc/X11/xorg.conf.20070201012639
 plz tell me in detail in am new in ubuntu

---

### Post by taurus on 2007-01-31
Well, you can make a backup of your /etc/X11/xorg.conf before you run that command.  The message is telling you that it will backup your original copy to xorg.conf.20070201012639 in case you need to use it later.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
And since it's a Dell, I bet you it has an Intel onboard graphic controller!

---

### Post by linux_believer on 2007-01-31
I found that to be an issue myself. In 6.06 you have the option to change your resolution. In 6.10 you are basically stuck with 1 or 2 resolution options

---

