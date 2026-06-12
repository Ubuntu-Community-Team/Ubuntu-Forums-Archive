---
title: "installing new version of ubuntu on dual boot system"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by alper_tr on 2005-09-18
Hi all,

I have a dual boot system(ubuntu and winXP), I am considering to install new version of ubuntu(breezy badger) over my existing ubuntu system. However I want to first clean everything from recent version of ubuntu and do a clean install, however I worry to mess up my grub config and other partitions accidently.

How would delete every file on the partition where ubuntu is installed and do a clean install on the same partition and not mess my grub config. 
Because I know, if I choose to install new version on the same partition, Ubuntu will try to upgrade or write new files next to older ones... 
Normally my method is to, first format my ubuntu partition with fat32 or ntfs, than booting into winxp, and than to format from my XP partiton, than booting with Ubuntu cd, and instaling over it with reiser fs... somehow formatting over linux doesnt works(At least it didnt before, files remains there)

Is there a better way that you would suggest? 

Thanks already

---

### Post by aysiu on 2005-09-18
I did a recent reinstall of Ubuntu to get Breezy, and this is what I think you should do. Back up your /home folder--particularly your internet browser and email folders. Don't forget to back up your files, too.

Then, just install the new Ubuntu. When you get to the part where it says Format the entire disk or Edit the partition table manually, select to edit it manually.

Then choose your old Ubuntu partition as the mount of point of / and format it as ext3.

When you're ask whether you want to install Grub to the MBR, say yes.

That's it.

---

### Post by alper_tr on 2005-09-18
Well, like I say, I want to do fresh install, and dont have any files I would feel sorry to loose in my recent Ubuntu partition. And I would definetely prefer to have my partition as reiser fs.
Thing is, if I choose format as reiser fs , my files will remain there, and I dont want that.

---

### Post by Leif on 2005-09-24
if you format a partition, regardless of the filesystem type, everything on it will be gone.

---

### Post by BoyOfDestiny on 2005-09-24
Alright no worries. I actually understand what you are saying here :). 

When you run the installer, go for the manual setting of the partition. Then when you select a partition and hit enter (going by memory here) there is an option that says "keep existing files" or something like that. Highlight that and hit enter, it will change to "erase partition".

Sorry if it's not exact, but it will keep your partitions as is, but will wipe what you don't need (usually I wipe / and leave /home with my stuff :) )

Good luck!

EDIT: Also, when you are changing the partition settings: double check that the mount points are correct too, last time I think breezy wanted to mount /home as /media or something =)

---

