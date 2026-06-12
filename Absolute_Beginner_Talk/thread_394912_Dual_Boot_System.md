---
title: "Dual Boot System"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-03-27
Ok all dumb question, I have Xp loaded to Master drive and Ubuntu Dapper to slave drive. Is there a way,without destroying any windoze files, for me to gain access to the windows drive through Ubuntu and still not allow access by anyone else? All I am wanting to do is copy some files over. Might use my USB zip if it will work and I have too.

---

### Post by alienexplorers on 2007-03-27
I am dual booting XP & Ubuntu.  I have XP data on a FAT32 partition.  My fstab looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2	/home		ext3	defaults	0	0
/dev/hda3       /windows        vfat iocharset=utf8,umask=000     0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy   auto    rw,user,noauto  0       0

You could also use the mount command like so:

sudo mount /dev/hd(drive letter) /media/windows

You have to create the mount location in media:

mkdir /media/windows

---

### Post by dstew on 2007-03-27
You need to install the ntfs-3g package from the Synaptic package manager. Use the search button to find it. You might need to enable the Universe repository under the Settings menu first. After ntfs-3g is installed, you can mount ntfs volumes onto your linux filesystem, and read/write them.

All this assumes your XP partition is ntfs. If it is FAT32, linux can mount it already with no new software.

---

### Post by brennydoogles on 2007-03-27
Your flash drive should work fine if you feel like rebooting several times, but your best bet is to mount the windows partition like in the other reply. If you plan on needing to copy files from your windows partition often (like I do) , add this line to the end of your your /ect/fstab

```
/dev/[COLOR="Red"]hda1[/COLOR] [COLOR="Blue"]/home/ubuntu/hdadrive[/COLOR] [COLOR="DarkGreen"]ext3[/COLOR] defaults 0 1
```

changing hda1 to the name of your drive (I would guess hda1, but just to be sure),
the blue text to wherever you want to mount it (I recommend /media/hda1 or whatever the drive is called)
and change the ext3 to whatever filesystem you are using (it will either be NTFS, Fat32, or Fat16)

Restart, and you should be good to go.

If you need help after that, just post!!

---

### Post by brennydoogles on 2007-03-27
> **dstew said:**
> You need to install the ntfs-3g package from the Synaptic package manager. Use the search button to find it. You might need to enable the Universe repository under the Settings menu first. After ntfs-3g is installed, you can mount ntfs volumes onto your linux filesystem, and read/write them.

All this assumes your XP partition is ntfs. If it is FAT32, linux can mount it already with no new software.

Ubuntu can mount NTFS no problem, but writing to your NTFS filesystem from Linux could be disastrous to windows if you don't use a program to help you.

---

### Post by Bigbluecat on 2007-03-27
I have my windows drives mounted. You can use the command listed in the earlier post or add them to you fstab file.

Ubuntu can read NTFS files systems fine without adding any extra programmes. This is sufficient to allow you to copy files from your windows directories and is perfectly safe.

If you also want to write to your NTFS drives you need to install NTFS-3G but I still here some mixed responses about this.

---

### Post by alienexplorers on 2007-03-27
A nice free program that would let you copy files from windows to Ubuntu is:

> Ext2IFS

This program is easy to setup and works like a charm.

It can be found at:

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

It makes your Ubuntu partition into another drive letter.

Say if you are running Windows on C:, it would then make your Ubuntu partition the next available drive letter (Example D: ).  You can then use Windows Explorer to transfer all your files to Ubuntu.

Don

---

### Post by J11Gyro on 2007-03-28
The partitions are not the problem, I just wanted access to a few graphic base files I use all the time that are in windows on a seperate drive. I thought if i got my usb zip working I could just use that as a file storage for both. XP is on a fat 32 master drive.

---

### Post by Bigbluecat on 2007-03-28
Using your USB drive will work perfectly well.

---

