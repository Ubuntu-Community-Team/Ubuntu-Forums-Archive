---
title: "[SOLVED] Beige G3 Tower (oldworld) Massive Fail"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by themacmeister on 2008-11-13
I am trying to install Xubuntu 7.0.4 (Feisty Fawn) PPC onto my new (second hand) G3 Beige megatower with ATI Rage Pro (6MB VRAM). I have 584MB RAM, PCI USB Card (working in OS9.21&OSX 10.2), 6GB HDD (500MB for OS9, 500MB for swap, 5GB for /).

I have reset the PRAM, I am using latest BootX (1.22), and have a slow-burnt copy of Xubuntu PPC alternate install CD. I also have the 17" AV monitor with 2 ADB ports, headphone jack etc.

Using the Kernel and the RamDisk on the Xubuntu installer CD, I am able to boot into the text install for Xubuntu. Unfortunately, that is almost as far as I get. I have free space available for the Linux partitions, but the partitioner is flakey. I can only select XFS as an option if I select manual partitioning. If I select automatic using available space, It selects ext2 for /boot (32MB), and ext3 for the rest.

Here is where my problem occurs!

Upon creation and finishing partioning, the installer fails to mount ANY type of partition - and THEREFORE CANNOT CONTINUE the install!

I have heard that some people with OldWorld Macs need a custom built kernel. I have also heard that upping the RamDisk size in BootX helps a great deal.

Can someone please help me out here, as this could be a great linux box!

Cheers

---

### Post by stream303 on 2008-11-13
There might be something in here that will help:

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

I'd love to hear about a sucessful old-world install!

---

### Post by themacmeister on 2008-11-13
That was a great read, but unfortunately no help to me. I believe I need to modprobe ide_core (as I have one of the first IDE drives) and possibly even 'mesh' and 'mace'. I will try a full install again when I find time.

I am SURE I need to UP the RAMDISK size in BootX - that seems to be a given, seeing what I've read online. I will try all these options next time...

PS. The screen is very very dark - and very very bright with OS9/X. darn software controlled AV monitor!!

This is a 1 1/2 year old distro - but should be good enough for my purposes (if I wanted to go retro, I would have kept OS9!! or even updated to Tiger). Jeez, tiger would be slow on this machine I think (300MHz).

---

### Post by stream303 on 2008-11-13
Just be careful with underscores and hyphens - I've seen them listed as ide-core and ide_core before, not knowing if it was a typo or not.  I guess try it both ways to be sure. :)

---

### Post by tiresia on 2008-11-13
Just some thoughts: I installed Ubuntu Hardy on my PowerPC 7500 and on my beige g3 and there was no problem.
I had a PCI USB card as well, but I had to remove it, otherwise I got always a kernel panic. 
Have you tried with a different CD Installer? Maybe also with Debian? Did you check the .iso image after the download?

---

### Post by themacmeister on 2008-11-13
Typing this in Firefox on my freshly installed Xubuntu 7.04 PPC Beige G3 MiniTower PowerMacintosh!!!! I will document my install procedure at the end of this post - to hopefully help those struggling with oldworld macs.

RTL8139D 10/100 PCI ethernet found and working now with ADSL. (better than built-in 10BaseT).

Screamer soundcard working OOTB.

ATI video driver working with or without "load DRI" in xorg.conf
Obviously no DRI support at the moment. I might try Mach64 driver later.

Listening to Joe Cocker in Audacious at the moment - very nice!

USB PCI card (generic) working beautifully. Printers (FX Docuprint 203A & HP Deskjet F2275) working beautifully. Computer is fairly responsive, considering.

Unaware if my G3 cache is enabled - not even sure if I have an L2 cache (pretty sure I only have an L1 cache of 1MB). see [http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_300_mt.html](http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_300_mt.html) for more info.

Instructions coming REAL SOON!!!

mplayer *IS* broken btw... found out for myself!

---

### Post by themacmeister on 2008-11-14
Step 1. (longest)

I have read many (well, one) posts that state zeroing all data when you reformat a hard disk is a first step to repeated success. I used a PLAIN HFS VOLUME, as you have read/write drivers under Linux. I selected Zero All Sectors in Drive Setup under MacOS 9.2.1 (under Initialisation Options). A 6GB ATA HDD took about 30min. Bigger disks mean bigger waits.

Use a custom partition setup of 200-500MB for OS9, can be smaller if you will never use OS9. Can be excrutiatingly small if you do a minimal install, and add internet utilities custom install (Aladdin StuffIt Expander). Using my method, you will not require FTP, HTTP, SCP or anything else.

Step 2. Install MacOS 9.x.x off a FULL install CD. Do not use an updater or recovery disk. The one I used was for a G4 9.2.1 (this is the first to contain the USB PCI Card extensions as a default - and a newer more reliable version at that). Make sure you install Aladdin Stuffit Expander - it is part of Internet Access.

Step 3. Boot into MacOS 9.x.x.

Download and install [http://penguinppc.org/historical/benh/BootX_1.2.2.sit](http://penguinppc.org/historical/benh/BootX_1.2.2.sit)
You can download it on another machine and transfer it via USB Thumb Drive - It works in OS9 exactly like windows (except OS9 thinks it is a removable cartridge, REMEMBER THOSE?!).

Insert your Ubuntu/Xubuntu/Fedora Core/Mandrake/Mandriva CD, and copy the Kernel and ramdisk image to your Mac Desktop. The Kernel will almost always be called "vmlinux" and the ramdisk is usually called "initrd.gz" (for Initial Ramdisk).

Create a new folder in System Folder called "Linux Kernels" and move vmlinux in there.

Move initrd.gz loose in the System Folder.

Step 4. TIME TO INSTALL LINUX!!!

Launch BootXApp, it should be in your Control Panels folder if you dropped both BootX files onto your System Folder.

The vmlinux file should automagically be detected, and under the options button, select a custom ramdisk - select the initrd.gz file you copied into the System Folder earlier.

IMPORTANT: Set the ramdisk size UP from 8192. I chose 10240 - your mileage may vary depending on how much RAM you have installed.

When all this is done, you can click the "Linux" button.

The screen will go black, and you should see the typical scrolling white text of a Linux startup procedure. 

To solve any non-loaded module problems, I used a second terminal (Control-Alt F3), and entered the following.

modprobe mesh
modprobe mace
modprobe ide_core
modprobe ide_disk

If you are using only SCSI, choose Force 'SCSI on' in BootX, and don't forget the above commands. FYI mesh=built-in ethernet, mace=built-in SCSI. mesh and mace may be back-to-front as well in their meanings

I got errors on mace and ide_core, but some systems may need these...

Go through the entire procedure as normal, except with the following caveats!!

a. Do a manual format, and select ext2 for the main portion of your partitioning. This was the safest way for me, as I had epic failure using ext3 previously. TAKE NOTE of the partition you formatted as / (root filesystem), as you will need to use it again in BootX. Also TAKE NOTE of the largest HFS partition, as you will need to mount that later as well.

I don't remember seeing it as an option, but I would have loved to use ReiserFS, as it performs wonderfully with many million small files, and the journal recovery process takes seconds, not MINUTES!

b. The install will seem to hang at certain points, in my case, it was at 86% of the original install, and also at 6% of the Xubuntu-Desktop install.

I believe it is timing out a lot of unnecessary wget commands, so it does take a LONG time (maybe 15-20min stall each time on a 300MHz G3).

You will get an alert at the end of the install that a bootloader could not be installed. This is FINE, as you will be using BootX to load Linux.

At the point when this warning occurs, you can go to the other terminal Cntrl-Alt-F3.

You need to mount your existing Mac and new Linux partition, just type:

mkdir /tmp/mac
mount -t hfs /dev/hda6 /tmp/mac
mkdir /tmp/lin
mount -t ext2 /dev/hda7 /tmp/lin
cp -R /tmp/lin/boot /tmp/mac/Desktop\ Folder/

This boot folder will be waiting on your OS9 desktop later, when you will need to replace vmlinux and initrd.gz you copied off the Linux CD earlier.

nano /etc/X11/xorg.conf

find the line that reads 

load "dri"

and change it to:

# load "dri"

as your graphics drivers and kernel do not support DRI/DRM

hit Cntrl-X and save as the same name (press Y then enter)

Switch back to the installer (Cntrl-Alt-F1 for text, Cntrl-Alt-F7 for graphic)

and REBOOT - the CD will be ejected - this is a good time for:

STEP 5. Reboot into OS9 install CD

Yes, the hard disk is completely fried, but by simply launching the OS9 install CD (you may need to first select it from the HD boot of OS9), and run Drive Setup, and Update Drivers... 

This fixes the disk to solve the flashing question mark, and now boots OS9/BootX as expected.

STEP 6. Reboot into hard disk OS9

At BootX screen, hit MacOS, and when at the desktop, open the folder called 'boot'

Rename the corresponding LONG named vmlinux and initd.gz files. Make sure you replace the VMLINUX file from before, or you will not be able to boot your newly installed Linux, the same applies for replacing the old initrd.gz.

Now launch BootXapp, and type in the Kernel Parameters field:

root=/dev/hda7

or whatever the root (/) install of Linux was installed earlier - YOU TOOK NOTE RIGHT???.

Select "Save to Prefs"

hit the Linux button.

SUCCESS!!! SUCCESS!!! SUCCESS!!!

NOTE: When BootX appears, you only have about 5 seconds to act, before it automatically continues booting OS9. If you begin typing it stalls this autostart. You may need to hit "save to prefs" the next boot, as this does not always "stick" the first time.

I would love to give you more information, but I have only just begun this myself. I have installed VLC for movies (as mplayer does not work), and Audacious for MP3s. All working wonderfully at the moment. My install of Xubuntu 7.0.4 included F11 and F12 mapped as the middle and right mouse buttons respectively. You may be lucky if this is the case for yours.

With X/K/Ubuntu there is a STAGGERING selection of PPC packages to install with apt-get (or Synaptic - the GUI frontend for apt). There are notable missing files, but certainly enough software to get started. If you want to do any building/compiling of software (almost a necessity in Linux), you will need to type:

sudo apt-get install build-essential

in a Terminal window. This will give you everything you need to configure and compile a program.

That is all for now. I am real tired. More later. Remember - GOOGLE is your friend!

---

### Post by themacmeister on 2008-11-14
I gleaned most of this info off the web. Not a lot out there either, and most people talk of custom kernels needed to boot etc.

The short answer is - if it boots off CD, it will work with BootX. If it doesn't boot with BootX using the above - it will almost certainly be a pain in the *ss, and most probably never work on that machine!

The long answer is - don't try any modern KDE or Gnome desktops unless you have a zippy G4 and a supported accelerated graphics card (Rage 128, 3Dfx Voodoo3, Radeon). Most of these OldWorld macs have no AGP port either, so you may not have a lot of choice.

If you get glx working in Direct Rendering mode, you can use fancy compiz/beryl effects. I use OpenBox (CrunchBangLinux!) on my Core2Duo machine, and it is AWESOME!

I am using a Mac-PC VGA dongle, which lets me use PC monitors. This gives me perfect screen postion and geometry every time. If you are using a Mac monitor, remember that some resolutions are WIERD (834x624) etc. I knocked all those out of xorg.conf, leaving only 1024x768, 800x600, 640x480.

Also defaulted to 24bit, where 16bit may be a LOT faster for you.

Cheers til later.

PS. I would LOVE to try FluxbuntuPPC, but when will that ever appear - 2 years overdue already!

---

### Post by Mocker on 2009-09-29
Hi folks,

Sorry to resurrect an old thread, but I'm trying to follow these instructions and have hit a snag.

I'm trying to get a Beige G3 (300Mhz, 384MB RAM, 250 GB IDE hard disk, ATI Mach 64 video card)  up and running on Xubuntu Jaunty. I followed all of the steps up to booting up Xubuntu for the first time to start the install. I found that in order to have the boot text appear, I needed check BootX's "No video driver" box (I assume this has to do with the ATI video card, which is in addition to the built-in video card). After that, things started promisingly, but then ground to a halt with these messages:

```

Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
Begin: Waiting for root file system ...
[ 269.065418] SCSI subsystem initialized
[ 269.074919] ide-gd driver 1.18
[ 269.106646] hda: max request size: 512KiB
[ 279,112143] mesh: configured for synchronous 5 MB/s
[ 269.266719] ide-cd driver 5.00
[ 269.993279] Adding 92520k swap on /dev/ramzswap0. Priority:100 extents:1 across:92520k
[ 273.265390] eth0: BMAC at 00:05:02:d9:f5:13
[ 270.497683] mesh: performing initial bus resey...
[ 273.670750] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63
[ 273.700018] hda: cache flushes supported 
[ 273.726199] hda: [mac] hda1 hda2 hda3 hda4 hda5 hda6 hda7 hda8
[ 273.764372] ide-cd: hdc: ATAPTI 24X CD-ROM drive, 128kB Cache
[ 273.790533] Uniform CD-ROM driver Revision: 3.20
[ 273.966247] ide-gd: hdd: No disk in drive
[ 274.038813] ide-gd: hdd: 98304kB, 32/64/96 CHS, 4096 kBps, 512 sectior size, 2941 rpm
[ 274.525627] scsi0 : MESH
Done.
Gave up while waiting for root device. Common Problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! does not exist. Dropping to a shell!

```

and drops me to an initramfs prompt.

I've tried several things:

[LIST]
[*]Upping the size of the ram disk in BootX, in case the initrd was too large (although I'm not sure... does initrd go into this ram disk, or is the ram disk separate?)
[*]Tried setting a rootdelay value of 50
[*]Double-checked to make sure the proper vmlinux and initrd.gz files were copied. They came from the /casper/powerpc/ directory on the Xubuntu CD.
[*]Tried the modprobe commands to make sure all of the necessary modules are loaded. This didn't seem to have any effect, though (i.e. no new modules appeared in /proc/modules).
[*]Trying to manually mount the cdrom (/dev/hdc, I think). That fails with an "Invalid Argument" error 
[/LIST]

So, I've run out of things to try. I don't know how to check for what the boot process thinks is the root device (and is this different than the root file system?)  Anyone else have any ideas? 

Thanks!

---

### Post by eldon.t on 2009-10-04
i've got the exact same problem here on a g3 beige i try to upgrade

did you try another distro to see if it's xubuntu's ppc boot cd's fault ?

also there's an usb adapter card on this g3 and usb seems to be properly detected showing a /dev/sda "kingston" device when my kingston usb key is plugged in at boot. 
I was wondering if it would be possible to launch the install from an usb install disk ? i used ubuntu's usb disk creator to put that xubuntu ppc iso on the usb device.

finally can something actually be done from that shell or is it useless to start the install ?

hope someone can give us some hints..


-edit
debian 503 ppc netinst boots without problem from bootx (using vmlinuz and initrd.gz), is there a difference between those debian boot cds and xubuntu ones ?

---

### Post by abtabt on 2009-10-04
hi dont give up 

i have a lot of experience of old world mac 

.i always use the alternative cd 
 (i dont think the xfce cd will work on old world mac but i am not sure correct if i have wrong

(i have use it from start ubutu  5.04 - 9.04 the alternative cd)

and start to install only server dont select ubuntu-desktop yet
 
then when the server works 

 add the desktop you want (icewm , lxde or xfce )

witch version of ubuntu ?????

---

### Post by eldon.t on 2009-10-04
i have installed debian 5.03 netinst successfully

during install you have to be very careful about two things that were described here and there :
- you need to have a bootable mac os9 at all times !
That means either you have a bootable install CD and make sure it works, which i don't, or a working hd with mac os9, here it was my orginal scsi disk i didn't modify because i was replacing that hd with another one for bootx/linux.
That's because when you use the linux install to make your partitions it will corrupt the mac boot (mbr ?) and after linux installs, your disk won't boot anymore and you'll have to boot either from cd or from another disk and restore the disk driver on your "broken bootx mac os"..

-if you install debian make sure you use ext3 partitions and not ext2 because debian installer will try to install quik bootloader on your system and i have no idea what kind of problems it can introduce, but will fail to do so if you don't have an ext2 partition.

besides that you need to specify both vmlinuz and initrd.gz in bootx and set the bootloader option "root=/dev/xxx", with xxx being your linux root partition.

all of that was already described in other tutorials but that's really the only three obstacles i had to face.

then i wasn't able to mount the hfsplus mac os partition to copy the new vmlinuz and initrd from the fresh install and had to mount/use an usb key. 
If you forget about that at the end the debian install, as i did, you can boot the debian install again from bootx as you did the first time and then do your mounts and copies using a shell from the install menu at the bottom.


debian comes with gnome, it's a bit slow on my ppc 333MHz with 384Mb of ram, i'll try to change the ati driver and check the xorg conf to see if it improves performances, and i'll also try to install xfce as a gnome replacement.

maybe i'll try some ubuntu/xubuntu alternate cd later to see if it works the same way debian does.

---

### Post by eldon.t on 2009-10-05
Hi

okay it seems the distros using the debian installer work fine but not the distros having a graphical interface.

so both ubuntu-ppc-alternate and xubuntu-ppc-alternate work fine.



Now for some post install configuration i was wondering if anyone managed to get xorg to set the monitor at 1024x768, here no matter what i do i can't make it use that resolution although 1024 works in mac os9. I use a vga dongle mac/pc.

my beige powermac g3 has an ati rage 3d and the driver used seems to be mach64, anyone with a working 1024x768 xorg.conf ? do you need to pass a "vga=" option on the boot command line ?

thx

---

### Post by abtabt on 2009-10-07
so both ubuntu-ppc-alternate and xubuntu-ppc-alternate work fine.


Thats my experince to , only alternative cd works for old world mac

Now for some post install configuration i was wondering if anyone managed to get xorg to set the monitor at 1024x768, here no matter what i do i can't make it use that resolution although 1024 works in mac os9. I use a vga dongle mac/pc.

yes it can be done but you need to edit xorg.conf

sudo nano /etc/X11/xorg.conf

and put in right hoz ,ver hz for the monitor     

before you do that check
 
code

nano /var/log/Xorg.0.log

thats the log for the server and maybe you see there whats wrong


my beige powermac g3 has an ati rage 3d and the driver used seems to be mach64, anyone with a working 1024x768 xorg.conf ?

the driver is ati , check the /var/log/Xorg.0.log


 do you need to pass a 
"vga=" option on the boot command line ?

no you dont 

A easy way too get 1024*768

is to change driver for the video card 

only put in 

Driver "fbdev" in xorg  (framebuffer)


example

ection "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
#       BusID           "PCI:0:17:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

then the mac os9 resolution  must be set to 1024*768

and version of UBUNTU ???

---

### Post by eldon.t on 2009-10-07
thx abtabt for your reply

i managed to set the resolution by adding sync lines to xorg otherwise upper resolutions would not be detected, i added those two lines to my monitor setup :

```
Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	HorizSync 	30-96
   	VertRefresh 	50-160
EndSection
```



Unfortunately on my oldworld g3 333MHz/384MB, xubuntu with xfce4 is quite slow especially the 9.10 karmic.

Debian xfce install was faster but i've decided to move to an even lighter desktop manager and begin to appreciate the swiftness of lxde.

it's significantly faster than xfce here, and if you're on karmic you'll probably want to get rid of gdm (login manager) which is simply terribly slow !

Doing all that i must have damaged my distro a bit because bits and parts are missing here and there so i'll probably start again with a fresh ubuntu-alternate install without gnome desktop and then install lxde.

There's also no need to use xubuntu if you're going to use lxde, it will not do much harm if you use it but i guess it just installs some unnecessary apps and packages..

i'm getting close to a really nice linux ppc setup.

---

### Post by abtabt on 2009-10-08
some things i share


Unfortunately on my oldworld g3 333MHz/384MB, xubuntu with xfce4 is quite slow especially the 9.10 karmic.

have you enable the cache ?? and 16 bit colur in xorg

if you disable the desktop speed up tings (

i have not use 9.10 yet,i still use 9.04 but i use icewm and no login manager (if need a faster login manager use slim )

icewm need some conf but you can get like you want 
and use part of xfce uilty like xfce panel etc etc even ubuntu parts can 
be used
 but the speed is better then gnome ,xfce. 
lxde parts have i not tried yet on icewm

and for browser and e-mail 
i use OPERA on  a PPC 4400 with 108 MB memory

---

### Post by Mocker on 2009-10-13
Thanks to the posts here, I've been able to make some progress... I get to install Xubuntu using the alternate install ISO, and get all the way to the step of copying the boot directory to the Desktop Folder. 

When I get to step 5 themacmeister's instructions, rebooting into OS 9.2 using the CD, I find the hard disk is marked as uninitialized.  The Update Driver menu option in Drive Setup's Function menu is dimmed, even when I select the hard disk. The only thing I can do is initialize it. 

I figured this might be caused by the way I partitioned the disk (I just created the partition for Mac OS using only part of the disk, and then used the Xubuntu installer to create the Linux partitions I needed). So, I tried again, using Mac OS's Drive Setup to create the partitions for Mac OS, Linux, and Linux swap. I set the partition types of the last two to Linux Home and Linux Opt, hoping the Mac would just ignore any changes to the partitions. However, I have the same problem... I can't go any further without initializing the hard disk which, of course, wipes out all of my work! Oddly, when I say to initialize the disk, the Drive Setup program *does* warn me that I'm about to nuke my Mac OS and Linux volumes... so it **is** somehow aware of them, it just refuses to do anything with them. :mad:

The one oddity in the setup I is the hard disk is a 250GB IDE drive (the old disk croaked and the only IDE I had lying about was the 250GB). Mac OS seems to only see half of it, or 125GB or so. I've been creating three partitions, one for Mac OS that's about 60GB, one of Linux, also about 60GB, and a 1-2GB swap partition. Could the size of my partitions be throwing something off? 

How have other partitioned their disks?

---

### Post by eldon.t on 2009-10-13
i beleive your partitioning is wrong.

here when i installed my fresh mac os 9.2 on the new ide drive it created 5 or 6 (not sure from memory) partitions for the mac os only !
then after macos 9 is done installing and i can boot from the ide mac os, i can install bootx, copy the vmlinux/initrd and boot linux from bootx.
In the linux setup i add three linux partitions "/" "/home" "swap" which are indeed hda7 8 9, showing clearly that a bunch of partitions are already present from the fresh macos install..

The other thing important is not to install any boot sector for linux because it may cripple your macos install. Boot sector or not your linux hd won't boot mac anymore after additional partitioning has been performed that's why you need to boot a working mac (cd or hd, in my case) and perform a "driver update" on your "unmounted mac/linux hd". To do so i open the mac disk utility where you can use the "initialize" button, select the unmounted driver then use the top menu to "update driver" that disk. If your "update driver" was grayed out it may have to do with your "faulty" mac os partitioning, why do i have 6 partitions and you have only one ?
I'd say your update driver problem could come from there.

---

### Post by Mocker on 2009-10-14
eldon.t,

That's essentially what I did before... I did end up with 6 Mac partitions as viewed from Linux. What I meant was that I partitioned the disk within Mac OS, asking Disk Manager to make a single Mac partition the first time (which I guess translates into it actually making 6?) and the second time asking it to partition the disk into three pieces, one for Mac and 2 for Linux (which, behind the scenes ends up making 8 in total.)

I'll go through again and document what I'm doing, step by step:

[LIST=1]
[*] Boot OS 9.2.1 from CD. 
[*] Run Drive Setup.
[*] Selected the hard disk from the list of drives, and clicked **Initialize...**
[*] Clicked **Custom Setup**
[*] Left Partitioning Scheme as 1 Partition. Under Volume Info, changed the **Size** to 5-6GB, and click **OK**. That leaves most of the disk space as "Extra."
[*] Clicked **Initialize** to initialize the disk, then quit Drive Setup.
[*] Ran the Mac OS installer, installing on the newly initialized disk. Reboot.
[*] Downloaded BootX 1.2.2.
[*] Copied BootX Extension to the System Folder/Extensions folder.
[*] Copied BootX App to System Folder/Control Panels folder.
[*] Inserted the Xubuntu Jaunty Alternate CD.
[*] Created a Linux Kernels folder in the System Folder directory.
[*] Copied initrd.gz and vmlinux from the Xubuntu CD's install/powerpc folder to the Linux Kernels folder.
[*] Started BootX from the Apple menu's Control Panel entry.
[*] Clicked **Options...** next to the Kernel selector.
[*] Selected **Force SCSI ON** (I seem to need this to get the CD to be recognized during the linux install... but I'm not sure it's a scsi CD...)
[*] Selected **Use specified RAM Disk**.
[*] A file selection window should pop up. Navigate to the System Folder's Linux Kernels folder, select initrd.gz. and clock **Open**.
[*] Clicked **OK** to get back to the main BootX screen.
[*] Changed the ramdisk size to 10420 or something larger.
[*] Selected **No video driver** (I seem to need this when using my ATI PCI video card.... otherwise, the linux booting screen is just black).
[*] Clicked **Linux** to boot Linux.
[*] When the installer starts, go through the language selection, keyboard type, timezone, and computer name screens as appropriate (for me, English, USA, USA Macintosh keyboard).
[*] On the *Partition disks* screen, selected **Manual**. Here I can see that the MacOS install has created 6 existing partitions.
[*] Selected the **Free Space** entry in menu.
[*] Selected **Create a new partition**.
[*] Made the partition slightly smaller than the remaining disk space (238GB).
[*] Selected **Beginning** as the location for the new partition.
[*] Selected **Use as** and changed the type to **Ext2**. Partition is automatically set to be mounted as the / directory, with the bootable flag off.
[*] Selected **Done Setting Up partition**.
[*] Repeated the previous 6 steps, only this time, used all of the remaining disk space and selected **swap area** under Use As.
[*] Selected **Finished partitioning and write changes to disk**.
[*] Selected **Yes** when asked to write changes to disk.
[*] Waited for a while as the installer creates partition #7 and formats it as Ext2, and installs the base system.
[*] Set up user name and password, and select **No** when asked to encrypt the home directory.
[*] Hit enter when asked for HTTP proxy info, and select **Yes** to download language support files.
[*] Just hit **Continue** on the *Software selection* screen, figuring if it actually works, I can just install stuff later. It goes and installs some stuff anyhow... :confused:
[*] Get to the screen *Continue without boot loader*, which tells me the boot loader has not been installed because I either chose not to or that the architecture doesn't support it. Hit **Continue**.
[*] At the *Finish the installation screen*, I hit control-option-F2 to get to a console.
[*] Entered ```
mkdir /tmp/lin; mkdir /tmp/mac
```
[*] Entered ```
mount /dev/hda7 /tmp/lin
```
[*] Entered ```
mount -t hfsplus /dev/hda6 /tmp/mac
``` (I found I needed to use hfsplus here, since otherwise the Mac partition wasn't mounted properly, and instead got a directory with just a file named "Where are all my files?" which indicated the file system couldn't be mounted using an older filesystem standard).
[*] Enter ```
cp -R /tmp/lin/boot /tmp/mac/Desktop\ Folder
```
[*] Hit control-option-F1 to go back to the installer.
[*] Selected **No** when asked if clock was set to UTC.
[*] Replaced the Xubuntu CD with the Mac OS 9.2.1 CD when the drive opened.
[*] Selected [B]Continue[\B] to reboot computer.
[*] After Mac OS 9.2.1 boots, run Drive Setup.
[*] Hard disk once again shows up as <not initialized>. The Update Driver command on the Functions menu remains dimmed out. Disk First Aid won't even recognize the drive.
[/LIST]

So, I've tried this every way I can concieve of: let Mac OS create the partitions to install into, manually create them under the Xubuntu installer, have the Xubuntu installer do it through guided partitioning of the empty space, etc. I don't think the install process is actually messing things up by trying to install a bootloader... it seems to know it can't do that. 

I guess I can try downloading a straight Debian install CD and see if that would work. This computer's eventual fate is to offered up for free on one of the local freecycle lists. I had thought that installing Xubuntu would make the machine more useful, while still relatively user-friendly. Straight Debian, as I recall, wasn't all that friendly.

---

### Post by Mocker on 2009-10-14
Apparently, I've solved my issue. It looks like larger hard disks (mine was a 250GB) really really confuse poor MacOS 9.2.1, such that anything touching the hard disk without its involvement (i.e. installing Linux) leaves it unable to cope with the hard disk. Or, possibly anything extending beyond it's built-in disk limitations really blows its little mind.

I figured this out after trying a Debian install, and also trying to install just up to the part where I partitioned the drive. In both cases, Mac OS decided the isk was uninitialized and would have nothing to do with it.

I did have an inkling about this, since I had noticed that MacOS would only see about 120GB of the disk overall (hardware seems to be able to access it all, since Linux sees the entire drive). Finally, I dug deep within the junk closet and found a 30GB Death... err Deskstar and tossed that into the Mac. After running yet another Debian install (canceling it halfway through) I was able to boot back into the OS 9 CD, and run Disk Manager to reinstall the disk drivers... and viola! The Mac OS 9 install on the hard disk is just fine. Now, I just need to try an actual Xubuntu install and see if that does the trick.

---

### Post by themacmeister on 2009-10-17
Where, oh where did you get Xubuntu Jaunty? I was using something way older than that... 7.04 or something shocking. 9.04 should not even be available?!?!

Luckily, I didn't have a drive bigger than 120GB. Believe it or not, you should have been able to format it from a WinBlows system using diskpart (with the extension id=af)

Anyways, glad to know you are up and running. That extra step about booting into OS9 and restoring the drivers is a MUST DO!

Hell, 120GB is enough for just about anything, and old IDE drives are cheap as chips now!

Best of luck with your install - I have dumped both my G3 and my iMac, and I am now experimenting with OSX86 on my AMD box. All is working except restart, and sleep when a USB printer is connected.

I think my next purchase will be a Mac Mini for the parents, as the WinXP box just confuses them! It is possible to install OSX86 onto this box, but very hard to get 8400GS video working right. I might give it another try shortly - before forking out AUS$1000+ for a Mini. :)

---

### Post by eldon.t on 2009-10-17
@Mocker

yeah you have to consider limitations of this old generation softwares. 
As soon as you see that some of your new hardware is not natively supported by your software (bios or system) you should consider changing hardware.

I didn't run into such problems as i simply put an old xbox 10GB hard drive in that g3, replacing the ultra "noisy" scsi original hd.

My final g3 linux setup runs fine, i decided to stick to lxde, substituted pcmanfm which doesn't have a trash (!), with thunar and removed the login manager, making it autologin to a single user.

Surprisingly today's huge applications do run, such as firefox 3.0 or openoffice, although they do take 30 sec to open..
I also managed to get the sound/mp3 working, internal speaker works too :)

Looks like it's not really capable of playing any kind of recent divx/xvid videos and most media player will crash, tried vlc or mplayer, i put that on the old ppc arch maybe not fully compatible with nowdays compilers those ppc packages are based on.. I didn't try to build them myself.

The one thing that is missing pretty badly is any kind of decent macromedia flash support, although you probably couldn't play a youtube video even SD, it can be quite useful in some cases for streaming audio and websites menus.

Anyways it was more than enough in my case to get a mail client running and access critical web pages. So, thank you linux powerpc :)

---

### Post by themacmeister on 2009-10-20
Great to hear,

The slower G3 isn't a patch on the G4. If I had a mirror face G4 tower, with a 1.2GHz cpu - that equates to roughly a 2GHz CoreDuo. You can do everything with those, and newer PPC distros will work on them OOTB!

I have had to dump OSX86 in favour of Mint Linux, as I am doing some coding (hopefully) for an Open Source project. Will take a while :)

Cheers.

---

### Post by allinfo on 2010-07-13
I am trying to do the same thing with Power Mac 9500 (Os 9.1) but I have no disks for the operating system.  So got nowhere yet.  Maybe a way around it?

---

### Post by linuxopjemac on 2010-07-14
There is one Classic MacOS to download.
[http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.5_Version_7.5.3/](http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.5_Version_7.5.3/)
[http://lowendmac.com/macos.shtml](http://lowendmac.com/macos.shtml)

---

