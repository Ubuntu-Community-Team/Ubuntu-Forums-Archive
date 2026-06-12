---
title: "Dual Boot Ubuntu Err 21 on PC with XPPro on RAID0 Drive and Ubuntu on eSATA drive"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-06
Last night I tried to install Ubuntu 7.04 onto my WinXP Pro PC and received Grub Error 21 

and when I reversed the boot order in the BIOS I read a message saying Error Loading 

Operating System.

My hardrives are configured as Such:

Drive 0 and Drive 1 are SATA RAID 0 74GB WD Raptors
Drive 2 is a SATA Non-RAID 74 GB Raptor (The drive I installed Ubunto onto)
Drive 3 is a SATA 250 GB Samsung Drive

When, I installed Ubuntu from the Live CD, I disconnected Drive 3 to avoid any confusion.
I was trying to set up a dual boot system with Windows as default and I could press a 

button during boot-up to run Ubunto.  I followed the following instructions from the Ubuntu 

website guide for dual boot: 

[I]"Case 1: You haven't installed Ubuntu yet
Do a fresh install of Ubuntu with the windows hard drive still plugged in. Ubuntu will 

automatically detect the other hard drive, and Grub will automatically list it as a choice 

at startup. You can then also see the other hard drive and access it while in Ubuntu by 

mounting it."[/I]

From what I have read all around the Web today is that my MBR got screwed up and can only 

be recovered by acessing the Windows Recovery Console.  I don't have a Windows disk.  I 

have one of those install disks that you get when you buy a new PC and some other progs 

besides Windows are on it.  Do ya think i could install the recovery console using that 

disk?  Is there some command line utility that i could do to fix my problem with out 

screwing up the RAID 0 configuration?  Another wierd thing is that I can no longer mount 

the Windows RAID 0 volume in from Ubuntu Live CD even though it still recognizes the size 

as 2x74GB

Any help will be appreciated.

Thanks in advance,

VC

---

### Post by phr0ze on 2007-06-06
I have a feeling its something with Grub not liking the RAID controller. Perhaps you can get grub setup on Drive 2, then have the bios boot to drive 2. Then finally add windows back to the grub menu for drive 0/1. 

Your system will be able to start grub on drive 2, and when you choose windows you get the performance of the raid.

I'm not a grub expert. Maybe someone else can fill the holes.

---

### Post by gn2 on 2007-06-06
There's plenty helpful info here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Your MBR can be repaired with a SuperGrub Disc, there's info about that on Herman's excellent site.

---

### Post by videocheez on 2007-06-06
> **phr0ze said:**
> I have a feeling its something with Grub not liking the RAID controller. Perhaps you can get grub setup on Drive 2, then have the bios boot to drive 2. Then finally add windows back to the grub menu for drive 0/1. 

Your system will be able to start grub on drive 2, and when you choose windows you get the performance of the raid.

I'm not a grub expert. Maybe someone else can fill the holes.

I was also concerned about that install getting sqrewy because of the RAID controller.  My fear is that Ubuntu wrote files to only one of the RAID drives and now they are permanently out of sync.  Looks like I'm gonna miss my gaming night.

---

### Post by videocheez on 2007-06-07
> **phr0ze said:**
> I have a feeling its something with Grub not liking the RAID controller. Perhaps you can get grub setup on Drive 2, then have the bios boot to drive 2. Then finally add windows back to the grub menu for drive 0/1. 

Your system will be able to start grub on drive 2, and when you choose windows you get the performance of the raid.

I'm not a grub expert. Maybe someone else can fill the holes.

I took your advice and got Ubunto installed on drive 2 by disconnecting all drives and re-instaling form the live CD.  Cool it works.
Next I disconnected drive 2 and reconnected drive 0/1 and recovered Windows and got it back up and running.  
Now I need to figure out how to dual boot the system.  Any suggestions will be appreciated.

Thanks in advance ,

VC

---

### Post by confused57 on 2007-06-07
> **videocheez said:**
> I took your advice and got Ubunto installed on drive 2 by disconnecting all drives and re-instaling form the live CD.  Cool it works.
Next I disconnected drive 2 and reconnected drive 0/1 and recovered Windows and got it back up and running.  
Now I need to figure out how to dual boot the system.  Any suggestions will be appreciated.

Thanks in advance ,

VC

When you set bios to boot first to your Ubuntu drive, set your Window's drive(Raid0) to boot second...then you should be able to add an entry to your /boot/grub/menu.lst to boot your Windows, similar to the one in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by videocheez on 2007-06-09
> **confused57 said:**
> When you set bios to boot first to your Ubuntu drive, set your Window's drive(Raid0) to boot second...then you should be able to add an entry to your /boot/grub/menu.lst to boot your Windows, similar to the one in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Thanks for the links.  By mistake, I was able to get a dual boot set up without editing the menu.lst file but my method is goofy and I'm not totally satisfied.  

For reference my hardrive set up is listed below:

Drive 0 and Drive 1 are SATA RAID 0 74GB WD Raptors
Drive 2 is an eSATA Non-RAID 74 GB Raptor (The drive I installed Ubunto onto)
Drive 3 is a SATA 250 GB Samsung Drive

I disconnected drives 0/1 and drive 3 and installed Ubuntu to Drive 2  and made drive 2 the primary.  When this drive is powered on, I start my computer and automatically boot to Ubuntu.  If I power drive 2 off, the secondary Windows drive 0/1 boots.  I think this is a dual boot install but  c'mon, i want to see grub give me the option of which OS to choose.  I'm gonna wear out my hardrive switch.
From what I've read, if I'm understanding correctly, I can edit my menu.lst file so that when Ubuntu loads, I will seen an option to boot to windows or Ubuntu.  I would like to do this if possible.
My concern is that the examples that I've read did not have the situation where windows was on a RAID0 drive so I don't know how to write the correct code.  Can I edit the menu.lst file to have the choice to boot to Windows on a RAID0 array?  
FYI, when I'm in Ubuntu, I cannot mount the windows RAID0 drive.  Details from the failure to mount read:
*mount: wrong fs type, bad option bad superblock on /dev/ sda1, missing codepage or some other error.  In some cases useful info is found in syslog try  dmesg| tail or so *
Maybe windows will not let a foreign OS mount the root drive?.   Does this even matter?

I read somewhere that I will need to to install dmraid, which I did already to deal with a fakeRAID array but the person who responded to my questions believed that I want to install Ubuntu to the RAID drives.
The links that you suggested appear to have instructions for doing what I want to do but I want to know if you suggest a back up plan in case I screw up the menu.lst file and mess up ubunto completely.

Thanks in advance,

VC

---

### Post by videocheez on 2007-06-10
Thanks for the links confused57,  I got  the dual boot scenario that I wanted and learned a whole lot getting it all set up.  I think I will summarize everything so that if I forget what I did in the future or I have to do it again, I'll know where to look.

My hardrives are configured as Such:

Drive 0 and Drive 1 are SATA RAID 0 74GB WD Raptors (Windows drive)
Drive 2 is an eSATA Non-RAID 74 GB Raptor (The drive I installed Ubunto onto)
Drive 3 is a SATA 250 GB Samsung Drive (storage drive)

I purchased a separate hardrive and a Vantec NST-360SU-BK Nexstar3 3.5" SATA external hardrive kit for $35 to which also contains a PCI SATA adpater so that I could have an external SATA drive.

[LIST=1]
[*]I disconnected the Windows drives
[*]installed ubuntu via the live CD onto drive 2
[*]changed BIOS to make drive 2 primary
[*]reconnected the windows drives
[*]rebooted and went straight to ubuntu
[*]modified the menu.lst file
[/LIST]

The following code was used to modify the menu.lst file for dual boot:
```

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

```

I had to put in admin password to edit the menu.lst file.

```

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Next I also edited the menu.lst file by unhiding the hiddenmenu command by deleting the # in front of it and changing the default time out to 10s instead of 3s for the time that the boot option window appears.

Please note that I was able to have dual boot without modifying the menu.lst file simply by turning off the eSATA drive prior to booting and the computer automatically loaded Windows.  This approach was cool because Windows was also totally separate from Linux but it's kinda goofy switching off the drive each time I want to switch OS's and may not be easy for someone who does not have ubuntu running on an external drive

Useful links where I got the code and many dual boot examples is located below.
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Thanks again and now the fun begins.

VC

---

### Post by confused57 on 2007-06-10
Thanks for the update...I've seen other users with similar hard drive configurations successfully dual boot this way...hoped it would work for you.  Enjoy your dual boot...using & learning Linux is challenging & fun for me, I'm sure it will be for you, also.

---

