---
title: "Ubuntu on Imac G3 help, read please!"
date: 2007-06-23
forum: Apple PPC Users
---

### Post by danielbrown162 on 2007-06-23
Basically id like to run ubuntu on my imac g3 (400mhz, 512mb ram, 20 gig) but i cant even get the cd to boot yet, my guess is that this is because im just burning the powerpc iso version of ubuntu straight to a disc. 

The question is, what is the contents of the cd supposed to look like, do i burn the contents of the iso image onto a disc?

a picture would be much appreiciated!

thanks in advance, dan!:popcorn:

p.s also i do not have a cd re writer, i have to go to my local libary to burn a disc, they use windows. hope there is a way around this!

id be willing to pay for someone to make me a live disc? just pm me if your intrested!

---

### Post by angryfirelord on 2007-06-23
You have to use something like [ImgBurn]("http://www.imgburn.com/") to write the cd. All you do is select the iso image and burn it using that.

You can always use ShipIt as well.

---

### Post by webaake on 2007-06-23
Don't forget to check your firmware version! Use the latest possible. Very important on G3's!

---

### Post by danielbrown162 on 2007-06-24
> **angryfirelord said:**
> You have to use something like [ImgBurn]("http://www.imgburn.com/") to write the cd. All you do is select the iso image and burn it using that.

You can always use ShipIt as well.

Thanks, i guess i could burn it to a usb drive, then take it to my local libary? then put onto a disc?

also, is there a shipit for powerpc discs? i did get a pc version, whats great on pc! but not on my g3 :(

also, the firmwre is all up to date! so i just need a bootable disc!

regards,dan.

---

### Post by pxwpxw on 2007-06-24
> **danielbrown162 said:**
> Thanks, i guess i could burn it to a usb drive, then take it to my local libary? then put onto a disc?

also, is there a shipit for powerpc discs? i did get a pc version, whats great on pc! but not on my g3 :(

also, the firmwre is all up to date! so i just need a bootable disc!

regards,dan.

Doubtfull about all that.  This might help:

Firstly:
The list of files and folders on the cdrom should look something like this:

casper,   dists,  install,     pics,  ppc,      README.diskdefines,
cdromupgrade,  etc,    md5sum.txt,  pool,  preseed,  ubuntu.

But you must have the applemac powerpc iso, so thats one reason why the CD wont boot.

In macosx you should be able to see what files are in the downloaded iso, by just clicking on the iso.

Then if you have macosx you should have no trouble burning to a cd using Disk Utility.

You only need to download the iso to your mac  from  [[COLOR="Magenta"]cdimage.ubuntu.com/ports/releases/[/COLOR]]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")

If you want to install on your mac get this one (should work well for the g3):
Mac (PowerPC) and IBM-PPC (POWER5) alternate install CD

If you want to try it just from the CD (may not work for your g3):
Mac (PowerPC) and IBM-PPC (POWER5) desktop CD

If you need more help, will need more info about which (desktop or alternate) you want to try, and about your g3 disk space and macos version. There are several ways you might get going.

---

### Post by danielbrown162 on 2007-06-24
> **pxwpxw said:**
> Doubtfull about all that.  This might help:

Firstly:
The list of files and folders on the cdrom should look something like this:

casper,   dists,  install,     pics,  ppc,      README.diskdefines,
cdromupgrade,  etc,    md5sum.txt,  pool,  preseed,  ubuntu.

But you must have the applemac powerpc iso, so thats one reason why the CD wont boot.

In macosx you should be able to see what files are in the downloaded iso, by just clicking on the iso.

Then if you have macosx you should have no trouble burning to a cd using Disk Utility.

You only need to download the iso to your mac  from  [[COLOR="Magenta"]cdimage.ubuntu.com/ports/releases/[/COLOR]]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")

If you want to install on your mac get this one (should work well for the g3):
Mac (PowerPC) and IBM-PPC (POWER5) alternate install CD

If you want to try it just from the CD (may not work for your g3):
Mac (PowerPC) and IBM-PPC (POWER5) desktop CD

If you need more help, will need more info about which (desktop or alternate) you want to try, and about your g3 disk space and macos version. There are several ways you might get going.


Okay, this is what i burned to a disc at the local libary, 


[IMG]http://i10.tinypic.com/54b4ld0.jpg[/IMG]

and is this what you want me to burn? (please check that everything is there)

[IMG]http://i12.tinypic.com/4pjxwgp.jpg[/IMG]


I hope this is all right now, im getting frustrated! also i should probably note, the local libary has very tough restrictions on their computers which means i cant install any software!

i really do like ubuntu, its great on my family pc, i wish it was as simple to put on my Imac :-(

---

### Post by pxwpxw on 2007-06-24
Yes the Ubuntu_PowerPC_feisty iso is the right one if you want to install.

You burn from the iso, not the contents.

When you insert your blank CD-R, select Disk Utility.
Then drag the iso onto Disk Utility and select it.
The Burn icon should light up, select burn, then select the lowest available speed 
(8x on my g4) with Verify burned data. Then burn it. 

Then recheck the finished CD in Macosx and you should have the 11 files and folders as in your screenshot.

Then read the Doc.

Then you need to decide how to partition the drive for ubuntu.

---

### Post by danielbrown162 on 2007-06-25
Thats the problem though, i dont have a cd re-writer on this imac, just a dvd rom. 

The only way i can do this is if i go to my local libary and copy the contents one by one or pay someone on here to make me a copy :-(

would it be possible to copy the files over one by one?

regards,dan.

---

### Post by pxwpxw on 2007-06-25
Ah, yes I forgot, but hang on, you can probably do it using the iso on your macos. Let me reread everything.
OK.

Check this: you have a 20GB drive? Plenty for Macosx and ubuntu. What version macosx? Check in macosx how much disk space used/free.

Open the  terminal app in macosx, get your current disk partition map and post it
```

 sudo pdisk -l

```

Have a look at my notes  about  booting install with no cd, (the ISO option) for an idea of the way to do it.
[ **ISO install** ]("http://ubuntuforums.org/showpost.php?p=2887410&postcount=4")

---

### Post by danielbrown162 on 2007-06-25
> **pxwpxw said:**
> Ah, yes I forgot, but hang on, you can probably do it using the iso on your macos. Let me reread everything.
OK.

Check this: you have a 20GB drive? Plenty for Macosx and ubuntu. What version macosx? Check in macosx how much disk space used/free.

Open the  terminal app in macosx, get your current disk partition map and post it
```

 sudo pdisk -l

```

Have a look at my notes  about  booting install with no cd, (the ISO option) for an idea of the way to do it.
[ **ISO install** ]("http://ubuntuforums.org/showpost.php?p=2887410&postcount=4")

Yes, i have a 20gb drive and have used about 7gb's of it, i really would like to be just booting ubuntu so this shouldnt be a problem!\\ I am using osx 10.3.9 aswell with 512mb of ram which is plenty.

i shall read through your notes but im not computer expert, im not good with the whole coding thing but i shall give it a go!

ive got this so far in terminal:

Last login: Tue Nov 20 16:34:30 on ttyp1
-bash-2.05b$ sudo pdisk -l
pdisk: no command specified
usage:  pdisk <raw device> <option>
        where <raw device> is the live partition ie. /dev/rdisk0
        and <option> is one of the following:
Option
-blockSize              : display the block size used by the map
-dump                   : dump the list of partitions
-isDiskPartitioned      : is the disk partitioned
-diskSize               : prints the size of the disk in megs
-partitionSize          : get the partition size in blocks
-partitionBase          : get the partition base in blocks
-partitionType          : get the partition type
-partitionName          : get the partition name
-partitionEntry         : get the partition name, type, base, and size
-splitPartition         : split an existing partition in two pieces
-createPartition        : create a new partition
-initialize             : initialize the partition map
-deletePartition        : delete a partition
-getPartitionOfType     : get partition of specified type
-getPartitionWithName   : get partition with specified name
-makeBootable           : make a partition bootable
-setAutoMount           : set or clear the auto-mount bit for HFS volumes
-setWritable            : set or clear the writable bit in the pmap
For more info on the option, type pdisk <raw device> <option>
-bash-2.05b$ partitionEntry
-bash: partitionEntry: command not found
-bash-2.05b$ 


where do i go from here?

regards,dan.

---

### Post by pxwpxw on 2007-06-25
right, its a different version to pdisk on 10.4

try

sudo pdisk -dump

or 

sudo pdisk /dev/rdisk0 -dump

Edit - hd-media files to download:

In the notes, under the section < ISO install. (no burning)>
You should use the hd-media set.
Where it says:
For 32bit powerpc the hd-media set of vmlinux, initrd.gz, yaboot, yaboot.conf
is good for installing from an Alternate or Server cd .iso on the hard drive.
hd-media set vmlinux initrd.gz and yaboot.conf. Plus yaboot from the Network Install - current images above.

(using the links in the notes)

You can download the 4 small files vmlinux, initrd.gz, yaboot.conf, and yaboot to your macosx drive patition.
That just leaves booting the installer from open firmware for a trial run. I will go through that when you are ready.

---

### Post by danielbrown162 on 2007-06-25
hi,

ive download the 4 files although im not quite sure what to do with them!

also, i got the terminal window up and it shows:

-bash-2.05b$ sudo pdisk /dev/rdisk0 -dump
/dev/rdisk0  map block size=512
   #:                 type name                 length   base     ( size )
   1:  Apple_partition_map Apple                    63 @ 1       
   2:       Apple_Driver43*Macintosh                56 @ 64      
   3:       Apple_Driver43*Macintosh                56 @ 120     
   4:     Apple_Driver_ATA*Macintosh                56 @ 176     
   5:     Apple_Driver_ATA*Macintosh                56 @ 232     
   6:       Apple_FWDriver Macintosh               512 @ 288     
   7:   Apple_Driver_IOKit Macintosh               512 @ 800     
   8:        Apple_Patches Patch Partition         512 @ 1312    
   9:           Apple_Free                           0+@ 1824    
  10:            Apple_HFS Apple_HFS_Untitled_1 39747320 @ 263968   ( 19.0G)
  11:           Apple_Free                           0+@ 40011288

Device block size=512, Number of Blocks=40011300
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

-bash-2.05b$ 

hope thats right! looks like it!

---

### Post by pxwpxw on 2007-06-26
> **danielbrown162 said:**
> hi,

ive download the 4 files although im not quite sure what to do with them!

also, i got the terminal window up and it shows:

-bash-2.05b$ sudo pdisk /dev/rdisk0 -dump
/dev/rdisk0  map block size=512
   #:                 type name                 length   base     ( size )
   1:  Apple_partition_map Apple                    63 @ 1       
   2:       Apple_Driver43*Macintosh                56 @ 64      
   3:       Apple_Driver43*Macintosh                56 @ 120     
   4:     Apple_Driver_ATA*Macintosh                56 @ 176     
   5:     Apple_Driver_ATA*Macintosh                56 @ 232     
   6:       Apple_FWDriver Macintosh               512 @ 288     
   7:   Apple_Driver_IOKit Macintosh               512 @ 800     
   8:        Apple_Patches Patch Partition         512 @ 1312    
   9:           Apple_Free                           0+@ 1824    
  10:            Apple_HFS Apple_HFS_Untitled_1 39747320 @ 263968   ( 19.0G)
  11:           Apple_Free                           0+@ 40011288

Device block size=512, Number of Blocks=40011300
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

-bash-2.05b$ 

hope thats right! looks like it!

Yes, thats good.

Drop the 4 files into your macosx disk icon (at the root of your MacosX partition,  not in a folder).
And put the Ubuntu_PowerPC_feisty  iso there with them, not on the desktop.

So you will have 5 files: Ubuntu_PowerPC_feisty .iso, vmlinux, initrd.img, yaboot, yaboot.conf, - all together in the root of your MacosX partition.

A window shot of the finder showing  them  all in postion would be good, but in the finder, change your view option to "List" and show files sizes. 

Also please post a copy of the yaboot.conf file you downloaded.
 
One more terminal command to get your boot-device setting - try these (not sure if they will be the same for your macosx version):
```

 sudo nvram boot-device
 sudo nvram -p

```

Then I  can tell you how to set the boot-device to boot yaboot and the installer for a trial run.

---

### Post by danielbrown162 on 2007-06-26
Okay, i understand all of tht apart from, drop the 5 files into the mc osx disc. where is this?

i have all the files ready to copy over (i wont copy the folder over as you said)

[IMG]http://i12.tinypic.com/504ppy0.jpg[/IMG]

p.s thanks so much for your help, it would had been easier if you could of donethis all for me, less stressful for you too im sure. Remote desktop could had came in handy :-p

---

### Post by pxwpxw on 2007-06-26
No stress here, all good fun. :p

Just leave the 5 files where they are in the folder for now. When all else is ready you just drag and drop them into your "imac G3" startup disk icon, and open "imac G3" in the finder to check them. Get rid of any other iso in there, may confuse the installer. 

But first can you save a copy of the 5 files to a usb stick? You may have to reinstall MacosX if resizing the partition from the installer crashes, and you dont want to lose your downloaded ubuntu iso. You need MacosX there until ubuntu is installed and running. 

Also you need to clear all those other iso images right off the imac, they could cause confusion mounting the ubuntu iso, and they take up space. I dont know what that XP stufff is doing there, trash it. (Make sure the trash is emptied also).

You still need to run the nvram command so we know the boot-device and other setting and how to get back into MacosX. 
```

 sudo nvram boot-device
 sudo nvram -p

```
And open yaboot.conf in textedit (dont change anything) post the text here.

Then you can try booting, you can back out of the installer before any partion changes are made, and retry without any permanent changes.

When you finally get to run the installer you will have to resize the MacosX partition using a command line console from the installer, because the Menu based partitioner cannot do it for macos extended (I just tried it here). Only needs 3 or 4 commands using "parted", I will show you that exactly.

First thing is to get the installer booted and try it.

**Edit:**

If resizing the MacosX partition from ubuntu install is a problem, you can do this very easily using iPartition (not free ware though), it will also defrag/consolidate to give max free space for ubuntu.

[http://www.coriolis-systems.com/**iPartition**.php]("http://www.coriolis-systems.com/iPartition.php")

---

### Post by danielbrown162 on 2007-06-27
Okay, the nvram thing is as follows:

Last login: Wed Nov 21 08:54:12 on console
-bash-2.05b$ sudo nvram boot-device
Password:
boot-device     mac-io/ata-4@1f000/@0:10,\\:tbxi
-bash-2.05b$ sudo nvram -p
default-router-ip
diag-file       ,diags
oem-banner?     false
boot-script
virt-size       -1
fcode-debug?    false
output-device   screen
output-device-1 scca
real-mode?      false
use-generic?    false
input-device    keyboard
mouse-device    mouse
virt-base       -1
selftest-#megs  0
default-server-ip
load-base       0x800000
boot-screen
default-subnet-mask
screen-#columns 100
aapl,pci        /@f0000000/@10/@0%00geometry%00%ab#O%f3%9e%c7%ad$Q%ef%9d%c6%a9%1fP%ef%a0%c5%fb%0a%bb3%00/offscreen-display%00gprf%00%ff%01%07%01%01%ff%04%00/@f0000000/@10%00Sime%00%ff%01%1b%ff%01%cb%ff%01%82%10%ff%01%00
ASVP    0110??001;<;%00
oem-logo
boot-file
real-base       -1
pci-probe-mask  -1
input-device-1  scca
boot-command    mac-boot
auto-boot?      true
diag-switch?    false
default-mac-address?    false
screen-#rows    40
boot-device     mac-io/ata-4@1f000/@0:10,\\:tbxi
diag-device     enet
boot-args
ram-size        0x20000000
prev-lang:kbd   en:2
little-endian?  false
oem-banner
console-screen
default-client-ip
nvramrc
default-gateway-ip
use-nvramrc?    false
real-size       -1
oem-logo?       false
-bash-2.05b$ 


Then the yaboot.conf file is:

## This yaboot.conf is for hd-media booting only, do not use as reference.
## Ubuntu 7.04 PowerPC

default=install
root=/dev/ram

message=/boot.msg

image=/vmlinux
	label=install
	initrd=/initrd.gz
	initrd-size=17217
	append="--"
	read-only

image=/vmlinux
	label=expert
	initrd=/initrd.gz
	initrd-size=17217
	append="priority=low --"
	read-only

image=/vmlinux
	label=server
	initrd=/initrd.gz
	initrd-size=17217
	append="base-installer/kernel/linux/extra-packages-2.6= tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false --"
	read-only

image=/vmlinux
	label=server-expert
	initrd=/initrd.gz
	initrd-size=17217
	append="base-installer/kernel/linux/extra-packages-2.6= tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low --"
	read-only

image=/vmlinux
	label=rescue
	initrd=/initrd.gz
	initrd-size=17217
	append="rescue/enable=true --"
	read-only


I just tried to drag the files onto my imac g3 startup disc bit but its not letting me drop them there

[IMG]http://i13.tinypic.com/4kwm9au.jpg[/IMG]

i cant think of anywhere else you may have meant, but im soo close to getting it running! just a matter of time now.

:D:D:D

---

### Post by danielbrown162 on 2007-06-27
> **pxwpxw said:**
> No stress here, all good fun. :p

Just leave the 5 files where they are in the folder for now. When all else is ready you just drag and drop them into your "imac G3" startup disk icon, and open "imac G3" in the finder to check them. Get rid of any other iso in there, may confuse the installer. 

But first can you save a copy of the 5 files to a usb stick? You may have to reinstall MacosX if resizing the partition from the installer crashes, and you dont want to lose your downloaded ubuntu iso. You need MacosX there until ubuntu is installed and running. 

Also you need to clear all those other iso images right off the imac, they could cause confusion mounting the ubuntu iso, and they take up space. I dont know what that XP stufff is doing there, trash it. (Make sure the trash is emptied also).

You still need to run the nvram command so we know the boot-device and other setting and how to get back into MacosX. 
```

 sudo nvram boot-device
 sudo nvram -p

```
And open yaboot.conf in textedit (dont change anything) post the text here.

Then you can try booting, you can back out of the installer before any partion changes are made, and retry without any permanent changes.

When you finally get to run the installer you will have to resize the MacosX partition using a command line console from the installer, because the Menu based partitioner cannot do it for macos extended (I just tried it here). Only needs 3 or 4 commands using "parted", I will show you that exactly.

First thing is to get the installer booted and try it.

**Edit:**

If resizing the MacosX partition from ubuntu install is a problem, you can do this very easily using iPartition (not free ware though), it will also defrag/consolidate to give max free space for ubuntu.

[http://www.coriolis-systems.com/**iPartition**.php]("http://www.coriolis-systems.com/iPartition.php")

I forgot to mention, when i get ubuntu running im going to be useing instead of osx, therfore i wont need osx on my system anymore so i wont need to partion!

or will i have to to run ubuntu?

regrds,dan.

---

### Post by pxwpxw on 2007-06-27
> **danielbrown162 said:**
> I forgot to mention, when i get ubuntu running im going to be useing instead of osx, therfore i wont need osx on my system anymore so i wont need to partion!

or will i have to to run ubuntu?

regrds,dan.

Well, doing it this way you need the Macosx partiton there for running the installer from the ISO - which is on the macosx partition (or from the network), and need to  keep it there if you dont get everything right first go - which often happens.  Once ubuntu is installed you dont need MacosX, and you could re-allocate the space from ubuntu.
The catch is that you have to resize the MacosX partition down to minimum to make free space available for ubuntu - as mentioned in my last post.

If you had an install CD, you could trash macosx entirely and install ubuntu from the DVD /CD player, and let it automatically partition the whole drive to suit ubuntu.

But keeping a small (5GB) macosx partiton is a usefull thing to have, because you can leave the iso there and rescue ubuntu or repeat the install any time, as well as a backup for interrnet access using safari.  Even a 1GB macos extended partiton is handy for backup booting and rescue.

I have a basic MacosX 10.4.8 partiton on an iBook, using only 4GB, including one 700MB iso, so 5GB would be plenty (the remainder of the 40GB disk is 2 Linux systems). 

But if you have the MacosX 10.4 or 10.3 install DVD, the simplest thing would be to just reinstall MacosX on a 5GB partition, and leave the rest free for ubuntu.  That should only take an hour or less, from memory.  But save a copy of your iso to USB first (plus any other valuables).

 And if you do that, and you get the option to install MacosX without Macos9 support, I think that will eliminate all those 10 or so small Apple driver and patch partitions from the partition table that you posted.

Your choice.;)

[COLOR="Red"]EDIT:
I completely missed some of your previous post with nvram results etc, reading now, will post corrections as soon as can. Sorry about that.[/COLOR]

---

### Post by pxwpxw on 2007-06-28
This will come in stages as I read back, I will be adding bits, and correcting spelling errors.
 Fisrstly, forget iPartition, you need it on a cd to do anything usefull. The ubuntu iso can do it. Chance of it crashing macosx, well worth a try though. 

Can you post from another computer for any problems? - if not you need a copy of some of this info so you can refer to if you cant use the macosx.
 
1. For dropping the 5 files into imac-g3 - not in the startup menu, but  into the imac-g3 icon top right of your desktop. Should go in without trouble. (I find reference to the Staartup disk confusing too). Actually we are talking about the root of your macosx partition.

2. You need to know how to get back into Macosx after doing a trial run of the installer. Try these ways:

Try starting with the Option key held down, see if this gets an Open Firmware screen or a startup Icon picker screen with Macos. If you can get the icon picker and back into macosx that way, you can skip the nextbit about open firmware:
 
 {{ Another way to start in open firmware:
 Hold down 4 keys Command(Apple) Option o f
 from before the chime at restart.
 This should start into Open Firmware.white screen }}
 In open frmware you get some lines of help about booting and shutting down and a prompt
0>
Then type 
```

printenv boot-device

```
then if you have to reset boot-device later on, you would do this
```

setenv boot-device mac-io/ata-4@1f000/@0:10,\\:tbxi
### that would reset it to the same as you got using nvram inmacosx
### but if ubuntu changes the partition numbers, you might have to change the 0:10 to 0:11

```
and check it by doing printenv boot-device again.
To boot 
```

boot

```
To restart
```

reset-all
### or
shut-down

```


3. The safest way to boot yaboot and the installer is to boot directly from open firmware. This avoids changing the boot-device setting, so a restart will automatically boot back into macosx. If the command fails, it will just report an error, might be a typo, check carefuly, try again or restart the mac. First get into the open firmware screen at restart, as above. 
 
If you have put the 5 files into correct position in the ibook-g3 partiton top level.
This should boot yaboot from open firmware:
```

0> boot mac-io/ata-4@1f000/@0:10,yaboot

```

Then you should see the yaboot welcome and boot: prompt, hit <tab> to see the options which are the"labels" in yaboot.conf. 
The default is <install>. It should detect the iso and it will mount it as /cdrom. You can run the installer  up to the partitioner, select "manual partitioning" and get a listing of the partitions. Then back out  before it actually does any changes (it will ask you). You can just abort the install to reboot from there, we just want to see if the installer runs OK for starters.




======

---

