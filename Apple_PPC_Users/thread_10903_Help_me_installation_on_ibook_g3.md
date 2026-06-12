---
title: "Help me installation on ibook g3"
date: 2005-01-12
forum: Apple PPC Users
---

### Post by soundsgood on 2005-01-12
Hi everybody

I've decided to install a linux distro on my ibook dual usb g3.
There's a problem : i don't know how!

Can you help me?

My problems are:

A) I want reinstall Panther too. In which order i must do it? 1) Panther 2) Ubuntu or 1)Ubuntu 2) Panther? How many partitions and how large (hd 20gb)?

B) How can i configure a boot loader to chose which O.S: start every time?

Thanks very very much 4 who help me!

---

### Post by slux on 2005-01-12
I think the proper order is Panther first, then ubuntu although I haven't really got experience on how OS X behaves when there's another OS on the drive. On the other hand I know well how a certain one from Redmond behaves... At least I'm fairly confident ubuntu will behave well so I'd install it after Panther.

For partitioning, I'd suggest at least 5GB for Ubuntu although you can get along with a bit less (typing this on a machine with 3GB HD but it's pretty full). In any case, you can also use your OS X partitions from Ubuntu so you don't necessarily need much space for anything else except the apps.

You can just have one big root partition and a swap partition. /home can be nice to have on a separate partition as then you can easily do reinstalls but more than that isn't really essential but I do tend to have separate partitions for /usr, /tmp, /var if the disk I'm installing on has the space.

Getting OS X to boot after that should not be a big issue. If Ubuntu doesn't handle it itself, you can just add a "macosx = /dev/hdX" line to your /etc/yaboot.conf and run ybin. After that you can select which OS you want to boot into.

---

### Post by soundsgood on 2005-01-13
Thanks!!!! :p 

Another question:
is there a way to install java2 sdk 5.0 on ubuntu ppc? ](*,)

---

### Post by soundsgood on 2005-01-13
When i started Panther the first time after the installation of ubuntu the bootloader it's disappeared! Now i can only start Panther.
Why????? :sad:

---

### Post by slux on 2005-01-14
I've not heard of such a thing happening but you can probably boot with the ubuntu cd, drop into console, mount the root partition and rerun yaboot (ybin). After that panther hopefully won't replace it a second time. :P

---

### Post by chascon on 2005-01-14
The apple disk utility will only allow for free space to be place first (above), and OS X below that.

As for configuring the bootloader, penguenppc has a tutorial for that.

If the boot loader doesn't work, you can still boot linux by pressing option while booting.  It'll drop you into apple's graphical boot loader.  It take a few min.s to fully load, and then select the linux drive with your mouse, press continue.  voila linux starts to boot.

Once in you can try to run ybin.  You might need the pathway leading to ybin.  And this is done sudo.

---

### Post by soundsgood on 2005-01-15
> **chascon]The apple disk utility will only allow for free space to be place first (above), and OS X below that.[/QUOTE]

So the best way for not having problems with yaboot is create 2 partitions, the first one with free space and the second one where i install mac os x. said:**
> If the boot loader doesn't work, you can still boot linux by pressing option while booting. It'll drop you into apple's graphical boot loader. It take a few min.s to fully load, and then select the linux drive with your mouse, press continue. voila linux starts to boot.
it's ok!

---

### Post by chascon on 2005-01-15
I don't know if my install way the best way to not have bootloader problems.  All I know is that it is the user friendly way.  I rather do it this way than some debian-ppc manuals that tell you to install debian first and to make partitions with something like mac-fdisk.  Can we make dual boot installs more terse for newbies that still depend on propitary OSs (or that still are unsure about making the jump over)?  I'm not sure about any ubuntu-ppc dual boot install manuals as I haven't looked because I been doing dual boot installs for a few years now (I don't need to).

Actually the debian basic install is now very simple, almost as simple as ubuntu's.  But I can still customize very easily.  But some of the mauals out there are ugh!

Yes, install linux into the FreeSpace partition.  From there you quit the OS X disk utility, install OS X.  Then you install from the ubuntu-ppc CD and install ubuntu into the Free Space (choose manual-partition?  and find the Free Space partition [you can find the disk0S designation that corresponds to ubuntu's by looking at disk utility info button. Or you an tell them apart if you make the partitions different sizes]).  Once done that, bootloader will take care of itself (I don't think ubuntu even prompts you for it).

But for this install:
I take it apple's bootloader works for you.  Great!  It's good to know your mac hardware.  I'd still run sudo ybin from term once inside ubuntu-ppc to try to repair yaboot as there is no reason to reinstall for such a minor issue.  

There is no reason to make things terse and reboot from the ubuntu-ppc cd.

---

### Post by cow_racer on 2005-01-15
[QUOTE=soundsgood]Thanks!!!! :p 

Another question:
is there a way to install java2 sdk 5.0 on ubuntu ppc? ](*,)[/QUOTE]

Last time I checked there was no sdk 5.0 for PPC linux.  The latest one
is 1.4.2 from IBM.  And jdk 1.4.1 from blackdown.

---

### Post by cow_racer on 2005-01-15
[QUOTE=cow_racer]Last time I checked there was no sdk 5.0 for PPC linux.  The latest one
is 1.4.2 from IBM.  And jdk 1.4.1 from blackdown.[/QUOTE]


actually blackdown only has jdk 1.3.1

---

