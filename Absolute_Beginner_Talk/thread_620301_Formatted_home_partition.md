---
title: "Formatted /home partition"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by ba1n0 on 2007-11-22
OK, so running gutsy and had a few apps that I needed windows to use. I have the following disk structure

dev /sda1  Swap
dev /sda2  /   80GB
dev /sdb    /home  160GB
dev /sdc    /media/Storage   200GB

So I used the gparted live CD to resize sdb to 100GB NTFS and 60GB for /home. My plan was to install vista on the 100GB partition and leave everything as is. There was a problem and now when I boot, ubuntu starts but the session fails because it cannot find /home.  Grrr

I don't keep much in my home since I use my Storage drive, so formatting wouldn't be a problem, but looks like all my settings and config files are gone.

Is there anyway to reset the home location and then generate standard config files? I really don't feel like installing again as I had ubuntu running perfectly.

Bear in mind I'm writing this on Vista so anything you guys ask me to try, I'll have to reboot into ubuntu to do it so my responses may take a while.

Cheers for any help.

---

### Post by hyper_ch on 2007-11-22
always make a backup before altering partitions... (well, also make backups on a regular base).

What kind of problem did you encounter upon partitioning?

---

### Post by ba1n0 on 2007-11-22
everything seemed to go fine, home just wasn't there after reboot. This is gonna be a pain in the ***. I can only do anything with a failsafe xTerm session. I'm thinking that a reinstall may be my only option.

---

### Post by philinux on 2007-11-22
Can you post your fstab?

---

