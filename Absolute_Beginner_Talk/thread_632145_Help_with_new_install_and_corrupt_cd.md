---
title: "Help with new install and corrupt cd"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by bartoni on 2007-12-05
I need some help! I damaged grub trying to install a bad Gutsy.

Been dual booting ubuntu and XP for a while... decided to upgrade to Gutsy today, downloaded ISO, burnt a CD, booted and started the install... 
I have 2 drives, partitioned up for XP in some way but I forget what is what exactly, I selected manual partition and selected the existing 6gb ext3 partition as root and the existing swap as swap - as these will be the existing ubuntu partitions that I want to overwrite. 

Install starts, gets some way through and then complains of a bad CD.  I reboot and do the CD check, sure enough it fails. I decide to reboot into XP and burn using nero at 2x... only I can't, GRUB is throwing an error.

I'm now running from the live CD unable to access XP (or my previous ubuntu installation of course).  Could someone please help me restore grub so I can get back into Windows?

Help really appreciated

---

### Post by subs on 2007-12-05
how far did the installer progress b4 it gav u that error message

---

### Post by PmDematagoda on 2007-12-05
You can use [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download") to try and restore your XP boot-loader or GRUB.

Or, a better way(Since you cannot burn the Super GRUB CD), edit you menu.lst file.

If you wish to edit the menu.lst file, then you may first post the file here. I believe you can mount the file systems manually on the Live CD, so if you could provide us with the locations, we can help you get them mounted.

---

### Post by bartoni on 2007-12-05
> **PmDematagoda said:**
> You can use [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download") to try and restore your XP boot-loader or GRUB.

Or, a better way(Since you cannot burn the Super GRUB CD), edit you menu.lst file.

If you wish to edit the menu.lst file, then you may first post the file here. I believe you can mount the file systems manually on the Live CD, so if you could provide us with the locations, we can help you get them mounted.

Where is the menu.lst file?  I can't find any grub files from my previous install.

Don't remember exactly where the install failed, it was quite early into the install just after the name and password were entered.

---

### Post by PmDematagoda on 2007-12-05
Then your partition may not be mounted. Hmm, don't know if this may work, but try:-

```
cat /etc/mtab
```

---

### Post by bartoni on 2007-12-05
> **PmDematagoda said:**
> Then your partition may not be mounted. Hmm, don't know if this may work, but try:-

```
cat /etc/mtab
```


Gives this...

proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev/sda6 /media/BACKUP vfat rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree 0 0
/dev/sdb1 /media/disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb2 /media/disk-1 ext3 rw,nosuid,nodev 0 0

---

### Post by PmDematagoda on 2007-12-05
Oh, it works, nice:).

So now could you check out disk-1? It could be your old Ubuntu OS partition. If so, post what you get in /boot/grub/menu.lst.

---

### Post by bartoni on 2007-12-05
/media/disk-1 is linux, but doesn't look like my old ubuntu install (none of my own stuff in home/) 

disk-1's boot contains...

abi-2.6.22-14-generic     initrd.img-2.6.22-14-generic.bak  System.map-2.6.22-14-generic
config-2.6.22-14-generic  memtest86+.bin                    vmlinuz-2.6.22-14-generic

looks like possibly current live cd stuff?


/media/disk looks like my windows partition

Is it possible to recreate grub, or remove it from MBR?

---

### Post by PmDematagoda on 2007-12-05
From what you said in your first post, you said that you reinstalled Ubuntu on the older root partition, did you by any chance keep an isolated Home partition? If not then your old Home directory is gone.

---

### Post by bartoni on 2007-12-05
> **PmDematagoda said:**
> From what you said in your first post, you said that you reinstalled Ubuntu on the older root partition, did you by any chance keep an isolated Home partition? If not then your old Home directory is gone.

Yeah my plan was to completely wipe my old ubuntu install including home directories, so no surprise to see it gone.  At the moment I'd just like to get back into XP so I can burn another CD and try again. Grub is complaining about missing files (error 15) and not letting me in .  I release my old ubuntu install has gone, along with the grub stuff it seems.

---

### Post by PmDematagoda on 2007-12-05
Missing files could mean that it is missing the menu.lst file. Do you see a Grub directory in the Boot directory of where you are right now?

---

### Post by bartoni on 2007-12-05
No, the only boot directory is the one I posted 4 posts back.

Is there a way to remove grub from the mbr in linux?

---

### Post by PmDematagoda on 2007-12-05
If you have the Windows XP CD, then you repair the MBR using the Fix MBR option.

---

### Post by bartoni on 2007-12-05
I don't have a Windows CD here. Is that the only way to fix this?

---

### Post by PmDematagoda on 2007-12-05
Well, you could try getting the files in the Grub folder from another person and then edit them to fit your PC.

---

### Post by bartoni on 2007-12-05
but there isn't a grub folder... I suspect the boot folder I see now is some kind of temporary / Live CD thing?

---

### Post by bartoni on 2007-12-05
I see supergrub has a floppy image... unfortunately the program to copy the image to the disk is windows! argh.

---

### Post by PmDematagoda on 2007-12-05
What about the USB image? It seems possible.

And I believe that the folder you are looking at is from the old Ubuntu partition since it states in mtab:-
```

/dev/sdb2 /media/disk-1
```

---

### Post by bartoni on 2007-12-05
I found an old XP CD.  All is well! I'll download and burn another CD now, this time I'll verify the CD before I start.

 Thanks for your help.

---

### Post by PmDematagoda on 2007-12-05
Glad I could help:), and good luck with your new install, and just to be on the safe side, check the CD for defects before installing.

---

