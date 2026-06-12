---
title: "NTFS in Ubuntu 6.06 LTS"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-04-05
As the title suggests, I'm trying to get Ubuntu to be able to mount my NTFS partition.

I looked at the Community Contributed Documentation, and it tried to explain some stuff, but it REALLY doesn't make sense to me.

I find it incredibly confusing and I have no idea what it's asking me to do. It asks me to install some repositories, which I can't find, and asks me to do some terminal commands (I think?) which give the following response:

```

sudo: deb: command not found

```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28NTFS%29]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28NTFS%29")

Can someb)ody please explain to me in incredibly simple terms how I can get Ubuntu 6.06 LTS to mount my NTFS XP partition?

Thanks alot to anybody who helps in this matter.

---

### Post by taurus on 2007-04-05
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```
Assuming /dev/hda1 is your ntfs partition.

---

### Post by teaker1s on 2007-04-05
[http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by theninthdimension on 2007-04-05
I might be able to help. I just mounted my Windows C drive in my Ubuntu 6.10 install yesterday using the directions in "The Official Ubuntu Book". I will attempt to underline all computer commands that you need to type. Here goes:

Open a terminal window and type sudo fdisk -l you will probably be required to enter your password. This command will return a list of all the drives your computer is recognizing. My return looks like this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 * 7 60408 485179065 7 HPFS/NTFS
/dev/sda3 60410 60801 3148740 db CP/M / CTOS / ...

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 59665 479259081 83 Linux
/dev/sdb2 59666 60801 9124920 5 Extended
/dev/sdb5 59666 60801 9124888+ 82 Linux swap / Solaris

What you want to look for is the device listed as an NTFS type. Mine is the /dev/sda2 listing above. This is what you will want to mount. Once you have found the drive's location, you will want make a place to mount the drive (I always crack up when I think of mounting drives). Anyway, the book recommends creating a mount point in the “media” file on your main file system. To do this, type sudo mkdir /media/C In this case the C is the drive letter.

Now, for mounting that bad boy. To do this, you need to make changes to your “fstab” file in the /etc directory. You may want to make a back-up of the file before you modify it. I didn't, and everything worked fine, but sometimes fortune favors the dumb. Anyway, you will now need to type the command sudo gedit /etc/fstab in your terminal. This will bring up the fstab file. Mine looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=c791e04d-fe04-4fe7-975a-786b398a5abd / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb5
UUID=5dacee55-3692-4556-98e3-6111cb268835 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

At the bottom of this list, you simply need to type the following entry and then hit the save button:
/dev/sda2 /media/C ntfs nls=utf8,umask=0222 0 0

The /dev/sda2 refers to the device that the sudo fdisk -l command should have returned (see above). The /media/C entry tells the file where this disk should be mounted. The ntfs entry tells the file what format the beast is in. The nls=utf8,unmask-0222 entry allows any user on your Ubuntu install to read the file (I don't know how to modify this yet). I have no idea what the two 0s following this mean, but they were in the book so I added them.

The last thing you will need to do in the terminal is actually activate the mount. You do this by typing sudo mount -a. This immediately mounted the C drive for me, but you might have to restart your X-windows session by typing Ctrl+Alt+Backspace. Make sure that anything you want saved is already saved before you do this.

I have had no trouble reading any of the files that are readable on my C drive through this technique. I don't think you can edit them, but I haven't tried that yet.

Jeff.

---

### Post by Neon_Knight on 2007-04-05
Wow!

+Googolplex hit points for you, my friend!

Thanks alot, that explained EVERYTHING I needed to know!

:guitar: 

And now I can listen to my 2,500 tracks of music even though Windows XP is completely dead!

:lolflag:

---

### Post by the.csmith on 2007-04-10
I would also like to thank you for your simple explanation.  

I knew it shouldn't have to involve downloading software and the like.  

Cheers!

---

