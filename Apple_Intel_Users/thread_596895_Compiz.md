---
title: "Compiz ???"
date: 2007-10-30
forum: Apple Intel Users
---

### Post by justincormier on 2007-10-30
ok so i just picked up a little macbook and of course threw the new gutsy on it.. im also pretty sure i overwrote leopard (whoops) cause ubuntu does not offer me os x in the grub.. i even had reFIT installed as well.. oh well.. here is my main problem.. WHERE IS COMPIZ???  this should be here by default right? i tried to install the setting manager but this is what my terminal told me..

justin@justin-laptop:~$ sudo aptitude install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      


notice the no packages installed.. whats the deal? anyone got any clues for either problem?


thanks guys,

-justin

---

### Post by kvonb on 2007-10-30
Did you enable the restricted/universe/multiverse repositories?

On the main menu, goto: System->Admin->Software Sources, and select all, then it will reload it's lists on exit.

Then I would use the GUI Synaptic manager from the menu: System->Admin->Synaptic, that way you can simply search for **compiz** and you will get to see everything compiz related (more cool options).

---

### Post by justincormier on 2007-10-30
AWWWWWWWWWWWEEEEEEEEESSSSSSSOOOOOOOOOOOMMMMMMMME  THANKS!

you know how to get OS X to load??

---

### Post by Crafty Kisses on 2007-10-30
Thread is solved.:KS

---

### Post by kvonb on 2007-10-30
> **justincormier said:**
> AWWWWWWWWWWWEEEEEEEEESSSSSSSOOOOOOOOOOOMMMMMMMME  THANKS!

you know how to get OS X to load??

hmm, not sure about that one.

But to see if the OSX partition is still there, open a terminal (menu->accessories->terminal) and type this:

```
 sudo fdisk -l

```
Here's mine for comparison:

```
 kev@kevs-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1961    15751701    7  HPFS/NTFS
/dev/sda2            1962        4742    22338382+  83  Linux
/dev/sda3            4743        4864      979965   82  Linux swap / Solaris
kev@kevs-laptop:~$ 
```

Note my first partition (**/dev/sda1**) is type NTFS, well you should see something about an OSX type.  Or at least something other than the 2 standard Linux partitions (as in my example: /dev/sda2 & /dev/sda3).

If you only have the Linux partitions, then you may proceed to sob uncontrollably, and maybe even bang your head a few times on your desk, as I would suggest that you deleted the OSX one when you installed Ubuntu :(.

But, if you have the restore disk that should have come with the laptop, I would use that to wipe the disk and re-install OS/X, then re-install Ubuntu, but this time don't do an automatic install, select manual partitioning and create one partition for *****/*** (between 3 to 6 gig, type: *reiserFS), one for the swap file (twice the size of your RAM, change type to: *linux-swap), and one for ****/home** (use whatever is remaining, again type: *reiserFS).

When you click on create partition, you will have to select a ***type** and ****mount point**, that is what I mean in the above paragraph.

And when it comes to the question about where to install grub,make sure it is in the MBR, or the root of your disk, usually /dev/sda.

You should then get OS/X as a boot option.

---

### Post by cyberdork33 on 2007-10-30
I would say you overwrote OSX. If you want to reinstall it, make sure to use the disk utility to partition the disk, making one partition big enough for all your Ubuntu OS (Root and swap and any other partitions you want). Then install OSX to the other partition. 

Then when you boot the Ubuntu CD, you need to delete that partition you made for Ubuntu, then use the free space when the installer asks where to install.

If you plan to triple boot, it gets a bit more complicated.

---

