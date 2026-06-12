---
title: "Another newbie with mounting problems"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by e lo on 2006-04-23
Hi, all, 

I'm new to Linux -- I used UNIX for a while in college, but that was the better part of a decade ago, and it's been nothing but Windows boxes since then, so this is a nice change for me.

I have Breezy 5.10 installed on a partition on the same SATA drive as my Win XP NTFS partition. I also created a FAT32 partition. I've been able to mount the NTFS partition fine (with no write priveleges), and I see it on my desktop as expected. I cannot seem to mount the FAT32 partition, however. I created the folder for it in /media using

[INDENT]sudo mkdir /media/sda5/[/INDENT]

I then tried to mount it using

[INDENT]sudo mount /dev/sda5 /media/sda5/ -t vfat -o iocharset=utf8,umask=000[/INDENT]

I recieved the error message 

[INDENT]mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/INDENT]

I've also attached a screen shot of the message, as well as the output from fdisk. I don't have a reference to the sda5 partition in my fstab yet -- I figured I'd wait until I knew that I could mount it before I put that in.

Thanks, and any help would be appreciated.

---

### Post by unbuntu on 2006-04-24
Try mounting in GUI
System->Disks

---

### Post by joshrobinson on 2006-04-24
i would do it in fstab

```
sudo gedit /etc/fstab
```

add the line

```
/dev/sda5       /media/sda5   vfat    umask=0000    0 0
```

then do
```
sudo mount /dev/sda5
```

if it doesnt show up on your desktop, reboot and it should be there

---

### Post by steve.horsley on 2006-04-24
Daft question - have you formatted the partition? If not, format it with windows and then ty again.

---

### Post by e lo on 2006-04-24
Thanks for the suggestions, everybody. Got it fixed.  

I (thought I) had formatted the partition with Gparted, so I didn't think that would have been the problem. 

System->Admin->Disks saw the partition just fine, and saw it as vfat formatted, but it was inaccessable, and couldn't be enabled. I formatted it from within the Disks utility, and it mounted just fine. I also put it in my fstab to mount it automatically @ start up.

Thanks again!

---

