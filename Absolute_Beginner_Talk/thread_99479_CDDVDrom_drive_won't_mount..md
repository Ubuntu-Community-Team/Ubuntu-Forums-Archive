---
title: "CD\DVDrom drive won't mount."
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-12-05
This is the error I get when I pop a CD in.

-----
~Unable to mount the volume. There is probably no media in the device.~

Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: No medium found
Error: could not execute pmoun
-----

This makes no sence to me because the drive worked perfectly any other time i placed (the same) CD's\DVD's in.

---

### Post by blastus on 2005-12-05
Is it a music CD? Those can't be mounted.

---

### Post by CPUFreak91 on 2005-12-05
I get a UDI error on some rewritable dvds and I make sure to unmount it (if possible) then I go to a console and type:  [FONT="Courier New"]mount /dev/cdrom[/FONT]
or in your case you can also try: [FONT="Courier New"]mount /dev/hdx[/FONT] where x is your drive letter

---

### Post by kalos on 2005-12-05
Does that error happen as soon as you put the CD in or when you try to mount the device?

---

### Post by nitricacid on 2005-12-05
ok, all the CDs I put in my drive are CD-R's and are data only.
Usually the cdrom drive would mount on it's own and would have an icon on the desktop with a picture of a CD and w\e the name of the cd is.
I don't know how long my cddrive has been down since i think the last time i used it was to transfer some music files i had burned from one computer to this one that is running linux.

The error only accurs when i to to Places>Computer>cd rom\dvd rom drive because the ICON does not show up on the desk top anymore.
It will not find any of the CDs i place in the drive which i find really weird considering it would automaticly be for.

I have tried to mount the drive using ```
sudo mount /dev/cdrom
``` and it says No media found.
I try ```
 sudo mount /dev/hdx (x is drive letter D i believe)
```
and return with this error [code[mount: can't find /dev/hdd in /etc/fstab or /etc/mtab[/code]

Here is my fstab settings.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by kalos on 2005-12-05
from the last line of your fstab, it looks like /dev/hdc is your cdrom.
Try ```
sudo mount /media/cdrom0
``` (that should use your fstab settings to mount the cd).

Or you can do 
```
sudo umount /media/cdrom0
sudo mount -t auto /dev/hdc /media/cdrom0
```
That should ensure that nothing is already  mounted in /media/cdrom0

Can you show /etc/mtab ? (type cat /etc/mtab)

-kalos

---

### Post by nitricacid on 2005-12-05
Print out:

nitricacid@ubuntu:~$ sudo mount /media/cdrom0
mount: No medium found
nitricacid@ubuntu:~$ sudo umount /media/cdrom0
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

nitricacid@ubuntu:~$ sudo mount -t auto /dev/hdc /media/cdrom0
mount: you must specify the filesystem type
nitricacid@ubuntu:~$

nitricacid@ubuntu:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
/dev/hdc  /media/cdrom0  udf,iso9660 user,noauto 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0

nitricacid@ubuntu:~$ sudo cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
/dev/hdc  /media/cdrom0  udf,iso9660 user,noauto 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
nitricacid@ubuntu:~$

-------

I definitly think something in either the /etc/fstab or /etc/mtab got messed up because its not finding anything it needs within those 2 files.

---

### Post by kalos on 2005-12-05
I must admit I'm no linux pro yet, so I'm not quite sure what's wrong.

Strange, you have /media/cdrom0 mounted, but can't unmount. I suppose you could do a lazy unmount...

try ```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```

If you reboot (without any CD in drive), is there an entry for /dev/hdc in mtab? What about when you insert CD?

---

### Post by nitricacid on 2005-12-05
I did happen to get a glimps of some error message on the shutdown cmdline after it "sending process the TERM signal", it was somthing about the CDrom drive but didn't make out exactly what it said.

It was something to the extent of unmounting problems with cdrom drive, or something like that.

---

### Post by nitricacid on 2005-12-06
BUMP and an update.

I think i figured out why my cdrom drive isn't working.
It seems i never unmounted the drive the last time i used it, thus it think the drive is still mounted from the last time.
Anyone know how to clear this error, and set it back to believing that everything is unmounted?
```
 nitricacid@ubuntu:~$ sudo umount /media/cdrom0
umount: /media/cdrom0: not mounted
```

This is what i get when i have CD in the drive and try to mount it.
```
nitricacid@ubuntu:~$ sudo mount -t iso9660 /dev/hdc /media/cdrom0
Password:
mount: No medium found
nitricacid@ubuntu:~$

```

---

### Post by cilynx on 2005-12-06
The proper command is "umount" without the 'n'.  Brilliant, eh?
[edit]does 'df' show your cd as mounted?[/edit]

---

### Post by nitricacid on 2005-12-06
[QUOTE=cilynx]The proper command is "umount" without the 'n'.  Brilliant, eh?
[edit]does 'df' show your cd as mounted?[/edit][/QUOTE]
 DF? No it doesn't show the CD mounted at all.

Is this how my /etc/fstab should be?
/dev/hdc        /media/cdrom   udf,iso9660 user,noauto     0      0

I also read on another forum about the exact same problem and it ended up being a bug in the system.

---

### Post by cilynx on 2005-12-06
Yup, this is the line from my (working) fstab

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

The "cdrom0" is only because I have 2 cdroms.

This is kindof a cheesy test:

Eject the cdrom, button on the front or software, doesn't matter.  Try to mount said cdrom with the tray out.  It shouldn't matter if you click the icon or try to mount on the command line.  Does it bring the tray in when you do this?

---

### Post by nitricacid on 2005-12-06
[QUOTE=cilynx]Yup, this is the line from my (working) fstab

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

The "cdrom0" is only because I have 2 cdroms.

This is kindof a cheesy test:

Eject the cdrom, button on the front or software, doesn't matter.  Try to mount said cdrom with the tray out.  It shouldn't matter if you click the icon or try to mount on the command line.  Does it bring the tray in when you do this?[/QUOTE]

I don't have 2 CDROm drives, only one that is CD-rom & DVD-rom (in one).
Yes, When i mount the drive with the tray out it sucks the tray in and trys to read the cd but nothing happend. just this error...

Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: No medium found
Error: could not execute pmount


I have tried everything i could think of why it might be saying this and nothing has worked.
I never messed with any files that partain to the CDrom drive so i don't understand why it doesn't work.

---

### Post by wyohermit on 2005-12-06
Hi, I have been following this thread hoping someone had a solution, because I have exactly the same problem.  Which I have been fighting for quite a while.  I have tried changing everything, (slave/master, hoary/breezy. new install of debian 3.1, every possible config of fstab that I could find or think of) and nothing has helped.  The wierd part on my system is that dvd's both video and data work just fine.

---

### Post by ramba on 2005-12-09
I have the same problem, except I can open the drive from /media/cdrom0. For some reason my ubuntu doesn't want to load it on desktop and "Computer" folder anymore. I have compiled the newest kernel with cK patchset and modified the bootup process so I must have broken something along the way.

Well, I hated that cdrom icon anyway! :cool:

Edit:
*Ow, and the error what I get is actually different. It can't mount the drive because it's already mounted or something..*

---

### Post by CHUCKYCHUCK on 2005-12-10
i had similar problems before, i just rebooted my computer and all was normal again

---

