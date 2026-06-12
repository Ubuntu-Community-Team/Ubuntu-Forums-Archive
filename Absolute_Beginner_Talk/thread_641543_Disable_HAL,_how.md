---
title: "Disable HAL, how?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2007-12-15
How do I disable HAL so it don't get loaded when i start the computer?

Reason is that HAL don't support my WLAN so i need to use ndiswrapper to get it working but i think that HAL will cause a confilct.

[[img=http://img228.imageshack.us/img228/7710/halng1.th.png]](http://img228.imageshack.us/my.php?image=halng1.png)

---

### Post by SpinningAround on 2007-12-17
Someone?

I want to disabel it so it show a red instead of green

---

### Post by nowshining on 2007-12-17
try looking in

system - preferences - session

click on the one u'd like to disable then click remove and restart :) if not then let me know.. Hal also mounts usb drives if u have one example a pen drive.

---

### Post by SpinningAround on 2007-12-18
Didn't seem to work, i want to disabel it so it wont be loaded. As it's now I think it is still loaded since it is a restricted modul or something.

Possible that it need to be blacklisted also?

---

### Post by SpinningAround on 2007-12-18
Can this be correct`? [http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)
It was for ubuntu 7.04 does it still work?

---

### Post by psusi on 2007-12-18
What makes you want to disable HAL?  For the most part it just maintains a list of what hardware you have; it has nothing to do with lan drivers.

Edit:

Nevermind... different HAL.

---

### Post by nowshining on 2007-12-18
> **SpinningAround said:**
> Can this be correct`? [http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)
It was for ubuntu 7.04 does it still work?
u can try but if u'd like to disable it then do this in terminal

sudo apt-get install sysv-rc-conf

then once installed

(reboot once unce done, remember where the astricks and what they are under as i forgot exactly which run level ubuntu boots off of, i think it's level 3 so leave the others un-astricked, q on ur keyboard to quit) Also runlevel 0 is for halt and 6 is for reboot.

sudo sysv-rc-conf

some links
Debian and Ubuntu runlevels (ubuntu is based off of debian by the way)
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

An intro of runlevels
[http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)

---

