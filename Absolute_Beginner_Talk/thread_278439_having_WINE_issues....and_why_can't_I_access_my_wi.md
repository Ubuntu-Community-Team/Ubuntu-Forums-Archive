---
title: "having WINE issues....and why can't I access my windows partition?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-16
hey.

I have two problems right biw, perhaps you could help me? ^^;

Question 1:
I sorta can't mount or do anything with the partition which Windows is on. I know NTFS is oftentimes a problem for Linux or anything else that isn't windows, but I see that some people actually manage to access other partitions, I always get "access denied". Why? Even when I log in with root ( or what I believe is root since I can get the root terminal without entering a P/W ), I still get "access denied" when I try to get
to the partition windows is on. Also Wine can't autofind it when I run the setup. Why is this so, and how can I get around it?


Question 2: Why can't wine run the internet explorer or any other program? I read that it's SUPPOSED to work with the internet explorer.
but I get:
> 
 #claudia@duronUBUNTU:~$ wine /home/claudia/Desktop/My Data/ie6setup.exe
Invoking /usr/lib/wine/wine.bin /home/claudia/Desktop/My Data/ie6setup.exe ...
Converted drive type to new entry HKLM\Software\Wine\Drives "A:" = L"floppy"
Converted drive type to new entry HKLM\Software\Wine\Drives "C:" = L"hd"
Converted drive type to new entry HKLM\Software\Wine\Drives "D:" = L"cdrom"
Converted drive type to new entry HKLM\Software\Wine\Drives "X:" = L"hd"
Converted drive type to new entry HKLM\Software\Wine\Drives "Y:" = L"network"
Converted drive type to new entry HKLM\Software\Wine\Drives "Z:" = L"hd"
Converted temp dir to new entry HKCU\Environment "TEMP" = L"X:\\"
Converted path dir to new entry HKCU\Environment "PATH" = L"C:\\Windows;C:\\Windows\\System;X:\\;X:\\test;Y:\\"
Converted windows dir to new entry HKCU\Environment "windir" = L"C:\\Windows"
Converted system dir to new entry HKCU\Environment "winsysdir" = L"C:\\Windows\\System"
wine: cannot find '/home/claudia/Desktop/My'
Wine failed with return code 1

OR:

> root@duronUBUNTU:/home/claudia # cd /home/claudia/Desktop/My Data/ie6setup.exe
bash: cd: /home/claudia/Desktop/My: No such file or directory
root@duronUBUNTU:/home/claudia # cd /home/claudia/Desktop/ie6setup.exe
bash: cd: /home/claudia/Desktop/ie6setup.exe: Not a directory
root@duronUBUNTU:/home/claudia # wine ie6setup.exe
Invoking /usr/lib/wine/wine.bin ie6setup.exe ...
wine: creating configuration directory '/root/.wine'...
wine: '/root/.wine' created successfully.
wine: cannot find 'ie6setup.exe'
Wine failed with return code 1
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Deleting /tmp/wine.log.sHtxHp
root@duronUBUNTU:/home/claudia # /home/claudia/Desktop/ie6setup.exe wine ie6setup.exe
bash: /home/claudia/Desktop/ie6setup.exe: Permission denied
root@duronUBUNTU:/home/claudia #

why? What am I doing wrong NOW ?!

Bless you all if you bother to help this dummy out a bit...^^;


Using: Ubuntu "Hoary Hedgehog" release. ( EXT3 )
Windows 2000 Professional ( NTFS )
and the wine package I got through synaptic...

---

### Post by timetunnel on 2006-10-16
You have spaces in the path:
> /home/claudia/Desktop/My Data/ie6setup.exe
If you read the error messages, you can see that they tell you about that problem:
> wine: cannot find '/home/claudia/Desktop/My'
So, if there are space in a path, *always* use quotes around it:
```
wine "/home/claudia/Desktop/My Data/ie6setup.exe"
```
That should get you a big step further to your goal.

---

### Post by CatKiller on 2006-10-16
First, some links that might help you out:

[ How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")
[Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")

[File Permissions in Ubuntu]("http://www.psychocats.net/ubuntu/permissions")
[RootSudo wiki page]("https://help.ubuntu.com/community/RootSudo")

Next, answers to some of your questions:

It's probably a bad idea to attempt to run programs that you've installed in Windows through Wine from your Windows partition. If that program had put entries in your Windows registry, for example, then those entries will not be in Wine's pretend registry and so the program is unlikely to work as desired. Instead, you should install the program using Wine to Wine's pretend C: drive with Wine's pretend registry.

There are a number of HOWTOs for getting Internet Explorer working in Wine. I haven't read any of them, but I suspect that if it was entirely straightforward there wouldn't be quite so many of them. I suggest that you read one, some, or more, of them.

In your first attempt listed above, you've not taken the space in the path into consideration. The easy way to deal with this is to use Tab-completion for paths and file names. Start to type in the command or filename and press Tab. If there is a unique way to fill in the rest, it will automatically do so. If there is more than one way to complete it the computer will beep and pressing Tab again will give you a list of the possible ways.

---

### Post by bodhi.zazen on 2006-10-16
Or "escape the white space:```
wine /home/claudia/Desktop/My[color=red]\[/color] Data/ie6setup.exe
```

---

### Post by Ryupower on 2006-10-16
thanks guys! Now using 

> [COLOR="DarkSlateBlue"]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab[/COLOR]

got me:

> [COLOR="DarkSlateBlue"]root@duronUBUNTU:/home/claudia # sudo umount /media/hda1
umount: /media/hda1: not found
root@duronUBUNTU:/home/claudia # sudo umount /media/hda2
umount: /media/hda2: not found
root@duronUBUNTU:/home/claudia # sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
root@duronUBUNTU:/home/claudia # sudo cp /etc/fstab /etc/fstab_backup
root@duronUBUNTU:/home/claudia # gksudo gedit /etc/fstab

(gedit:13127): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/COLOR] 

and then I tried again...
> 
root@duronUBUNTU:/home/claudia # sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@duronUBUNTU:/home/claudia # sudo mount -a/dev/hda2
mount: invalid option -- /
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
root@duronUBUNTU:/home/claudia # mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
root@duronUBUNTU:/home/claudia # mount /dev/hda2
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@duronUBUNTU:/home/claudia # mount /dev/windows
mount: can't find /dev/windows in /etc/fstab or /etc/mtab
root@duronUBUNTU:/home/claudia # fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
root@duronUBUNTU:/home/claudia # /media/windows
bash: /media/windows: is a directory
root@duronUBUNTU:/home/claudia #
root@duronUBUNTU:/home/claudia # mount /media/windows
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@duronUBUNTU:/home/claudia # /mnt/windows



and now I'm confused.

---

### Post by bodhi.zazen on 2006-10-16
please post your /etc/fstab (easier then reading though all that output) and we can then directly configure fstab....

---

### Post by Ryupower on 2006-10-16
> **CatKiller said:**
> First, some links that might help you out:

[ How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")
[Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")

[File Permissions in Ubuntu]("http://www.psychocats.net/ubuntu/permissions")
[RootSudo wiki page]("https://help.ubuntu.com/community/RootSudo")

Next, answers to some of your questions:

It's probably a bad idea to attempt to run programs that you've installed in Windows through Wine from your Windows partition. If that program had put entries in your Windows registry, for example, then those entries will not be in Wine's pretend registry and so the program is unlikely to work as desired. Instead, you should install the program using Wine to Wine's pretend C: drive with Wine's pretend registry.

There are a number of HOWTOs for getting Internet Explorer working in Wine. I haven't read any of them, but I suspect that if it was entirely straightforward there wouldn't be quite so many of them. I suggest that you read one, some, or more, of them.

In your first attempt listed above, you've not taken the space in the path into consideration. The easy way to deal with this is to use Tab-completion for paths and file names. Start to type in the command or filename and press Tab. If there is a unique way to fill in the rest, it will automatically do so. If there is more than one way to complete it the computer will beep and pressing Tab again will give you a list of the possible ways.

OK, so it's suggested to not open things from the windows partition in wine. Because wine runs better on its on.
I'd still like to access some documents and pics I have on that though..
thanks

---

### Post by Ryupower on 2006-10-16
oh, nvm.
wrong hda. It was hda4.
I feel like a complete idiot now. ](*,) 

So anyways, now everything seems mounted.
[I][COLOR="DarkSlateBlue"]
root@duronUBUNTU:/home/claudia # sudo mount -a /dev/hda4
mount: /dev/hda4 already mounted or /media/windows busy
mount: according to mtab, /dev/hda4 is already mounted on /media/windows[/COLOR][/I]

so how do you get to the files on that partition now? ( supid newbie I know. :/ )

---

### Post by bodhi.zazen on 2006-10-16
In nautilis browse to /media/windows/

In a terminal:```
cd /media/windows
```

---

### Post by Ryupower on 2006-10-16
IT'S WORKING!!!
*excited*
Thanks again!All of you!  Was very nice of you to bear with me here....

---

