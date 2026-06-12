---
title: "Updates and installlations wont work"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Kedster on 2007-09-14
i try to install updates and stuff like Updates and the time syc program (nts i think) and other programs from add and remove and  this comes up 
E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1

please help

---

### Post by Daveth on 2007-09-15
the error relates to a failure of the fw-cutter package from Synaptic which you tried to download.

You are not alone

[http://ubuntuforums.org/showthread.php?t=525386](http://ubuntuforums.org/showthread.php?t=525386)

but I do not know how to resolve the failure. Anyone?

---

### Post by Kedster on 2007-09-15
umm i dont think i istalled that but i really want to (need to) fix it  ant one got any ideas




Ps: is that pakge part of NDISwraper

---

### Post by st33med on 2007-09-15
No, fw-cutter is completely different than ndiswrapper in how it handles drivers. I have heard it disconnects often with Broadcom cards.

But that's just me.

---

### Post by Kedster on 2007-09-16
please i need to install things with out this problem

---

### Post by Kedster on 2007-09-16
bump

---

### Post by Kedster on 2007-09-16
pleaase

---

### Post by st33med on 2007-09-16
Do you know your wireless card? if not:

```
lspci
```
And post here. I bet we could find an alternative installation through ndiswrapper.

---

### Post by forestpixie on 2007-09-16
to get rid of the fw-cutter

try this

```
sudo apt-get remove --purge bcm43xx-fwcutter
```

---

### Post by Kedster on 2007-09-16
what was the bcm43xx-fwcutter part of or for

---

### Post by forestpixie on 2007-09-16
synaptic says this 

> Utility for extracting Broadcom 43xx firmware

other than that I have no idea - but you'll get nowhere until you deal with this, at some point you must have tried to install it 

> E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1

if you need it you can try reinstalling it 

```
sudo aptitude reinstall bcm43xx-fwcutter
```

do the ```
lspci
``` as well

---

