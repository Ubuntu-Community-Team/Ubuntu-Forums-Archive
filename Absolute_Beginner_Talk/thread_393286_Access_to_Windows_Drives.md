---
title: "Access to Windows Drives"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by gusoceros on 2007-03-25
Hi everybody- new to ubuntu linux, I dont know my way around linux very well.  I am running a dual boot machine, its an AMD64, and Im running 6.06 Dapper Drake.

My windows system will not boot- I get an error in the windows system 32 file, it tells me to run the windows Repair feature- which doesnt work, because the windows disk does not boot.  However, joy of joys, my Ubuntu works.

I want to harvest my files from the windows drive, however it tells me I do not have permission to access this hda2 drive- I get this error:

**You do not have the permissions necessary to view the contents of "hda2".**

However- that drive, and the recovery partition are icons on my desktop, and it seems that they both are mounted.

**[COLOR="Blue"]Any ideas how I can give myself access to this drive?  [/COLOR]**

Thanks in advance for your help- 

G

---

### Post by benerivo on 2007-03-25
If it is just a permissions problem, you could try altering the /etc/fstab file in Ubuntu. If you open this file you will see the line containing the mount settings for hda2. Change it to something like this...
/dev/hda2   /media/hda2   ntfs   rw,umask=000   0 0

Your line will very probably be different, but the important bit is to include the rw,umask=000 which will provide all users with full permissions.

---

### Post by AlexKarm on 2007-03-25
Well, I'm relatively new to Ubuntu, but let me give this a shot (People, feel free to correct me if you notice anything wrong):

First, you cannot directly access /dev/hda2, if that is what you are trying to do. Everything in /dev/ (well, almost everything, anyway) is direct access to devices (hardwave, etc) which really isn't a good idea :P

Every drive has to be mounted, which tell the system how to access that drive, such as which file system it uses (NTFS in case of Windows XP), and where to put it (Ubuntu seems to use /media/something to mount things)

To mount your drive always (I assume you don't just want a one time deal), you need to add a line to the fstab. Whenever you modify something, rule one is to back it up. Trust me, it's no fun trying to go back without one. 

sudo cp /etc/fstab /etc/fstab_backup

To open up fstab after you back it up, use:

sudo nano /etc/fstab

You could replace nano with another text editor if you like. Anyway, I use nano a lot, so we will assume you are working with that. To save it's ctrl+O (stands for write-Out), and to exit it's ctrl+X (stands for eXit).

You will see lines for each of the default mounts with comments above each one. Don't worry to much about what is already there. Ubuntu uses UUIDs to mount drives instead of /dev/hda# style. It has it's advantages but looks messy and hard to read. What you need to do is add a line to the end of it that looks something like this:

/dev/hda2   /media/hda2    ntfs    defualts,utf8,umask=007,gid=46    0    1

(For your future information, the important part of that is gid=46. That tells it that people in group 46 have access. Group 46 is the plugdev group, which you should have been added to when you installed Ubuntu)

Save your modified fstab. Next we need to make that folder that it's going to mount it to.

mkdir /media/hda2

Now, it knows what to mount, where to mount it, and how to mount it. You could reboot here, in which case fstab is called when the computer boots, OR, much faster is to use:

sudo mount -a

which mounts everything in fstab again. Please note that you will get a bunch of warnings or errors because you can't mount all the stuff that is already mounted (90% of fstab :P ) but it will work fine.

Once that's done, you should have access to /media/hda2... heck, it might even be on your desktop, but I find that's hit and miss with Ubuntu to date.

Let me know how it goes.

---

### Post by gusoceros on 2007-03-25
> **benerivo said:**
> If it is just a permissions problem, you could try altering the /etc/fstab file in Ubuntu. If you open this file you will see the line containing the mount settings for hda2. Change it to something like this...
/dev/hda2   /media/hda2   ntfs   rw,umask=000   0 0

Your line will very probably be different, but the important bit is to include the rw,umask=000 which will provide all users with full permissions.

Thanks for the quick reply- it appears I do not have permission to edit this file- how do I go about doing this?  Do I navigate to the file, or should I do something with the terminal?

I do understand file hierarchies, but not much about terminal commands yet

G

---

### Post by lamalex on 2007-03-25
add sudo before your command to edit

---

### Post by gusoceros on 2007-03-25
> **AlexKarm said:**
> Well, I'm relatively new to Ubuntu, but let me give this a shot (People, feel free to correct me if you notice anything wrong):

First, you cannot directly access /dev/hda2, if that is what you are trying to do. Everything in /dev/ (well, almost everything, anyway) is direct access to devices (hardwave, etc) which really isn't a good idea :P

Every drive has to be mounted, which tell the system how to access that drive, such as which file system it uses (NTFS in case of Windows XP), and where to put it (Ubuntu seems to use /media/something to mount things)

To mount your drive always (I assume you don't just want a one time deal), you need to add a line to the fstab. Whenever you modify something, rule one is to back it up. Trust me, it's no fun trying to go back without one. 

sudo cp /etc/fstab /etc/fstab_backup

To open up fstab after you back it up, use:

sudo nano /etc/fstab

You could replace nano with another text editor if you like. Anyway, I use nano a lot, so we will assume you are working with that. To save it's ctrl+O (stands for write-Out), and to exit it's ctrl+X (stands for eXit).

You will see lines for each of the default mounts with comments above each one. Don't worry to much about what is already there. Ubuntu uses UUIDs to mount drives instead of /dev/hda# style. It has it's advantages but looks messy and hard to read. What you need to do is add a line to the end of it that looks something like this:

/dev/hda2   /media/hda2    ntfs    defaults,utf8,umask=007,gid=46    0    1

(For your future information, the important part of that is gid=46. That tells it that people in group 46 have access. Group 46 is the plugdev group, which you should have been added to when you installed Ubuntu)

Save your modified fstab. Next we need to make that folder that it's going to mount it to.

mkdir /media/hda2

Now, it knows what to mount, where to mount it, and how to mount it. You could reboot here, in which case fstab is called when the computer boots, OR, much faster is to use:

sudo mount -a

which mounts everything in fstab again. Please note that you will get a bunch of warnings or errors because you can't mount all the stuff that is already mounted (90% of fstab :P ) but it will work fine.

Once that's done, you should have access to /media/hda2... heck, it might even be on your desktop, but I find that's hit and miss with Ubuntu to date.

Let me know how it goes.

OK- I added that line to the fstab, with your assistance- there are now 2 lines in there about the hda2- should I remove the first one?  It still does not give me permissions.

This is what my fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda2       /media/hda2     ntfs    defaults,utf8,umask=007,gid=46 0 1

---

### Post by benerivo on 2007-03-25
> **gusoceros said:**
> OK- I added that line to the fstab, with your assistance- there are now 2 lines in there about the hda2- should I remove the first one?  It still does not give me permissions.

This is what my fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda2       /media/hda2     ntfs    defaults,utf8,umask=007,gid=46 0 1

Yes, remove the first one, and if it still doesn't give permissions after a reboot, then change the line to...
/dev/hda2       /media/hda2     ntfs    rw,umask=000 0 0

---

### Post by gusoceros on 2007-03-25
> **benerivo said:**
> Yes, remove the first one, and if it still doesn't give permissions after a reboot, then change the line to...
/dev/hda2       /media/hda2     ntfs    rw,umask=000 0 0

I removed the first line, tried the sudo mount -a , and it did not work- so I rebooted- and I now have access to that drive.  I cant thank you enough, I have a huge amount of information I now have access to again.  You sir- rock

:guitar: 

Thanks for your help!

Any good links to tutorials and such that could help a person become more acclimated to the terminal usage, and the structure of linux?

G

---

### Post by Yorboy on 2007-03-28
I am pretty new to linux.  I have tried it several times in the past but didn't find it too user friendly until i came upon Ubuntu.  Still need some tweaking 

to use my xp drive (NTFS) and other features.  I have not been able to get my system to be to use my XP drive even though it shows on my fdisk listing.  Have 

tried several things as recommended by the posts on Ubuntu forums, to no avail.  Here is what i have.

AMD 64 3700+ processor
Gigabyte MB with dual channel and Raid, 2gig ram.  Not using the raid at this time.
80g HD with WinXP on the sata connection.  NTFS formated.
80g HD with Ubuntu on EIDE connection.  I have my system booting from this drive with grub.
I am running Ubuntu Edgy 64 bit 6.10.
The sdb drive below is my thumb drive i had attached at the time.

How do i get the system to use the NTFS drive.  I have further instructions on the forums to be able to read/write to the drives but can't use because it 

doesn't recognize it.  I'm stymied.  HELP>>>>>  Oh, by the way, please don't use anacronyms that we newbies don't know.  I don't know what some of them mean. 

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






This resulted after i edited fstab with the following line.  I added the directory /media/sda1 before editing fstab and tried mounting the drive after 

changing the fstab.  I also tried rebooting with the same results.


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


HELP!   I really want to migrate to Ubuntu and wean away from windows.

---

### Post by benerivo on 2007-03-31
Check your line in fstab. The umask option must not be spelt with an 'n' (ie. umask and not unmask). Try setting it to read...
/dev/sda1 /media/sda1 ntfs rw,umask=000 0 0
and reboot.

---

