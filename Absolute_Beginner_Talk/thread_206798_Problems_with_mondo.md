---
title: "Problems with mondo"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Perfex on 2006-06-30
Hello I am trying to use mondo to backup my HD, however I am having problem getting it to burn to cd,

I put this for the location of the cdrw : /dev/hda, 2nd time i tryed /dev/hda        /media/cdrom0 

My fstab 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Below are the logs I think are needed to troubleshoot this, any help would be appreciated

---

### Post by jordilin on 2006-07-22
I have seen the log file and says:
> --------------------------------start of output-----------------------------
umount: /mnt/cdrom: not mounted
--------------------------------end of output------------------------------

which is the same thing I obtain. Anyone else knows anything about this?

---

### Post by richbarna on 2006-07-22
I looked at the log files, and it's not detecting your cdrom drive or there is a cdrom permissions problem:-
> --------------------------------start of output-----------------------------
insmod: can't read 'ide-scsi': No such file or directory
--------------------------------end of output------------------------------ 
Try starting mondo with root permissions from the terminal :-

> gksudo mondo 
To set that as permanent:-
> Open the Alacarte Menu Editor and, in Command, place gksudo ahead of the executable name (e.g. gksudo mondo) 

See if that works.

Later make sure that you have read/write permissions for your user group.

---

### Post by jordilin on 2006-07-22
Mondo is run at the command line by:
```
sudo mondoarchive
```
and I'm getting these errors:
If I put the DVD before running mondoarchive then I get 
> --------------------------------start of output-----------------------------
umount: /mnt/cdrom: not mounted
--------------------------------end of output------------------------------
If I don't put the DVD, then it says Manual CD tray+DVD not supported yet. 
It seems that Mondo is quite buggy in Ubuntu. 
Richbarna, does it work for you?

---

### Post by richbarna on 2006-07-22
> **jordilin said:**
> 
Richbarna, does it work for you?

I used it on another pc before, so just to see, I installed it and got this :-
> sudo mondoarchive
Initializing...
See /var/log/mondo-archive.log for details of backup run.
Checking sanity of your Linux distribution
Done.
---FATALERROR--- Can't write DVDs as sudo because growisofs doesn't support this  - see the growisofs manpage for details.
If you require technical support, please contact the mailing list.
See [http://www.mondorescue.org](http://www.mondorescue.org) for details.
The list's members can help you, if you attach that file to your e-mail.
Log file: /var/log/mondo-archive.log
FYI, I have gzipped the log and saved it to /tmp/MA.log.gz
Mondo has aborted.
Execution run ended; result=254
Type 'less /var/log/mondo-archive.log' to see the output log


I'll have a look and check it out, as I was thinking of doing a backup myself.

---

### Post by jordilin on 2006-07-22
Mondo is a really important tool to make a complete backup for Linux systems. It should run out of the box ](*,)

---

### Post by richbarna on 2006-07-22
Ok, I know I have growisofs (dvd+rw-tools) so I checked for a bug report.
[http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=314782](http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=314782)

I suppose a solution would be to do a backup to harddrive and then burn it as an iso.

---

### Post by jordilin on 2006-07-22
Boys, look at what I've found in the manpage of mondo:
>  -r Use  DVD drive as backup device and its disks as backup media. Growisofs decides on the best speed for your drive. **Note that calling mondoarchive using sudo when writing to DVDs will fail because growisofs does not support this** - see the growisofs manpage for details.

Then, how are we going to run mondo? By setting up the root account, then doing a su an run mondoarchive??

---

### Post by richbarna on 2006-07-22
> **jordilin said:**
> Mondo is a really important tool to make a complete backup for Linux systems. It should run out of the box ](*,)

I know, the last system backup I did was on another pc with TAR.
Take a look at this guide :-
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by richbarna on 2006-07-22
> **jordilin said:**
> Boys, look at what I've found in the manpage of mondo:

Then, how are we going to run mondo? By setting up the root account, then doing a su an run mondoarchive??

YAY !!!!! :mrgreen: SOLVED !!
In terminal type su and enter password and then mondoarchive.

My system is now backing up to dvd as we speak :-D:-D

---

### Post by jordilin on 2006-07-22
> **richbarna said:**
> I know, the last system backup I did was on another pc with TAR.
Take a look at this guide :-
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)
We will have to forget Mondo and try other solutions. I'll try using the info pointed out in this link or the powerful rsync :-D

---

### Post by richbarna on 2006-07-22
> **jordilin said:**
> We will have to forget Mondo and try other solutions. I'll try using the info pointed out in this link or the powerful rsync :-D

See my post above :mrgreen:

---

### Post by jordilin on 2006-07-22
> **richbarna said:**
> YAY !!!!! :mrgreen: SOLVED !!
In terminal type su and enter password and then mondoarchive.

My system is now backing up to dvd as we speak :-D:-D

Yes, but what have you done? Have you enabled the root account by doing
```

sudo passwd root
```
or just
```
sudo -i
``` to enter a root console

---

### Post by richbarna on 2006-07-22
ok, have you tried "su"? did you get prompted for your password?

If not "sudo passwd root", enter new unix password (I always use the same one), that's it, run mondo as root, no dvd problems.:)

---

### Post by jordilin on 2006-07-22
Damn it!! Although running with su (root account) I still get the error
> umount: /mnt/cdrom: not mounted
my dvd drive is /dev/hdc, what the hell is going on? ](*,)

---

### Post by jordilin on 2006-07-22
Richbarna, what are the contents of your fstab file, if you don't mind.
Mine is:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


---

### Post by richbarna on 2006-07-22
> **jordilin said:**
> Damn it!! Although running with su (root account) I still get the error

my dvd drive is /dev/hdc, what the hell is going on? ](*,)

Try :-
> sudo mount /media/cdrom0/ -o unhide

---

### Post by jordilin on 2006-07-22
I get:
> root@lamacchina:~# mount /media/cdrom0 -o unhide
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

](*,)

---

### Post by jordilin on 2006-07-22
doing a
```
dmesg | tail 
```
I get the following:
> [4296786.519000] cdrom: open failed.
[4296786.750000] cdrom: open failed.
[4296828.684000] cdrom: This disc doesn't have any tracks I recognize!
[4301263.022000] cdrom: This disc doesn't have any tracks I recognize!
[4302303.569000] attempt to access beyond end of device
[4302303.569000] hdc: rw=0, want=68, limit=4
[4302303.569000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[4302356.775000] attempt to access beyond end of device
[4302356.775000] hdc: rw=0, want=68, limit=4
[4302356.775000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

I don't know if Ubuntu works well with my cdrom drive. I've never had any problem with Fedora. :evil:

---

### Post by richbarna on 2006-07-22
> **jordilin said:**
> doing a
```
dmesg | tail 
``` I get the following:

I don't know if Ubuntu works well with my cdrom drive. I've never had any problem with Fedora. :evil:

Have you tried burning anything else on dvd? music, films, files etc.
Have you got DMA enabled?
> sudo hdparm -d /dev/cdrom

Oh, guess what, Mondo tried to use my "CD" ROM instead of my "DVD" ROM to write the files. I need to find how to change that as well now ](*,)

---

### Post by jordilin on 2006-07-22
> **richbarna said:**
> Have you tried burning anything else on dvd? music, films, files etc.
Have you got DMA enabled?


Oh, guess what, Mondo tried to use my "CD" ROM instead of my "DVD" ROM to write the files. I need to find how to change that as well now ](*,)

Yes, I burn CDs and DVDs without any problem. It seems that Mondo does not find where the cd or dvd is mounted. I specify the /dev/hdc location but I get the error 
> umount: /mnt/cdrom: not mounted when, in fact, the cdrom is mounted and not in /mnt/cdrom but in /dev/hdc or /media/cdrom0 as specifies my fstab file.

---

### Post by richbarna on 2006-07-22
This could be interesting :-
[http://216.239.59.104/search?q=cache:vRU7YHITUTEJ:www.chem.vu.nl/~stol/Mondo-Rescue-Mindi-Linux-HOWTO.pdf+mondo+configuration&hl=en&gl=es&ct=clnk&cd=23#16]("http://216.239.59.104/search?q=cache:vRU7YHITUTEJ:www.chem.vu.nl/%7Estol/Mondo-Rescue-Mindi-Linux-HOWTO.pdf+mondo+configuration&hl=en&gl=es&ct=clnk&cd=23#16")

---

### Post by richbarna on 2006-07-22
Well, I ran "cdrecord -scanbus" and got this :-
> root@richbarna-desktop:/home/richbarna# cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-25-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
root@richbarna-desktop:/home/richbarna#


---

### Post by richbarna on 2006-07-22
Ok, I'm trying backup-manager from the repos, It says that it can backup to dvd/cd/harddrive. Also going to try partimage.

---

### Post by jordilin on 2006-07-23
> **richbarna said:**
> Ok, I'm trying backup-manager from the repos, It says that it can backup to dvd/cd/harddrive. Also going to try partimage.

Partimage works with unmounted partitions, so if I want to backup my home I have to unmount it :(. Backup manager can be nice, but it's just a replacement of tar+gzip/bzip2, so I'll go for rsync or just tar+gzip/bzip2.

---

### Post by richbarna on 2006-07-23
> **jordilin said:**
> Partimage works with unmounted partitions, so if I want to backup my home I have to unmount it :(. Backup manager can be nice, but it's just a replacement of tar+gzip/bzip2, so I'll go for rsync or just tar+gzip/bzip2.

I haven't tried it yet, but how about using mondo with "backup to harddrive" and then burning that to a dvd?

I am still investigating how to get mondo to look for my dvd drive instead of going to my second cd drive. It seems to work ok and goes through the back up fine, until it gets to where it has to burn the data.

I'm going to look more closely at the command line options to choose the different device.

I'll post back later this evening if I can find a solution.

---

### Post by jordilin on 2006-07-23
It seems that Mondo works if you store the backup to the hard drive instead of the DVD. If I only want to backup my /home, when Mondo asks for which directories to backup I put /home/myuser and then when it asks which directories to exclude I put / Is that ok?

---

### Post by jordilin on 2006-07-23
I'll try another solution. Mondo takes a long time to do a backup to my hard drive

---

