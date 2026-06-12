---
title: "SATA controllers swapping positions"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by kextyn on 2007-07-22
I have 7.04 installed on an Asus A8N-SLI Deluxe motherboard.  It has a Silicon Image and NVIDIA SATA controller for a total of 8 SATA ports.  I have every one of them filled.  The problem is it seems like every time I reboot my computer they swap positions sort of randomly.  Sometimes the NVIDIA drives will be sda-sdd and sometimes they'll be sde-sdh.  This is getting pretty annoying having to edit my mdadm.conf and fstab and then reboot and have to do it again.

If this is answered somewhere else please direct me there, I couldn't find anything related while searching.

---

### Post by MrHippocampus on 2007-07-23
Instead of using /dev/sd* you could try /dev/disk/by-uuid/...... the uuid's dont change even when the sd*'s do, you just need to figure out which uuid is which drive.

---

### Post by jimbob on 2007-07-23
Use the command *[COLOR="Blue"]blkid[/COLOR]* to see which drive UUID is which.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by kextyn on 2007-07-24
I have seen that before in a previous version of Ubuntu but wasn't sure if it would still work in Feisty.  I'll give that a shot. Thanks.

---

