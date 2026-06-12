---
title: "Resolution problem"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2006-12-23
I've just installed Edgy Eft and all is mostly OK exept resolution is maxed at 800 x 600.  I have AMD 64x2 4200 with ATI RADEON EXPRESS 200.  Monitor runs at 1280 x 1064 in Windows.

Suggestions?

Tnx,

Joe

---

### Post by taurus on 2006-12-23
You need to install a driver for your ATI card before you can get a higher resolution...

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by jgf621 on 2006-12-24
Thank you.  I've tried following instructions at site you referred to.  (Remember I'm new at this.)  When I try to add repositories as directed using terminal program, I get BASH:  DEB command not found.

What am I doing wrong?

Joe](*,)

---

### Post by taurus on 2006-12-24
You have to open a text editor and add that line in there.  You can edit your /etc/apt/sources.list by

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Now, add that line from the link to the end of it.  Save it and exit.  Continue with the instructions...

---

### Post by impakt on 2006-12-24
Try

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the prompts and answer the questions correctly. 

You may also want to read this. 

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by MkfIbK7a on 2006-12-24
Try

> Code:

sudo dpkg-reconfigure xserver-xorg

Follow the prompts and answer the questions correctly.

You may also want to read this. 

yes this should solve the problem you can set the resolutions the monitor is capable of in here

---

### Post by jgf621 on 2006-12-24
To all that tried to help, thanks but...

Trying  "sudo dpkg-reconfigure xserver-xorg" generates following message

xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized

I managed to alter file gksudo gedit /etc/apt/sources.list  and then following command "sudo aticonfig --initial"  gives me this

sudo: aticonfig: command not found

Joe

](*,)

---

