---
title: "Cannot boot"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Corvair on 2007-12-11
Hello everyone,

I have screwed up my system and I cannot boot anymore.

Dual boot system, 7.10, kernel 2.6.22-14 and Windows XP

Laptop Gateway MX6453.

Windows is ok, this is where I am writing from.

I tried to hook up my display to another monitor, LG 226WTQ, and could not configure it to display correctly so I took it out. When going back to my laptop display it did not display correctly and I was requested to select gnome or x display. I selected x and that has caused the problem, I think.

When booting up from the generic kernel 2.6.22-14,  I get the following: Laptop login: (137.191147)
bcm43xx:error:Microcode "bcm43xx_microcode 5.fw" not available or load failed,     and keeps on giving this type of message.

When trying from recovery mode I get this: Setting up console font and keymap...
Warning: unknown X keysym  "0xfe11"
Root@claude-laptop:~#

I don't know what to do next.
I have to disconnect the battery in order to get out of that situation .
I am in X display instead of Gnome, or something like that.

Does anyone understand what I am trying to explain?
Please help if you can.
Thanks for your attention.

---

### Post by Dr Small on 2007-12-11
When booting from recovery mode, try running this command:
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Corvair on 2007-12-11
Thanks for the quick reply, I will try it out

---

### Post by Corvair on 2007-12-11
Dr Small,

This is what I get back

Package 'xserver-org' is not installed and no info is available
Use dpkg --info (= dpkg-deb --info) to examine archive files and dpkg --content (= dpkg -deb --content) to list their content.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed.
root@claude.....

can you help further?

---

### Post by spiderbatdad on 2007-12-11
try:
```
sudo dpkg-reconfigure -a
```this may take some time
or:
```
sudo dpkg --configure -a
```

---

### Post by Corvair on 2007-12-11
thanks spiderbatdad, will try that

---

### Post by oeolycus on 2007-12-11
Why not just:

```
sudo aptitude install xorg
```

since dpkg reports that the xserver isn't installed?

---

### Post by spiderbatdad on 2007-12-11
well thats a good point. maybe xorg got wiped.
```
sudo apt-get install xorg xserver-xorg xserver-xorg-core
```

---

### Post by Corvair on 2007-12-11
Thanks for the new suggestions because I tried reconfiguring dpkg and I still have the microcode errors.
I will let you know what happens

---

### Post by Corvair on 2007-12-11
Hello again,

I tried installing xorg and I got or an answer : no new package installed or removed, ect, so that does not seem to be the problem.

I still get the bcm43xx:error:microcode "bcm43xx-microcode 5.fw" not available or load failed

---

### Post by Corvair on 2007-12-12
To everyone who helped, thanks a lot.
I am back in the saddle again.

To Dr Small in particular, I have tried your suggestion again,  after trying out the other
suggestions and this time I got the following result. After I typed exit and the gnome window opened
up and I signed in without any problem.

sudo dpkg -Reconfigure -phigh xserver-xorg
GTK-warning **:cannot open display: at/usr/share/per15/Debconf/FrontEnd/Gnome.pm line54.
debconf:unable to initialize frontend: Gnome.
debconf: (DISPLAY) problem?
debconf:falling back to frontend: Dialog
xserver-xorg postint warning: overwriting possibly-customised configuration file;
backup in )etc/X11/xorg.conf. 20071211232143

I copied this by hand so there may be errors of copy.
This may help you to understand what happened.

Thanks again to everyone
:)

---

