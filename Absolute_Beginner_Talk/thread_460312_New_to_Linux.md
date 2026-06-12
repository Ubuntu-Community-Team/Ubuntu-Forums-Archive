---
title: "New to Linux"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Clintonostra on 2007-05-31
Being new to Linux and Unix and having installed Ubuntu 7.04 (Feisty Fawn ) a month ago, I have read most documentation, FAQ, Howto's, forum comments and my opinion is that the people providing answers and documentation assume that most beginners know more than they actual do. Most of the instructions assume everything will work correctly and if it doesn't, then you have to search for an answer 
to the problem and hopefully find a clue as to what is happening. In many forums and bug sites, the majority of comments are directed towards working around a problem. Presented below is a case in point,
I believe this problem has been discussed for a number of months . There were any number of comments about how to get around this problem, to it being solved with an update.

Burning a CD:
 I don't known if any of this information is useful. Prior to this installation, both devices worked with Windows (don't want to use) and Fedora 6 (problems).
	When I try to burn a CD with C/D / DVD creator, the following messages appeared:
(1) Reload a rewritable or blank disk (it can read size of file) and (2) writing files to disk.
When I right click on CD-RW/DVD RW Drive:
	This message appears: Cannot mount volume. Invalid mount option when attempting to mount the volume 'UDF Volume'.
Also, when I try to mount the floppy, this message appears; cannot mount volume.  mount: /dev/fdo is not a valid block device.

Both of these devices can read a disk.
Below are commands I ran after looking a bug reports #62986,#66254,#44233 and #6415.


At the end of running DMESG

[   47.544000] Unable to identify CD-ROM format. 
[22866.180000] Unable to identify CD-ROM format. 
[23156.092000] Unable to identify CD-ROM format. 
[23253.824000] end_request: I/O error, dev fd0, sector 0 
[23253.848000] end_request: I/O error, dev fd0, sector 0 
[23257.664000] end_request: I/O error, dev fd0, sector 0 
[23257.688000] end_request: I/O error, dev fd0, sector 0 
[23267.016000] end_request: I/O error, dev fd0, sector 0 
[23267.040000] end_request: I/O error, dev fd0, sector 0 
[23327.592000] Unable to identify CD-ROM format. 
[24460.608000] Unable to identify CD-ROM format. 
[24666.344000] Unable to identify CD-ROM format. 
[24666.344000] Unable to identify CD-ROM format. 
[30979.064000] Unable to identify CD-ROM format. 

$ mount 
/dev/sdb1 on / type ext3 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
/sys on /sys type sysfs (rw,noexec,nosuid,nodev) 
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
procbususb on /proc/bus/usb type usbfs (rw) 
udev on /dev type tmpfs (rw,mode=0755) 
devshm on /dev/shm type tmpfs (rw) 
devpts on /dev/pts type devpts (rw,gid=5,mode=620) 
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw) 
/dev/sda2 on /media/windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw) 

uname -a 
Linux jack-desktop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux 

$ /usr/lib/nautilus-cd-burner/list_cddrives 
Drive: 
  name:                 DVD+-RW TS-H653A 
  device:               /dev/scd0 
  door:                 closed 
  type:                 CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD 
  is mounted:           FALSE 
  max read speed:       8468 KiB/s (CD 56.4x, DVD 6.2x) 
  max write speed:      8468 KiB/s (CD 56.4x, DVD 6.2x) 
  write speeds:         8468 KiB/s (CD 56.4x, DVD 6.2x) 
                        7056 KiB/s (CD 47.0x, DVD 5.2x) 
                        5645 KiB/s (CD 37.6x, DVD 4.1x) 
                        4234 KiB/s (CD 28.2x, DVD 3.1x) 
                        2823 KiB/s (CD 18.8x, DVD 2.0x) 
                        1412 KiB/s (CD 9.4x, DVD 1.0x) 

Media: 
  label:                'UDF Volume' 
  type:                 CD-R (has-data) 
  is writable:          FALSE 
  is appendable:        TRUE 
  capacity:             701.00 MiB approx. or 80 mins 0 secs 
  size:                 0.63 MiB approx. or 0 mins 0 secs 


jack@jack-desktop:~$ cdrecord 
Quickly guessing the name of a drive capable to write CD-R, please wait... 
Found /dev/cdrw, assuming dev=/dev/cdrw 
wodim: No tracks specified. Need at least one. 
Usage: wodim [options] track1...trackn 
Use     wodim dev=help 
to get a list of possible SCSI transport specifiers. 
jack@jack-desktop:~$ wodim dev=help 
Supported SCSI transports for this platform: 

Transport name:         sg 
Transport descr.:       Generic transport independent SCSI 
Transp. layer ind.: 
Target specifier:       bus,target,lun 
Target example:         1,2,0 
SCSI Bus scanning:      supported 
Open via UNIX device:   not supported 

Transport name:         ATA 
Transport descr.:       ATA Packet specific SCSI transport 
Transp. layer ind.:     ATAPI: 
Target specifier:       bus,target,lun 
Target example:         ATAPI:1,2,0 
SCSI Bus scanning:      supported 
Open via UNIX device:   not supported 

Transport name:         ATA 
Transport descr.:       ATA Packet specific SCSI transport using sg interface 
Transp. layer ind.:     ATA: 
Target specifier:       bus,target,lun 
Target example:         1,2,0 
SCSI Bus scanning:      supported 
Open via UNIX device:   not supported 

Transport name:         RSCSI 
Transport descr.:       Remote SCSI 
Transp. layer ind.:     REMOTE: 
Target specifier:       rscsi@host:bus,target,lun 
Target example:         REMOTE:rscsi@host:1,2,0 
SCSI Bus scanning:      supported 
Open via UNIX device:   not supported 	


jack@jack-desktop:~$  wodim dev=b,t,l driveropts=help -checkdrive 
wodim: Invalid argument. 
Cannot open SCSI driver!

---

### Post by Sparkster185 on 2007-05-31
Are you asking for help with this issue, or just making a statement about people assuming others know too much?

---

### Post by dstew on 2007-05-31
Regarding the floppy, what mount command are you using? The error message "mount: /dev/fdo is not a valid block device" is entirely correct. The device name should be **/dev/fd0**, not dev/fdo (that is, use the numeral '0', not the letter 'o').

---

### Post by Clintonostra on 2007-06-01
> **Sparkster185 said:**
> Are you asking for help with this issue, or just making a statement about people assuming others know too much?

I need all the help that I can get.

---

### Post by Clintonostra on 2007-06-01
> **dstew said:**
> Regarding the floppy, what mount command are you using? The error message "mount: /dev/fdo is not a valid block device" is entirely correct. The device name should be **/dev/fd0**, not dev/fdo (that is, use the numeral '0', not the letter 'o').

How do I fix this error. The directory /media/floppy0 is empty.

---

### Post by phr0ze on 2007-06-01
> **Clintonostra said:**
> Most of the instructions assume everything will work correctly and if it doesn't, then you have to search for an answer to the problem and hopefully find a clue as to what is happening. 

Thats because if an error is encountered it is probably unique to your hardware and must be handled on a Case-by-case basis. If the error is very common, the fix wouldn't be put in a set of installation instructions, the fix would just be made to the OS.

---

### Post by Clintonostra on 2007-06-01
> **phr0ze said:**
> Thats because if an error is encountered it is probably unique to your hardware and must be handled on a Case-by-case basis. If the error is very common, the fix wouldn't be put in a set of installation instructions, the fix would just be made to the OS.

How do I rectify the fact that I can't burn a CD.

---

### Post by annda on 2007-06-01
sorry but i can't help with you floppy problem. i don't have one.

as to burning CDs, try installing and running k3b - it is an excellent burning utility. if you have problems with it, post back with any error messages you get.

---

### Post by RelativelyQuantum on 2007-06-01
> as to burning CDs, try installing and running k3b

If you were wondering how to go about doing that, here's the code:

```
sudo apt-get install k3b
```

Enter that in the Terminal application and the plugin will be retrieved, considering you are connected to the internet. Alternatively, you could try installing it from Synaptic Package Manager, located in System > Administration. Just search for "k3b" and click the box next to it to mark it for installation. It will be downloaded when you click "Apply"

Hope this helps.

---

### Post by forger on 2007-06-01
> When I try to burn a CD with C/D / DVD creator
**WRONG**
go from the menu: Applications > Add/Remove
(allow update if asked)
search for **brasero** or **k3b**
(As a note: k3b is  more "worked on" and much easier)
install by pressing "apply" and "ok" ;)
then go to Applications > sound/video > Brasero disk burning application

that should easen things up a bit

---

### Post by Clintonostra on 2007-06-02
Thank you very much for the reply.

Couldn't burn CD. Received this message:
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
TSSTcorp DVD+-RW TS-H653A D300 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

K3bIsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

Used versions
-----------------------
mkisofs: 1.1.2

mkisofs
-----------------------
/usr/bin/genisoimage: 
Unable to find previous session PVD '/dev/scd0'.
/usr/bin/genisoimage: Unable to find previous session PVD '/dev/scd0'.

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -cdrecord-params 0,11722 -prev-session /dev/scd0 -gui -graft-points -print-size -quiet -volid CONVERSION -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jack/k3bTdLI7a.tmp -rational-rock -hide-list /tmp/kde-jack/k3bVDjzFa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-jack/k3bPhaPFb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-jack/k3bmwzDRb.tmp 

msinfo
-----------------------
0,11722

msinfo command:
-----------------------
/usr/bin/wodim dev=/dev/scd0 -msinfo

---

### Post by Clintonostra on 2007-06-02
> **annda said:**
> sorry but i can't help with you floppy problem. i don't have one.

as to burning CDs, try installing and running k3b - it is an excellent burning utility. if you have problems with it, post back with any error messages you get.

Thank you for the reply.
Still can't burn. See error message below.
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
TSSTcorp DVD+-RW TS-H653A D300 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

K3bIsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

Used versions
-----------------------
mkisofs: 1.1.2

mkisofs
-----------------------
/usr/bin/genisoimage: 
Unable to find previous session PVD '/dev/scd0'.
/usr/bin/genisoimage: Unable to find previous session PVD '/dev/scd0'.

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -cdrecord-params 0,11722 -prev-session /dev/scd0 -gui -graft-points -print-size -quiet -volid CONVERSION -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jack/k3bTdLI7a.tmp -rational-rock -hide-list /tmp/kde-jack/k3bVDjzFa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-jack/k3bPhaPFb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-jack/k3bmwzDRb.tmp 

msinfo
-----------------------
0,11722

msinfo command:
-----------------------
/usr/bin/wodim dev=/dev/scd0 -msinfo 

I don't know if this is any help.

Cd-RW/DVD RW Drive Properties
Volume:
	Label: Volume
	Size: 644.0 KB
	Media: CD-R Disc
	UUID:
	File System: udf
	Mount point: not mounted
	File system: not mounted
	Mount options: not mounted

Or if this sheds any light on it.

 /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=b528580b-d06d-456e-bde6-487db2aab9d4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=331cb40a-87e0-4450-85be-2b93b2b00897 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda2 /media/windows ntfs umask=222,utf8 0 0

---

