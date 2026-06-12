---
title: "Using External Hard Drives"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by jdlainez on 2007-09-30
Hi guys:

 I am about to switch from Windows XP to Ubuntu  and I already stored all my data in my external Hard drive.  Does anybody know if this hard drive will work OK once Ubuntu is installed?
My HD is " Western Digital My Book Essential 250 GB USB External Hard Drive".

 Thanks.

---

### Post by hotweiss on 2007-09-30
Yes, all of your data will still be there. If it's partitioned with NTFS and FAT32 you'll be able to read it. If it's partitioned with FAT32 you'll be able to write with no problems and if it's partitioned with NTFS you'll need to install NTFS-3g to write. You can install NTFS-3g with out any problems using Automatix2.

---

### Post by eph1973 on 2007-09-30
I use a dual boot setup, with a Seagate Free Agent Desktop 500 GB External USB HD.  In fact, I run Ubuntu from this drive.  If you already transfered data from your XP to your external HD, you may want to install ntfs-3g so you can write to the HD, assuming its file system is NTFS.  One problem I had is with Linux remounting the drive as read only after it spun down (happens if it is not used for like 10 minutes).  There's a work around with that to make some shell scripts to make it so that Linux will allow the drive to restart without mounting it as read only.

Let me know if you want to know what I did for the spin down issue.  Also if you do want to know, let me know which version of Ubuntu you are running

---

### Post by TimPJones on 2007-10-12
I have the problem with a freecom external usb hard drive so the script would be useful.

I also have a problem because I have several users set up. When switching between users the second user is unable to mount the drive unless the first one unmounts it first. Is there a way round this as all the shared files are stored on this drive.

Thanks

---

### Post by danwosere2007 on 2007-10-12
Hi im having problems with my external 500gb mybook, to start it worked fine (albeit with read only access), but recently it totally stopped working, and also i would like to be able to write to it, as thats the purpose of it, to back things up!, other than that some kind soul helped me with a problem with my screen resolution which has now been resolved, and i shall continue using Ubuntu for a bit. Just need to sort this harddrive problem and all will be excellent. Any ideas or suggestions would be appreciated. Cheers - Dan.

---

### Post by eph1973 on 2007-10-12
Here's what I have done to deal with the spin down issue.

Open up gedit, and add the following to a new file:
```
BUS=="scsi",KERNEL=="sd?",SYSFS{vendor}=="Seagate"SYSFS{model}=="FreeAgentDesktop",RUN+="/usr/bin/usbhdfix %k"
```
and save the file as "85-usb-hd-fix.rules"
Of course, if you have a different make/model of your external HD, you would change the {vendor} and {model} information accordingly.

Now open a new file in gedit, and enter the following:
```

#!/bin/bash
echo 1024 > /sys/block/sda/device/max_sectors
echo 1 > /sys/block/sda/device/scsi_disk:0:0:0:0/allow_restart

```
and save this file as "usbhdfix"

Now, if you are not already in the the terminal, go to the terminal, and type the following (assuming you are in the directory you made the previous two files):
```

sudo cp 85-usb-hd-fix.rules /etc/udev/rules.d
sudo cp usbhdfix /usr/bin

```

I do not run a NTFS file system on my external USB hard drive.  If you are looking to use a NTFS file system, you might want to check out this [howto]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G").

---

