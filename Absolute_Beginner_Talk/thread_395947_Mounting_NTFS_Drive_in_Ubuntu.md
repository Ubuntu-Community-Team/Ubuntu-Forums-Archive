---
title: "Mounting NTFS Drive in Ubuntu"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Yorboy on 2007-03-28
I am pretty new to linux. I have tried it several times in the past but didn't find it too user friendly until i came upon Ubuntu. Still need some tweaking

to use my xp drive (NTFS) and other features. I have not been able to get my system to be to use my XP drive even though it shows on my fdisk listing. Have

tried several things as recommended by the posts on Ubuntu forums, to no avail. Here is what i have.

AMD 64 3700+ processor
Gigabyte MB with dual channel and Raid, 2gig ram. Not using the raid at this time.
80g HD with WinXP on the sata connection. NTFS formated.
80g HD with Ubuntu on EIDE connection. I have my system booting from this drive with grub.
I am running Ubuntu Edgy 64 bit 6.10.
The sdb drive below is my thumb drive i had attached at the time.

How do i get the system to use the NTFS drive. I have further instructions on the forums to be able to read/write to the drives but can't use because it

doesn't recognize it. I'm stymied. HELP>>>>> Oh, by the way, please don't use anacronyms that we newbies don't know. I don't know what some of them mean.

Thanks in advance for any help.


My fdisk -l results:

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


Device Boot Start End Blocks Id System
/dev/hdb1 * 1 9331 74951226 83 Linux
/dev/hdb2 9332 9729 3196935 5 Extended
/dev/hdb5 9332 9729 3196903+ 82 Linux swap / Solaris


Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


Device Boot Start End Blocks Id System
/dev/sda1 * 1 9728 78140128+ 7 HPFS/NTFS


Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes


Device Boot Start End Blocks Id System
/dev/sdb1 1 992 999813+ 6 FAT16


This resulted after i edited fstab with the following line. I added the directory /media/sda1 before editing fstab and tried mounting the drive after

changing the fstab. I also tried rebooting with the same results.


gksu gedit /etc/fstab

/dev/sda1 /media/sda1 ntfs defaults,unmask=0 0 0

It also did the same error message when i edited fstab for /dev/sda1 /media/sda1 ntfs rw,unmask=000 0 0
the same occured when i used dev/sda1 /media/sda1 ntfs defualts,utf8,umask=007,gid=46 0 1


(gedit:5924): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified
are supported and host-based authentication failed.

royboy@royboy-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so


This is the dmesg i get for these errors.

~$ dmesg | tail
[ 126.549466] Bluetooth: HCI device and connection manager initialized
[ 126.549477] Bluetooth: HCI socket layer initialized
[ 126.601746] Bluetooth: L2CAP ver 2.8
[ 126.601749] Bluetooth: L2CAP socket layer initialized
[ 126.604990] Bluetooth: RFCOMM socket layer initialized
[ 126.605003] Bluetooth: RFCOMM TTY layer initialized
[ 126.605005] Bluetooth: RFCOMM ver 1.7
[ 139.110646] FAT: utf8 is not a recommended IO charset for FAT filesystems,
filesystem will be case sensitive!
[ 658.560296] NTFS driver 2.1.27 [Flags: R/O MODULE].
[ 658.561094] NTFS-fs error (device sda1): parse_options(): Unrecognized mount
option unmask.


HELP! I really want to migrate to Ubuntu and wean away from windows.
Edit/Delete Message

---

### Post by h0ax on 2007-03-28
Hey there, I will try not to use any acronyms, but I apologize in advance if I do.

Are you wanting to read/write on the drives or just simply read them?

---

### Post by Yorboy on 2007-03-28
The drive does not even show anywhere on my system except in the fstab.  I can't even mount it.  It doesn't show on my desktop, in the mount directory or anywhere else.  I have been trying to get the system to recodnize it so i can at least see it.  It must have somethng to do with the coding in the fstab and being a sata drive.  Tried everything i have found on the forum, to no avail.

---

### Post by DreamcastJack on 2007-03-28
I would also like to know how to just read mine, and I cant find mine in the same way as mentioned I'm using Ubuntu Edgy. my specs are.

Biostar Geforce 6100-m9 mobo
AMD Athlon 64 3200+
40gb and 20gb HDDs (20gb is the one I need into)
1gb ddr400 ram.

thanks.

---

### Post by machoo02 on 2007-03-28
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=217009&") for mounting ntfs drives

---

### Post by Yorboy on 2007-03-29
Thanks for the suggestion. But i have alreadry tried that thread.   :(

---

### Post by Yorboy on 2007-03-31
Well, after all that effort in Edgy, i decided to upgrade to Fiesty 7.04 Beta.  

All my problems have been solved.  Great work on the Fiesty product.  I now have access to read my NTFS, can copy and paste from it.  etc.  My screen refresh rates are now very good.

Thanks for all those that tried to help me solve the 6.10 issues.

---

### Post by theninthdimension on 2007-03-31
I might be able to help. I just mounted my Windows C drive in my Ubuntu 6.10 install yesterday using the directions in "The Official Ubuntu Book".  I will attempt to underline all computer commands that you need to type. Here goes:

	Open a terminal window and type _sudo fdisk -l_ you will probably be required to enter your password. This command will return a list of all the drives your computer is recognizing. My return looks like this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       60408   485179065    7  HPFS/NTFS
/dev/sda3           60410       60801     3148740   db  CP/M / CTOS / ...

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59665   479259081   83  Linux
/dev/sdb2           59666       60801     9124920    5  Extended
/dev/sdb5           59666       60801     9124888+  82  Linux swap / Solaris

	What you want to look for is the device listed as an NTFS type. Mine is the /dev/sda2 listing above. This is what you will want to mount. Once you have found the drive's location, you will want make a place to mount the drive (I always crack up when I think of mounting drives). Anyway, the book recommends creating a mount point in the &#8220;media&#8221; file on your main file system. To do this, type _sudo mkdir /media/C_ In this case the C is the drive letter.

	Now, for mounting that bad boy. To do this, you need to make changes to your &#8220;fstab&#8221; file in the /etc directory. You may want to make a back-up of the file before you modify it. I didn't, and everything worked fine, but sometimes fortune favors the dumb. Anyway, you will now need to type the command _sudo gedit /etc/fstab_ in your terminal. This will bring up the fstab file. Mine looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c791e04d-fe04-4fe7-975a-786b398a5abd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=5dacee55-3692-4556-98e3-6111cb268835 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

	At the bottom of this list, you simply need to type the following entry and then hit the save button:
[U]/dev/sda2	/media/C	ntfs	nls=utf8,umask=0222	0	0
[/U]
	The /dev/sda2 refers to the device that the sudo fdisk -l command should have returned (see above). The /media/C entry tells the file where this disk should be mounted. The ntfs entry tells the file what format the beast is in. The nls=utf8,unmask-0222 entry allows any user on your Ubuntu install to read the file (I don't know how to modify this yet). I have no idea what the two 0s following this mean, but they were in the book so I added them.

	The last thing you will need to do in the terminal is actually activate the mount. You do this by typing _sudo mount -a_. This immediately mounted the C drive for me, but you might have to restart your X-windows session by typing Ctrl+Alt+Backspace. Make sure that anything you want saved is already saved before you do this.

	I have had no trouble reading any of the files that are readable on my C drive through this technique. I don't think you can edit them, but I haven't tried that yet.

Jeff.

---

