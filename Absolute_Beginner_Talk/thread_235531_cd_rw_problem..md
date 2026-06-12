---
title: "cd rw problem."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-08-13
hello to all.... im having trouble getting my cd - rw to work here. its so complicated. it reads any cd that i out into it but when it comes to blank cd-r's it cant write data files or audio files. here are some results of the error and my fstab specs.


Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
Details:

mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



Fstab Specs:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660 defaults,user,rw,noauto 0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0


I cant burn anything on my cd-rw. hope somebody helps me, any help would be greatly appreciated. Thank you

---

### Post by klytu on 2006-08-13
> **rck_hitokiri said:**
> hello to all.... im having trouble getting my cd - rw to work here. its so complicated. it reads any cd that i out into it but when it comes to blank cd-r's it cant write data files or audio files. here are some results of the error and my fstab specs.


Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
Details:

mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



Fstab Specs:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660 defaults,user,rw,noauto 0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0


I cant burn anything on my cd-rw. hope somebody helps me, any help would be greatly appreciated. Thank you

Your /etc/fstab looks OK as far as I can tell. But you might want to try changing this line:

> /dev/hdc        /media/cdrom0   iso9660 defaults,user,rw,noauto 0       0

to this:

> /dev/hdc        /media/cdrom0   auto user,noauto 0       0

and seeing if that has any effect. (Make a back-up copy of your /etc/fstab before trying this.)

By the way, how are you attempting to burn onto your blanks? Are you using nautilus? If so, you might want to try installing gnomebaker or k3b and attempting to burn with one of those. 

There could be any number of reasons why you are having difficulty. It might even possibly be the brand of CD-R or CD-RW blanks you are using. If the suggestions above don't help, please post the output of:

```
dmesg | grep hdc 
```

and 

> cat /var/log/messages | grep hdc

after a failed burn.

---

### Post by rck_hitokiri on 2006-08-13
rxk@rxk-mir:~$ dmesg | grep hdc
[   35.332735]     ide1: BM-DMA at 0x1058-0x105f, BIOS settings: hdc:DMA, hdd:DMA
[   36.354163] hdc: CW099D ATAPI CD-R/RW, ATAPI CD/DVD-ROM drive
[   36.850386]  hdd:<6>hdc: ATAPI 16X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   74.860751] cdrom: hdc: mrw address space DMA selected
[   99.768531] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[   99.768556] hdc: drive_cmd: error=0x04 { AbortedCommand }
[ 2812.458113] cdrom: hdc: mrw address space DMA selected
[ 2812.487306] hdc: rw=0, want=68, limit=4
[ 2812.488892] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[12664.238713] cdrom: hdc: mrw address space DMA selected
[12664.403938] hdc: rw=0, want=68, limit=4
[12664.404161] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[15884.684265] cdrom: hdc: mrw address space DMA selected
[15884.703968] hdc: rw=0, want=68, limit=4
[15884.704189] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

heres cat/var/log/messages | grep hdc:
Aug 13 03:07:39 rxk-mir kernel: [  940.359265] cdrom: hdc: mrw address space DMA selected
Aug 13 03:07:40 rxk-mir kernel: [  940.572749] cdrom: hdc: mrw address space DMA selected
Aug 13 03:07:41 rxk-mir kernel: [  942.013984] hdc: rw=0, want=68, limit=4
Aug 13 03:07:41 rxk-mir kernel: [  942.014167] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
Aug 13 03:08:08 rxk-mir kernel: [  968.936648] cdrom: hdc: mrw address space DMA selected
Aug 13 03:08:08 rxk-mir kernel: [  968.961247] cdrom: hdc: mrw address space DMA selected
Aug 13 03:08:08 rxk-mir kernel: [  968.975769] hdc: rw=0, want=68, limit=4
Aug 13 03:08:08 rxk-mir kernel: [  968.975934] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
Aug 13 03:08:32 rxk-mir kernel: [  993.336411] cdrom: hdc: mrw address space DMA selected
Aug 13 03:08:32 rxk-mir kernel: [  993.362674] cdrom: hdc: mrw address space DMA selected
Aug 13 03:08:33 rxk-mir kernel: [  993.412922] hdc: rw=0, want=68, limit=4
Aug 13 03:08:33 rxk-mir kernel: [  993.413089] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
Aug 13 03:11:21 rxk-mir kernel: [ 1161.632460] cdrom: hdc: mrw address space DMA selected
Aug 13 03:11:21 rxk-mir kernel: [ 1161.662574] cdrom: hdc: mrw address space DMA selected
Aug 13 03:11:21 rxk-mir kernel: [ 1161.707776] hdc: rw=0, want=68, limit=4
Aug 13 03:11:21 rxk-mir kernel: [ 1161.707955] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

/etc/fstab after editing:
etc/fstab:
mount: I could not determine the filesystem type, and none was specified.

there you have it... all complete.. any suggestions?

---

### Post by klytu on 2006-08-13
OK. How are you trying to burn? Are you using Nautilus? If not, what? If you have tried more than one burning application, do you get the same errors each time?

EDIT: Moments after I posted this response, I did a search to try to find some info to help you and I noticed you had cross-posted this same problem at least three times to different parts of the forums (including here). In another post you indicated that you tried Gnomebaker and nautilus. Next time you try a burn with Gnomebaker, don't put a blank in the drive. Set up your project normally and then click create data disk. Wait for Gnomebaker to ask you to put in a blank, then put in your blank, close the drive and click OK to continue. If that doesn't work, see below.

> [ 36.354163] hdc: CW099D ATAPI CD-R/RW, ATAPI CD/DVD-ROM drive
[ 36.850386] hdd:<6>hdc: ATAPI 16X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)

How many CD drives do you have? It seems like you have at least two (hdd and hdc), but only one is listed in fstab (hdc). What is the result of:

```
sudo cdrecord dev=ATAPI -scanbus
```?


> [ 74.860751] cdrom: hdc: mrw address space DMA selected
[ 99.768531] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[ 99.768556] hdc: drive_cmd: error=0x04 { AbortedCommand }
[ 2812.458113] cdrom: hdc: mrw address space DMA selected
[ 2812.487306] hdc: rw=0, want=68, limit=4
[ 2812.488892] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[12664.238713] cdrom: hdc: mrw address space DMA selected
[12664.403938] hdc: rw=0, want=68, limit=4
[12664.404161] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[15884.684265] cdrom: hdc: mrw address space DMA selected
[15884.703968] hdc: rw=0, want=68, limit=4
[15884.704189] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=1

I got errors similar to this in the past when my CD burner didn't like the physical disks I was trying to burn to. If all else fails you might want to try a different brand of disk blanks, but I can't tell for sure if that is the problem yet.

---

### Post by rck_hitokiri on 2006-08-13
heres what you requested bro.


rxk@rxk-mir:~$ sudo cdrecord dev=ATAPI -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'CyberDrv' 'CW099D CD-R/RW  ' '140M' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
dont know what i did wrong here. i tried gnomebaker but really didnt work out alsa k3b. thanks for your troubles bro. :(

---

### Post by klytu on 2006-08-14
> **rck_hitokiri said:**
> heres what you requested bro.


rxk@rxk-mir:~$ sudo cdrecord dev=ATAPI -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'CyberDrv' 'CW099D CD-R/RW  ' '140M' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
dont know what i did wrong here. i tried gnomebaker but really didnt work out alsa k3b. thanks for your troubles bro. :(

OK. So as far as cdrecord is concerned you have just one drive. Now I am confused by an earlier error message referencing hdd also as a cd drive. You have just one, correct? Did you recently change any of the physical connections to it?

What happened when you tried burning with gnomebaker as I suggested in my previous post? (where I suggested not putting a blank disk into the drive until after setting up your project and gnomebaker asks you to). Did you get the same kinds of error messages?

Did you modify /etc/hdparm.conf recently? In fact, please post its contents:

```
cat /etc/hdparm.conf
```

and while you're at it let's have a look at the entire output of dmesg. Since it will be rather long, you could direct the output to a file and attach the file like so, for example:

```
dmesg>bootlog
```

Then attach bootlog to your post. I'll be looking at the log for how your drives are being recongnized and mapped at start-up. If your drive worked before, there is probably a setting or two that was inadvertently changed. I'll try to help as best I can.

---

### Post by rck_hitokiri on 2006-08-14
Thanks Bro for all your help. About Gnomebaker i did what you asked me to, it happened the same i tried k3b and the same thing happened. well heres what you asked for:

rxk@rxk-mir:~$ sudo cat /etc/hdparm.conf
## This is the default configuration for hdparm for Debian.  It is a
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you
## like.  Note that an in-line comment is not supported.  If a line
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that
## use non # comment characters will be interpreted by the initscript.
## This has probably minor, but potentially serious, side effects for your
## hard drives, so please follow the guidelines.  Patches to improve
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm'
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need
## to run hdparm to set parameters for your root disk, please use the
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.
#It is provided for those more comfortable with hdparm syntax.

#/dev/discs/disc0/disc {
#       mult_sect_io = 16
#       write_cache = off
#       spindown_time = 240
#}

#/dev/discs/disc1/disc {
#       mult_sect_io = 32
#       spindown_time = 36
#       write_cache = off
#}

#/dev/cdroms/cdrom0 {
#       dma = on
#       interrupt_unmask = on
#       io32_support = 0
#}

#/dev/hda {
#       mult_sect_io = 16
#       write_cache = off
#       dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
rxk@rxk-mir:~$ sudo dmesg>bootlog

Here you go. thanks again for your troubles.

---

### Post by rck_hitokiri on 2006-08-14
> **klytu said:**
> OK. So as far as cdrecord is concerned you have just one drive. Now I am confused by an earlier error message referencing hdd also as a cd drive. You have just one, correct? Did you recently change any of the physical connections to it?

What happened when you tried burning with gnomebaker as I suggested in my previous post? (where I suggested not putting a blank disk into the drive until after setting up your project and gnomebaker asks you to). Did you get the same kinds of error messages?

Did you modify /etc/hdparm.conf recently? In fact, please post its contents:

```
cat /etc/hdparm.conf
```

and while you're at it let's have a look at the entire output of dmesg. Since it will be rather long, you could direct the output to a file and attach the file like so, for example:

```
dmesg>bootlog
```

Then attach bootlog to your post. I'll be looking at the log for how your drives are being recongnized and mapped at start-up. If your drive worked before, there is probably a setting or two that was inadvertently changed. I'll try to help as best I can.


yes i have just one cd-rw drive my other drive on hdd is ntfs, i didnt change any physical connections to it as far as i can remember. I dont remember having edited my hdparm.conf. Sorry if i seem useless, im still a noob when it comes to linux. thanks a lot brother.

---

### Post by klytu on 2006-08-14
> **rck_hitokiri said:**
> yes i have just one cd-rw drive my other drive on hdd is ntfs, i didnt change any physical connections to it as far as i can remember. I dont remember having edited my hdparm.conf. Sorry if i seem useless, im still a noob when it comes to linux. thanks a lot brother.

OK. I looked at your dmesg log. I personally have not encountered errors like this before unless either the CD drive doesn't like the blanks being used or the drive itself is failing:

> [ 5482.518641] ide: failed opcode was: unknown
[ 5482.518650] end_request: I/O error, dev hdc, sector 0
[ 5482.518661] Buffer I/O error on device hdc, logical block 0
[ 5482.520975] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[ 5482.520994] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }

Let's assume for the moment your drive is OK, since it worked before. And for now let's assume your drive likes your blanks and the blanks are OK (But this might not be. You could rule out bad blank media and possibly a failing drive by burning something on the same drive with the same blanks while running Windows). I found a suggestion in another thread that worked for a couple of folks who couldn't burn in Nautilus. Even if it works I don't think it will correct your being unable to burn in gnomebaker or k3b. Here goes:

```
gconf-editor
```

navigate to apps>nautilus-cd-burner check the box for burnproof, clear the box for overburn if it's checked, then close the editor and try to burn a blank using nautilus. If by some miracle this works you can at least burn in Nautilus. 

If that has no effect - and it very well may not - if you have a CD-RW, try blanking it from the command line and looking at what happens. Pop open your CD drive and put in a CD-RW blank (don't close the drive). Then do this:

```
cdrecord dev=/dev/hdc blank=fast
```

Post what happens when you try that. Also post back what your current /etc/fstab looks like:

```
cat /etc/fstab
```

I realize you posted your /etc/fstab before, but you made a change earlier when I suggested it, right? I'd like to see what it looks like now before trying one more thing if everything else has failed.

---

### Post by rck_hitokiri on 2006-08-14
Heres for cat/etc/fstab:

rxk@rxk-mir:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660 ro,user,noauto  0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0
rxk@rxk-mir:~$


For nautilus burn it was the same error as what i posted before. Cd-rw's get blanked but blank cd'rs still the same....
You think this could be in my ide settings? what if i change my ide settings and see what happens... thanks bro.

---

### Post by klytu on 2006-08-14
> **rck_hitokiri said:**
> Heres for cat/etc/fstab:

rxk@rxk-mir:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660 ro,user,noauto  0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0
rxk@rxk-mir:~$


For nautilus burn it was the same error as what i posted before. Cd-rw's get blanked but blank cd'rs still the same....
You think this could be in my ide settings? what if i change my ide settings and see what happens... thanks bro.

CD-RWs get blanked, you wrote. Can you burn stuff to CD-RWs? If so, then I'd bet heavy that your CD-R blanks are the problem and try a different brand of CD-R. If you've already ruled out bad CD-R blanks (for example, by burning with the same drive and same blanks in Windows) then you might want to try this:

```
sudo modprobe -r ide-cd
sudo modprobe ide-scsi
```

Then try a burn.

What this does is set-up SCSI emulation for your IDE CD drive. I used to  use Red Hat Linux and had to use SCSI emulation to get my CD and DVD drives working properly, but it hasn't been necessary for me with Ubuntu. If this works for you, you would need to make some changes to keep it working after a reboot. I don't remember how offhand (in Red Hat I used a boot option for the 2.4 kernel when it booted), but if it works for you I'll look it up.

---

### Post by klytu on 2006-08-14
> **rck_hitokiri said:**
> Heres for cat/etc/fstab:

rxk@rxk-mir:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660 ro,user,noauto  0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0


Oh, yeah and by the way remove the "ro" and change this:
>  /dev/hdc /media/cdrom0   iso9660 ro,user,noauto  0       0
to this:
> /dev/hdc /media/cdrom0   iso9660,udf user,noauto  0       0
and leave it that way.

---

### Post by rck_hitokiri on 2006-08-14
im sorry bro but.... didnt work out.... im hopeless now... thanks for the help you got for me.... thanks.

---

### Post by klytu on 2006-08-15
> **rck_hitokiri said:**
> im sorry bro but.... didnt work out.... im hopeless now... thanks for the help you got for me.... thanks.

OK. I know it's frustrating but don't give up yet. Did you test that this isn't due to CD-R blanks that your drive doesn't like? (If you did, post how you did this) Also, you didn't indicate whether you can burn to CD-RWs but not CD-Rs. If CD-RWs can be blanked, you should be able to burn to them as well. 

The last change I posted for you to make to your /etc/fstab should be correct for you; don't change that while trying to figure this out. If you tried the last suggestion I made about SCSI emulation and it didn't work, reboot (with the corrected /etc/fstab) and you should be back to the state where your CD drive is handled as a IDE drive again - though your burning problem may persist.

---

### Post by rck_hitokiri on 2006-08-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso966,udf user,noauto  0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0


ok heres the fstab ive changed it the way you suggested it to be configured and i can clear the rw disks but i cant still write sadly, i hope were not fighting a loosing battle here cauz here in the philippines cd-rw drives dont cost cheap... hehe know what i mean? i also rebooted as said. Asad to say still aint workin what you have posted here.. the command with the burn=fast. thanks again doc.

---

### Post by klytu on 2006-08-16
> **rck_hitokiri said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso966,udf user,noauto  0       0
/dev/hdd1       /windows2       ntfs    nls=utf8,umask=0222 0   0


ok heres the fstab ive changed it the way you suggested it to be configured and i can clear the rw disks but i cant still write sadly, i hope were not fighting a loosing battle here cauz here in the philippines cd-rw drives dont cost cheap... hehe know what i mean? i also rebooted as said. Asad to say still aint workin what you have posted here.. the command with the burn=fast. thanks again doc.

If you've tried a different brand of CD-R blanks and that didn't help, I'm sorry but I am out of ideas. If you haven't, you really should make sure it's not the blanks that are causing your troubles. I once bought a bad batch of CD-Rs and I would get all sorts of weird error messages when I put the blanks in the drive or tried to burn. Sometimes, I couldn't even eject the blanks without rebooting because they would cause the drive to hang. It was really frustrating because of course the drive worked fine earlier the same day and I hadn't change any system settings. Just taking a shot, I put in a blank from a batch that I had burned on already and had no problem!

Anyway, good luck - I hope you eventually solve your problem.

---

### Post by rck_hitokiri on 2006-08-16
Well bro, youve been really nice to me here. youre the only one who helped me though theres really almost no hope of fixing my cd-rw. Thank you so much for really helpin out, your the best man. Anyway im gonna try and buy a cd-rw when i have money, heheh. thanks a lot bro i hope this isnt or last. thanks again... cheers

---

### Post by klytu on 2006-08-16
> **rck_hitokiri said:**
> 
/dev/hdc        /media/cdrom0   iso966,udf user,noauto  0       0


I think this was just a typo error, but the line above should be:

> /dev/hdc        /media/cdrom0   **iso9660**,udf user,noauto  0       0

Otherwise, nothing new to add. Again good luck, and I hope you work this out.

---

### Post by cazub on 2006-08-17
hey there, very similar problems. Been looking through forums for about a week now trying to figure out how to get burning again. The obvious problem seems to be that cdrecord isn't exactly supported in the 2.6.x kernals. Previous distro's used cdrecord fine and when i upgraded to Dapper it basicaly stopped working. I had no success until i ran dpkg-reconfigure cdrecord and set the SUID and then DIDN"T use k3b's setup program. This allowed me to burn 2 cd's. I went on vacation for about a week, installed some updates and POW i'm back to cdrecord not working. so:

1) are permissions being Reset everytime i boot somehow?
2) is there a cdrecord alternative? i know of Cdrao but not sure how to get my k3b to use that and plus thats only for audio cd's.

my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 nouser,defaults,errors=remount-ro,usrquota,grpquota,atime,auto$
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb1 /media/hdb1/ vfat  iocharset=utf8,umask=000  0    0


and my burning errors (looking at DMA and crc error?)


HL-DT-ST DVDRAM GSA-4160B A302 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 356891

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4160B'
Revision       : 'A302'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 17295 kB/s 98x CD 12x DVD
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   697 MB        
Total size:      800 MB (79:18.54) = 356891 sectors
Lout start:      800 MB (79:20/41) = 356891 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 2957
Starting to write CD/DVD at speed 4 in dummy SAO mode for single session.
Last chance to quit, starting dummy write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  697 MB written.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 1F 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 10 DE B6 92 80 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 63488 bytes
Writing  time:   43.650s
Average write speed 109.1x.
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:   23.503s
/usr/bin/X11/cdrecord: fifo had 65 puts and 2 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 1 times full, min fill was 98%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=4 -dao -dummy driveropts=burnfree -eject -data -tsize=356891s - 

mkisofs
-----------------------
356891
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.14% done, estimate finish Thu Aug 17 15:38:54 2006
  0.28% done, estimate finish Thu Aug 17 15:38:54 2006
  0.42% done, estimate finish Thu Aug 17 15:38:54 2006
  0.56% done, estimate finish Thu Aug 17 15:38:54 2006

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-cazub/k3bV98Msb.tmp -rational-rock -hide-list /tmp/kde-cazub/k3bMn98db.tmp -joliet -hide-joliet-list /tmp/kde-cazub/k3bgRKZSb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-cazub/k3blNM29b.tmp 


//-------------------end debug report ----------
So any help would be apreciated! I'm out of ideas at this point

---

### Post by klytu on 2006-08-18
> **cazub said:**
> hey there, very similar problems. Been looking through forums for about a week now trying to figure out how to get burning again. The obvious problem seems to be that cdrecord isn't exactly supported in the 2.6.x kernals. Previous distro's used cdrecord fine and when i upgraded to Dapper it basicaly stopped working. I had no success until i ran dpkg-reconfigure cdrecord and set the SUID and then DIDN"T use k3b's setup program. This allowed me to burn 2 cd's. I went on vacation for about a week, installed some updates and POW i'm back to cdrecord not working. so:

1) are permissions being Reset everytime i boot somehow?
2) is there a cdrecord alternative? i know of Cdrao but not sure how to get my k3b to use that and plus thats only for audio cd's.

my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 nouser,defaults,errors=remount-ro,usrquota,grpquota,atime,auto$
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb1 /media/hdb1/ vfat  iocharset=utf8,umask=000  0    0


and my burning errors (looking at DMA and crc error?)


cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4160B'
Revision       : 'A302'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 17295 kB/s 98x CD 12x DVD
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   697 MB        
Total size:      800 MB (79:18.54) = 356891 sectors
Lout start:      800 MB (79:20/41) = 356891 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 2957
Starting to write CD/DVD at speed 4 in dummy SAO mode for single session.
Last chance to quit, starting dummy write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready. 

I get a lot of these same warnings and errors all the time when I burn, but nevertheless I can pretty much burn CDs and DVDs with no problem. I don't think the problem lies in cdrecord. Also, on my system I never had to set the SUID and I have no idea why your permissions might be reset at boot, though other forum members might.

Why did you chose these settings in /etc/fstab for your drive?:

> /dev/hdc /media/cdrom0 udf,iso9660  user,atime,noauto,rw,dev,exec,suid 0 0

Was it trial and error or do you have a specific reason for it?

These errors/warnings, I don't get:

> BURN-Free is OFF.
Turning BURN-Free on
Sending CUE sheet... 
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  697 MB written.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 1F 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 10 DE B6 92 80 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 63488 bytes
Writing  time:   43.650s
Average write speed 109.1x.

This MIGHT be a hardware issue. Do you have DMA on for your cd burner? Please post output of this:

```
cat /etc/hdparm.conf
```

---

### Post by ShaqArif on 2007-04-29
> **klytu said:**
> I get a lot of these same warnings and errors all the time when I burn, but nevertheless I can pretty much burn CDs and DVDs with no problem. I don't think the problem lies in cdrecord. Also, on my system I never had to set the SUID and I have no idea why your permissions might be reset at boot, though other forum members might.

Why did you chose these settings in /etc/fstab for your drive?:



Was it trial and error or do you have a specific reason for it?

These errors/warnings, I don't get:



This MIGHT be a hardware issue. Do you have DMA on for your cd burner? Please post output of this:

```
cat /etc/hdparm.conf
```

I'm having exactly the same issue, here is the relevant section from my /etc/hdparm.conf:


```
#/dev/cdroms/cdrom0 {
#       dma = on                   
#       interrupt_unmask = on
#       io32_support = 0
#}
```

Should dma be on or off?

The DVD Writer is brand new, it is my third in as many months :-(

Doesn't have a problem playing CDs/DVDs???

Please help!!!

---

### Post by ShaqArif on 2007-05-03
Bump!

Any ideas on this people?

I've tried every suggestion I've seen on the forums, switching DMA on/off, trying different media, SCSI emulation, running every burner in the ubuntu world (including command line), but still no joy. :( 

I really would like to Fiesty Fawn, but this one issue is preventing me.  Would reinstalling Ubuntu (Edgy) again from scratch help?

Please help!!

---

### Post by ShaqArif on 2007-05-04
OK, some limited success...

I had a liveDisc for 'Enlightenment' that I got from the Linux Format magazine.  I installed this on a new partition and I was then able to use this to download and burn Fiesty Fawn without any issues.

At least this shows that it is not a hardware/media issue, so that's a good thing I suppose.

I am hoping to install FF this weekend, and see if that sorts out my CD/DVD writing problems - I'll keep you posted!

---

