---
title: "[SOLVED] usb floppy is recognized but not mounted?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by weezerisrock on 2007-09-20
Hello all.  I have an external usb IBM floppy drive.  I'm trying to get it to be recognized in linux but am completely unsuccessful.   I have two linux boxes (home PC and a laptop) and the same thing is happening on both.  I plug in the floppy, I can see it in hardware but thats it.  

Can anyone help me recognize it so I can use it?  

Please help!  I was hoping to setup a dual boot tonite!

---

### Post by vikram on 2007-09-20
have you tried manually mounting it ? the command is 
sudo **mount** /dev/fd0 /floppy -t vfat

If your device isn't fd0 try

sudo fdisk -l


for details take a look at 
[https://help.ubuntu.com/community/Mount?highlight=%28mount%29]("https://help.ubuntu.com/community/Mount?highlight=%28mount%29") 

hope this helps

---

### Post by weezerisrock on 2007-09-21
no luck, as far as I know the drive is being recognized but not as a floppy drive maybe?


here is my fdisk -l
```
mckayr@frodo:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

```

as you can see the floppy is not listed at all.

But under device manager I can see it.  According to device manager it has taken /dev/sg2...
But when I try to mount that I get....

```
mckayr@frodo:/dev$ sudo mount /dev/sg2 floppy -t vfat
mount: mount point floppy does not exist

```

---

### Post by yabbadabbadont on 2007-09-21
Try:
```
sudo mount -t vfat /dev/sg2 /media/floppy
```

---

### Post by weezerisrock on 2007-09-21
```
mckayr@frodo:~$ sudo mount -t vfat /dev/sg2 /media/floppy
Password:
mount: mount point /media/floppy does not exist

```

Thanks for your help thus far.  I hope I can get this going!

---

### Post by asmoore82 on 2007-09-21
Does the floppy original belong to an IBM Thinkpad?
If so, you may need to add the boot parameter ``floppy.floppy=thinkpad''

---

### Post by weezerisrock on 2007-09-21
it says nothing about being for a thinkpad.  I'm borrowing it from my work.

Its actually made by TEAC if that makes a difference.  Part number is 19308801-19 just for completeness.

---

### Post by yabbadabbadont on 2007-09-21
> **weezerisrock said:**
> ```
mckayr@frodo:~$ sudo mount -t vfat /dev/sg2 /media/floppy
Password:
mount: mount point /media/floppy does not exist

```

Thanks for your help thus far.  I hope I can get this going!

What version of Ubuntu do you have installed?

What is the output when you run, in a terminal window, the following:
```
ls -l /media
```

---

### Post by weezerisrock on 2007-09-21
I have feisty installed

```
mckayr@frodo:~$ ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2007-09-19 12:00 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-09-19 12:00 cdrom0

```

---

### Post by yabbadabbadont on 2007-09-21
Hmm.  It must not have made any entries for a floppy since it didn't detect one when you originally installed.  Create a mount point for the floppy using ```
sudo mkdir /media/floppy
``` and then try the command again.

---

### Post by weezerisrock on 2007-09-21
different error now.

```
mckayr@frodo:~$ sudo mount -t vfat /dev/sg2 /media/floppy
mount: /dev/sg2 is not a block device

```

---

### Post by yabbadabbadont on 2007-09-21
That would seem to indicate that /dev/sg2 is not the correct device for your usb floppy drive.  Unplug the drive, then plug it back in.  Now run "dmesg" in a terminal window and you should see some messages at the bottom regarding the floppy drive.  Look for a device name in that output.

---

### Post by weezerisrock on 2007-09-21
ok here is the output

```
[ 9438.804973] scsi 10:0:0:0: Direct-Access     TEAC     FD-05PUB         1026 PQ: 0 ANSI: 0 CCS
[ 9439.188785] sd 10:0:0:0: Attached scsi removable disk sdb
[ 9439.188825] sd 10:0:0:0: Attached scsi generic sg2 type 0

```

so sdb then?

```
mckayr@frodo:~$ sudo mount -t vfat /dev/sdb /media/floppy
mount: No medium found

```

again thank you for your help, sounds like we're getting closer!

---

### Post by yabbadabbadont on 2007-09-21
Are you sure that there is a disk in the drive and that is has been formatted for DOS/Windows?  If so, you might try this:
```
sudo mount -t vfat /dev/sdb1 /media/floppy
```
That shouldn't work by the way as floppies generally aren't partitioned.  (However USB thumb drives usually are.  Go figure.  :D)

---

### Post by weezerisrock on 2007-09-21
that command gave me special device doesn't exist error.

I tried a different floppy just to be on the safe side, but when I run the command
```
mckayr@frodo:~$ sudo mount -t vfat /dev/sdb /media/floppy
```
I get the same error as before (no medium found) however, its not even attempting to look at the disk, the green light on the floppy never lights up and the drive never spins up.  The error also pops up immediately with zero waiting.

---

### Post by yabbadabbadont on 2007-09-21
Do you get the same error if you run "sudo fdisk -l /dev/sdb"?  If so, does that usb drive work with any other OS or on any other computer?

---

### Post by weezerisrock on 2007-09-21
nothing happens when I type that in, it just goes back to the prompt.

And I know it works in windows, used it at work not that long ago.  The only reason I needed it was to setup my home pc to dual boot.  (stupid windows and no sata drivers)  in hindsight, it might have been easier to attempt to make a slipstream disk.

---

### Post by yabbadabbadont on 2007-09-21
Sorry, I'm stumped.

---

### Post by weezerisrock on 2007-09-21
no worries, I'll just scream incompatibility.  (seems likely since it works in windows but wouldn't work in two separate ubuntu boxes.)  I'll just go the way of the slipstream and see if I'm smart enough to make it happen.

Thanks for your time and effort, it is very appreciated.

---

### Post by alienexplorers on 2007-09-21
Try:
> sudo pmount -t vfat /dev/sdb /media/floppy

---

### Post by weezerisrock on 2007-09-21
I get command not found.

---

### Post by alienexplorers on 2007-09-21
Go into synaptic and enable pmount.
or
sudo apt-get install pmount

---

### Post by alienexplorers on 2007-09-21
Load your usb floppy using:
> sudo pmount -t vfat /dev/sdb /media/floppy

---

### Post by AlCarmon on 2007-09-21
2 things come to mind;

Be sure support for the USB floppy is not disabled in the BIOS.

Try USB floppy  formating, information utilities at [http://www.geocities.jp/tedi_world/format_usbfdd_e.html](http://www.geocities.jp/tedi_world/format_usbfdd_e.html)
with a blank disk.

---

### Post by weezerisrock on 2007-09-22
I apologize for making you guys do all this work.   The floppy which worked last week in windows, no longer does.  It does the same thing as in linux.  I see it appear in My Computer, then I put in a floppy disk and tell it to access it and I immediately get the insert disk error, and it never even attempts to look.  So it looks like the fault was mine all along.  

I apologize again and thank everyone for their help.

---

### Post by yabbadabbadont on 2007-09-22
As long as you learned something, then the effort was well spent.  :)

---

### Post by zhangweiwu on 2008-01-28
Please take a look at \
[http://ubuntuforums.org/showthread.php?p=4221425#post4221425](http://ubuntuforums.org/showthread.php?p=4221425#post4221425)

Which describe an identical problem except that the owner of the floppy driver must be working. There seems do exist a bug in automatically mounting a DOS format floppy for such USB driver. By the way the model of the USB driver is also the same.

---

