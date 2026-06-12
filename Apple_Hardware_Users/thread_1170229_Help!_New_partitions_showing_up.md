---
title: "Help! New partitions showing up"
date: 2009-05-26
forum: Apple Hardware Users
---

### Post by monsterfromthefuture on 2009-05-26
I need help.  Im new to linux and am running a white macbook 4,1 ubuntu 8.10.  I recently have tried to get the isight camera working and am running into numerous issues.  I followed this tutorial [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight)

Along with isight still not working new partitions have showed up, 
device: sda1 
    mount point: /media/EFI                              
Type: vfat

device:sda2 
     mount point:/media/Macintosh_HD              
Type :hfsplus


Along with these issues itunes is no longer responding in Mac OSX,  I am extremely worried I haved messed up my computer.  Any help would be greatly appreciated

---

### Post by cyberdork33 on 2009-05-26
> **monsterfromthefuture said:**
>  Along with isight still not working new partitions have showed up, 
device: sda1 
    mount point: /media/EFI                              
Type: vfat

device:sda2 
     mount point:/media/Macintosh_HD              
Type :hfsplus

what do you mean by they "show up"? Those partitions should have always been there, though they should not mount by default.


> **monsterfromthefuture said:**
> Along with these issues itunes is no longer responding in Mac OSX,  I am extremely worried I haved messed up my computer.  Any help would be greatly appreciated boot from your OSX Install disc and do a repair on your OSX partition with Disk Utility.

---

### Post by monsterfromthefuture on 2009-05-26
The partitions show up after I boot ubuntu, a disk manager icon shows up on the menu and asks if I want to configure the new mentioned partitions.
which is weird , it has never asked me to do this before.  Should I mount these partitions? what are the reprocussions?

"boot from your OSX Install disc and do a repair on your OSX partition with Disk Utility."
How do I do this?  any insructions would be greatly appreciated.  

aslo trhanks cyber for responding.

---

### Post by cyberdork33 on 2009-05-28
> **monsterfromthefuture said:**
> The partitions show up after I boot ubuntu, a disk manager icon shows up on the menu and asks if I want to configure the new mentioned partitions.
which is weird , it has never asked me to do this before.  Should I mount these partitions? what are the reprocussions?I have never seen that before. I would generally not mount any of them unless you specifically need a certain file from there.

> **monsterfromthefuture said:**
> "boot from your OSX Install disc and do a repair on your OSX partition with Disk Utility."
How do I do this?  any insructions would be greatly appreciated.  
1. boot from the OSX Install DVD
2. Start Disk Utility (It is available in the menu once you get it started).
3. In Disk Utility, select your drive and Repair.

---

### Post by monsterfromthefuture on 2009-05-28
Thanks for the help.  I'll just ignore the partitions for now.  Maybe I changed some startup preferences? 


 Also itunes works when im connected to a valid wireless network.  If i turn airport off or connect wirelessly itunes works.  But if Im at home itunes will not respond,  my internet service has beeb recently dissconnected but my router is still on.  Is that the issue? Or has something in ubuntu damaged itunes?

Should I still try to repair OSX with disk utililty or should I try to fix it through the iTunes end and check the settings and prefs of the program.

Thanks for help, more would be greatly appreciated!

I'm new to linux but I have found that I love ubunutu and I want to keep this operating system and make it run optimally.

---

