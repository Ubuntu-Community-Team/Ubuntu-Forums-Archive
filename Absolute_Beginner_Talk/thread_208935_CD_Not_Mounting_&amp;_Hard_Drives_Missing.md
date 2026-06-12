---
title: "CD Not Mounting &amp; Hard Drives Missing"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by bludhound on 2006-07-04
Hi there, I'm totally new to Linux, and after some considerations, I decided that Ubuntu would be the best choice for me. After a few days of working around with the installation, my Ubuntu 6.06 LTS desktop is finally up and running. Well, sort of.

Following some forum posts, I have successfully mounted my hard drives, and they appeared in 'Places / Computer'. Next, I proceeded on to try out my DVD-ROM and DVD-RW drives. They are the HL-DT-STDVD-ROM GDR8164B (LG) and IOMEGA DVDRW12448IND-B respectively. Only the LG DVD-ROM appeared in 'Places / Computer'. Next, I did an update.

After my kernel has been updated to 2.6.15-25-386, however, all my hard drives disappeared from 'Places / Computer' mysteriously. They can still be accessed on their respective mount paths though.

The second, more serious problem is that my DVD drives started to behave strangely after the update. When I placed a CD/DVD into any of the drives, the system would detect the media as a blank media, and would refuse to mount it.

I decided to try mounting the CD/DVD manually. On the Desktop and 'Places / Computer', the 'Blank CD/DVD' icon would still remain, but if I browse straight into the mount path, I would be able to read the files from the media. However, I would be unable to open my drive door until I tried a reboot.

I would really appreciate it if anyone is able to help me with my problems. Is there any more detail I need to provide?

---

### Post by givré on 2006-07-04
Yeah, we need more information.
First past here what you have in /etc/fstab (which set the option of your devices), and the result of the command
```
sudo fdisk -l
```

---

### Post by bludhound on 2006-07-04
[QUOTE=givré]Yeah, we need more information.
First past here what you have in /etc/fstab (which set the option of your devices), and the result of the command
```
sudo fdisk -l
```[/QUOTE]
Whoo! Thanks for helping out!
Here is my fdisk output:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2499    20073186    7  HPFS/NTFS
/dev/hda2   *        2500        4892    19221772+  83  Linux
/dev/hda3            4893        4998      851445    5  Extended
/dev/hda5            4893        4998      851413+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4865    39078081    7  HPFS/NTFS

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4982    40017883+   7  HPFS/NTFS
/dev/sda2            4983        9964    40017915    7  HPFS/NTFS
/dev/sda3            9965       14946    40017915    7  HPFS/NTFS


-----------------------------------------------------------------------------------

And here's what's in my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1	/cdrive		ntfs	nls=utf8,umask=0222 0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1	/games		ntfs	nls=utf8,umask=0222 0
/dev/sda1	/documents	ntfs	nls=utf8,umask=0222 0
/dev/sda2	/multimedia	ntfs	nls=utf8,umask=0222 0
/dev/sda3	/devngraphics	ntfs	nls=utf8,umask=0222 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd	/media/cdrom1	udf,iso9660 user,noauto     0       0

---

### Post by givré on 2006-07-04
ok, everything seems to be correct there, so the problem is not here.
When you try to mount manually your DVD, do you use the terminal or a gui?
If you don't try from a terminal, try that
```
sudo mount /dev/hdd #or /dev/hdc depending of the device of your DVD player
```
and see what output you have.

---

### Post by bludhound on 2006-07-04
Yep, I used the terminal to mount my DVD manually. There was no output, so I assumed it was successful. I can't access the DVD from the Desktop and 'Places/Computer' though - it is still displayed as a blank DVD. However, I can still access it from /media/cdrom.

---

### Post by givré on 2006-07-04
So i guess the problem is gnome-volume-manager, and it's could be why you don't see all your device in place>cumputer.
I'm not yet one my ubuntu box, so i couldn't check some things, but i will try to help you more.
For the moment, the best way to unmount your DVD player is
```
sudo umount /dev/hdd
```
But we should be able to fix your problem.

---

### Post by bludhound on 2006-07-04
Alright, thanks a lot. In the meantime I'll play around with the settings. I am going to reinstall my Ubuntu once I finish backing up all my NTFS partitions.

---

### Post by givré on 2006-07-04
I'm back.
So if i'm right the problem is gnome-volume-manager, we can try to lauch it in non-daemon mode to know what's happens.
First kill it 
```
killall gnome-volume-manager
```
and then restart it in no-daemon mode
```
gnome-volume-manager
```
You could already check the settings, but if you didn't change them, that's should be ok.
Then try to insert a dvd or a cd to know what's happens.

Try to insert also a CD audio, this type of cd isn't manage by g-v-m and we could be sure that the problem is really g-v-m.

---

### Post by bludhound on 2006-07-05
I've restarted the gnome volume manager in no-daemon mode, but nothing unusual seemed to show up.

I have tried to insert an audio CD, and nothing happened at all. I subsequently loaded up Totem and tried to open the CD, but it displayed an error saying that my CD wasn't mounted. Next, I tried Sound-Juicer instead. It did not detect my audio CD. So following that, I went into the terminal and tried to mount the audio CD. An error appeared, saying that I tried to mount a volume with an invalid FS.

Anyway, I redid a clean installation of Ubuntu, and applied the updates once again. This time, my hard drives appear on the Desktop and in 'Places / Computer', so that issue is gone. In addition, my USB mass-storage devices mount as per normal. However, the problem with my DVD-ROM drive and DVD-RW drive still persists. In summary,

1) My CDs and DVDs are always detected, but as a blank media, on both of the drives. And they aren't mounted automatically.
2) I can't load and mount audio CDs
3) As for data CDs and DVDs, I can mount/unmount them in the terminal as required.
4) Even after I manage to mount the CD/DVD, I can't access the CD/DVD via the 'CD-ROM Disc' icon on the Desktop/Places/'Places/Computer'. It will bring me to CD Creator when I try to do so. I can access my CD/DVD via /media/cdrom0, though.

One thing I should be glad about now is that at least I can still access my DVD drives, although I have to do the mounting and unmounting manually. However, I would still very much hope that someone has a solution/workaround for this annoying problem I am facing.

---

### Post by bludhound on 2006-07-06
Latest update - I tried inserting an audio CD and starting the CD Player applet, and it said 'Drive Error'.

---

### Post by bludhound on 2006-07-07
Hmm.. I have been trying out different flavors of Linux for the past few days, and I realized that this problem is common to all flavors of Linux. Therefore, I conclude that it is probably a kernel issue.

Oh, and I forgot to mentioned, I can never start any distro of Linux without using the irqpoll option.

I'm still patiently hoping for someone who can help me work out a solution to the problem.

---

### Post by bludhound on 2006-07-07
Hohoho!! Finally I got it to work!! I randomly hacked away at some SATA settings in my BIOS and now everything's working! Now I'm happy..

---

