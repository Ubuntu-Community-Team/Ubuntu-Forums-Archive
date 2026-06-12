---
title: "need to de-activate/unistall/remove somthing"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-04-25
I need to make the OS stop trying to use my INTERNAL wireless card.  It is a known ubuntu problem

I keep getting this error 
bcm43xx:error:microcdode "bcm43xx_microcode5.fw" not available on load failed
I have lost my desktop trying to fix a video card problem ([http://ubuntuforums.org/showthread.php?p=2531700#post2531700](http://ubuntuforums.org/showthread.php?p=2531700#post2531700)) and i can't get my desktop problem fixed b/c ubuntu gets hung up on this error, I can't even run the puregnome command to remove the kde desktop because this error won't stop

Please help, I am very frustrated right now.

---

### Post by got_nix on 2007-04-25
blacklist the bcm43xx drivers..... it wont try loading it.. I think that might fix it.

sudo vi /etc/modprobe.d/blacklist

and add the line blacklist bcm43xx.. if its already there and commented out.. uncomment it.

---

### Post by rich.bradshaw on 2007-04-25
you might want to replace vi with nano if you don't know vi...

---

### Post by eentonig on 2007-04-25
or gedit if you prefer working GUI style

---

### Post by mkjarema on 2007-04-25
I am getting 
"cannot open display"
when i run the gedit commands

---

### Post by mkjarema on 2007-04-25
if i boot up with the live cd will the changes i make there remain when i reboot via the HD?

---

### Post by Gina on 2007-04-25
If you edit the HD file by first mounting the partition and then editing... yes.  But editing the live CD system (which resides in memory)  it won't be kept.

---

### Post by mkjarema on 2007-04-25
> **Gina said:**
> If you edit the HD file by first mounting the partition and then editing... yes.  But editing the live CD system (which resides in memory)  it won't be kept.

Please excuse my ignorance, could you please walk me through how to do this?  Or am I better off "re loading" feisty?  I would rather not do that, however I know so little I feel that is my only option.

---

### Post by mkjarema on 2007-04-26
re installed feisty, now to just fix the resolution....thanks for your help

---

