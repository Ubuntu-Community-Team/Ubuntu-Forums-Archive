---
title: "new external hard drive"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by huviduc on 2006-11-16
i just recieved my new 250GB external hardrive and i a need to format it so that that XP and Ubuntu can recognize it. i am dual booting and i need to be able to use it on either OS. when i go to System> Administration> Disks, the drive shows up but it needs to be formatted, i just dont know what format type to use so it will be interchangeable. thank you

---

### Post by aidanr on 2006-11-16
fat32 (vfat)

---

### Post by huviduc on 2006-11-16
ok, i was pretty sure i needed to use FAT32, but i could not seem to figure out what the vFAT was. thank you very much. i just installed ubuntu last night, and i have spent over 8 hours on it today, i am loving it so far. and the forums are a HUGE help, thanks

---

### Post by huviduc on 2006-11-16
ok, i just went to format it using the disks utility with the vFAT filesystem and i hit format, it asks if i am sure, i hit yes, and it doesnt do anything else. any ideas?

---

### Post by LLRNR on 2006-11-16
Well... just as an idea... you could try to format it from within the XP install CD (you'd have to enter recovery console mode for this, first use diskpart to create a partition then use format to format it)... Though I'm not really sure why it can't be done using the disk utilities within Ubuntu.

---

### Post by huviduc on 2006-11-16
ok, i wen tin and used a live cd and used Gnome partition editor and it is formated with fat32 and shows the amount of free space and says its Windows virtual FAT(vfat), but it wont let me browse it. if i go to places>Computer and click on it i get an error saying its unable to mount the selected drive and states in the more details section "mount: only root can mount /dev/sda1 on /media/sda1mount", i havent the slightest idea what that means

---

### Post by aidanr on 2006-11-16
check if you have priviledges to auto mount it, System->Administration->Users and Groups->Properties->Priviledges->Access external storage devices automatically, also check System->Preferences->Removable Drives and Media->Mount removable drives when hot-plugged, then unmount it if its already mounted, plug it out and plug it back in and it *should* automatically open up nautilus at the external drive (im not 100% sure its the exact same on dapper btw)

---

### Post by GenX on 2006-11-16
So my drive has to be Fat32 to install Edgy on? The one I have is NTFS.

---

### Post by huviduc on 2006-11-16
> **aidanr said:**
> check if you have priviledges to auto mount it, System->Administration->Users and Groups->Properties->Priviledges->Access external storage devices automatically, also check System->Preferences->Removable Drives and Media->Mount removable drives when hot-plugged, then unmount it if its already mounted, plug it out and plug it back in and it *should* automatically open up nautilus at the external drive (im not 100% sure its the exact same on dapper btw)

i checked both of those and its still not working. I think i figured out the problem, but i do not know how to fix it. Earlier today i was messing around and i followed this thread ([http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)) to figured out how to make my windows files read/write capable, but i tried that on my other external so i could read the files on it. So, i think it is having trouble mounting is because its looking in the wrong place because i changed the properties with fdisk. Can someone tell me how to get it back to default?

---

