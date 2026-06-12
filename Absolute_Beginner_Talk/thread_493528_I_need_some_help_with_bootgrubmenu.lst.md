---
title: "I need some help with /boot/grub/menu.lst"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-07-05
I just partitioned my HDD and installed SAM PCLinuxOS on /dev/hda3. I was under the impression that my Ubuntu's boot menu list which is on /dev/hda1 would appear on boot up. I was wrong about that. I get SAM's boot menu instead. I still want Ubuntu's menu  to be the one that appears on boot up.

What can I do to get my preferred menu list to appear at boot up? Do I go into GParted and change which /dev to have as boot? I am in the dark about this. This is my first time to partition a HDD 

Here are my original settings with GParted "[COLOR=Red]before[/COLOR]" I installed SAM to /dev/hda3:

.............................................Size.  ......................Used.....................Unused
/dev/hda1.......ext3.......85.38 GiB...............4.56 GiB.................80.82 GiB..(boot)  Ubuntu Feisty Fawn 
/dev/hda3.......ext2.......21.53 GiB...............390.15 MiB.............21.15 GiB  SAM PCLinuxOS
/dev/hda4.......ext2.......20.10 GiB...............367.41 MiB.............19.74 Gib
Unallocated.................20.59 GiB................----------...................----------
/dev/hda2.......ext2........1.44 GiB................----------...................----------
/dev/hda5 Linux-Swap....1.44 GiB...............----------...................----------


Note: GParted would not allow me to decrease /dev/hda1 any smaller than what you see above on line one.

I think during the installation of SAM that without knowing it, either I or SAM defaulted to using SAM's boot menu list. If that is true, then (boot) would probably appear on the second line above instead of the first line.

Hope you can clear this up and get my original boot up menu to appear. 
Thank you for your assistance.
kh

---

### Post by orb9220 on 2007-07-05
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)
[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

---

### Post by kittyhawk63 on 2007-07-05
> **orb9220 said:**
> [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)
[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

Orb9220,
I'll be sure to check these two links out. I hope that one or both will help resolve my problem. Thanks for your responding to my inquiry.
kh

---

### Post by confused57 on 2007-07-05
> **kittyhawk63 said:**
> Orb9220,
I'll be sure to check these two links out. I hope that one or both will help resolve my problem. Thanks for your responding to my inquiry.
kh
I would recommend using the 2nd link orb9220 gave you to restore Ubuntu's grub to the mbr, then add a configfile entry to your menu.lst to boot PCLinuxOS:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Here's an excellent guide for partitioning:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
and
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

You'll get a better idea of your partitions with the command:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by kittyhawk63 on 2007-07-05
> **confused57 said:**
> I would recommend using the 2nd link orb9220 gave you to restore Ubuntu's grub to the mbr, then add a configfile entry to your menu.lst to boot PCLinuxOS:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Here's an excellent guide for partitioning:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
and
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

You'll get a better idea of your partitions with the command:
```
sudo fdisk -l
```-l is a lowercase "L"

Thank you Confused57.
kh

---

### Post by kittyhawk63 on 2007-07-06
OK. I followed the instructions given in the second link suggested by orb9220 and it failed to work. So, I guess that I will try something different. Does anyone know the command to start grub in SAM PCLinuxOS and what command lines to type into grub so that I can start Ubuntu from SAM's grub? My Feisty Fawn is on /dev/hda1
I hope you can help.
kh

---

### Post by confused57 on 2007-07-06
> **kittyhawk63 said:**
> OK. I followed the instructions given in the second link suggested by orb9220 and it failed to work. So, I guess that I will try something different. Does anyone know the command to start grub in SAM PCLinuxOS and what command lines to type into grub so that I can start Ubuntu from SAM's grub? My Feisty Fawn is on /dev/hda1
I hope you can help.
kh
You can use a configfile entry to boot Feisty:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

You should be able to add the entry to PCLinuxOS grub menu(I'm not sure what SAM's is though)...open Konsole, enter:
```
su
cd /boot/grub
cp menu.lst menu.lst_backup
kwrite menu.lst
```

Then add your configfile entry to the very bottom of your menu.lst, something like this:
```
title        Feisty on /dev/hda1
configfile   (hd0,0)/boot/grub/menu.lst
```

quit & save...

Added:  Just Googled for SAM PCLinux OS, seems it uses Xfce...you'll probably need to edit your menu.lst with:
```
nano menu.lst
```
add your configfile entry...Ctrl+X, y, enter...this will save the changes.

---

### Post by alienexplorers on 2007-07-06
Boot your Ubuntu Live-cd.  Enter Terminal and type sudo grub.
Enter:
> find /boot/grub/stage1
You should get an output like (hd#,#)

Enter:
> root (hd#,#)
setup (hd#)
quit grub
reboot

---

### Post by kittyhawk63 on 2007-07-06
> **confused57 said:**
> You can use a configfile entry to boot Feisty:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

You should be able to add the entry to PCLinuxOS grub menu(I'm not sure what SAM's is though)...open Konsole, enter:
```
su
cd /boot/grub
cp menu.lst menu.lst_backup
kwrite menu.lst
```Then add your configfile entry to the very bottom of your menu.lst, something like this:
```
title        Feisty on /dev/hda1
configfile   (hd0,0)/boot/grub/menu.lst
```quit & save...

Added:  Just Googled for SAM PCLinux OS, seems it uses Xfce...you'll probably need to edit your menu.lst with:
```
nano menu.lst
```add your configfile entry...Ctrl+X, y, enter...this will save the changes.

Thank you for your information.
kh

---

### Post by kittyhawk63 on 2007-07-06
> **alienexplorers said:**
> Boot your Ubuntu Live-cd.  Enter Terminal and type sudo grub.
Enter:

You should get an output like (hd#,#)

Enter:

quit grub
reboot

Thank you for your input. I'm taking notes of what everyone is saying.
kh

---

