---
title: "Installed everything except yaboot, problem."
date: 2007-09-12
forum: Apple PPC Users
---

### Post by prestosd on 2007-09-12
Hey all, I have a 1Ghz 256MB RAM 40GB HD eMac G4 running OS X 10.4.10. :KS

I have an external enclosure with a 250GB HD (actually about 230GB to be exact). And I installed Ubuntu 7.04 for PPC on it. 

Problem: During the manual partition (which I have done many times successfully, but not on a PPC) I didn't make a NewWorld or yaboot or whatever partition. I just made root ext3 and swap. I got some error, but ignored it (wee! dumb move!) having never installed Linux on a mac before.

Now, openfirmware doesn't find the OS on the external drive. And I don't know how to boot it or install yaboot. All the guides/threads I've found are for people reinstalling it. I'm going from blank.

If the only option is to reinstall, please explain the need, purpose, and requirements of a yaboot partition. 

The HD is for a upcoming movie project (The Awakening [www.the-awakening.co.nr](www.the-awakening.co.nr)) and I have a large (208GB about) partition for the iMovie project. The 2 ones I explained above (the root is about 24GB and the swap 805MB).

I've reinstalled 2 or 3 times already, from other issues. This is now the only one (w00t). Thanks for your help in advance.

P.S. I read all the "similar threads" and 1 or 2 were kinda helpful. But didn't state how exactly to reinstall yaboot, or how exactly to make a yaboot partition.

---

### Post by stmiller on 2007-09-12
You can just hold down the alt/option key and select Linux from the external drive to boot to Linux, as a work around.

But to have yaboot work, it will have to overwrite the boot partition on your main internal hard drive. So this can be tricky to set up with an external Linux install, as you have to be sure to install yaboot onto the internal disk, and not your external disk.

Or just hold down alt to boot to Linux. :)

---

### Post by prestosd on 2007-09-12
Sorry, that's what I meant when I said: "openfirmware doesn't find the OS on the external drive." 

But yah, the option boot menu doesn't find it. The install didn't really finish, it went to about %94 when it ran into the yaboot issue.

I figured this was probably the issue/solution. How can I install grub on my internal?

Thanks for replying!

---

### Post by pxwpxw on 2007-09-13
> **prestosd said:**
> Sorry, that's what I meant when I said: "openfirmware doesn't find the OS on the external drive." 

But yah, the option boot menu doesn't find it. The install didn't really finish, it went to about %94 when it ran into the yaboot issue.

I figured this was probably the issue/solution. How can I install grub on my internal?

Thanks for replying!

( ppc g4 =yaboot.  pc intel = grub )

Hi,

The boot partition for normal yaboot installation must be type
  Apple_Bootstrap, 900KBytes minimum, format hfs (mac standard).
 (AKA NewWorld bootstrap or bootblock).
The yaboot installer installs files ofboot.b, yaboot, yaboot.conf.
All this is normally handled by the installer if all goes well, but usually goes wrong with externals and the current ubunutu release.

The external hard drive connection type affects booting, and the yaboot installer may need help.
 
 Is the exterernal drive firewire or usb?

The output from commands below using a terminal in macosx (10.4.10 here) will help decide how to go. With the external drive connected and runing, restart and do these commands in terminal, and post please: 
```

  nvram boot-device
  sudo bless --info --verbose
  diskutil list 
  sudo pdisk -l

```

You can also check your external drive details from the macosx System Profiler (about this mac).

---

### Post by prestosd on 2007-09-13
Right, sorry. I meant yaboot. I'm just used to saying grub.

Hmm, okay. Thanks for the info.

The external drive is USB.

Which terminal?

Here's the info on my bus and device from System Profiler:

> USB Bus:

  Host Controller Location:	Built In USB
  Host Controller Driver:	AppleUSBOHCI
  PCI Device ID:	0x0019
  PCI Revision ID:	0x0001
  PCI Vendor ID:	0x106b
  Bus Number:	0x19

Mass Storage Device:

  Capacity:	232.89 GB
  Removable Media:	Yes
  Detachable Drive:	Yes
  BSD Name:	disk2
  Version:	1.00
  Bus Power (mA):	500
  Speed:	Up to 12 Mb/sec
  Manufacturer:	Prolific Technology Inc.
  OS9 Drivers:	Yes
  Product ID:	0x2506
  Serial Number:	00
  S.M.A.R.T. status:	Not Supported
  Vendor ID:	0x067b
  Volumes:
OSX:
  Capacity:	208.09 GB
  Available:	207.99 GB
  Writable:	Yes
  File System:	Journaled HFS+
  BSD Name:	disk2s10
  Mount Point:	/Volumes/OSX

---

### Post by pxwpxw on 2007-09-13
> **prestosd said:**
> Right, sorry. I meant yaboot. I'm just used to saying grub.

Hmm, okay. Thanks for the info.

The external drive is USB.

Which terminal?

Here's the info on my bus and device from System Profiler:


System Profiler USB drive info - note these 3 lines:

Speed: Up to 12 Mb/sec
OS9 Drivers: Yes
OSX Volume: File System: Journaled HFS+

Do you have a higher speed usb or firewire alternative?

The terminal results for the commands in my post should show all the other partitions on both drives  and show where you might put an Apple_Bootstrap partition on the internal drive, as well a other boot info.

The terminal.app is in Macosx: Applications:Utilities - it can do copy and paste or save text to file.

---

### Post by stmiller on 2007-09-13
Ah- the drive is USB. That is why open firmware cannot see the drive. It does not support booting to a USB drive, only firewire. But you can make a hacked yaboot.conf to point to that USB drive. pxwpxw is the expert with booting issues. You are in good hands. :)

---

### Post by prestosd on 2007-09-13
> **pxwpxw said:**
> System Profiler USB drive info - note these 3 lines:

Speed: Up to 12 Mb/sec
OS9 Drivers: Yes
OSX Volume: File System: Journaled HFS+

Do you have a higher speed usb or firewire alternative?

The terminal results for the commands in my post should show all the other partitions on both drives  and show where you might put an Apple_Bootstrap partition on the internal drive, as well a other boot info.

The terminal.app is in Macosx: Applications:Utilities - it can do copy and paste or save text to file.

Nope, no alternatives. Well, actually....

Okay, I didn't know if you meant the Mac OS X terminal or the Ubuntu one. :)

> Ah- the drive is USB. That is why open firmware cannot see the drive. It does not support booting to a USB drive, only firewire. But you can make a hacked yaboot.conf to point to that USB drive. pxwpxw is the expert with booting issues. You are in good hands.

Dang...is it possible to hack yaboot into using it? If so, how?

Through all this, I'm willing to install on my internal drive. The above instructions helped a lot, but I need a bit more: where does the yaboot partition go? Does it have to be at the beginning or end of the drive/partition? What is the format, HFS or NewWorld? etc.

---

### Post by pxwpxw on 2007-09-13
**prestosd**

I need to see this info from macosx terminal, that will save a lot of questions, then can take it from there.
With the external drive connected and running, restart into macosx terminal and post.

```

  nvram boot-device
  sudo bless --info --verbose
  diskutil list 
  sudo pdisk -l

```

---

### Post by prestosd on 2007-09-22
From the mac terminal:

```
Prestons-eMac-G4:~ user$ nvram boot-device
boot-device     mac-io/ata-4@1f000/@0:9,\\:tbxi
```

```
Prestons-eMac-G4:~ user$ sudo bless --info --verbose

WARNING: Improper use of the sudo command could lead to data loss
or the deletion of important system files. Please double-check your
typing when using sudo. Type "man sudo" for more information.

To proceed, enter your password, or type Ctrl-C to abort.

Password:
OpenFirmware found at IODeviceTree:/openprom
OpenFirmware model is " OpenFirmware 3"
Current OF: mac-io/ata-4@1f000/@0:9,\\:tbxi
bsd name is /dev/disk0s9
looking at partition disk0s9, type Apple_HFS, name Untitled
Partition name is Untitled. Partition type is Apple_HFS
No external booter needed
mount: /
Mount point for / is /
Boot blocks read successfully
finderinfo[0]: 1210433 => Blessed System Folder is /System/Library/CoreServices
finderinfo[1]:      0 => No Blessed System File
finderinfo[2]:      0 => Open-folder linked list empty
finderinfo[3]: 1168798 => OS 9 blessed folder is /System Folder
finderinfo[4]:      0 => Unused field unset
finderinfo[5]: 1210433 => OS X blessed folder is /System/Library/CoreServices
64-bit VSDB volume id:  0xFBB4F8D64ACFCD99
```

```
Prestons-eMac-G4:~ user$ diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *37.3 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:         Apple_Driver43                    28.0 KB   disk0s2
   3:         Apple_Driver43                    28.0 KB   disk0s3
   4:       Apple_Driver_ATA                    28.0 KB   disk0s4
   5:       Apple_Driver_ATA                    28.0 KB   disk0s5
   6:         Apple_FWDriver                    256.0 KB  disk0s6
   7:     Apple_Driver_IOKit                    256.0 KB  disk0s7
   8:          Apple_Patches                    256.0 KB  disk0s8
   9:              Apple_HFS Macintosh HD       37.3 GB   disk0s9
/dev/disk2
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *232.9 GB disk2
   1:    Apple_partition_map                    31.5 KB   disk2s1
   2:         Apple_Driver43                    28.0 KB   disk2s2
   3:         Apple_Driver43                    28.0 KB   disk2s3
   4:       Apple_Driver_ATA                    28.0 KB   disk2s4
   5:       Apple_Driver_ATA                    28.0 KB   disk2s5
   6:         Apple_FWDriver                    256.0 KB  disk2s6
   7:     Apple_Driver_IOKit                    256.0 KB  disk2s7
   8:          Apple_Patches                    256.0 KB  disk2s8
   9:              Apple_HFS OS X               232.7 GB  disk2s10
```

```
Prestons-eMac-G4:~ user$ sudo pdisk -1
pdisk: invalid option -- 1
pdisk: bad usage - bad arguments

usage:  pdisk [-h|--help]
        pdisk [-i|--interactive]
        pdisk [-l|--list] [name] [...]
        pdisk [-r|--readonly] name [...]
        pdisk [-v|--version]
        pdisk name [...]
        pdisk name command

command:
        -blockSize           display the block size used by the map
        -createPartition     create a new partition
        -deletePartition     delete a partition
        -dump                dump the list of partitions
        -initialize          initialize the partition map
        -isDiskPartitioned   is the disk partitioned
        -partitionEntry      get the partition name, type, base, and size
        -splitPartition      split an existing partition in two pieces
```

Hope this helps! Sorry I posted so late, school started. ;)

---

### Post by pxwpxw on 2007-09-23
**prestosd**

2 main points:

1. Cant see any sign of linux partitions on disk2 240GB external, pdisk should show any free space.

2. 
```
 sudo pdisk -l 
```
Thats l for leather not figure 1.

It will show if there is any free space on the 40Gb internal drive to put boot files, otherwise for exterrnal usb hard drive boot, you can probably put them in your  
9:              Apple_HFS Macintosh HD       37.3 GB   disk0s9

But you need to have somethiong on the external to boot.
It might be simpler just to make 10Gb or so available for ubuntu install on the internal drive and use the external for storage. Depends what your needs are.

---

### Post by prestosd on 2007-09-25
> 2 main points:

1. Cant see any sign of linux partitions on disk2 240GB external, pdisk should show any free space.

Right, I don't have any linux partitions right now. I deleted them all. :) I can make some if you want.

> 2. 
Code:
 sudo pdisk -l
Thats l for leather not figure 1.

Ooh! Sorry! Here's the output:

```
Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name              length   base     ( size )
 1: Apple_partition_map Apple                 63 @ 1       
 2:      Apple_Driver43*Macintosh             56 @ 64      
 3:      Apple_Driver43*Macintosh             56 @ 120     
 4:    Apple_Driver_ATA*Macintosh             56 @ 176     
 5:    Apple_Driver_ATA*Macintosh             56 @ 232     
 6:      Apple_FWDriver Macintosh            512 @ 288     
 7:  Apple_Driver_IOKit Macintosh            512 @ 800     
 8:       Apple_Patches Patch Partition      512 @ 1312    
 9:           Apple_HFS Untitled        78163528 @ 1824     ( 37.3G)
10:          Apple_Free                        8 @ 78165352

Device block size=512, Number of Blocks=78165360 (37.3G)
DeviceType=0x0, DeviceId=0x0
Drivers-
1:  23 @ 64, type=0x1
2:  36 @ 120, type=0xffff
3:  21 @ 176, type=0x701
4:  34 @ 232, type=0xf8ff
```

> It will show if there is any free space on the 40Gb internal drive to put boot files, otherwise for exterrnal usb hard drive boot, you can probably put them in your 
9: Apple_HFS Macintosh HD 37.3 GB disk0s9

But you need to have somethiong on the external to boot.
It might be simpler just to make 10Gb or so available for ubuntu install on the internal drive and use the external for storage. Depends what your needs are.

Well, the thing is, I've only got 12GB free on my internal. :( I would like to put the boot files on the internal but the OS on the external.

---

### Post by pxwpxw on 2007-09-26
From what you say, these look to be the options:

1. You might be able to shrink the MacosX partition to make room for a linux boot partition, Apple_Bootstrap, hfs format, around 30Mb. This would hold  boot and kernel files ofboot.b, yaboot, yaboot.conf, vmlinux, initrd.img.  Probably try to include that bootstrap partition in the linux install, then add kernel images and edit yaboot.conf. This would give a text boot menu to select Macosx or linux, with preselected default and timeout.
Catch: I dont know how shrinkable your Macosx partition might be.

2. Or put the boot and kernel files, except for ofboot.b. in the existing MacosX hfs+ partition. This would use the Option apple picker to boot Macosx, with auto boot to the external linux via boot-device setting and yaboot, otherwise I think it will default to macosx if the external is missing. 
Just accept an installer default boot partiton on the external usb. Later the yaboot install to usb bootstrap  partition will probably fail, just continue (it will install the yaboot package files on the root / partiton).

Both options are easier said than done, but I think (2) would be easiest to try, you could always go to (1) later.

---

### Post by computer geek on 2007-09-26
sorry about these 2 poasts.

---

### Post by computer geek on 2007-09-26
i was playing around with the fourm that i axedintily hit save

---

### Post by prestosd on 2007-09-27
> 2. Or put the boot and kernel files, except for ofboot.b. in the existing MacosX hfs+ partition. This would use the Option apple picker to boot Macosx, with auto boot to the external linux via boot-device setting and yaboot, otherwise I think it will default to macosx if the external is missing. 
Just accept an installer default boot partiton on the external usb. Later the yaboot install to usb bootstrap partition will probably fail, just continue (it will install the yaboot package files on the root / partiton).

So install Ubuntu onto the external, then yaboot fails, then move the boot files onto my mac partition. Then Ubuntu would be the default boot, unless the USB drive isn't plugged in. In which case would it boot Mac OS X by default? I don't wanna have to go to that Option menu every time I boot. But I wouldn't mind just leaving the USB drive off, then turning it on when I need it.  


Question: Where do I move the files to on the mac partition?

---

### Post by Lo'oris on 2007-09-27
> **prestosd said:**
> Question: Where do I move the files to on the mac partition?
[SIZE="1"](I've just finished installing ubuntu into the usb disk).[/SIZE] I was going to ask the same question.

There's no /boot here on osx, I've no idea on how the boot system works here.

Btw, I've noticed there is more than 100MB of empty space (according to the ubuntu partitioner) in the internal hard drive, maybe they could be used to host the /boot partition?

I'll post in the other threads output of some of the commands, in case it helps (not posting in this thread to avoid confusion)

---

### Post by prestosd on 2007-09-27
Hey, I'm installing 7.10 now instead...lol, hope this doesn't change a lot....

EDIT: The ISO is 705MB, which means IT DOESN'T FIT ON A CD!!!! So I guess I'll just upgrade after the install....

---

### Post by pxwpxw on 2007-09-27
> **prestosd said:**
> So install Ubuntu onto the external, then yaboot fails, then move the boot files onto my mac partition. Then Ubuntu would be the default boot, unless the USB drive isn't plugged in. In which case would it boot Mac OS X by default? I don't wanna have to go to that Option menu every time I boot. But I wouldn't mind just leaving the USB drive off, then turning it on when I need it.  


Question: Where do I move the files to on the mac partition?


Files to boot ubuntu from external usb:

4 files are required on the Macosx hfs+ partition root.

1. from the installed system (example - my release version, yours may differ, the full files not the symbolic link).

   initrd.img-2.6.20-15-powerpc64
   vmlinux-2.6.20-15-powerpc

2. from your install CD,  yaboot is around 150Kbytes, in the CD /install folder
or from /usr/lib/yaboot/yaboot in the installed system.

   yaboot

3. To be written (by me I suppose):

   yaboot.conf


All 4 placed in the root of your Macosx partition (not the desktop).

  Then the remaining job is to set the Apple boot-device to point to yaboot on the Macosx partition.

However it may be necessary to use the Option key to get Macosx. This is system dependant, only way is to try it. The boot-device can be reset for macosx by
  Zapping the Pram.    Command-Option-P-R


To be continued....setting the boot-device.

---

### Post by pxwpxw on 2007-09-28
yaboot external booting
[http://ubuntuforums.org/showthread.php?p=3441233#post3441233](http://ubuntuforums.org/showthread.php?p=3441233#post3441233)

---

