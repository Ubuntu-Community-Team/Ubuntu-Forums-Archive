---
title: "Grub configuration messed up"
date: 2014-01-13
forum: Any Other OS
---

### Post by Tristan_Williams on 2014-01-13
I have ubuntu 13.10 on /dev/sda 
I have just installed gentoo on /dev/sdb 
Every time I mess with grub I screw up.

I run "emerge grub" and it installs grub2. 
/boot/grub/ does not exist. Wtf...

So I think maybe ill just add gentoo to grub on /dev/sda1. 

Nope, since I replaced the other OS with gentoo, grub won't even boot on sda1... 

What genuine poop do I do here???

---

### Post by deadflowr on 2014-01-13
Can you still boot into the 13.10 OS?
If so, just try running the
```
sudo update-grub
```
command and see if the os-prober grub utility sees the gentoo install(s?).
Grub doesn't need to be installed on another OS.
As long as the other OS's kernel can be seen, that's what matters.

---

### Post by Tristan_Williams on 2014-01-13
No I cannot boot into the other OS. I did fix it though
I used the minimal installer to install ubuntu on the second HDD.
Grub got reinstalled on the same partition as it was origionally on.

---

### Post by Bucky Ball on 2014-01-13
*Thread moved to **Other OS/Distro Support.***

---

### Post by grahammechanical on 2014-01-15
For future reference you could have partially fixed this another way. Run a Ubuntu live session. Open sda to mount it and run in a terminal this command.

```
sudo grub-install /dev/sda
```

The command installs Grub into sda. That should get you a Grub that is pointing to sda and once into Ubuntu you can then run the command

```
sudo update-grub
```

and hope it detects the OS on sdb.

Regards.

---

### Post by rewyllys on 2014-01-15
> **grahammechanical said:**
> For future reference you could have partially fixed this another way. . . .
Thanks, Graham.  I'm glad to know this, and I've saved it in a personal file for possible future reference.

---

