---
title: "Old World Mac- New Life"
date: 2006-06-24
forum: Apple PPC Users
---

### Post by Uta on 2006-06-24
I have finally, after 2 days of trying, installed Eubuntu (5.10) on my Power Tower Pro, which is an old world mac with a G3 card,firewire card,usb card,D-Link ethernet card,IDE adapter. I simply could not get Dapper to install on my main scsi drives nor could I get Breezy to install on my scsi drives. Each had it's own issues with my system, so I finally put the IDE adapter/IDE HD in and installed to that with Breezy. The installation went smoothly.

I didn't realize I had installed Eubuntu till I saw the desktop, (I thought it was the regular desktop version). 
I would like to hear from other "Old World Mac" owners if they have had success installing Ubuntu to their main scsi drive, and if so what version of Ubuntu was installed? 
I do not have a stable system with eubuntu 5.10 running off my IDE drive, I get a lot of fatal system freezes. I believe this is caused by an error call to the IDE drive? My IDE drive is ID as (slave) although it is the default Mac OS boot drive. Could that be the issue and if so should I try reconfiguring the jumpers on the drive?
My last question is about the Eubuntu 5.10, should I upgrade to Dapper via the system updater, is that a stable way to upgrade or should I repartition the IDE HD again and do a clean install of Dapper? Thanks

---

### Post by irclemomo on 2006-06-24
Same problem here...
I have been looking at the documentation for hours, and I still cannot understand why the SCSI adapter of my Power Macintosh 7500 (w. 604e/200 CPU upgrade) is not recognized by Dapper.

Is there a fix for this? Is there anybody who has a modified kernel that enables SCSI devices? I am quite a newbie in the Linux world, and therefore any help would be greatly appreciated!

Pleease!

---

### Post by irclemomo on 2006-06-24
Maybe I could use a Debian kernel for the installation process, and then build my own one in Xubuntu and choose it in BootX? I'll try that...

---

### Post by Uta on 2006-06-24
Have you tried other versions of Ubuntu? Where does your install process fail? With Dapper on scsi it failed at the 'partition setup' and with Breezy it failed trying to install the kernel (my experience). I think it is possible, just need others who have been successful to share their process.

To answer my own post, I did use a jumper config on my IDE drive and it is now seen as master and the system seems a bit better (more stable). 
Still waiting to hear from scsi HD users who have a stable sucessful install?

---

### Post by nkbj on 2006-06-24
The reason the Dapper install CD does not recognize SCSI is that the MESH SCSI driver was not enabled in kernel 2.6.15-23. It has been corrected in 2.6.15-25, so it should work after an upgrade. Rumors has it, that a respin of the CD's is coming - just don't know when.

---

### Post by rexbinary on 2006-06-25
Does that mean they are going to start supporting OldWorld machines again? I was really disappointed when they dropped OldWorld support in 6.06. Linux for everyone, except OldWorld users. :-k 

Ubuntu 6.06 installed on my OldWorld machine, but as soon as I updated the kernel it wouldn't boot anymore. Xubuntu 6.06 would not install correctly at all, which is what I really wanted to run. Ubuntu 5.10 still runs fine though, I just don't want to be stuck at 5.10 forever.

---

### Post by irclemomo on 2006-06-25
[QUOTE=nkbj]The reason the Dapper install CD does not recognize SCSI is that the MESH SCSI driver was not enabled in kernel 2.6.15-23. It has been corrected in 2.6.15-25, so it should work after an upgrade. Rumors has it, that a respin of the CD's is coming - just don't know when.[/QUOTE]

As OldWorld Macintoshes need BootX, the Kernel must be loaded onto the hard drive, meaning it is not necessary to have an updated CD, but only the kernel, and eventually the ramdisk (although it might be possible to stick with the actual one, enabling mesh manually?)...
Is there a way to get those two updated files? This might be a stupid question, but I am a newbie, and I do not know where to get the files...

---

### Post by irclemomo on 2006-06-25
Should I try to install Breezy and then upgrade?

---

### Post by Uta on 2006-06-25
If you did install Breezy and then via the upgrade manager bumped up to Dapper, I would like to know your results. Was your install to the scsi drive, were you able to update to Dapper via the system's update manager? thanks.

---

### Post by dcer10 on 2006-07-20
Hi,

Dont know if it helps anyone but I have just spent about 20 hours getting my old world G3 PPC to work under ubuntu 6.06

I wrote a step by step guide which I have put up online at:

[http://www.dcerecords.dnsalias.com/support/](http://www.dcerecords.dnsalias.com/support/)

If it is of any help to anyone. It sounds like you guys have got this far already, but perhaps some other people will find this post useful.

It does not overcome the problem of updating the kernel.

Best Regards,

John

---

### Post by printmkr on 2006-07-20
stupid question here... what exactly defines an "Old World" Mac? G3 or less? A box Apple says does not "officially" support OS X?

---

### Post by avtolle on 2006-07-20
Partial answer, as I understand it. The designation "Old World" Mac refers to those with CPUs before a certain model of the G3. Thus, certain G3s are "Old World", and certain g3s are "New World". G4s and G5s are "New World"; other powerpc CPUs (prior to that G3 line of demrcation are "Old World". There is also a difference in the firmware, IIRC, the "New World" Macs being Open Firm Ware, w/ "Old world Macs" having Closed (?) Firm Ware. From my memory, to boot on "Old World" Macs under Linux requires an app w/the name of Boot X, which runs under the Mac OS. There is an alternative w/ the name of "quik". Hopefully, a more knowledgeable user can give a more complete explanation.

---

### Post by eby on 2006-07-20
OldWorld means Apple PPC based machines with 4MB ROM and OpenFirmware (but can't update firmware on these machines)+ PCI interface instead of NuBus and onboard serial, SCSI & ADB ports.

Early NuBus based PPC mac's couldn't run anything but MacOS because they lacked OpenFirmware.

NewWorld machines, have only 1MB ROM instead of trad 4MB, have updatable OpenFirmware. support for traditional ports replaced with USB, FW ports, oh and a PPC cpu [-(  eg. any coloured mac's

hope this helps.

---

### Post by eby on 2006-07-20
Oh, by the way, i tried to install 5.10 on my beige tower, scsi cd-rom, ide hdds:confused: 8-[ . I managed to boot, but got stuck at "VFS cannot mount root device".

got mad, and installed OS X .2 & X.3 server. 

i may run ubuntu 6.x on my beige if it supports scsi cd-roms, ide hdds and a simple inst procedure (can't go thru *dcer10*'s procedure. it is toooooo complicated for me ](*,) ).

---

