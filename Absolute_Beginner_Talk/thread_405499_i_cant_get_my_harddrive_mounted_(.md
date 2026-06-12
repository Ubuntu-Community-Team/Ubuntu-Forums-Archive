---
title: "i cant get my harddrive mounted :("
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by drab on 2007-04-09
i took a harddrive from my little bro n put it in my comp but i was wondering how to get the thing to mount cuz im retarded :*( i cant seem to get windows to see the damn thing and when i went to go onto ubuntu i was able to see the drive. so i wana copy the stuff off the drive n put it on my linux partition. so i can get the files that are stranded on the drive :) the one i want to mount is the 160gig harddrive

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       23733   190635291    7  HPFS/NTFS
/dev/hdc2           23734       36483   102414375    c  W95 FAT32 (LBA)

Disk /dev/hdd: 30.0 GB, 30000000000 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3495    28073556   83  Linux
/dev/hdd2            3496        3647     1220940    f  W95 Ext'd (LBA)
/dev/hdd5            3496        3647     1220908+  82  Linux swap / Solaris

---

### Post by taurus on 2007-04-09
If you want to access Linux partitions from Windows, you need to install fs-driver first, [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by drab on 2007-04-09
thats not what i meant. the harddrive i just put in isnt showing up in windows and its ntfs format so what i want to do is since i can actually see it in linux i want to mount the hd and then copy over all the files on it to my fat32 partition from linux. is that possible? :/ or so i need to be in windows to copy from ntfs to fat32?

---

### Post by taurus on 2007-04-09
Then, you just need to mount that harddrive under Ubuntu and copy whatever you want to vfat partition then.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by poppers1957 on 2007-04-09
I want to get this off quick because it may save you a BIG headache!!!!!!!!!!!!!!!!  [http://www.softpedia.com/get/System/Hard-Disk-Utils/Maxtor-Big-Drive-Enabler.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Maxtor-Big-Drive-Enabler.shtml)
Go to this site and download the big disk drive enabler.  If you try to access any more then 137 gig in windows, you WILL lose your data.  

Anything else you ever need to know about Linux is in IRC in the freenode server.  There are channels there for any Linux version.  Forums are really nice, but with xchat that I use, live chat assistance is sometimes nicer.

---

### Post by drab on 2007-04-09
um i had a 300 gig harddrive as my main drive that was just one partition and i didnt lose my data :/ are you sure thats right? :/ also ive had that hardrive as just something to hold data for a while with one partition of 149 gigs or so. ive never lost my junk :/ also i think i used a thing called diskmounter one time what is that? im sorry im retarded i cant remember anything when i get really pissed while working on comps..i used disk  mounter to mount my main windows partition and my fat32 patition does anyone know wat im talkin bout? if i could figure out how i did it b4...ugh..

---

