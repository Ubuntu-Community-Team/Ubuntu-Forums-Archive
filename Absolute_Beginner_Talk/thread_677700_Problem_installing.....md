---
title: "Problem installing...."
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by shaheel16 on 2008-01-25
Hello everyone there.. Im new to linux... IF you could help me with this ubuntu install it will be great..

Well I have a primary partition NTFS about 25 Gb with windows XP on it and a logical drive with 15 GB actually being in Fat32. I would like to format that logical drive and use those15 Gb for ubuntu without disrupting my windows xp..

So, my question is how to set up that logical drive so as to install ubuntu on it.. i dont know nothing about swap, root ...can anyone help plzz..???:confused:

---

### Post by kplaxmaster on 2008-01-25
Simple enough.  First off, welcome to the Ubuntu community!

Simply put your ubuntu live-cd in, boot it (by pressing whatever key if necessary to boot from cdrom prior to hard-drive).  In the installer, it asks where to install.  Simply select the partition that is your Fat32 (you can tell by knowing the sizes, and usually your WinXP will be the first partition of your drive).

To make sure however, before installing... while running the live cd, go to System > Administration > GParted.  It will show your current partitions and their file type, as well as their dev (nice name for devices) name.  Memorize which is which, and go back to the install window and select the right one!

After you select which partition, you select that you want to use recommended settings (will setup your swap, boot, and all those nice directories for you nicely without you having to know it--well now you know it... so nvm).

Hopefully this helps!

Note: once you install Ubuntu, it automatically installs a utility called Grub.  Grub lets you dual boot windows and linux.  Grub will automatically see your other WinXP partition and create the appropriate link to it so everytime you restart your computer you can boot either operating system.

---

### Post by hyper_ch on 2008-01-25
if you don't want that fat32 partition at all anymore you could first delete it complete and leave that space unpartitioned... during the install you could then select "use largest continuous empty space" (or something like this). Just make sure you don't select "use full disk"

---

### Post by mexpolk on 2008-01-25
Check these resources:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Hope this helps!

---

### Post by shaheel16 on 2008-01-25
yea thanks a lot.. im planning to delete that partition and letting ubuntu to do the rest..hope it works and my xp dont get screw up..

---

