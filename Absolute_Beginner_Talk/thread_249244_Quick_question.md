---
title: "Quick question"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Imsati on 2006-09-02
Hello everyone! About a week ago, I reinstalled UB just to start fresh and not worry about what I tried to do and didn't try to do. The install went perfect, but now when I boot to UB I get an odd message. 

Before, I had installed UB with my XP drive disconnected, When I connected the XP drive, and booted from UB, it would go normal with no problems, but I couldn't see the XP drive on the UB /Computer.

During the re-install, I had installed UB with the XP drive attached. XP is set as Master (and 1st boot), UB as Slave. When I enter the Boot Menu to load up UB, I now get 4 options (Boot UB Normal, boot UB in recovery mode, something else (looks like code), and boot from XP). That wasn't there before the re-install. I just select Boot UB normally, and it loads up. However, during the loading (after opening the kernal and the first part of the checklist) it goes to a full-screen DOS-view and starts loading stuff from there. Eventually, it comes to a part where it says 'not automatically fixing this' and holds for about 5-8 seconds. After that, it continues to boot and enters the sign-in screen. Everything is perfect after that.

Any thoughts? Random? Try a re-install again?

It runs fine, I'm just curious and don't want it to create problems in the future.

Thanks!

--Jay

---

### Post by jorn on 2006-09-02
It would be informative if you could tell us what is being loaded when the screen turns text-based. And before the message:'not automatically fixing this'.

---

### Post by Imsati on 2006-09-02
it just scrolls so fast. I'll watch it a few times and see if I can decipher any of it.

---

### Post by macdo on 2006-09-02
Try running fsck from the command line. Read the man page first, though!
```
man fsck
sudo fsck
```
The screen you're seeing at boot is the Grub menu - it allows you to choose your OS or do a memory test.

HTH

---

### Post by Imsati on 2006-09-02
Ok, the Ubuntu loading screen (Logo, things coming up 'OK') pauses on the check all filesystems, then goes into the DOS-type. From what I can tell, it's looking at the XP drive when the 'not automatically fixing this' is displayed. Afterwards, things go back to the Ubuntu logo screen and loads right up.

I tried the 'man fsck' and browsed through that, then the 'sudo fsck' (I selected 'no' b/c I wasn't sure what would happen.

If I take away the XP drive, will it go normally? Also, my XP drive is on the Master end of the IDE, but jumped to Slave (and 1st boot), and my UB is on the Slave end, but jumped to Master. Could that be the cause of anything?

---

### Post by macdo on 2006-09-02
When you selected "no", what was the question?

At a guess, Windows is on the HD you boot from - so I wouldn't unplug it (although you can try...)

---

### Post by Imsati on 2006-09-02
tI answered 'no' to the question... "Running e2fsck on a mounted filesystem may cause SEVERE damage. Do you really want to continue?"

---

### Post by macdo on 2006-09-02
hmm, fsck is trying to check your Ubuntu disk.
Try using the chkdisk utility in Windows - rightclick on the HD in My Computer, then choose Tools.

---

### Post by Imsati on 2006-09-02
Checkdisk is fine.

XP is formatted as FAT32 (not a new install, upgraded from 98SE)
UB is all ext3 formatted

I'm just going to try a re-install of UB later and see what happens. Trial and error, right? <grin>

Thanks a bunch!

---

### Post by jorn on 2006-09-02
Could you paste the output of:
> sudo cat /etc/fstab
I want to see if there are any hints here.

---

### Post by Imsati on 2006-09-02
Yes, I will in a few minutes once I get back on the Ubuntu OS.

Can FAT32 be read by Ubuntu? All of the partitions on that drive are ext3. I'd like to make one that is FAT32 so Windows can read it, but when I installing Ubuntu and trying to make a partition with that file system, I always recieved an error message.

---

### Post by macdo on 2006-09-02
Fat 32 can be read and written to by Ubuntu - but so can NTFS if you install the right thing: [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)

Your choice!

---

### Post by Imsati on 2006-09-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hdb1       /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda4       /usr            ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Imsati on 2006-09-02
Macdo,

Were I going to do all of that in Windows, I'd be all over it. But at this point in my Linux learning curve, I'm not ready to try that yet--I know my limits.

I know how to create partitions during the Setup, but *where* should the FAT32 directory be? I tried making /home FAT32, but always wound up with the error message saying it couldn't be placed there.

Current partitions are...

Swap - 1GB Partition 1
/root - 4 GB Partition 2
/home - 40 GB Partition 3
/usr - 10.9 GB Partition 4

---

### Post by jorn on 2006-09-02
I hope this:
dev/hda4 /usr ext3 defaults 0 2
is placed on it's ovn line or else I think it causes trouble.
Is it a pasting failure?
Normally the /(root patition) is mounted on the first partition.
Well, I'm not an expert, maybe others could analyse this.

---

### Post by Imsati on 2006-09-02
Jorn,

Yes, it was a pasting error.

See partition info in above post

---

### Post by macdo on 2006-09-02
```
/dev/hdb1 /media/hdb1 vfat
```

That means that the device known as hdb1 (the first partition on the second hard drive) has a mount point at /media/hdb1. It uses the vfat file system (that's fat32 to most people...).
hda1 is swap, hda2 is root, hda3 is home, hda4 is usr.

Use nautilus to have a look at it - if there is nothing there, then in a console, type ```
sudo mount /dev/hdb1
```

There is also a neat prog that installs ext2/3 drivers in windows, if you're interested... ext2ifs is it's name. [http://www.fs-driver.org/](http://www.fs-driver.org/)

HTH

---

### Post by Imsati on 2006-09-02
the hdb1 disk is the XP hard drive

I'm going to look into that ext 2/3 thing for XP

---

