---
title: "Need to completely re-install grub.. NO CD."
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-09-11
I don't have a CD-drive.
I want to reinstall grub because all of the files in /boot/grub/ are probably the problem, and "reinstalling" through apt-get doesn't even touch these files.. I need grub completely reinstalled. 

This shouldn't be that hard.

But the main grub resources (web pages) that i have read are way too long.. I just don't have the time.

i have tried the set of commands..
sudo grub..
find .. 
root ..
setup.

It doesn't work.

Please is there a simple solution?

---

### Post by bodhi.zazen on 2007-09-11
you could delete /boot/grub (careful do not delete /boot)

Then 

sudo apt-get remove --purge grub

sudo apt-get install grub

sudo grub

grub > root (hdx,y)

grub >setup (hd0)

grub > quit

_Note_ the grub > represents the grub prompt, not part of the command to enter ;)

All you need to know is your root partition in grub speak

First HD =0
First partition =0

so /dev/xda1 = (hd0,0)

and on ...

---

### Post by systemintheglitch on 2007-09-11
> **bodhi.zazen said:**
> you could delete /boot/grub (careful do not delete /boot)

Then 

sudo apt-get remove --purge grub

sudo apt-get install grub

sudo grub

grub > root (hdx,y)

grub >setup (hd0)

grub > quit

_Note_ the grub > represents the grub prompt, not part of the command to enter ;)

All you need to know is your root partition in grub speak

First HD =0
First partition =0

so /dev/xda1 = (hd0,0)

and on ...

I lost you at that last part.

"All you need to know is your root partition in grub speak

First HD =0
First partition =0

so /dev/xda1 = (hd0,0)
"

Can you help me find my root partition.. ?

I don't get the relation between hdx,y and sda2, etc..

---

### Post by bodhi.zazen on 2007-09-11
If your ubuntu root partition is /dev/sda2, this translates into (hd0,1) in grub speak :twisted:

See if this helps : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

