---
title: "Mac-On-Linux?"
date: 2006-10-11
forum: Apple PPC Users
---

### Post by munchbach on 2006-10-11
Ok:

I'm sort of new to this but I didn't see anything that really covered my issue on the forums.  And as helpful as the MOL wiki page was I still can't seem to get this working.  So any help woule be appreciated.  

Ever time I run "startmol" this is what i see:

```
root@Pubuntu:~# startmol
Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Running in PowerPC 7400 mode, 48 MB RAM
Timebase: 08.32 MHz, Bus: 33.28 MHz, Clock: 833 MHz
Could not open driver 'drivers/misc.nw': No such file or directory
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not connect to X server
Could not open driver 'drivers/video.nw': No such file or directory
Fullscreen video on VT 8.
Could not open '/var/lib/mol/console.kbd'
Cache enabled for console-video
Video driver(s): [console_video]

    1280* 854, depth 8,15,32   { 60.0 } Hz
    1440* 960, depth 8,15,32   { 0.0 } Hz

No video mode match the default one.
Autoswitching to console
ALSA sound driver (device 'default')
Could not open driver 'drivers/scsi.nw': No such file or directory
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------
----> /dev/hda2 might be a boot-strap partition.
    Unembedded HFS+ /dev/hda3                       <rw> 71552 MB
------> /dev/hda4 is linux-mounted with write privileges.
Could not open '/dev/hda4' with read-write permissions
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'

Could not open driver 'drivers/blk.nw': No such file or directory

>> =============================================================
>> Mac-on-Linux OpenFirmware 0.9.70

>> --- No bootable disk was found! -----------------------------
>> If this is an oldworld machine, try booting from the MacOS
>> install CD and install MacOS from within MOL.
>> -------------------------------------------------------------
cleaning up...
Terminating threads...
DONE

```

My OS X partition is on /dev/had3.  This is what the boot portion of molrc.osx looks like:

```
#       MOL will boot from CD if it invoked through 'startmol -X --cdboot'.

blkdev:                 /dev/cdrom      -cd ${cdboot}

ifempty ${altconfig} {
    # default configuration
    blkdev:             /dev/hda3 -boot -rw
    blkdev:             /dev/sda        -rw
    blkdev:             /dev/sdb        -rw

} else {
    # alternate configuration
    blkdev:             /dev/hda3 -boot -rw
    #blkdev:            /dev/loop0      -rw
}



```

Thank you in advance for any help you can offer.

---

### Post by munchbach on 2006-10-11
Ok, update.  I went to debian and downloaded:

mol-driver-linux
mol-driver-macosx
mol-driver-macos

When I run "startmol" this is what I see:

```
root@Pubuntu:~# startmol
Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Loading Mac-on-Linux kernel module:
insmod /lib/modules/2.6.15-26-powerpc/kernel/drivers/macintosh/mol/mol.ko
Running in PowerPC 7400 mode, 48 MB RAM
Timebase: 08.32 MHz, Bus: 33.28 MHz, Clock: 1666 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not connect to X server
Fullscreen video on VT 8.
Could not open '/var/lib/mol/console.kbd'
Cache enabled for console-video
Video driver(s): [console_video]

    1280* 854, depth 8,15,32   { 60.0 } Hz
    1440* 960, depth 8,15,32   { 0.0 } Hz

No video mode match the default one.
Autoswitching to console
ALSA sound driver (device 'default')
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------
----> /dev/hda2 might be a boot-strap partition.
    Unembedded HFS+ /dev/hda3                       <rw> 71552 MB
------> /dev/hda4 is linux-mounted with write privileges.
Could not open '/dev/hda4' with read-write permissions
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'


>> =============================================================
>> Mac-on-Linux OpenFirmware 0.9.70
>> os_seek error

>> --- No bootable disk was found! -----------------------------
>> If this is an oldworld machine, try booting from the MacOS
>> install CD and install MacOS from within MOL.
>> -------------------------------------------------------------
cleaning up...
Terminating threads...
DONE

```

Anyone have any ideas?  I feel like I'm getting closer!

Cheers.

---

### Post by pauljwells on 2006-10-11
Did you run sudo molvconfig to set the video modes?

---

### Post by munchbach on 2006-10-11
> **pauljwells said:**
> Did you run sudo molvconfig to set the video modes?

Yes, I set that up already I have a feeling that something is going on with the boot partition but I can't tell what.  I know it it not mounted.

```
CD   /dev/cdrom       CD-ROM         <read-only>   ------
----> /dev/hda2 might be a boot-strap partition.
    **Unembedded HFS+ /dev/hda3                       <rw> 71552 MB**
------> /dev/hda4 is linux-mounted with write privileges.
Could not open '/dev/hda4' with read-write permissions
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'


>> =============================================================
>> Mac-on-Linux OpenFirmware 0.9.70

>> --- No bootable disk was found! -----------------------------
>> If this is an oldworld machine, try booting from the MacOS
>> install CD and install MacOS from within MOL.
>> -------------------------------------------------------------
cleaning up...
Terminating threads...
DONE

```

---

### Post by ssam on 2006-10-11
did you try
```
startmol -x
```

---

### Post by munchbach on 2006-10-12
> **ssam said:**
> did you try
```
startmol -x
```

That seemed to produce a more desirable outcome but OS X is still not booting, this is what I see.  I treid to reconfigure the video driver settings with molvconfig but it didn't seem to have an effect.  What is everyone using for these settings?  I have a G4 PowerBook DL-SD 1.67GHz with 2 G of RAM.

[IMG]http://web.mac.com/munchbach/Screenshot.png[/IMG]

I've let it sit there for a little while but nothing seems to come up.

Thanks for all your help.

---

### Post by munchbach on 2006-10-12
Well I finally figured it out.  They key was going to get the debian mol-drivers-macosx.  The command that finally worked was:

```
sudo -i
```

then

```
startmol -X
```

for full screen

and 

```
sudo startmol -X 
```

for the picture in picture type view.

Thanks to everyone for their help!

---

### Post by salguod on 2006-10-18
where does one download the debian mol-drivers-macosx?

---

### Post by salguod on 2006-10-18
found it...
sudo apt-get install mol-drivers-macosx
 or
[http://packages.debian.org/unstable/otherosfs/mol-drivers-macosx](http://packages.debian.org/unstable/otherosfs/mol-drivers-macosx)

---

### Post by salguod on 2006-10-18
I get a similar result when i use the command startmol

douglas@douglas-laptop:~$ startmol
Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Mac-on-Linux must be setuid root!
douglas@douglas-laptop:~$ sudo startmol
Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Loading Mac-on-Linux kernel module:
insmod /lib/modules/2.6.15-26-powerpc/kernel/drivers/macintosh/mol/mol.ko
Running in PowerPC 7400 mode, 48 MB RAM
Timebase: 33.33 MHz, Bus: 133.32 MHz, Clock: 667 MHz
Could not open driver 'drivers/misc.nw': No such file or directory
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
Could not open driver 'drivers/video.nw': No such file or directory
Fullscreen video on VT 8.
Could not open '/var/lib/mol/console.kbd'
Cache enabled for console-video
Video driver(s): [xvideo] [console_video]

     640* 480, depth 8,15,32   { 59.9, 74.9, 89.9, 99.7 } Hz
     640* 480, depth 8,15   { 116.6 } Hz
     800* 600, depth 8,15,32   { 56.2, 60.3, 70.0, 72.1, 74.9, 89.9 } Hz
     800* 600, depth 8,15   { 94.8 } Hz
     800* 600, depth 8,15,32   { 99.9 } Hz
    1024* 768, depth 8,15,32   { 60.0, 70.0, 74.8, 75.0 } Hz
    1152* 768, depth 8,15,32   { 54.7 } Hz
    1280* 854, depth 8,15,32   { 0.0, 60.0 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,32   { 0.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

ALSA sound driver (device 'default')
Could not open driver 'drivers/scsi.nw': No such file or directory
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------
----> /dev/hda2 might be a boot-strap partition.
------> /dev/hda3 is linux-mounted with write privileges.
Could not open '/dev/hda3' with read-write permissions
------> /dev/hda5 is linux-mounted with write privileges.
Could not open '/dev/hda5' with read-write permissions
No volumes found in '/dev/hda'
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'

Could not open driver 'drivers/blk.nw': No such file or directory

>> =============================================================
>> Mac-on-Linux OpenFirmware 0.9.70
>> os_seek error

>> --- No bootable disk was found! -----------------------------
>> If this is an oldworld machine, try booting from the MacOS
>> install CD and install MacOS from within MOL.
>> -------------------------------------------------------------
cleaning up...
Terminating threads...
DONE
douglas@douglas-laptop:~$



when I use startmol -X, by screen leaves the gui mode and I have to restart to get it back. 

the startx command tells me that is is already running

---

### Post by munchbach on 2006-10-18
Try downloading this:

> [http://packages.debian.org/unstable/...drivers-macosx](http://packages.debian.org/unstable/...drivers-macosx)

You should be able to doube click it to install, afterwards type:

```
sudo startmol -X
```

Captial X capitalization may be important!

Good luck!

---

### Post by salguod on 2006-10-18
hi,
thanks for your reply. things are still bad, but i guess they are improving! sudo startmol -X does not go into non-gui anymore, but MOL still does not start.

from what i can understand, it cannot find the Mac 0s startup disk. I KNOW that OS X is on hda5. How to I tell it do find it there? BTW, my mac partition is mounted in linux - does that make a difference?

here is the output:

douglas@douglas-laptop:~$ sudo startmol -X
Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Running in PowerPC 7400 mode, 96 MB RAM
Timebase: 33.33 MHz, Bus: 133.32 MHz, Clock: 667 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
Fullscreen video on VT 8.
Could not open '/var/lib/mol/console.kbd'
Video driver(s): [xvideo] [console_video]

     640* 480, depth 8,15,32   { 59.9, 74.9, 89.9, 99.7 } Hz
     640* 480, depth 8,15   { 116.6 } Hz
     800* 600, depth 8,15,32   { 56.2, 60.3, 70.0, 72.1, 74.9, 89.9 } Hz
     800* 600, depth 8,15   { 94.8 } Hz
     800* 600, depth 8,15,32   { 99.9 } Hz
    1024* 768, depth 8,15,32   { 60.0, 70.0, 74.8, 75.0 } Hz
    1152* 768, depth 8,15,32   { 54.7 } Hz
    1280* 854, depth 8,15,32   { 0.0, 60.0 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,32   { 0.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

ALSA sound driver (device 'default')
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------
----> /dev/hda2 might be a boot-strap partition.
------> /dev/hda3 is linux-mounted with write privileges.
Could not open '/dev/hda3' with read-write permissions
------> /dev/hda5 is linux-mounted with write privileges.
Could not open '/dev/hda5' with read-write permissions
No volumes found in '/dev/hda'
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'


>> ==================================================
>> MacOS X Boot Loader 0.9.70
>> SyncRead: error
>> SyncRead: error
>> --> Boot loader failure: No bootable disk found

cleaning up...
Terminating threads...
DONE
douglas@douglas-laptop:~$

---

### Post by munchbach on 2006-10-18
> from what i can understand, it cannot find the Mac 0s startup disk. I KNOW that OS X is on hda5. How to I tell it do find it there? BTW, my mac partition is mounted in linux - does that make a difference

Go to "Places" and click "Computer".  You should see your machintosh HD volume there.  If you double click it to open it should give you an error message that says, "Can not mount /dev/hda*x*"

This is where you OS X partition is.  Make sure you change your MOL config file to reflect that.

Your /dev/hda5 is your linux partition it says so right in the error message.  Try hda4 that is usually what it is.

Cheers.

---

