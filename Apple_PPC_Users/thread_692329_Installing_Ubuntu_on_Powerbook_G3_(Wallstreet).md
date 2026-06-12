---
title: "Installing Ubuntu on Powerbook G3 (Wallstreet)"
date: 2008-02-09
forum: Apple PPC Users
---

### Post by warder on 2008-02-09
(Sorry if this is considering double posting, but the only reply I received in my previous thread was a url over here to the Apple PPC section...so here I am)

Hi everyone, thanks in advance for any help you provide...

I'm trying to get Ubuntu Gutsy installed on my PowerBook G3:

292MHz Processor with 1MB cache (I don't know how to verify this, but that is what I was told from my friend who I bought it from)
192 MB RAM
30GB HD, 400mb alloted to the os9 install, the rest unallocated. 
DVD Drive 
No onboard usb or firewire

I've got it booting to the alternate install cd, but it keeps dropping me to BusyBox. The last set of lines looks like this:

```

Begin: Waiting for roo file system... ... 
[ 101.585101] SCSI subsystem initialized
[ numbers] mesh: configured for synchronous 5 MB/s
[ numbers] mesh: performing initial bus reset...
[ numbers] scsi0 : MESH
[ numbers] eth0: BMAC at (my hardware address)

(it stops at the eth0 line for about 5 minutes)

Done. 

	Check root= bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls dev
ALERT! does not exist. Dropping to a shell!

(busybox indentifier, etc..)

(initramfs)


```

So I've been searching around for awhile, tried "modprobe ide_core" and "modprobe ide_disk" with exit after that. It returns the same check root error. 

Just last night I've found that I should try "root=/dev/hda#" in my bootx additional commands input. I'm in the process of trying that, waiting for it to fail and running the modprobe ide_core command. 

Thanks again! Let me know if you need any other info.

-warder

---

### Post by warder on 2008-02-09
As i said before I was going to cycle through all the hda's in the root=/dev/hda# bootx kernel arguments and try running mod_probe ide_core after each failed.. I went from hda (no number) to hda10 with no success. Here's an example: 



```


Done.
	Check root= bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda2 does not exist. Dropping to a shell!

(busybox version)

(initramfs) modeprobe ide_core

[  numbers] Uniform Multi-Platform E-IDE driver revision: 7.00alpha2
[  numbers] ide: Assuming 33MHz system bus seept for PIO Modes; override with idebus=xx
[  numbers] ide0: Found Apple Heathrow ATA Controller, bus ID 0, irq 26
[  numbers] hda: Enabling MultiKeyword DMA 2
[  numbers] ide0 at 0xcd04a000-0xcd04a007,0xcd04a160 irq 26
[  numbers] ide1: Found Apple Heathrow ATA controller, bus ID 1 (mediabay), irq 34
[  numbers] ide2: Found Apple Heathrow ATA controller, bus ID 4 (mediabay), irq 67
(initramfs) [  numbers] hda: max request size: 512KiB
[  numbers] hda: 58711968 sectors (30060 MB) w/8192KiB Cache, CHS=16383/255/63, (U)DMA
[  numbers] hda: cache flushes supported
[  numbers]   hda: [mac] hda1 hda2 hda3 hda4 hda5 hda6 hda7 hda8 hda9 hda10

(blinking cursor here as the prompt came back 3 lines up)

```

I type in exit and get the following:

```

stdin: error 0
Begin: Running /scripts/local-premount ...
Bone.
Usage: modprobe (flags details are list out here..) 
mount: Cannot read /etc/fstab: No such file or directory
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed: no such file or directory
Done. 
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

(busybox version)
Enter help..

(initramfs)

```

-warder

---

### Post by warder on 2008-02-10
I downloaded Xubuntu 6.06 Dapper Drake and seems to be installing...it's been at Detecting hardware for a while though...so we'll see what happens. 

-warder

---

### Post by VCF on 2008-02-10
> **warder said:**
> I downloaded Xubuntu 6.06 Dapper Drake and seems to be installing...it's been at Detecting hardware for a while though...so we'll see what happens. 

-warder

Having similar problems with my iMac G3, unless somebody has a silver bullet for you that works right away, install Dapper Drake to ugrade to Feisty (7.04) and stay there.   Gutsy seems to be seriously broken on many G3's

---

### Post by warder on 2008-02-10
> **VCF said:**
> Having similar problems with my iMac G3, unless somebody has a silver bullet for you that works right away, install Dapper Drake to ugrade to Feisty (7.04) and stay there.   Gutsy seems to be seriously broken on many G3's

yeah, it seems like they're dropping support for Gutsy on PPC... 


On the Xubuntu install I can't get past the partitioner...it just keeps bringing me back to the partition manager. It's partitioning them as I've restarted it still detects the new partitions the way I set them up the first time. I just can't go on. (I tried going on the next step manually, but it just loads the partitioner)

I've found a few things relating to it, but they relate to SATA drives though.. I'll keep looking. Maybe gparted if I can get it to boot?

Good luck with your mac though!

-warder

---

