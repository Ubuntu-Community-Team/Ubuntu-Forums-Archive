---
title: "Install DVD + ((ubiquity Install wizard + partman) | gparted)  !=   LVM"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by najevi on 2007-07-07
The install DVD (**ubuntu-7.04-dvd-i386.iso**) allows a "Live CD" style launch of ubuntu and at the desktop I find an "**Install**" icon for what appears to be a *ubiquity* installer to start a 7 step, intuitive GUI based install wizard. I _much_ prefer that GUI approach over the **text mode install** that I have tolerated in the past, but ...
... after "Step 4 of 7" (**partman**) I have difficulty creating my desired LVM based partition scheme!

[COLOR=Blue]Should the **partman** GUI be capable of creating Physical Volumes (PVs)  that can be marked for management by LVM and subsequently launch a GUI equivalent of **lvmcfg** to set up Volume Groups (VGs) and Logical Volumes (LVs)?[/COLOR]

If it is possible then would some kind soul *please post a "Step: action" style tutorial* to walk a newbie through the process. I feel I have tried seven ways from Sunday but with no joy!

[COLOR=Blue]If it is not possible then please list my LVM partitioning options.[/COLOR]

I _can_ successfully use the "**text mode install**" to achieve the VG and LV results that I want but that is a painfully tedious process. 

I'd prefer to use the ubiquity Install wizard GUI. 
I'd even be happy to run **gparted **from the "Live CD" desktop for this partitioning phase.
If a PV/VG/LVM heirarcy can be specified in a preseed.cfg file then I'd like to learn how. 
Although a distant fourth preference, I'd settle for an ubuntu customised LVM tutorial describing how to properly initialize lvm2 and use pvcreate, vgcreate and lvcreate at the terminal window.

I have patiently read the Ubuntu Installation Guide, searched this forum, googled and read the LVM HOWTO as well as dozens of promising blogs or articles but *none of these has shown me How to!*

Within the **partman **GUI  I have discovered the 'right-click on /dev/hdb' menu item to create a **new partition table**; and  within **gparted **I have discovered the **LVM **flag;  I've even installed and initialized **lvm2** and **lvm-common** in an effort to gain access to the pvcreate, vgcreate and lvcreate functionality. But ... no success!

Thank you for considering my request.

---

### Post by mbsullivan on 2007-07-13
bump.

---

