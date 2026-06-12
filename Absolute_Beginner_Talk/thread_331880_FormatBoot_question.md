---
title: "Format/Boot question"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-01-05
I have two questions please.

#1   We have Win.xp and ubuntu 6.10 on our first hdd and have installed a new 80g hdd which we want to use for storage for both xp and 6.10.
I read on here that it's best to format the new hd as Fat32 and add the driver to xp so it can access it.
Can you please tell me how to do that, keeping in mind that I'm really new to linux?

#2   Can you please tell me how to make ubuntu boot to my cd-rom drive first?

Thank you. 
Holly

---

### Post by jvc26 on 2007-01-05
Format the new HDD as FAT32 from the linux GParted/Windows - thats easy you dont need any new drivers to use windows and FAT32 it all works fine as does Ubuntu with FAT32. Basically put in the new drive, go to windows, format the drive with FAT32 and both Ubuntu and windows should be able to recognize the new device.

To boot from cd first? - do you mean as in from BIOS? - Press DEL when setting up, then down to something like standard CMOS features (wherever the list of boot devices is) and set the first boot device to cd. Is that what you meant?

Il

---

### Post by Sasa_Ivanovic on 2007-01-05
#1 insert your XP cd, restart follow the wizard on formatting choose Fat32.
#2 Restart your cpu, press Del to enter bios go to advanced options, find the order of booting, modify it.

---

### Post by jvc26 on 2007-01-05
Um wont that process run the risk of killing off the XP? - you can just go to 'my computer' right click on the HDD when its in and just click 'format as FAT32' under the format menu I thought - I used to do it from time to time.

Il

---

### Post by Sasa_Ivanovic on 2007-01-05
ok i have a similar question, here goes :

i have two hdd's one of them is ntfs. I can acsess it, but i can't change anthing. I tryed loging in as root and changing but i get the error : "the disk is read only".
Would this be fixed if i format the disk to Fat32 ?
And could i do this without deleting anyhing ?

---

### Post by Sasa_Ivanovic on 2007-01-05
> **Illuvator said:**
> Um wont that process run the risk of killing off the XP?
nah, i did it a few times.

---

### Post by jvc26 on 2007-01-05
> **Sasa_Ivanovic said:**
> ok i have a similar question, here goes :

i have two hdd's one of them is ntfs. I can acsess it, but i can't change anthing. I tryed loging in as root and changing but i get the error : "the disk is read only".
Would this be fixed if i format the disk to Fat32 ?
And could i do this without deleting anyhing ?

See answer to another post on booting just a few mins ago. Default, Ubuntu can only mount NTFS as read only, hence you can only read the NTFS partition. You can get some experimental NTFS drivers (not sure where the link is now, a google/forumsearch will help) which allow read-write but theyre just in beta at the moment and Ive never used them (see forum posts for what people think of them) They may well work well - its probably just a take a peek and see/see what other people have said.

Therefore its easier to format the thing as FAT32 as thats work out of the box for both Ubuntu and Windows both read and write. You cannot change the filesystem without formatting the drive (it will screw up all of your data trying to change it without a reformat) You'd have to back up everything and then reformat as FAT32. Hope that helps,
Il

---

### Post by Milt888 on 2007-01-05
I think I understand, however when I go to gparted the new hd is there but the only option I can find is to "set disklabel" with some options, ie. msdos, etc. Does that format the hd?
And I dont have an xp cd. The system came preinstalled.
Thank you.

---

### Post by Sasa_Ivanovic on 2007-01-05
Thanks illuvator, i guesed i needed to back it up. it will last for hours since it's around 120 GB.

---

### Post by Sasa_Ivanovic on 2007-01-05
> **Milt888 said:**
> 
And I dont have an xp cd. The system came preinstalled.


then use illuvator's method.

---

### Post by CroEragon on 2007-01-05
You can use beta drivers, i use them i don't have any problems. FAT32 gets fragmented easily and you can set up Ubuntu to write to ntfs in matter of 2 minutes.
Try beta drivers and if it doesn't work you can always partition it.
You can find guide about it [here.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")
Vjeruj mi, radi, ja te drivere stalno koristim.

---

### Post by Milt888 on 2007-01-05
I think we have figured it out now.
Thanks for all your help, and the link.
Holly

---

### Post by jvc26 on 2007-01-05
Just another brief note, the disklabel, if i remember rightly is just so Windows can have an idea what the disk is - you set the label, then you should get the opportunity to format it FAT32 - because its new it hasnt had a label yet.
Il

---

### Post by Milt888 on 2007-01-05
I understand. I'll set the disklabel to msdos then.
Thank you.

---

### Post by Duck2006 on 2007-01-05
When you got your new HD it sould have come with a utily diskm you can use this to format your new drive to the Fat32

---

### Post by jvc26 on 2007-01-05
There no need tbh with the Ubuntu GParted you can do it all straight away :)
Il

---

