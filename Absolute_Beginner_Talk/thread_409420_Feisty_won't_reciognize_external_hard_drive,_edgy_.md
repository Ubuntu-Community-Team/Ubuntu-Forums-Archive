---
title: "Feisty won't reciognize external hard drive, edgy and dapper did?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by petgraveyard on 2007-04-14
Hello,
I own a Seagate 400GB external hard drive, that connects with USB to my PC.  It's reciognized in both Ubuntu and Windows, well, that is, at least with Ubuntu 6.10.  I just ran the upgrade (not a clean install) to 7.04 beta, and I turned on my hard drive...and it didn't mount!  It won't mount after everything I've tried.  Does anyone know what I can do to get it to mount?

---

### Post by tgm4883 on 2007-04-14
Is your usb controller recognized?

---

### Post by petgraveyard on 2007-04-14
Definitely.  I'm running my keyboard, printer, mouse, and interactive mousepad off of the USB controller.  It's working well.

---

### Post by petgraveyard on 2007-04-14
Anyone know what the deal might be?  I know I sound impatient, but this is angering me.

---

### Post by b1k3r4ck on 2007-04-16
I have the same problem. I installed Feisty beta on my main machine in a dual boot setup after running the alpha pretty smoothly on my second machine. 

Both drives were initially recognized after installing and they are still recognized when I boot into the beta as a live cd. I notice the 200GB drive was missing and now both my 200GB and my 400GB aren't found when I login to the system. 

fdisk -l shows them though. 

fdisk -l

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801    7  HPFS/NTFS

Disk /dev/sde: 200.0 GB, 200049648128 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       24321   195358401    7  HPFS/NTFS

---

### Post by Bert Mariën on 2007-04-16
Go, see and read this threat

[http://ubuntuforums.org/showthread.php?t=408843](http://ubuntuforums.org/showthread.php?t=408843)

You should find something useful.

(I am a little tired of writing it down over and over again.

---

### Post by b1k3r4ck on 2007-04-17
I actually tracked my issue down shortly after I posted. It didn't make any sense to me that the drives were found on the live CD but not in my install. Figured it had to be an update I made so I looked at my fstab and found the problem to be Automatix. The ntfs mounting was going wacky so I uninstalled that feature and it's back to normal for me. Thanks for the response!

---

### Post by Omegatron on 2007-04-21
I have the same problem.  I have two USB Seagate drives connected and both used to be recognized.  After upgrading to Feisty today (not beta), one of them is not recognized but the other is.  I moved them to other USB ports and they behave the same way.

---

### Post by EnigMattic on 2007-04-21
I have a 320GB Seagate external hdd that behaves exactly the same way as the first poster's when running Feisty. I have gone back to using Edgy.

Could all this have something to do with the drives being FAT32? I'm really no expert.

Any help appreciated.

---

### Post by mikeunveil on 2007-04-21
Same here, exactly the same problem. Seagate external drive 320GB, model ST3320820U2-RK.

Hotplugging worked fine for this drive in Edgy but DOES NOT work in Feisty.

My pendrive still mounts fine by hotplugging.

Interestingly, my external Seagate 320GB is listed when I do fstab -l:

/dev/sda1   *           1       38913   312568641    c  W95 FAT32 (LBA)


This problem is really annoying. PLEASE HELP!

---

### Post by EnigMattic on 2007-04-21
hi mikeunveil --
My model number is, on inspection EXACTLY the same as yours... hmmm...

---

### Post by Bert Mariën on 2007-04-21
Did you read this threat (as metioned on page one):

[http://ubuntuforums.org/showthread.php?t=408843](http://ubuntuforums.org/showthread.php?t=408843)

---

### Post by mikeunveil on 2007-04-23
The question for me really is hotplugging more than just mounting. I use this external drive between 3 different computers (actually running different OS, 2 running Mac OS 10.4.9 and this one running Feisty) and the fact that Edgy was able to automatically mount this drive whenever I plugged it was great.

I start to suspect that there must be some issue with the USB drivers supplied with Feisty or something of the kind. I am starting to get desperate.

---

### Post by Omegatron on 2007-04-23
This apparently has something to do with Feisty changing hard drive names from hda to sda?  See [this thread]("http://ubuntuforums.org/showthread.php?t=405630").  I thought sda was only for external drives.  When I look in my system tools or partition editor or whatever it shows *both* for the same partition, which makes no sense.  I wish someone would post a clear description of the problem and solution.  Shouldn't fstab have been updated to the new style when Feisty was upgraded?

---

### Post by Hurons on 2007-04-23
just returned from vacation...ran my updates from Feisty Beta.......Feisty no longer finds my external HD's  or Sansa 4GB MP3 player. I have one Fat32 and 1 NTFS. All worked find before I left. I cannot believe this issue, since external drives and MP3 players are the backbone of most computer users. Ubuntu will take a huge step back if you cant plug and play drives.

Im really disappointed. Here I am with pictures up the ying yang and no computer to dump them to!

---

### Post by Omegatron on 2007-04-23
> **Hurons said:**
> I cannot believe this issue, since external drives and MP3 players are the backbone of most computer users. Ubuntu will take a huge step back if you cant plug and play drives.

Yeah.  Auto-configuration of stuff like this is supposed to be the kind of thing that Ubuntu is good at.  Why would this configuration ever need to be touched by hand?

---

### Post by Bert Mariën on 2007-04-23
The reason the disks change names like from hda to sda is caused bt the new 'libata' driver which now is used for (supports) not only SATA drives but also most PATA drives (so I'm told).
And again, if your computer can't find your drives, edit /etc/fstab and use UUID for your drives.

---

### Post by Omegatron on 2007-04-23
> **Bert Mariën said:**
> The reason the disks change names like from hda to sda is caused bt the new 'libata' driver which now is used for (supports) not only SATA drives but also most PATA drives (so I'm told).
Yeah, but didn't they realize this was going to screw up people upgrading?  

> And again, if your computer can't find your drives, edit /etc/fstab and use UUID for your drives.

Yeah, but isn't UUID unique for a specific partition, though?  How does that help with plugging in arbitrary USB drives where you don't know the UUID?  Am I supposed to add it manually each time?  This is supposed to be automatic; it was in Edgy.

---

### Post by Bert Mariën on 2007-04-23
> **Omegatron said:**
> Yeah, but didn't they realize this was going to screw up people upgrading?  


True. There should have been some kind of warning for the Ubuntu users. Probably they thought that we are smart enough to figure it out ourselves. :lolflag:

---

### Post by Bert Mariën on 2007-04-23
> **Bert Mariën said:**
> 
And again, if your computer can't find your drives, edit /etc/fstab and use UUID for your drives.

This was really meant for Hurons.

---

### Post by Hurons on 2007-04-23
> **Bert Mariën said:**
> This was really meant for Hurons.


Thanks..so How do I find the uuid? and would they remail static even the the drives are removable?

---

### Post by Bert Mariën on 2007-04-23
> **Hurons said:**
> Thanks..so How do I find the uuid? and would they remail static even the the drives are removable?

see /dev/.udev/db for UUID

---

### Post by Hurons on 2007-04-23
> **Bert Mariën said:**
> see /dev/.udev/db for UUID


That folder is a mess. I dont no where to start! here is an example of what I see:


/dev/.udev/db/%2fclass%2finput%2finput2%2fts1
/dev/.udev/db/%2fclass%2finput%2finput2%2fmouse1
/dev/.udev/db/%2fclass%2finput%2finput2%2fevent2
/dev/.udev/db/%2fclass%2finput%2finput1%2fevent1
/dev/.udev/db/%2fclass%2finput%2finput0%2fts0
/dev/.udev/db/%2fclass%2finput%2finput0%2fmouse0
/dev/.udev/db/%2fclass%2finput%2finput0%2fevent0

 All I want to do is plug in an external HD and a MP3 player and have it reconized. Is that possible like in 6.10? Or should I reinstall? Everytime I buy a new device am I going to have to configure it? Or if a friend brings over a device am I going to have to configure it?

---

### Post by petgraveyard on 2007-04-23
I'm back, and I was able to get mine mounted by simply adding:

/dev/sdb1   /media/external   vfat   iocharset=utf8,umask=000   0   0

to /etc/fstab after creating /media/external.  However, I don't know how to get it to appear as a drive, on my desktop and in the places menu.  It's more of an aesthetic issue, but does anyone know how to help me?

---

### Post by Bert Mariën on 2007-04-23
> **Hurons said:**
> That folder is a mess. I dont no where to start! here is an example of what I see:


/dev/.udev/db/%2fclass%2finput%2finput2%2fts1
/dev/.udev/db/%2fclass%2finput%2finput2%2fmouse1
/dev/.udev/db/%2fclass%2finput%2finput2%2fevent2
/dev/.udev/db/%2fclass%2finput%2finput1%2fevent1
/dev/.udev/db/%2fclass%2finput%2finput0%2fts0
/dev/.udev/db/%2fclass%2finput%2finput0%2fmouse0
/dev/.udev/db/%2fclass%2finput%2finput0%2fevent0

 All I want to do is plug in an external HD and a MP3 player and have it reconized. Is that possible like in 6.10? Or should I reinstall? Everytime I buy a new device am I going to have to configure it? Or if a friend brings over a device am I going to have to configure it?

You have to look for files that like like this

%2fblock%2fhda
%2fblock%2fhda%2fhda1
%2fblock%2fhda%2fhda2
%2fblock%2fsda
%2fblock%2fsda%2fsda1

etc

---

### Post by Omegatron on 2007-04-23
> **Bert Mariën said:**
> You have to look for files that like like this

%2fblock%2fhda
%2fblock%2fhda%2fhda1
%2fblock%2fhda%2fhda2
%2fblock%2fsda
%2fblock%2fsda%2fsda1

etc

Why?  There's no way to see these more directly?

---

### Post by roony1974 on 2007-05-10
I am a nevbie and are having trouble with an external usb disk seagate 320Gb, feisty cant find it at all.

My external usb Maxtor 300Gb disk works perfect, why not the Seagate? 

I have tried changing usb ports and only connecting  the Seagate.

---

### Post by Omegatron on 2007-05-12
> **roony1974 said:**
> I am a nevbie and are having trouble with an external usb disk seagate 320Gb, feisty cant find it at all.

My external usb Maxtor 300Gb disk works perfect, why not the Seagate? 

I have tried changing usb ports and only connecting  the Seagate.

I am having similar problems.  My Seagate external drive completely filled with a FAT32 partition works fine in Windows, but in Linux it gives all kinds of error messages, says the drive is 2 TB, etc.  I thought the drive was dead until I connected it in Windows, and everything worked fine.  I ran Windows disk checks on it and they said everything was fine.  I don't get it.

---

### Post by ry4n on 2007-05-12
:( I am having the same problem as most of you, i have a serial ATA external hard drive that always just pop up on my desktop and was ready to be read. I was never able to write on it through  Ubuntu but was always able to read it. Now i am not even able to do that. Feisty no longer is able to mount it, and i don't know what to do. 

I have tried uninstalling automatix (because i read that can cause the problem )that fixed nothing. I have tried going though ntfs-3g but that has fixed nothing. 

i don't know what to do please help me!

---

### Post by Omegatron on 2007-05-12
I installed Feisty from the CD last night to set up Ubuntu Studio, and tried the external Seagate drive in the fresh install.  Still doesn't work.  Says bizarre things like 

> May 12 22:17:02 Inspiron kernel: [ 8604.576000] SCSI device sdb: 4139797498 512-byte hdwr sectors (2119576 MB)

2 terabytes?  It repeatedly says:

> May 12 22:24:51 Inspiron kernel: [ 9073.589000] usb 4-1: reset high speed USB device using ehci_hcd and address 5

And things like this:

> May 12 22:23:49 Inspiron kernel: [ 9012.118000] sd 2:0:0:1: SCSI error: return code = 0x00050000
May 12 22:23:49 Inspiron kernel: [ 9012.118000] end_request: I/O error, dev sdc, sector 312544447

I would think that the drive has hardware problems, but it worked fine until I upgraded to Feisty, and continues to work fine in Windows XP.  I ran XP's error checker on it with no problems.  Is there a way to check a disk for problems in Linux?  I tried a little bit with smartmontools but couldn't get it to see the drive and gave up.

---

### Post by Omegatron on 2007-05-12
And after I pull out the USB cable, it goes crazy.

A disk called "Cypress Semi" appears in the *Computer* window, and says "Unable to mount media" if I try to open it, and the log messages just keep repeating the same things:

> 
May 12 22:28:35 Inspiron kernel: [ 9297.835000] sde : sense not available. 
May 12 22:28:35 Inspiron kernel: [ 9297.835000] sde: Write Protect is off
May 12 22:28:35 Inspiron kernel: [ 9297.837000] sde : READ CAPACITY failed.
May 12 22:28:35 Inspiron kernel: [ 9297.837000] sde : status=0, message=00, host=1, driver=00 
May 12 22:28:35 Inspiron kernel: [ 9297.837000] sde : sense not available. 
May 12 22:28:35 Inspiron kernel: [ 9297.838000] sde: Write Protect is off
May 12 22:28:36 Inspiron kernel: [ 9298.494000] sdg : READ CAPACITY failed.
May 12 22:28:36 Inspiron kernel: [ 9298.494000] sdg : status=0, message=00, host=1, driver=00 
May 12 22:28:36 Inspiron kernel: [ 9298.494000] sdg : sense not available. 
May 12 22:28:36 Inspiron kernel: [ 9298.494000] sdg: Write Protect is off
May 12 22:28:36 Inspiron kernel: [ 9298.496000] sdg : READ CAPACITY failed.
May 12 22:28:36 Inspiron kernel: [ 9298.496000] sdg : status=0, message=00, host=1, driver=00 
May 12 22:28:36 Inspiron kernel: [ 9298.496000] sdg : sense not available. 
May 12 22:28:36 Inspiron kernel: [ 9298.497000] sdg: Write Protect is off
May 12 22:28:36 Inspiron kernel: [ 9298.722000] sdh : READ CAPACITY failed.
May 12 22:28:36 Inspiron kernel: [ 9298.722000] sdh : status=0, message=00, host=1, driver=00 
May 12 22:28:36 Inspiron kernel: [ 9298.722000] sdh : sense not available. 
May 12 22:28:36 Inspiron kernel: [ 9298.722000] sdh: Write Protect is off
May 12 22:28:36 Inspiron kernel: [ 9298.722000] sdh : READ CAPACITY failed.
May 12 22:28:36 Inspiron kernel: [ 9298.722000] sdh : status=0, message=00, host=1, driver=00 
May 12 22:28:36 Inspiron kernel: [ 9298.723000] sdh : sense not available. 
May 12 22:28:36 Inspiron kernel: [ 9298.723000] sdh: Write Protect is off
May 12 22:28:36 Inspiron kernel: [ 9298.963000] sdi : READ CAPACITY failed.
May 12 22:28:36 Inspiron kernel: [ 9298.963000] sdi : status=0, message=00, host=1, driver=00 
May 12 22:28:36 Inspiron kernel: [ 9298.963000] sdi : sense not available. 
May 12 22:28:36 Inspiron kernel: [ 9298.963000] sdi: Write Protect is off
May 12 22:28:36 Inspiron kernel: [ 9298.966000] sdi : READ CAPACITY failed.
May 12 22:28:36 Inspiron kernel: [ 9298.966000] sdi : status=0, message=00, host=1, driver=00 
May 12 22:28:36 Inspiron kernel: [ 9298.966000] sdi : sense not available. 
May 12 22:28:36 Inspiron kernel: [ 9298.967000] sdi: Write Protect is off
May 12 22:28:37 Inspiron kernel: [ 9299.833000] sdf : READ CAPACITY failed.
May 12 22:28:37 Inspiron kernel: [ 9299.833000] sdf : status=0, message=00, host=1, driver=00 
May 12 22:28:37 Inspiron kernel: [ 9299.833000] sdf : sense not available. 
May 12 22:28:37 Inspiron kernel: [ 9299.833000] sdf: Write Protect is off
May 12 22:28:37 Inspiron kernel: [ 9299.834000] sdf : READ CAPACITY failed.
May 12 22:28:37 Inspiron kernel: [ 9299.834000] sdf : status=0, message=00, host=1, driver=00 
May 12 22:28:37 Inspiron kernel: [ 9299.834000] sdf : sense not available. 
May 12 22:28:37 Inspiron kernel: [ 9299.834000] sdf: Write Protect is off
May 12 22:28:37 Inspiron kernel: [ 9299.840000] sde : READ CAPACITY failed.
May 12 22:28:37 Inspiron kernel: [ 9299.840000] sde : status=0, message=00, host=1, driver=00 
May 12 22:28:37 Inspiron kernel: [ 9299.840000] sde : sense not available. 
May 12 22:28:37 Inspiron kernel: [ 9299.840000] sde: Write Protect is off
May 12 22:28:37 Inspiron kernel: [ 9299.841000] sde : READ CAPACITY failed.
May 12 22:28:37 Inspiron kernel: [ 9299.841000] sde : status=0, message=00, host=1, driver=00 
May 12 22:28:37 Inspiron kernel: [ 9299.841000] sde : sense not available. 
May 12 22:28:37 Inspiron kernel: [ 9299.841000] sde: Write Protect is off
May 12 22:28:38 Inspiron kernel: [ 9300.499000] sdg : READ CAPACITY failed.
May 12 22:28:38 Inspiron kernel: [ 9300.499000] sdg : status=0, message=00, host=1, driver=00 
May 12 22:28:38 Inspiron kernel: [ 9300.499000] sdg : sense not available. 
May 12 22:28:38 Inspiron kernel: [ 9300.500000] sdg: Write Protect is off
May 12 22:28:38 Inspiron kernel: [ 9300.501000] sdg : READ CAPACITY failed.
May 12 22:28:38 Inspiron kernel: [ 9300.501000] sdg : status=0, message=00, host=1, driver=00 
May 12 22:28:38 Inspiron kernel: [ 9300.501000] sdg : sense not available. 
May 12 22:28:38 Inspiron kernel: [ 9300.502000] sdg: Write Protect is off
May 12 22:28:38 Inspiron kernel: [ 9300.724000] sdh : READ CAPACITY failed.
May 12 22:28:38 Inspiron kernel: [ 9300.724000] sdh : status=0, message=00, host=1, driver=00 
May 12 22:28:38 Inspiron kernel: [ 9300.724000] sdh : sense not available. 
May 12 22:28:38 Inspiron kernel: [ 9300.725000] sdh: Write Protect is off
May 12 22:28:38 Inspiron kernel: [ 9300.727000] sdh : READ CAPACITY failed.
May 12 22:28:38 Inspiron kernel: [ 9300.727000] sdh : status=0, message=00, host=1, driver=00 
May 12 22:28:38 Inspiron kernel: [ 9300.727000] sdh : sense not available. 
May 12 22:28:38 Inspiron kernel: [ 9300.728000] sdh: Write Protect is off
May 12 22:28:38 Inspiron kernel: [ 9300.979000] sdi : READ CAPACITY failed.
May 12 22:28:38 Inspiron kernel: [ 9300.979000] sdi : status=0, message=00, host=1, driver=00 
May 12 22:28:38 Inspiron kernel: [ 9300.979000] sdi : sense not available. 
May 12 22:28:38 Inspiron kernel: [ 9300.979000] sdi: Write Protect is off
May 12 22:28:38 Inspiron kernel: [ 9300.990000] sdi : READ CAPACITY failed.
May 12 22:28:38 Inspiron kernel: [ 9300.990000] sdi : status=0, message=00, host=1, driver=00 
May 12 22:28:38 Inspiron kernel: [ 9300.990000] sdi : sense not available. 
May 12 22:28:38 Inspiron kernel: [ 9300.992000] sdi: Write Protect is off
May 12 22:28:39 Inspiron kernel: [ 9301.846000] sdf : READ CAPACITY failed.
May 12 22:28:39 Inspiron kernel: [ 9301.846000] sdf : status=0, message=00, host=1, driver=00 
May 12 22:28:39 Inspiron kernel: [ 9301.846000] sdf : sense not available. 
May 12 22:28:39 Inspiron kernel: [ 9301.846000] sdf: Write Protect is off
May 12 22:28:39 Inspiron kernel: [ 9301.847000] sde : READ CAPACITY failed.
May 12 22:28:39 Inspiron kernel: [ 9301.847000] sde : status=0, message=00, host=1, driver=00 
May 12 22:28:39 Inspiron kernel: [ 9301.847000] sde : sense not available. 
May 12 22:28:39 Inspiron kernel: [ 9301.847000] sde: Write Protect is off
May 12 22:28:39 Inspiron kernel: [ 9301.849000] sdf : READ CAPACITY failed.
May 12 22:28:39 Inspiron kernel: [ 9301.849000] sdf : status=0, message=00, host=1, driver=00 
May 12 22:28:39 Inspiron kernel: [ 9301.849000] sdf : sense not available. 
May 12 22:28:39 Inspiron kernel: [ 9301.849000] sdf: Write Protect is off
May 12 22:28:39 Inspiron kernel: [ 9301.850000] sde : READ CAPACITY failed.
May 12 22:28:39 Inspiron kernel: [ 9301.850000] sde : status=0, message=00, host=1, driver=00 

This is *without* the USB drive plugged in, on effectively a fresh install of Feisty.

---

### Post by DUDE_2000 on 2007-05-12
Huh, I've got a 120 gig wd external hhd, and that works perfectly in ubuntu ( v 7.04 feisty )

---

