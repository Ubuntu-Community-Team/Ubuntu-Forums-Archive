---
title: "root permissions"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-28
is it possible to give a user account the equivalent permissions of root?  if so, can someone please tell me how this can be done?

i have read posts from people asking this same question and the first responses i see to them are to advise against it and to question why someone would ever want to so this..

i completely understand the risks and security factors related to this type of change, and i would not ask unless i knew what it could do to my system.

any information would be greatly appreciated.  thanks.

---

### Post by emarkd on 2008-01-28
Well, any user that is in the admin group has root permission through sudo.  Is that what you're asking?

---

### Post by taurus on 2008-01-28
If you want somebody to modify system files with root privilege, just add the username of that person to group admin.  Then, he/she can use sudo/gksudo.

```
sudo useradd **username** admin
```

---

### Post by PeterJS on 2008-01-28
The answer is still the same as it was before. Root is defined as being UID 0, if you want to rename that account, and change it's home directory you can. But short of being UID 0 sudo/admin is the closest you can get to being root without actually being root. Sudo with no password doesn't seem to cut it for you, the only thing more you can do is actually become root.

---

### Post by Matt26 on 2008-01-28
thanks for the information- if that's the closest i can get to having root privileges then i guess that is what i am looking for- what i want is to have full and complete control over anything on my system, without the need of using override methods like sudo, gksudo etc.

so what do i need to do to make this happen?

---

### Post by PeterJS on 2008-01-28
You need to be UID 0. You can use the user perfernces manager to change the name of the UID 0 account if you want and where it's home directory is. And then make sure that GDM will allow you to log in as root.

---

### Post by emarkd on 2008-01-28
If you really want to, you can set the root password by doing

```
sudo passwd
```

then logout and log back in as root.

---

### Post by PeterJS on 2008-01-28
> **emarkd said:**
> If you really want to, you can set the root password by doing

```
sudo passwd
```

then logout and log back in as root.

Oh yeah that is a rather important step, forgot to mention that, good catch.

---

### Post by Matt26 on 2008-01-28
i did this but when i got back to the login screen and tried logging in as root it told me that administrator cannot login from this screen.. tried rebooting with the same result.  any ideas?

---

### Post by PeterJS on 2008-01-28
You need to enable root login first. Run gdmsetup from your admin account, you're looking for this:
[img]http://oregonstate.edu/~sandinp/Ubuntu/GDM_Setup.png[/img]

---

### Post by Matt26 on 2008-01-28
ok that allowed me to log in as root, but i still cannot change the things i want- maybe i am doing this wrong... how do i allow a user account to have FULL control over a volume?  i used sudo chown user:group /media/disk and this allowed me access to create files in the volume- although it didn't seem to stick as when i logged in again under the same account (but this time i had the option you just mentioned enabled for root login) i mounted the volume and went into it and couldn't get the option for creating files again- greyed out once more!

---

### Post by wankel on 2008-01-28
> **Matt26 said:**
>  (...)... how do i allow a user account to have FULL control over a volume?  i used sudo chown user:group /media/disk and this (...) 

What is the filesystem on that disk? I know that having a filesystem with FAT(xx) on it does not have the same behaviour as a fs more regularly used under GNU/Linux.

(ps, are you sure you want to run your system as root for this?)

---

### Post by Matt26 on 2008-01-28
both volumes are ext3 filesystems- right now, i am only trying to accomplish 2 simple tasks

1) rename the labels for each of the volumes- i have ready many posts on how to accomplish and i haven't found one that has worked for me yet

2) create files and folder on each of these volumes- i think i have figured this out with the sudo chown command, but am not sure that the permissions are sticking- can these permissions be reverted in any way after a reboot of the computer?

---

### Post by wankel on 2008-01-28
We could try to verify that the system connects with those disks correctly. 

We need two terminals and one of those disks.

- open a terminal
- keep an eye on /var/log/messages
- insert the disk
- check what fdisk has to tell

More detailed:

Open a terminal (I use kubuntu, so got konsole)
Type 
```
tail -f /var/log/messages
```
I am not root, so I type 
```
wbk@gao:~$ sudo tail -f /var/log/messages
[sudo] password for wbk:
Jan 28 22:56:49 gao kernel: [   68.416000] Bluetooth: L2CAP socket layer initialized
Jan 28 22:56:49 gao kernel: [   68.540000] Bluetooth: RFCOMM socket layer initialized
Jan 28 22:56:49 gao kernel: [   68.540000] Bluetooth: RFCOMM TTY layer initialized
Jan 28 22:56:49 gao kernel: [   68.540000] Bluetooth: RFCOMM ver 1.8
Jan 28 23:00:14 gao kernel: [  272.872000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 28 23:16:36 gao -- MARK --
Jan 28 23:31:53 gao kernel: [ 2172.248000] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks
Jan 28 23:56:37 gao -- MARK --
Jan 29 00:16:37 gao -- MARK --
Jan 29 00:36:40 gao -- MARK --

```
Insert the disk. My terminal with tail -f /var/log/messages says 
```
Jan 29 00:49:15 gao kernel: [ 6814.188000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jan 29 00:49:15 gao kernel: [ 6814.356000] usb 1-1: configuration #1 chosen from 1 choice
Jan 29 00:49:15 gao kernel: [ 6814.360000] hub 1-1:1.0: USB hub found
Jan 29 00:49:15 gao kernel: [ 6814.364000] hub 1-1:1.0: 2 ports detected
Jan 29 00:49:16 gao kernel: [ 6814.676000] usb 1-1.2: new full speed USB device using uhci_hcd and address 3
Jan 29 00:49:16 gao kernel: [ 6814.820000] usb 1-1.2: configuration #1 chosen from 1 choice
Jan 29 00:49:17 gao kernel: [ 6815.868000] usbcore: registered new interface driver libusual
Jan 29 00:49:17 gao kernel: [ 6816.088000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan 29 00:49:17 gao kernel: [ 6816.092000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan 29 00:49:17 gao kernel: [ 6816.216000] Initializing USB Mass Storage driver...
Jan 29 00:49:17 gao kernel: [ 6816.216000] scsi2 : SCSI emulation for USB Mass Storage devices
Jan 29 00:49:17 gao kernel: [ 6816.220000] usbcore: registered new interface driver usb-storage
Jan 29 00:49:17 gao kernel: [ 6816.220000] USB Mass Storage support registered.
Jan 29 00:49:22 gao kernel: [ 6821.224000] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.02 PQ: 0 ANSI: 0 CCS
Jan 29 00:49:23 gao kernel: [ 6821.712000] sd 2:0:0:0: [sdb] 251904 512-byte hardware sectors (129 MB)
Jan 29 00:49:23 gao kernel: [ 6821.716000] sd 2:0:0:0: [sdb] Write Protect is off
Jan 29 00:49:23 gao kernel: [ 6821.728000] sd 2:0:0:0: [sdb] 251904 512-byte hardware sectors (129 MB)
Jan 29 00:49:23 gao kernel: [ 6821.732000] sd 2:0:0:0: [sdb] Write Protect is off
Jan 29 00:49:23 gao kernel: [ 6821.732000]  sdb: sdb1
Jan 29 00:49:23 gao kernel: [ 6821.736000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Jan 29 00:49:23 gao kernel: [ 6821.736000] sd 2:0:0:0: Attached scsi generic sg1 type 0

```
Open another terminal. Type 
```
fdisk -l
```
In my case:
```
wbk@gao:~$ sudo fdisk -l
[sudo] password for wbk:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00019016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      489951   83  Linux
/dev/sda2              62         152      730957+  82  Linux swap / Solaris
/dev/sda3            1373        7296    47584530    5  Extended
/dev/sda5            5741        7296    12498570   8e  Linux LVM
/dev/sda6            3308        5739    19535008+  8e  Linux LVM
/dev/sda7            1374        3306    15526791   8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/sdb: 128 MB, 128974848 bytes
16 heads, 32 sectors/track, 492 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         492      125936   83  Linux
wbk@gao:~$


```

If I want to change the text below, I can do that in the properties (I think that that is what you tried as well). At the moment I am not quite sure what to press, because my system is in Vietnamese at the moment (don't ask) and I did not yet find out all the correct translations :P

What are your results so far?

---

### Post by wankel on 2008-01-28
I just come to realize, are you actually talking about USB devices, or volumes on your harddisk?

Usually I label my volumes when formatting them during install, and then they carry that label for years :-)

Did you have a look at a tool like the partition editor or qtparted?

---

### Post by Matt26 on 2008-01-28
i am talking about an IDE hard drive, and i used GParted to format both volumes on the drive- i wasn't given the option to edit the name of the volumes when they were created (i've done this a few times to be sure) and they mount to /media/disk and /media/disk-1.

---

### Post by wankel on 2008-01-28
Hmm... I usually end up using command line tools in such a case.

Not to frighten you, but maybe I found what you're looking for on a man page:
```

MKE2FS(8)                                                                                                                       MKE2FS(8)

NAME
       mke2fs - create an ext2/ext3 filesystem

SYNOPSIS
       mke2fs  [ -c | -l filename ] [ -b block-size ] [ -f fragment-size ] [ -g blocks-per-group ] [ -i bytes-per-inode ] [ -I inode-size
       ] [ -j ] [ -J journal-options ] [ -N number-of-inodes ] [ -n ] [ -m reserved-blocks-percentage ] [  -o  creator-os  ]  [  -O  fea&#8208;
       ture[,...]   ]  [ -q ] [ -r fs-revision-level ] [ -E extended-options ] [ -v ] [ -F ] [ -L volume-label ] [ -M last-mounted-direc&#8208;
       tory ] [ -S ] [ -T filesystem-type ] [ -V ] device [ blocks-count ]

```

Somewhere in between you'll find [ -L volume-label ], do you see it?

So, if there is no data on your volumes yet, you could safely set the label by 
```
mkfs.ext3 -L /dev/volume
```

If you do not know the volume yet, you can find it by entering 
```
mount
```
at the command line (that is, if those volumes indeed get mounted in /media/.... ); in my case:
```
wbk@gao:~$ mount
/dev/mapper/kubuntu-root on / type reiserfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /boot type ext3 (rw)
/dev/mapper/data-data on /data type reiserfs (rw)
/dev/mapper/data-home--linh on /home/linh type reiserfs (rw)
/dev/mapper/data-home--wbk on /home/wbk type reiserfs (rw)
none on /proc/bus/usb type usbfs (rw,devmode=0666)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,data=ordered)
wbk@gao:~$   
```                          

I only got /dev/sda1 on /boot as "normal" harddisk volume. At the bottom you can see the USB device, that  is mounted on /media/disk

Before too long I'll be in bed, so good luck!

---

### Post by Matt26 on 2008-01-28
i was able to change the labels using e2label- i also added entries for each volume to the /etc/fstab file to allow them to auto-mount the system starts.. i then rebooted to see if the changes took and now i can't see either of the volumes under Computer- they show up in GParted as mounted with the proper labels (but no option to unmount them).  any ideas what i might have done wrong here?  thanks.

---

### Post by wankel on 2008-01-29
Using Konqueror (file manager and browser for KDE), I get to see the partition labels under "storage media" (see attached picture)

I am always a bit in a fight with the Gnome programs to let them show or do what I want, which makes me not used to the views available for you.

You could asking a moderator to change the name of the thread into something more descriptive, like "setting volume labels and seeing them in a Gnome file manager", but then a bit more concise :-) 

I hope someone else can give you a hand!

---

