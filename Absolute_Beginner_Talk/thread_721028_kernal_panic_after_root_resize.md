---
title: "kernal panic after root resize"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by bleeping seauty on 2008-03-10
Hello,

I've got a dead Ubuntu system. I'm running  Feisty on an amd 64, HP6100. I love Ubuntu, generally my system works great.

History
I got a disk size warning, 97 % on /boot. Also unable to save error while updating/installing in Synaptic.

Fix
I installed Puppy Linux on a different disk, and used gparted to resize and move my /usr/local, and then expand /boot from 45 M to 1 G
Also
The other thing that may have caused the kernel panic, was while installing Puppy Grub, I chose the option to put the Grub Boot on the Linux superblock. 

The error message 
Running / scripts/init-bottom
Done
36.153311 Kernel Panic - not syncing: attempting to kill init!

Help please,
SBee

---

### Post by handydan918 on 2008-03-10
Ya know, you could diddle around with this for a ling time. Or you could reinstall in like 30 minutes....

---

### Post by bleeping seauty on 2008-03-10
Roger that. And Thanks. 

It's just that I've had bad experience with OS install scripts. They tend to not play nice with existing partitions and information.

Any other ideas / comments? Thanks

SBee

---

### Post by handydan918 on 2008-03-11
Yeah, I hear ya on the installer thing. Ubu particularly doesn't want to let you do it your way. 
Of course, if you know a little about what you're doing, the alternate install disk gives you a little more latitude as far as partitioning and where to install grub, etc...

---

