---
title: "unable to satisfy all constraints on the partition?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by superwazn on 2007-06-02
im having a terrible time trying to format an ntfs drive to fat32.  when i try to do this in gparted, i get the error "Unable to satisfy all constraint on the partition". what in the world does this mean, and what do i have to do now? this paticular hard drive has been giving me all sorts of headache recently, and i figured a fresh formatting might do something. does anyone know how to get around this error?

---

### Post by ca.kushagra on 2007-06-03
if u are using windows then use a bootable windows cd and make partitions. That will be easy.

---

### Post by superwazn on 2007-06-03
but this is also the other half of the problem, if i do so little as _turn the drive on_, windows will slow to much less that a crawl for around 20 minuites, then go back to normal for a little while, unless i do something related to the drive, it will get really slow again. also, even if i can bear with it to the disk managment, it doesnt show up. i also tried getting to "my computer" then right clicking it and choosing "format" but again, it was too messed up to even do anything. this is really driving me crazy

---

### Post by oilchangeguy on 2007-06-03
> **superwazn said:**
> but this is also the other half of the problem, if i do so little as _turn the drive on_, windows will slow to much less that a crawl for around 20 minuites, then go back to normal for a little while, unless i do something related to the drive, it will get really slow again. also, even if i can bear with it to the disk managment, it doesnt show up. i also tried getting to "my computer" then right clicking it and choosing "format" but again, it was too messed up to even do anything. this is really driving me crazy

you can't reformat xp after it's installed. you'll have to do a fresh reinstall and choose fat 32 at that time. however, if you're using a factory restore cd, you will not have this option.

---

### Post by superwazn on 2007-06-03
well, the drive i'm trying to format isnt my drive with windows on it. its an external. also, i got gparted to "format" it to fat32, but when i restart and check again, its back to ntfs. this hard drive has got a mind of its own

---

### Post by oilchangeguy on 2007-06-03
> **superwazn said:**
> well, the drive i'm trying to format isnt my drive with windows on it. its an external. also, i got gparted to "format" it to fat32, but when i restart and check again, its back to ntfs. this hard drive has got a mind of its own

a previous poster has correctly said that using a bootable windows cd would be easy. do you have a windows cd?

---

### Post by superwazn on 2007-06-03
er, i dont think so. unless it comes with the windows install cd, then i guess i've still got it. would it really be different than booting into windows anyway?

---

### Post by oilchangeguy on 2007-06-03
you've said that windows does not see the drive. so if you click on my computer, it is not seen as a removable media drive? or something like that. did it come with an install cd?

---

### Post by superwazn on 2007-06-03
sometimes it'll show up, sometimes it wont. there is an install cd, but it came with the HD enclosure and the drivers are for windows 98. shoud i check the manufactuers site for a new driver?
EDIT: wait i foud the install disk that came with the dive itself. what should i do, reinstall it?

---

### Post by vanadium on 2007-06-03
Make sure you know the device name of your drive, e.g. sdb or sdc. in a command prompt, type

sudo fdisk -l

and your ntfs drive should show up. Suppose your ntfs partition is /dev/sdb1

unmount the partition

sudo umount /dev/sdb1

format the partition

sudo mkfs -t vfat /dev/sda1 

the option -t stands for type, and vfat means fat32.

Formatting in vfat surprisingly takes only a few seconds in Linux!

---

### Post by oilchangeguy on 2007-06-03
> **superwazn said:**
> sometimes it'll show up, sometimes it wont. there is an install cd, but it came with the HD enclosure and the drivers are for windows 98. shoud i check the manufactuers site for a new driver?

it probably would'nt hurt. and it sounds like your present windows install has problems. check device manager to make sure there are no problems with the usb controller. if you've got a legal copy of windows on the computer, go to [www.microsoft.com](www.microsoft.com) click on security & updates, click on microsoft updates, and select custom. and install all critical, and hardware updates. check the software updates, and select only those that are needed. and as a last resort, do a clean install of windows.

---

### Post by superwazn on 2007-06-03
ok no way im going to microsofts website again. i had been trying to resolve this drive issue with them before and it took over 3 days of email tag for them to even tell me what i already knew about was wrong and the "hotfix" they gave me didnt do _anything_.  i guess a clean install could help, but and old problem with the drive, gailure to write to it, also was happening in ubuntu in the same way it would in windows, get halfway through writing some data then lock up. so i think its the drive itself just going haywire.

---

### Post by oilchangeguy on 2007-06-03
> **superwazn said:**
> ok no way im going to microsofts website again. i had been trying to resolve this drive issue with them before and it took over 3 days of email tag for them to even tell me what i already knew about was wrong and the "hotfix" they gave me didnt do _anything_.  i guess a clean install could help, but and old problem with the drive, gailure to write to it, also was happening in ubuntu in the same way it would in windows, get halfway through writing some data then lock up. so i think its the drive itself just going haywire.

did i say ANYTHING about emailing or chatting with microsoft? NO! i suggest you re-read my previous post, and get yourself a new internal drive, and do a clean install.

---

### Post by superwazn on 2007-06-03
ok. thanks for all your help. i guess i'll see what i can find at microsoft's site and hope that it does something this time
note to vanadium: after mkfs pretended to format it, it no longer shows up in sudo fdisk -l, just like when gparted pretended to format it too. when i reboot its gonna be ntfs again

---

