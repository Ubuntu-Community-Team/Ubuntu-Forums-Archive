---
title: "Can't read NTFS hard drives"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by GabrielKnight on 2007-07-28
Hello

I just started using Kubuntu 7.04 and am new to linux. My problem is that I can't get either my internal NTFS hard drive or my external USB NTSF hard drive to work. I think the problem is them being NTFS, since the external drive is detected when I plug it in (it asks me what to do with a new portable storage device). Nothing happens after I choose open in a new window though. If I understood correctly, I should use NTFS-config to enable write status to NTFS HDs. The problem is that I cannot get it to work. It seems to install properly, but when I try to open it from the Menu ---> System bar, nothing happens (the logo that should be on the left side of the program name is also missing). Any help would be appreciated.

---

### Post by Malta paul on 2007-07-28
Hi,  Hard drive partitions have to be enabled, Normally  NTFS is read and copy only, but can be made read and write.
Here is a good reference for you that should help: [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy) 
Hope this is of help :wink:

---

### Post by GabrielKnight on 2007-07-28
Thank you for the help. I got the internal HD mounted now with the help of NTFS-config. I got it to work by installing some extra gnome libraries (is that the right term, I needed to get the gksu command). I still can't get the external HD to mount though. I can see it when I sudo fdisk -l, but know of no way I could mount it. Opening NTFS-config only asks me if I want to enable write support for the internal and external drives, but doesn't assist me in creating a mount point, like it did for the internal drive. Any other ideas?

---

### Post by Malta paul on 2007-07-28
Good to hear you have had some success at least.
I have not mounted any external drives myself, only used a USB thumb drive with no problems. I did find some info that may point in the right direction: [https://help.ubuntu.com/community/DrivesAndPartitions?action=fullsearch&value=linkto%3A%22DrivesAndPartitions%22&context=180](https://help.ubuntu.com/community/DrivesAndPartitions?action=fullsearch&value=linkto%3A%22DrivesAndPartitions%22&context=180) 
Have fun :wink:

---

### Post by GabrielKnight on 2007-07-28
Well, since NTFS was the main problem I decided to take the easy way out and repartitioned the whole HD to FAT32 and it worked like a charm. Thanks for all your help though.

---

### Post by Malta paul on 2007-07-28
Great news, Well done :guitar:

---

