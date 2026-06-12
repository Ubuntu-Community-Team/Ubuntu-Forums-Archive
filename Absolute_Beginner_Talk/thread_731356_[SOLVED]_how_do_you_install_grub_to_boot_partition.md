---
title: "[SOLVED] how do you install grub to boot partition"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Arch Parsons on 2008-03-21
I have a single drive triple booting XP, Vista and Ubuntu.

I am planning to back up my disk to a second disk using Acronis True Image 11.  It mentions in the guide:  For Linux loaders (e.g. LiLo and GRUB), you might consider installing them to a Linux root (or boot) partition boot record instead of MBR before activating Acronis Startup Recovery Manager. 

Could somone please tell me the simplest and safest way to do this prior to making the backup

How will this affect the booting of my system?

Thank you in advance for any comments.

---

### Post by mikewhatever on 2008-03-21
Try this guide [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

I don't know much about it, but if grub is installed to the boot or root partition the MBR is unaffected, so Windows should boot regularly. In order to boot Ubuntu, you'll need to add an entry to boot.ini (I think) pointing it to GRUB.

---

### Post by louieb on 2008-03-21
Quick and easy
In a terminal window
```
sudo grub
```
if you have a separate /boot partition
```
find /grub/stage1
```
if you don't have a separate /boot partititon
```
find /boot/grub/stage1
```
Returns where it found the file. in the form of (hd#,#) 
Use what it returned to put GRUB IPL code in the boot sector of the partition.
```
 
root (hd#,#)

``````
setup (hd#,#)
```
```
quit
```
Should not affect the way you boot now. This sets up the partition to allow a boot loader to chainload booting to the partition.
More here:[IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by brandonclyon on 2008-03-21
There really isnt a problem to installing it to a windows partition and adding it to the MBR, its just when you want to ditch linux (though I have no idea why you would) you have to pop in your windows XP cd, go into recovery console and type in "fixmbr" otherwise Windows will freakout like a ninja and not boot

---

### Post by Arch Parsons on 2008-03-22
Thanks to all for the clarification and resources.  the only boot partition I have in the Ubuntu partition is the one that I had to create. When I type sudo grub I get this:

grub>

 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

I get "command not recognized" for the other find stage 1 commands.  

I am only concerned with being able to boot Ubuntu if and when I should have to restore an image of my whole drive.  When trying to enter recovery console in my XP cd in the past I have been asked to insert a recovery disk which I don't have, so I'm not sure Iif I will be able to use the fix mbr command..

---

### Post by Arch Parsons on 2008-03-22
I just read this reply from an earlier posting I made on the same subject to Wilders Security Forum:   

Re: Triple Boot Disk Cloning 

--------------------------------------------------------------------------------

archp2008:

Yes, TI can back up XP, Vista, and Linux partitions. You will be able to use your new disk to store images of your current disk, should you so choose.

The special considerations for restoring a Linux partition will arise if you have GRUB installed to the Linux partition. If so you may need to keep a Live Linux CD handy in order to repair GRUB after restoring the Linux partition. If GRUB is installed to the MBR then you should not need a repair after restoration.

If you want to create a RAID-1 array then there is no need to do anything to prepare your new disk; it can be blank. With most RAID controllers including motherboard-based RAID you would install a second disk, boot to the motherboard BIOS and configure your two disks as a RAID-1 array. The RAID controller should then take care of the task of duplicating the contents of your original disk to the new, blank disk to make the two disks identical. Consult your motherboard documentation for details.
__________________
Mark
True Image 10.0 and Disk Director Suite 10.0 user 


Sorry I'm so dense on this stuff. The RAID-1 setup sounds most attractive to me if it will work as Mark describes.  Any further comments on this alternative would be appreciated.

---

### Post by Arch Parsons on 2008-03-22
I've done a little research today on using RAID, and the consensus seems to be that RAID is not a substitute for doing regular scheduled backups.  Since I'm only going to have two drives, I'm tending to lean towards using Acronis to backup to the seccond drive.  I'll have another go at using  those Ubuntu commands to see if I have more luck.  Thanks again. I'm still not clear if Acronis really requires this.  Thanks in advance for any further comments. I'm trying to increase the font size in this window so that I can see what I am typing, but nothing seems to work.

---

### Post by Arch Parsons on 2008-03-22
Louie,  
Thanks for the instructions.  Unfortunately, I am evidently not doing something correctly:  
find /grub/stage1 returns hd(0,4) but setup hd(0,4) returns Error 11: Unrecognized device string.

---

### Post by Arch Parsons on 2008-03-22
I think I typed it wrong.  Actually this is what I should have done but I get Invalid Device

grub> setup (hd0,4)

Error 12: Invalid device requested

---

### Post by logos34 on 2008-03-22
> **Arch Parsons said:**
> 
I am only concerned with being able to boot Ubuntu if and when I should have to restore an image of my whole drive.

Then why don't you try making a grub boot floppy:

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

---

### Post by Arch Parsons on 2008-03-22
I already have SuperGrub.  I just tried it and it only takes a second or two to overwrite the MBR. Evidently, I don't need to worry about what Acronis would do to the MBR if I had to do a restore.  In a matter of seconds I can have Grub back the way it was.  Do you agree?

---

### Post by logos34 on 2008-03-22
yeah, you can boot ubuntu and/or restore grub with SGD.

---

### Post by Arch Parsons on 2008-03-23
Thanks to All!

---

### Post by louieb on 2008-03-23
Just realized left out setting the grub root in post #3. That's why your getting the invalid device. I've fixed the post. 
 
Just wondering saw some mention of RAID earlier. Are you using RAID now? if so my suggestion earlier may not be good? 
Have not used a RAID array so don't know for sure how GRUB and raid work or don't work together.

---

