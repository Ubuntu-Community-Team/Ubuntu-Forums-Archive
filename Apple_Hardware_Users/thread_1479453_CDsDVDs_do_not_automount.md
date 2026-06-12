---
title: "CDs/DVDs do not automount"
date: 2010-05-10
forum: Apple Hardware Users
---

### Post by JoeMac42 on 2010-05-10
Now that I can successfully [_[COLOR="Blue"]load the media,[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=9263201") I would like to figure out how to get a DVD or CD to automount in Lucid on my Dual-G4 PowerPC Mac.  Right now I have to use the "mount" command in terminal to successfully mount the media. lshw identifies the drive as a Pioneer DVD-RW DVR-105. My other, less unusual (i.e. Cannonical supported) Lucid installs just pop an icon onto the desktop and within nautilus and for video-DVDs they even open up VLC for me and bring up the DVD menu.

---

### Post by JoeMac42 on 2010-05-10
This is getting odd.  I just plugged in the external cd/dvd usb drive from my hp mini 311 into my mac g4 and both cds and dvds automount from there.  Still no joy from the internal atapi Pioneer drive...maybe I need to try editing fstab...any ideas?

---

### Post by linuxopjemac on 2010-05-11
When I have the time I will have a look into this issue. I have Lucid Lynx running too now.

---

### Post by linuxopjemac on 2010-05-11
On my PowerBook G3 Pismo, automounting works out of the box. In my fstab there is no entry for cdrom. I don't have a Pioneer though, I have:

[    5.667210] Probing IDE interface ide2...
[    6.066974] hde: MATSHITA CR-175, ATAPI CD/DVD-ROM drive
[    6.402944] hde: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    6.403057] hde: MWDMA2 mode selected
[    6.403233] ide2 at 0xe9062000-0xe9062070,0xe9062160 on irq 23
[    6.403481] ide-gd driver 1.18
[    6.403612] hda: max request size: 512KiB
[    6.830946] hda: 78242976 sectors (40060 MB) w/8192KiB Cache, CHS=16383/255/63
[    6.831399] hda: cache flushes supported
[    6.831728]  hda: [mac] hda1 hda2 hda3 hda4 hda5 hda6 hda7
[    6.839981] ide-cd driver 5.00
[    6.842418] ide-cd: hde: ATAPI 24X CD-ROM drive, 128kB Cache
[    6.842447] Uniform CD-ROM driver Revision: 3.20

It seems to only affect the Pioneer drive ?

I can recommend Debian with LXDE Mint, it also looks good and it will probably work better with respect to automounting CDROMS.

---

### Post by JoeMac42 on 2010-05-12
I think I'll stick with Ubuntu for now.  I'm loading up Debian/LXDE on a netbook, so if I like it I might consider eventually going the Mint route.  Right now I'm thinking this is some sort of kernel module or udev thing, so I'm not sure changing distributions would necessarily help.

---

### Post by JoeMac42 on 2010-05-14
Is anyone else on here having problems with ATAPI Pioneer Superdrives?

---

### Post by linuxopjemac on 2010-05-14
Debian LXDE Mint is based on an older kernel and older udev. You might have more luck than with Ubuntu. Just my 2 cents.

---

### Post by JoeMac42 on 2010-05-14
The only reason I moved to Lucid was to get a kernel with Nouveau support that worked well with my video card.  That much worked very well with my nvidia 6600 AGP video, so I'm reluctant to switch without learning more.  Also, with dual-1.4GHz G4s and 2G of ram I really don't have any trouble running Gnome.  Nothing against LXDE, but I've grown to like Gnome for the most part.  If I did switch the G4, it would be to Lenny or Squeeze.  I'm trying not to take one step forward and two back.

> **linuxopjemac said:**
> Debian LXDE Mint is based on an older kernel and older udev. You might have more luck than with Ubuntu. Just my 2 cents.

---

### Post by JoeMac42 on 2010-05-14
Could I be having some sort of problem with Gnome-Volume-Manager?

---

### Post by JoeMac42 on 2010-05-14
Looks like I'll answer myself  - gnome-volume-manager was dropped from lucid.  So how is automounting handled now?


> **JoeMac42 said:**
> Could I be having some sort of problem with Gnome-Volume-Manager?

---

### Post by linuxopjemac on 2010-05-14
[https://launchpad.net/ubuntu/lucid/powerpc/gnome-volume-manager/2.24.1-3ubuntu1](https://launchpad.net/ubuntu/lucid/powerpc/gnome-volume-manager/2.24.1-3ubuntu1)

---

### Post by JoeMac42 on 2010-05-14
That confirms it's deletion from Lucid...now I need to figure out if this is a udev issue or a hal issue.  I thought hal had been removed from the Lucid packages in favor of udev, but apparently I have both. I need to do more digging...  

> **linuxopjemac said:**
> [https://launchpad.net/ubuntu/lucid/powerpc/gnome-volume-manager/2.24.1-3ubuntu1](https://launchpad.net/ubuntu/lucid/powerpc/gnome-volume-manager/2.24.1-3ubuntu1)

---

### Post by JoeMac42 on 2010-05-14
Anyone have any experience using ivman in Lucid to do this?

---

### Post by frenchy82 on 2010-05-15
hi,
JoeMac42: after inserting your cd, is there something special with dmesg?

---

### Post by JoeMac42 on 2010-05-15
I will take a look.  Someone was helping me debug this over in Launchpad and suggested adding a line in fstab - I missed that one.  There probably should be an fstab line for the drive since it is an internal ATAPI device, not an external device.  I think I have been barking up the wrong udev/hal tree with this.  I am slowly learning...

I'll try editing fstab first then take another look at dmesg to see if anything is there.  

> **frenchy82 said:**
> hi,
JoeMac42: after inserting your cd, is there something special with dmesg?

---

### Post by JoeMac42 on 2010-05-16
The folks over at [https://answers.launchpad.net/ubuntu/+question/111055]("https://answers.launchpad.net/ubuntu/+question/111055") suggested some lines for fstab, but so far nothing has worked for automounting media in the internal CD/DVD in Lucid.

---

### Post by JoeMac42 on 2010-05-16
More info:

```
 $ lshal | egrep cdrom
  info.linux.driver = 'ide-cdrom'  (string)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdplusrdl = false  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrdl = false  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 5644  (0x160c)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 2822  (0xb06)  (int)
  storage.cdrom.write_speeds = {'2822', '2116', '1411', '705'} (string list)
  storage.drive_type = 'cdrom'  (string)
$ ls -l /dev/{cd,dvd}*
lrwxrwxrwx 1 root root 3 2010-05-16 10:15 /dev/cdrom -> hde
lrwxrwxrwx 1 root root 3 2010-05-16 10:15 /dev/cdrw -> hde
lrwxrwxrwx 1 root root 3 2010-05-16 10:15 /dev/dvd -> hde
lrwxrwxrwx 1 root root 3 2010-05-16 10:15 /dev/dvdrw -> hde
$ hdparm -I /dev/hde

/dev/hde:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange 
```

---

### Post by JoeMac42 on 2010-05-21
I filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/584052]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/584052")
Anyone else having this problem in lucid please check in there...

---

### Post by JoeMac42 on 2010-06-20
This appears to be the same as the bug reported here:

[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/590448]("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/590448")

udisks is not polling to detect the media.  There is a partial solution shown in the bug report to force usdisks to poll:

udisks --poll-for-media /dev/<devicename>

in my case, this was:
```
udisks --poll-for-media /dev/hde
```

If I do this after inserting media into the drive, the media is properly recognized in the ATAPI drive and mounted to the desktop and/or the appropriate application is started for playing audio CDs or movie DVDs. It should also be run after ejecting media.

---

### Post by JoeMac42 on 2010-06-21
The following gives exactly the desired behavior with the ATAPI drive:
```
eject -T && udisks --poll-for-media /dev/hde
```

It works for opening the drive, inserting media and mounting/playing as well as opening the drive and properly unmounting the media.  Now if I could only figure out how to bind that code successfully to the Apple keyboard's "eject" key, then I would have a work-around until someone provides a proper fix for the powerpc version of udisks...

---

### Post by abtabt on 2010-06-24
hi joemac 42 and others

this kernel 2.6.32-22 on 10.04 

need to be update to 2.6.34-xx to be ok with the cd problem

but i think  10.04 will not come with kernel 2.6.34-xx ever 

but if you compile  kernel  2.6.34-xx it can solve the problem

have a nice day

---

### Post by JoeMac42 on 2010-06-29
abtabt, can you confirm that you've been able to fix this problem on the powerpc port of 10.04 by compiling kernel 2.6.34-xx?  If so, is a compiled kernel available to try?  Any chance that the "fix" can be backported into a new powerpc 2.6.32-xx kernel?

---

### Post by abtabt on 2010-06-30
Linux Kernel 2.6.34 for Ubuntu 10.04 - PowerPC

[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by Frobber on 2010-06-30
I've been half-heartrdly following this item since 10.04 for ppc was posted. 

I question why we think the kernel is the problem. My system is a tripple boot, Ubuntu Lucid Lynx, Debian 'squeeze', and OSX. The deb distro has 2.6.32-5 powerpc deb kernel. 

While in the debian squeeze I have no problems with CD's or DVD's, install a disk and it auto mounts. I can right click and unmount, or eject. I can also eject from the MAC keyboard eject button.

I've noted in the filesystem,  /media has an symbolic link to /cdrom and an additional folder labeled cdrom0. The /etc/fstab has an entry for dev/hda   /media/cdrom0   udf,iso9660   user,noauto   0   0. I have been playing with the fstab and creating the alias in /dev but have yet to sucessfully automount in Ubuntu.

My machine - IMAC G5, 20", circa 2005.

---

### Post by JoeMac42 on 2010-07-05
I'm not convinced that it's the kernel, but I think there are differences in how the 2.6.32-xx kernel was compiled for squeeze vs. lucid.  I had thought the problem was with udisks until I started seeing forum posts referring to compiling 2.6.34 as fixing the issue.  Even then, I'm not sure if the issue there is the kernel version or (maybe more likely) how it is compiled since there are other 2.6.32 kernels that don't have this problem and I read of at least one instance of 2.6.34 having the same issue with CDs and DVDs.  I know forcing udisks to poll does mount the media, but then again I don't really understand how udisks "normally" polls for the presence of media, so I'm not sure if the problem is udisks or something else.

---

### Post by Nyx_The_Mage on 2010-11-08
I know I am a little late for this thread but I thought I'd mention a quick work around for anyone else with this issue. Just add the following to crontab so it runs every few minutes and the disc will automatically be mounted:

```
udisks --poll-for-media /dev/cdrom
```

The system will run just like it would without the bug. I also doubt this would be taxing on CPU cycles unless you have a machine far below 1Ghz. I have used this solution on my iBook G4 1.2Ghz for now while I wait for a real fix.

---

### Post by Nonmouse on 2010-11-13
Well this is apparently still an issue.  I have a fresh install of 10.10 on a Mac Mini G4 with a superdrive and I have to run the same command line of udisk to get an audio cd to mount.

---

### Post by JDFIght on 2011-02-05
Hello!

This is a bit of a drastic fix,  but I was able to fix the CD/DVD mounting problem on my g4 powerbook Ubuntu 10.04 LTS system...  The CD/DVD mounting issue had previously annoyed me for months until I finally gave up and just created a taskbar launcher that runs the "udisks --poll-for-media /dev/hdb" command...   

One day, on a completely unrelated whim, I decided I wanted to give KDE a try.  So ,I installed kubuntu-desktop... At first it ran terribly slow on the powerbook g4 system...  However,  I soon noticed,   when I am used KDE session,  DVDs/CDs automounted perfectly...  when I switched back to GNOME,  it's broken again...  So,  I have switched to using KDE as my main desktop session for now... 

KDE runs poorly with the default settings on my system.  The Radeon mobility card just burns up with the OpenGL Compositing Effects - and I was starting to worry that KDE was going to fry my system - My fans were going into overdrive every few minutes -  So I went in and changed the following settings : >System Settings>Desktop>Compositing type: XRender

If you experience graphic glitches while compositing is enabled with XRender,  just disable Desktop Effects altogether : uncheck System Settings>Desktop>General> Enable Desktop Effects - 

Ultimately,  Disabled effects and Disabled compositing gives the best performance on my system IMO,  even without the fancy effects enabled,  it looks better than GNOME.    

Anyway, My KDE session is running well and CDs and DVDs actually mount automatically now! Yay for basic functionality!

UPDATE:

After about a week of running KDE,  I noticed that my system performance degraded badly over time.  So,  I switched back to GNOME...  However, now I am running the KDE plasma-desktop in gnome and still have the benefits of KDE Device Notifier and can use other KDE widgets that I like...  Best of both worlds and CD automount works again :)

More info about running plasma desktop in gnome may be found here : [http://ubuntuforums.org/showthread.php?t=1291048](http://ubuntuforums.org/showthread.php?t=1291048)

---

