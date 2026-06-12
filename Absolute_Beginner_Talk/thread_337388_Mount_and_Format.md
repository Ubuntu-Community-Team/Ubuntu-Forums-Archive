---
title: "Mount and Format"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by drake18746 on 2007-01-12
Hi.  I just recently (re)installed Ubuntu 6.06 on a computer in my house.  When I had it running earlier, I had a 300 gig hard drive that I wanted to access through the server.  In the process of mounting it though, I did something funky (no, I don't remember what I did, unfortunately).  As such, neither Windows will recognize the drive, nor linux.

It is currently in the computer running Dapper Drake as what would have been hdb, but fdisk -l does -not- list it there.  Nor do any of the other disk usage commands work to display it.

I know its there, connected correctly since BIOS recognizes the drive after POST.  But I have absolutely no idea how to make Linux recognize it and, after that, how to format it so that it has the correct partitions.

Additionally and idealy, I'd like to be able to partition it so that Linux can use it without deleting the data currently stored on it, but I've been without that data for so long that if I have to lose it all, I won't shed a tear.

Any help would be greatly appreciated.  Couldn't find anything to help me that made sense so far, unfortunately...

---

### Post by sardion on 2007-01-12
This sounds an awful lot like the drive isn't actually being recognized by the computer (BIOS POST aside).  You sure all the master/slave etc is correct?

I hate to suggest this, but if you a windows cd, try booting off that and see if the window install program "sees" the drive.  If so, then the linux folks ought to know so they can fix it.  If not, something is wrong with the drive or the setup.

---

### Post by jem7v on 2007-01-12
Or instead of a windows CD, you could try using the GParted LiveCD.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by drake18746 on 2007-01-12
I havw Windows installed on my laptop for school, and every time I put the drive into an external case and attach it to the computer, it starts to load up the data on it, then shortly after it tells me there was a write error and then I'm unable to access the drive until I reboot.  And if I do reboot and try again, the result is the same.

I have a whole bunch of boot disks though for 6.06 so if its possible to erase the drive from there I can do that.  I think, if I remember correctly, I was able to see the drive or something when I used that?  I can't remember exactly, its been a few days.

---

### Post by drake18746 on 2007-01-12
That GParted LiveCD...  How do I use it?  Just burn it to CD and boot up the computer with it?

---

### Post by logos34 on 2007-01-13
> That GParted LiveCD... How do I use it? Just burn it to CD and boot up the computer with it?

Yes, it's just an 'industrial strength' version of the gparted on the ubuntu livecd.  I was just going to suggest that running fdisk -l from either might detect  the drive where your installed dapper did not...Worth a try and if it works then you can go ahead and partition it.

---

### Post by drake18746 on 2007-01-13
Alright.  So once I can detect the drive, what do I do?  How do I full erase it or whatever it is that I need to do?

---

### Post by jem7v on 2007-01-13
The LiveCD has help files and instructions on it, so you could read those, but the grammar and English of the person who wrote them is, um, shakey at best.  It's a pretty straightforward interface for such a seemingly daunting task.

---

### Post by drake18746 on 2007-01-13
When I boot up the computer and log into Ubuntu like normal, I was able to detect the drive as hdb1, though it was formatted with HPFS (or something like that)/NTFS.  I was told that I should run the command **sudo mkfs -t ext3 /dev/hdb1**.  It would run for a while and then give me an error and stop.  After that, I wouldn't be able to detect the drive.  I tried rebooting and trying again, I was still able to detect the drive with the same partitions on it and I ran the command again, but I was faced with the same result.

I'm going to try running it again from the LiveCD, that might help somewhat.

---

### Post by drake18746 on 2007-01-13
Or apparently I'm not going to.  When I boot up into the LiveCD, it doesn't see the drive.

I'm totally stuck for ideas since I don't know how to mount drives into a running environment.

---

### Post by drake18746 on 2007-01-13
Alright.  I solved almost all my issues now.  I have the drive formatted and I've already started putting things on it.  All fine and dandy.  But I think that if I turn off the computer and turn it back on, the drive won't be automatically mounted?  If that is the case (I'm not going to test that out right now) What would I have to do to make the drive mount on boot?

Its drive hdb1 and it is currently mounted under /media/hdb1.

---

### Post by logos34 on 2007-01-13
You just need to add it to fstab to have it automount at boot.

post the output from:
> mount
> cat /etc/fstab

---

### Post by drake18746 on 2007-01-13
```
drake@LillyPad:~$ sudo mount
Password:
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
drake@LillyPad:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
drake@LillyPad:~$
```

---

### Post by logos34 on 2007-01-13
sorry about the delay (didn't hear my email beep!)...

> Its drive hdb1 and it is currently mounted under /media/hdb1

are you sure?  i only see hda1 under mount...no matter

what file type is hdb1 formatted as?

---

### Post by drake18746 on 2007-01-13
ext3.

I just (a couple of hours ago) formatted it through the GUI on the tower and it seemed to work.  So much so that I am currently transferring stuff to the drive so I know its there, especially since somebody else I know is able to view the data on that drive remotely.  So its there.

---

### Post by logos34 on 2007-01-13
if ext3, just add this line to your fstab:
> /dev/hdb1     /media/hdb1       ext3    defaults,errors=remount-ro  0  1

then 

> sudo mount -a


Reboot and see if it automounts.

If you want to add the uuidv#, i can give you the command for that too

---

### Post by drake18746 on 2007-01-13
When I did that I got this:```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
I have no idea what that means.

---

### Post by logos34 on 2007-01-13
what do you get with this
> ls /media

---

### Post by drake18746 on 2007-01-13
cdrom, cdrom0 and hdb1.

Don't know if the colours matter, but cdrom is bright cyan while cdrom0 and hdb1 are lightish blue.

Also, when I did a dmesg | tail I got this:
```
drake@LillyPad:~$ dmesg | tail
[ 6189.429325] end_request: I/O error, dev hdb, sector 40
[ 6189.429334] Buffer I/O error on device hdb, logical block 5
[ 6189.429347] end_request: I/O error, dev hdb, sector 48
[ 6189.429357] Buffer I/O error on device hdb, logical block 6
[ 6189.429369] end_request: I/O error, dev hdb, sector 56
[ 6189.429378] Buffer I/O error on device hdb, logical block 7
[ 6189.429419] end_request: I/O error, dev hdb, sector 0
[ 6189.429431] Buffer I/O error on device hdb, logical block 0
[10037.732724] end_request: I/O error, dev hdb, sector 65
[10037.733233] EXT3-fs: unable to read superblock
```
Don't know if that helps you at all.

---

### Post by logos34 on 2007-01-13
this disk could be failing.  Strange...you formatted it as ext3, mounted it at /media/hdb1, you could access it and copy files to it, but sudo fdisk -l cannot detect it, it doesn't show up under 'mount', and you get 'buffer i/o errors' when you add it to fstab and reboot.  

Try running a smart diagnostic on the disk.

first download smartmontools
> sudo apt-get install smartmontools

then run smartctl 
> sudo smartctl -H /dev/hdb

it'll say 'Passed' or 'failed'

---

### Post by drake18746 on 2007-01-13
> drake@LillyPad:~/moos/mooserver$ sudo smartctl -H /dev/hdb
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
Is that an ambiguous or a failed?

---

### Post by logos34 on 2007-01-13
try 
smartctl -i /dev/hdb

---

### Post by drake18746 on 2007-01-13
> drake@LillyPad:/media$ sudo smartctl -i /dev/hdb
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/hdb failed: No such file or directory
drake@LillyPad:/media$ cd /dev
drake@LillyPad:/dev$ sudo fdisk -l

Disk /dev/hda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12095    97153056   83  Linux
/dev/hda2           12096       12188      747022+   5  Extended
/dev/hda5           12096       12188      746991   82  Linux swap / Solaris
drake@LillyPad:/dev$
That's what I got.  Oddly enough, I can still access the drive after rebooting again, can still transfer stuff over to it.  I checked the fstab file, just to make sure I typed in ext3 (as opposed to ext2) and it says that.

Also, when I rebooted it told me that there was something wrong with the suberblock and that I should run something like e2fsc or something like that?  I can't remember exactly.

At any rate, as long as the computer boots up correctly without me having to be there to touch the keyboard and the drive is there, I'll be happy, so I've set fstab back to the way it was before.

---

### Post by logos34 on 2007-01-13
> man e2fsck

I was just going to suggest that.
I was looking for a good guide for it, but for now read the man page for it.  
It'll check for bad sectors and data corruption.  It might not be physical damage.

---

### Post by drake18746 on 2007-01-13
Checked out the manual, it actually made a bit of sense.  So I ran sudo e2fsck /dev/hdb1 and it told me to run e2fsck -b 8193 <device>.  Ran all sorts of variations on /dev/hdb for device and I always got the same result: No such file or firectory while trying to open /dev/hdb or whatever I had used as the device for that specific attempt.

And thanks for all your help regarding this.  I'm sure its probably driving you nuts having to water down your questions so that I can understand them.

---

### Post by logos34 on 2007-01-13
unmount hdb1 before you run e2fsck 

here are a couple commands
> Read-only method
sudo e2fsck -c /dev/hdb

Non-destructive read/write method
sudo e2fsck -c -c /dev/hdb

see what you get with that.

good luck

---

