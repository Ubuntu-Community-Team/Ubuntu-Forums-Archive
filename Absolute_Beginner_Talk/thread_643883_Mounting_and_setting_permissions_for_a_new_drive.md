---
title: "Mounting and setting permissions for a new drive"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Broodmdh on 2007-12-18
I am trying to mount a new 200GB SATA drive that I want to use as a fat32 file repository for the other machines on my network (Vista, XP and ubuntu).  For some reason, even when logged on to the machine itself, I can't move files to the new drive (it must be a permissions problem, but I don't understand it). 

fstab gives me the following:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1219     9791586   83  Linux
/dev/hda2            1220        2435     9767520   83  Linux
/dev/hda3            2436        2557      979965   82  Linux swap / Solaris
/dev/hda4            2558        9729    57609090    b  W95 FAT32

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24792   199141708+   b  W95 FAT32

I've taken a look at a few other posts, and I still can't figure this out.  Any suggestions would be welcome.  Things like this serve as a good reminder as to how little I truly understand linux.

---

### Post by taurus on 2007-12-18
How do you mount /dev/sda1?  Do you use /etc/fstab to mount it when you boot into Ubuntu?  Post your /etc/fstab.

```
cat /etc/fstab
```

---

### Post by Broodmdh on 2007-12-18
This is the output of my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=28394130-d609-49ca-ad04-683ca38339c1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=92cb7baa-b6ab-47dc-91bc-60b60c952653 /home           ext3    defaults        0       2
# /dev/hda4
UUID=68C6-EEF5  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=6b3c460a-d0d7-4661-a53f-ef51612a0cdb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda1       /media/networkdrive vfat        auto,rw,user,exec 0 0

---

### Post by Broodmdh on 2007-12-31
I still haven't had any success in making this drive visible to the other (Windows) computers on my network.  Can anyone offer any suggestions?  I didn't think that it would be so difficult to configure anonymous access to a drive on a local network.  In a possibly related note, I am unable to see any of those other computers from my Ubuntu box either.  Basically, I'm not sure how to proceed and any help would be appreciated.  Thanks.

---

### Post by observative on 2008-01-07
Have you tried looking at the Ubuntu wiki?
[http://ubuntuguide.org](http://ubuntuguide.org)
Im just a newb to Ubuntu too, but I found a lot of answers there.

Hm, Windows computer on your network, I believe this is a more specific wiki entry for you, [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Automatically](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Automatically). It's for NFS (Network File Server) connection mounts, and the entry looks like it uses an IP to do it...and you can connect from win to an IP by adding a network place... perhaps an ftp connection via new network place, if I recall win networking correct. Anyways good luck, you will get it, just keep trying.

---

### Post by qpieus on 2008-01-07
What are the permissions of the /media/networkdrive directory? Your fstab entry for sda1 looks ok, but if the /media/networkdrive directory permissions don't allow a regular user to write there, then that would explain why you can't copy files to that directory. Type in a terminal```
ls -la /media
``` to see the permissions of the subdirectories there.

As far as sharing with windows computers, the read/write abilities would be set by the samba configuration. What does your /etc/samba/smb.conf file look like? (Note that I am far from knowledgeable on samba, so hopefully someone else can join in here to help!)

---

