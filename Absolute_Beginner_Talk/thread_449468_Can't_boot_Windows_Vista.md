---
title: "Can't boot Windows Vista"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by ccl4 on 2007-05-20
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=268837](http://ubuntuforums.org/showthread.php?t=268837) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				hello,
i recently installed the ubuntu 7.04, however, i made the partitions by myself. 
after using ubuntu for a while, i wanted check whether windows still works well, and then it can not start, because of not finding the recovery data, as it stated. as i restarted pc, it shows grub error 17, and ubuntu was also not possible to boot. then i used the windows recovery cd, however grub error 22 was shown when pc was resarted after recovery.

> ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
mkdir: cannot create directory `/mnt/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda? /mnt/ubuntu
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
138 heads, 12 sectors/track, 141571 cylinders
Units = cylinders of 1656 * 512 = 847872 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        6185     5120000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        6185       87416    67259392    7  HPFS/NTFS
/dev/sda3           87416      141570    44838912    f  W95 Ext'd (LBA)
/dev/sda5           87418      141570    44837888    7  HPFS/NTFS
ubuntu@ubuntu:~$ 




so please help!

thanks

---

### Post by Kobalt on 2007-05-20
I hope for you the windows recovery CD hasn't erased the Ubuntu partitions... If it has not then you need to recover Grub [this way]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by ccl4 on 2007-05-20
it shows
>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find/boot/grub/stage1

Error 27: Unrecognized command

grub> 



....:(

---

### Post by Kobalt on 2007-05-20
There is a typo mistake, you must have a space between *find* and */boot/grub/stage1*: > find /boot/grub/stage1

---

### Post by ccl4 on 2007-05-20
>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> 

...

---

### Post by Kobalt on 2007-05-20
Then I fear it has erased your Ubuntu partition... Can you please post the output of ```
fdisk -l
```

---

### Post by ccl4 on 2007-05-20
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
138 heads, 12 sectors/track, 141571 cylinders
Units = cylinders of 1656 * 512 = 847872 bytes

Device Boot Start End Blocks Id System
/dev/sda1 2 6185 5120000 1c Hidden W95 FAT32 (LBA)
/dev/sda2 * 6185 87416 67259392 7 HPFS/NTFS
/dev/sda3 87416 141570 44838912 f W95 Ext'd (LBA)
/dev/sda5 87418 141570 44837888 7 HPFS/NTFS
ubuntu@ubuntu:~$

that you need?

---

### Post by Nekiruhs on 2007-05-20
It looks like it erased your Ubuntu Partition. :cry:

---

### Post by Kobalt on 2007-05-20
It's not there anymore, clearly it erased it.

---

### Post by ccl4 on 2007-05-20
the key question is: what should i do now?

thanks

---

### Post by Kobalt on 2007-05-20
You can reinstall Ubuntu from scratch.

---

### Post by Happy_Man on 2007-05-20
Buddy, the Vista, in all its perceived goodness, has erased your Ubuntu partition out of jealousy. You can reinstall, but it has some quirks. Use this guide:[http://www.apcstart.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://www.apcstart.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by ccl4 on 2007-05-20
however, i just have the recovery dvd, so the options shown there are not available

---

### Post by ccl4 on 2007-05-20
will it work if i install ubuntu first, then use the recovery dvd to install vista?

---

### Post by Happy_Man on 2007-05-20
No, because you'll be right back where you started. An even better idea is to just use the LiveCD version of GParted (System --> Administration --> GNOME Partition Editor) to make ntfs and ext3 partitions, basically make your partitions for both OS's, but DON'T INSTALL UBUNTU YET. Install Vista to the ntfs partition you made (should be at least 15 GB), and then use the guide to install Ubuntu.

---

### Post by ccl4 on 2007-05-20
but as i said that that is only a recovery dvd, i do not have choice where i want to install windows. i think the key point is how to recovery GRUB, however i do not know exactly how.

thanks

---

### Post by Kobalt on 2007-05-20
If you now  have Vista installed, you can boot on a LiveCD of Ubuntu, resize your partition and make space for Ubuntu to install on. It will install and configure Grub as well, listing your Vista, and allow you to have your dual-boot.
There is no need to restore grub here.

---

### Post by ccl4 on 2007-05-20
> **Happy_Man said:**
> No, because you'll be right back where you started. An even better idea is to just use the LiveCD version of GParted (System --> Administration --> GNOME Partition Editor) to make ntfs and ext3 partitions, basically make your partitions for both OS's, but [COLOR="Red"]DON'T INSTALL UBUNTU YET[/COLOR]. Install Vista to the ntfs partition you made (should be at least 15 GB), and then use the guide to install Ubuntu.


i was told that i should not install ubuntu first...

---

### Post by Kobalt on 2007-05-20
> **ccl4 said:**
> i was told that i should not install ubuntu first...
It's the other way around, so that Windows doesn't mess your Grub.

---

### Post by Happy_Man on 2007-05-20
Yeah, you're not, you're just making partitions....

---

### Post by ccl4 on 2007-05-20
well when i tried making new partition, error appear ...

---

### Post by Kobalt on 2007-05-20
Read the error message : it says you need to unmount the partition before resizing it. Go to Places > Computer and right click on your HD/Partition, select unmount, and try again.

---

### Post by ccl4 on 2007-05-20
i did it, 15 GB with ext3, is okay? and which flag should it have?or i do not need to care?
and then i install ubuntu on this partition?

thanks

---

### Post by Happy_Man on 2007-05-20
Don't worry about flags, and yes, that's where you install Ubuntu to....

---

### Post by ccl4 on 2007-05-20
all right i will do that. thx

---

### Post by ccl4 on 2007-05-20
so guys it is done!;), both OS work well,  so thank you all! it's true stating "humanity to others"

regards

---

### Post by Kobalt on 2007-05-20
You're welcome :)

---

### Post by Happy_Man on 2007-05-20
Yay!

---

