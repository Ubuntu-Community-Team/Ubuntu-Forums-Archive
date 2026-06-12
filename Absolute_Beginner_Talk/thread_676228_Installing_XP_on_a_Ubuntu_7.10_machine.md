---
title: "Installing XP on a Ubuntu 7.10 machine"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Long_Live_Linux on 2008-01-23
Ok, I really like Ubuntu 7.10 alot, but I am thinking about going back to Windows XP. So could someone please tell me how to install XP on a machine running Ubuntu 7.10? 

I am also thinking about Dual-booting Ubuntu/XP.

THANKS in advance!

---

### Post by mister_pink on 2008-01-23
Doing things this way round makes your life a bit more difficult since XP will overwrite grub, but not to worry! 
First you'll need to make space for XP. But before this first thing, make sure everything is backed up! Things can go wrong when moving partitions and installing operating systems! 
So, partitioning. This depends on how your hard drives are set up really, but I suggest using gparted from the live CD to create some blank space to install xp to. You'll have to use the live cd only if you need to move where ubuntu is currently installed. 
Next up, install XP! I'm sure you'll manage this bit, just make sure it installs where you want it to.
Now that XP has clobbered grub, you'll need to go back to the live cd. Open a terminal and type:
```
sudo grub
locate stage1
```
This will give you something like (hd0,0). Using that (ill put hdx,y, but use what that said!)
```
root (hdx,y)
setup (hdx)
quit
```
And you're done. Hopefully!

---

### Post by Thelasko on 2008-01-23
Might I suggest running a virtual machine in Ubuntu?  You won't have as much speed as with only XP but if  you have a newer machine you can do some pretty cool stuff with it.  You also don't have to reboot your whole machine to use one program in XP.

Wine might be another alternative.  It uses less power than a VM but isn't quite as compatible.  Check it out.

---

### Post by Long_Live_Linux on 2008-01-23
Thanks alot! I have one question though; do I just pop in the XP install CD when booting up? Or do I pop it in and run it from Ubuntu??

---

