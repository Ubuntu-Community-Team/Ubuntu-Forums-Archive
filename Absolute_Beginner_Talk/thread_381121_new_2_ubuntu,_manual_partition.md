---
title: "new 2 ubuntu, manual partition ?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Blandust on 2007-03-10
I installed Ubuntu last night and this morning I was curious as to wether I had chose the correct partition, so I put the Ubuntu Live Cd and rebooted just to see the current partitions, and I see that it looks like I still have windows on my 1st hard drive, How do you switch back and forth from windows to linux and... Should I re partition with different sizes or is the current configuration good? suggestions ? thanks

I selected manual edit  partition tables and im presented with




Partition     l     Filesystem      l   Size    l Used  l  Unused  l   Flags

/dev/hda1       ntfs                    14.94    9.61     5.32  

/dev/hda2        extended           18.54    --          ---             iba
>             
      /dev/hda5   ntfs                  17.23     3.19    14.04 
      /dev/hda6  linux-swap           1.35      --          --

/dev/hda3           ext3                41.04     2.54     38.50     boot

---

### Post by mikewhatever on 2007-03-10
Have you installed GRUB boot loader? At boot, GRUB menu should load and present you with options to boot either Windows or Ubuntu.

---

### Post by Blandust on 2007-03-10
no i havent, and also from looking at the partition arrangements and sizes does everything look to be set-up in good working order? Should I alter the partitions?

---

### Post by mikewhatever on 2007-03-10
Nothing seems to be wrong with your partitions. How do you boot Ubuntu or Windows without GRUB? Do you use CDs or something?

---

### Post by Blandust on 2007-03-10
<----uber noob here!!! I do have grub, i just actually shut-down and rebooted, I had restarted Ubunutu once or twice after I had installed so I hadnt had a chance to be presented with the select Os screen, it gave me like 3 options for Ubuntu and then other drive Os Windows Xp as an option as well. :) I see now!

---

