---
title: "Help please!!!!!"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-03-15
argh! please help! This is soo annoying! all i want to know is If I reinstall Windows XP will Ubuntu and all the partitions be restored to what they were and will ubuntu be gone??

Why will no one answer ??

---

### Post by glennric on 2008-03-15
If you reinstall windows xp, it will should not make any changes to the ubuntu partitions.  It will however overwrite grub in the MBR, so you will not be able to boot to Ubuntu. You can fix this by following the directions in
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by stunningman on 2008-03-15
I WOULD JUST say that you format all you partitions install windows xp then install ubuntu ,at the partition prompt of ubuntu selest manual partition option(note:don't selest resize windows option) make a root partition i.e /(ext3 journalising file system) and a swap partition.everything will come out o.k

---

### Post by FuturePilot on 2008-03-15
Yes it will overwrite the MBR. But it can be restored.
If you already have an empty partition set up just select that partition when you install and it shouldn't do anything to the Ubuntu partition.

---

### Post by krendar on 2008-03-15
> **Fraser from Scotland said:**
> argh! please help! This is soo annoying! all i want to know is If I reinstall Windows XP will Ubuntu and all the partitions be restored to what they were and will ubuntu be gone??


Yes, during partitioning of the windows installation you can select to completely wipe Ubuntu if you wish to.

---

### Post by benerivo on 2008-03-15
When you reinstall windows you will have to choose, the partition setup. You can...

1. Leave the ubuntu partition untouched, and install windows on another partition.

2. Delete the partition ubuntu is on, so you get just one partition on your hard drive with windows on it (like a new pc bought from a shop).

3. Put windows on the ubuntu partition, so you wipe ubuntu.

In all of these cases, you lose the grub bootloader and get the standard windows boot.

---

### Post by ruy_lopez on 2008-03-15
If you have more than one partition. Say Windows on one, and Ubuntu on another, you should be alright. The windows partition will be used for the fresh install. The Ubuntu partition should be left alone.

The other poster is right, though. The Boot record will be overwritten. You can reinstate the boot record later, if you want, using an Ubuntu LiveCD.

This shows you how:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

### Post by Fraser from Scotland on 2008-03-15
ok, thanks for the reply, but what i want is ubuntu gone. I want it to be removed because it will not recognise partitions, so I am not able to do anything on windows since I only have 2gb of space but it thinks I have 80gb of space.

---

### Post by handydan918 on 2008-03-15
> **Fraser from Scotland said:**
> argh! please help! This is soo annoying! all i want to know is If I reinstall Windows XP will Ubuntu and all the partitions be restored to what they were and will ubuntu be gone??

Why will no one answer ??

Patience, young Skywalker....
What do you *want* to happen?
If you want to hose Ubu, you can. If you want to preserve it, you can do that to.
Choose!

---

### Post by Fraser from Scotland on 2008-03-15
> **benerivo said:**
> When you reinstall windows you will have to choose, the partition setup. You can...

2. Delete the partition ubuntu is on, so you get just one partition on your hard drive with windows on it (like a new pc bought from a shop).



Ok, this is what i want to do. So all I have to do is reinstall windows and follow the options for totally wiping the HD ?

---

### Post by FuturePilot on 2008-03-15
> **Fraser from Scotland said:**
> Ok, this is what i want to do. So all I have to do is reinstall windows and follow the options for totally wiping the HD ?

yes

---

### Post by glennric on 2008-03-15
In the windows installer when it comes to the partitioning step, just delete all of the existing partitions.  Then install windows.

---

### Post by freebios on 2008-03-15
yes usually this could cause problems because windows can hose the grub and replace it with the windows boot loader.  this wont affect the partitions or Ubuntu, except for the fact it will not load if grub is hosed.  for the most part windows in not very friendly with other operating systems including Ubuntu.  if you need windows the best route is to install windows then reinstall grub, or Ubuntu again.  Ubuntu knows how to recognize windows and boot properly in a dual boot environment.  good luck, please let me know if you need more help. this post is a response to the original poster's thread.

---

### Post by handydan918 on 2008-03-15
> **freebios said:**
> yes usually this could cause problems because windows can hose the grub and replace it with the windows boot loader.  this wont afect the partitions or ubuntu, except for teh fact it will not load if grub is hosed.  for the most part windows in not very friendly with other operating systems including ubuntu.  if you need windows the best route is to install windows then reinstall grub, or ubuntu again.  ubuntu knows how to recognize windows and boot properly in a dual boot environment.  good luck, please let me know if you need more help.

With all due respect, I must disagree with this assessment. If the windows installer provides the option to format the entire disk, and that option is selected, it will indeed "affect" Ubuntu. 
Ubuntu will suffer an existential terminus.
In my experience, the big trick with installing windows is preventing exactly this from happening....

---

