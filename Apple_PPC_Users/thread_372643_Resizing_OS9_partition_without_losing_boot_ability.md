---
title: "Resizing OS9 partition without losing boot ability"
date: 2007-02-28
forum: Apple PPC Users
---

### Post by RosaireOuellet on 2007-02-28
Hi everyone !

I received an old Imac rev.C (G3/266 with 288MB RAM) and it is installed with OS 9.2.2

I tried the Xubuntu live-CD (Dapper Drake) and it runs pretty slow. I'd like to try installing Xubuntu on the HD but I'd like to keep the OS9 as a dual boot and don't want to lose the data on it.

Is there a way to resize partitions to make room for Xubuntu ?

Thanks in advance !

P.S., I don't have any install CD or MAC OS CDs.

---

### Post by grazie on 2007-02-28
gparted on the desktop cd can resize hfs partitions, but not hfs+. If you've got hfs+ I suggest turn journaling off on OS9 to switch to hfs. You shouldn't have any problems, but if you don't have a backup of you data there is an element of risk.

---

### Post by RosaireOuellet on 2007-03-01
Hi!

I tried to use Gparted from the live-CD and the partitioning went ok all along without an error.

But as I feared, I am now unable to boot from the OS9 partition.

When booting the iMac, I got the white screen and then the floppy icon with a flashing questionmark on it.

I am still able to boot Xubuntu from the live-CD (by pressing the C-key on boot). What should I do to render the OS9 partition bootable again ?

Thanks !

P.S., I didn't try to install Xubuntu yet, I'd like to fix the OS9 partition first.

---

### Post by rccharles on 2007-03-01
> **RosaireOuellet said:**
> Hi!

I tried to use Gparted from the live-CD and the partitioning went ok all along without an error.

But as I feared, I am now unable to boot from the OS9 partition.

When booting the iMac, I got the white screen and then the floppy icon with a flashing questionmark on it.

I am still able to boot Xubuntu from the live-CD (by pressing the C-key on boot). What should I do to render the OS9 partition bootable again ?

Thanks !



You might try pressing down the control key ( or alt key on a pc keyboard ) when you poweron the machine.  This will bring up the Mac boot manager.

Look up info on blessing or bless system folder. Not sure you can do this without Mac OS media.

Robert

---

### Post by 3rdalbum on 2007-03-03
> **rccharles said:**
> You might try pressing down the control key ( or alt key on a pc keyboard ) when you poweron the machine.  This will bring up the Mac boot manager.

The key is "Option", but that Mac is too old to have it.

---

### Post by ristosu on 2007-03-03
You could try to point Open Firmware directly to your Mac OS boot code:

1. About 1 s after chime, press (and hold) Cmd-Opt-O-F.

2. Enter: boot hd:,\System%20Folder\Mac‰20OS‰20ROM

Depending on the language, the names may vary, use 'dir hd:,\' to check. To point to partition 5, use 'dir hd:5,\' and 'boot hd:5,\...'. It's usually between 5 and 10.

If you get in, you could try to set startup disk via control panel.

---

### Post by fkdev on 2007-03-04
This may fix it:
1. Get your mac os 9 install cd
2. boot it up, go to disk application
3. select your os 9 partition
4. select install drivers (it's in the menus)

---

### Post by rccharles on 2007-03-04
> **fkdev said:**
> This may fix it:
1. Get your mac os 9 install cd
2. boot it up

This brings back a memory...
1. Get your mac os 9 install cd
2. boot it up

3. The install cd will let you set startup disk via control panel.
4. I think you can bless a folder too.

....

I do not think you have a startup disk :( 

eBay to the rescue.

Mac OS 10.2 or 10.3 will run on your system.

Robert

---

### Post by RosaireOuellet on 2007-08-02
Anyone got new ideas about how to render the OS9 partition bootable without the OS9 CD ?

I got ubuntu running fine but when I try to boot on OS9, I got the floppy with flashing questionmark.

Help would be appreciated !

Thanks !

---

### Post by ristosu on 2007-08-03
Can you see the OS9 partition and its contents from within Ubuntu?

---

### Post by pxwpxw on 2007-08-03
Could you post the output from ubuntu terminal running these commands
```

 sudo nvsetenv
 sudo mac-fdisk -l
 cat /etc/yaboot.conf

```

It is possible to add an open firmware path to macos in yaboot.conf.

---

### Post by RosaireOuellet on 2007-08-05
Nice Sunday everyone !

I think I forgot to specify I installed the Xubuntu Dapper Drake on that computer.

As for the previous question, I cannot access the Mac OS9 files from Xubuntu but I can see the partition with Gparted.

Also, here's the result of the three commands as asked:

1st command: sudo nvsetenv

little-endian?=false
real-mode?=false
auto-boot?=true
diag-switch?=false
fcode-debug?=false
oem-banner?=false
oem-logo?=false
use-nvramrc?=false
use-generic?=true
default-mac-address?=false
real-base=-1
real-size=-1
load-base=0x800000
virt-base=-1
virt-size=-1
pci-probe-mask=-1
screen-#columns=100
screen-#rows=40
selftest-#megs=0
boot-device=/pci@80000000/mac-io@10/ide@20000/disk@0:7,\\:tbxi
boot-file=
diag-device=floppy
diag-file=diags
input-device=keyboard
output-device=screen
mouse-device=mouse
oem-banner=
oem-logo=
nvramrc=
boot-command=mac-boot
fw-scsicfg=
fw-boot-path=
default-client-ip=
default-server-ip=
default-gateway-ip=
boot-script=
boot-args=
ASVP=0110??01063;
forced-boot=

2nd command : sudo mac-fdisk -l

/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2        Apple_Driver_ATA Macintosh                54 @ 64       ( 27.0k)  Unknown
/dev/hda3        Apple_Driver_ATA Macintosh                74 @ 118      ( 37.0k)  Unknown
/dev/hda4      Apple_Driver_IOKit Macintosh               512 @ 192      (256.0k)  Unknown
/dev/hda5           Apple_Patches Patch Partition         512 @ 704      (256.0k)  Unknown
/dev/hda6               Apple_HFS Macintosh HD        6144001 @ 1216     (  2.9G)  HFS
/dev/hda7         Apple_Bootstrap untitled               1954 @ 6145217  (977.0k)  NewWorld bootblock
/dev/hda8         Apple_UNIX_SVR2 untitled            6105469 @ 6147171  (  2.9G)  Linux native
/dev/hda9         Apple_UNIX_SVR2 swap                 342320 @ 12252640 (167.1M)  Linux swap

Block size=512, Number of Blocks=12594960
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 21, type=0x701
2: @ 118 for 34, type=0xf8ff

3rd command: cat /etc/yaboot.conf

## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda7
device=/pci@80000000/mac-io@10/ide@20000/disk@0:
partition=8
root=/dev/hda8
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macos=/dev/hda6

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"

End of commands results.

As you can see, I already modified yaboot to boot on the macos partition (hda6) but I still only get the floppy icon with a flashing questionmark.

Here's also a recap of what I did on the computer to date.

- I backed up all really important files from the MacOS9 partion.
- I booted from the like Xubuntu CD.
- I resized the MacOS9 partition to make room for the Xubuntu installation.
It is at this point that MacOS9 refused to boot and showed the floppy with questionmark,
- I booted again on the Xubuntu live-CD and installed Xubuntu on the hard drive.
- I edited the file Xorg.conf to adjust the refresh rate of the screen (and disable dri)

Since then, I used Xubuntu without a glitch but I'd really like to be able to boot again in MacOS9. Even if I backed up important stuff, I was unable to back already installed programs and I don't have installation disks for these programs, nor for the MacOS9 system.

As for purchasing OS9 disks, I didn't find any French OS9 disks anywhere and even the English ones are way to pricey IMO.

To finish my recap, here's my computer's specs :
Blueberry iMac G3/266, 288 Mb ram, 6 Gb hd, tray loading CD-ROM, Macally Apple Keyboard and Logitech USB mouse (2 buttons and scroll wheel).

I'll wait for your answers (thanks for the big help),

Rosaire Ouellet

---

### Post by pxwpxw on 2007-08-06
As I understand it, you have xubuntu606 installed and running well on the hard disk,
but when you try to run macos (how?), it wont go. I am not sure about this.

Your post above, boot-device , partitions, and yaboot.conf with macos=/dev/hda6, all seem correct. Installing yaboot has just changed the boot-device to hda7.
You could change it back manually but dont do that until we see if macos is broken.

To update the actual bootfiles on hda7 with the macos=/dev/hda6 setting option, you must run ybin in your installed xubuntu system.

In the installed xubuntu, in a terminal
```

sudo ybin -v

```
This should give you a small first stage text menu selection for linux, or macos.
If macos is still intact, it should run from that.

Alternately, you should also be able to run macos using startup keys (this info from original imac data, hopefully correct also for all the tray loading imacs including the 5 color)
 --- edit: maybe not for Rev C.

Hold down during startup: 
  Key combination Command-Option-Shift-Delete: 

(This ignores the boot-device setting and scans for alternate devices).

However you may have done all that, as I am not sure if the problem came after you first resized the macos partition, but before you installed anything, 
I dont think that should have damaged anything for macos at that stage. 

 If you cannot get macos started, you can access macos HFS files from xubuntu by mounting the macos partition, you may need to install hfsplus file system utility.

---

### Post by Bikerbob on 2007-08-06
Also as a NOTE.. and only for information.

Since you have a working OS on the machine.. and if you had access to a CDR burner that you could use with it(external?) then you could get OS 8.6 off of the net easy enough.. most consider the oldest upgradeable Mac OS.
You could burn this, boot it, archive and install and then get that partition back up to os 9 with updates from apple.com

I have had a little experience with re-sizing partitions, and so far... none of it good. You needed to have run all your disk utilities first, and defraged the drive (no built in utility in os 9 for that)  THEN you might have succeeded in resizing it. Gparted might move data when it resizes...(not even sure of that) but it has no way of informing the mac OS where it put the data fragments when it moved it.. Most likely part of the system itself has been scattered, and only a reinstall of a MAC OS will restore it. 
Using archive and install should save a lot of what was on the disk. As a direct answer to the question - I think at this point you are NOT going to be able to re-activeate that partition without an OS CD.

James

---

### Post by 3rdalbum on 2007-08-08
1. You cannot update from Mac OS 8.6 to 9 through internet updates.

2. This situation happened to me a little while ago - I tried resizing the existing Linux swap partition ( I did NOT touch any of the other partitions! ), and the Mac OS wouldn't start up. If you booted up a Mac OS CD, you would find that the Mac OS wouldn't be able to mount its own partition either. Drive Setup did detect the partitions, but of course it wouldn't mount them.

I ended off erasing the entire hard disk and restoring the Mac partition onto the entire disk from my backups. It wasn't my computer, and the owner was going to need to use his Mac programs the following morning, so I didn't have time to find a non-destructive solution (especially when I didn't know if there was one).

Send me a Personal Message - by the time I recieve it I may have thought of some options for you.

---

### Post by RosaireOuellet on 2007-08-08
Thanks everyone for your answers !

Even if none resolved the problem, I'm still hoping to get the miraculous message that will bring the solution !

I tried everything that got suggested since my last post and none of it seems to work.

The command+option+shift+delete combination don't work on rev.C and older macs in accordance to many other users (and neither on my mac).

I already used the ybin command to register the modifications in yaboot.conf and I also was getting the boot menu with choices C, L and M (this is how I tried booting on the hda6 partition) but I still can't get it to boot.

As for getting an older MacOS from the net, I don't think it is a good idea unless I could repair the OS9 partition with it. BTW, the latest full system available from Apple website is the 7.5.6. Other downloads are just upgrades and cannot be used to install on a fresh partition.

Like I said earlier, I want to repair the MacOS9 partition because I don't own the installation CDs for that OS and I'd like to keep the programs that were already installed on the computer when I received it. If I can't repair that OS, I'll probably erase the OS9 partition and use exclusively Xubuntu.

For those curious, the MacOS9 system on my computer is a french version. I had Microsoft office 2001 professional for Mac (french), Adobe Acrobat professional (French) and Adobe Photoshop (French, I don't remember version number). And a small number of games (mainly cards and also VGS) installed. You can easily see that all those programs are very hard to find   and most likely discontinued anyway....

Don't give up, I'm still searching for a solution and still get my hopes up !

Rosaire Ouellet

---

### Post by pxwpxw on 2007-08-08
That is sad news, macos9 seems to be unbootable by normal methods. 
I would try the suggestions by **ristosu ** to boot diectly, 
 ( your macos9 is at  hd:6,\ ), 
  you can see file listings from openfirmware using the "dir" command 
  0> dir hd:,\  or hd:6,\  or hd:6,\\ 

 Might permit some repairs if it boots, but I dont know if that works for macos9 and your mac firmware.

 I would also manually mount the macos partition using a terminal in ubuntu, to see if there are any files there to boot. The installer may have wiped the partition.

But realisticly, you would need a macos9 install CD to maintain your macos9, even then the only option may be to repartiton, which does not help much, although you could save some applications to an external drive or usb flash stick. Last macos9.1 cd I bought cost us$40 from AppleRescue, but their site (applerescue.com) seems to have died. 

I do not know if ubuntu may use some of the Apple_Driver and other partitions (hda2..hda5), you need to get further advice before doing any complete repartition of the whole hard drive from ubuntu install. Probably someone has done that.  

The macos9 partition hda6 would make a nice /home partition for ubuntu.

---

### Post by RosaireOuellet on 2007-08-17
Hello everyone !

Just to summarize, let's say that I tried everything I could think of (booting from firmware, zapping pram, nvram, mounting the partition on Xubuntu, etc...) and absolutely nothing works.

Then, I just declared that OS9 is dead and really dead on my computer.

I am now happy to announce that my blueberry G3 is now a complete Xubuntu machine :KS

Thanks to everyone who helped me on this thread, even if we weren't successful, your help was greatly appreciated !!!

Good night everyone.

Rosaire Ouellet

---

### Post by msinkm on 2008-02-19
I was just about to declare the resized Os 9 partition dead, but I thought I'd try the good old Norton Utilities 6.0 cd to see what I could do with the partition.  I had used speed disk on this cd to prepare the partition for resizing.  Then, I booted from the live CD for Feisty and shrunk the hfs+ partition with gparted. Then, of course, I had the same problem Rosaire had -- blinking question mark when I tried to boot into the Mac os.  I had Norton do its check, and it fixed some things that gparted should have -- special files indicating the size of the partition, etc.  Still, it could not mount the partition, but it made mention of the disk drivers, so I booted with the mac OS9 restore disk, and used drive setup to update the disk drivers.  This made the partition bootable, but as soon as I could get to the desktop, I made sure to go directly to the updated drive setup application and updated the drivers again, because the original disks with 9.0.4 had different disk drivers that the 9.2.2 which was on there.  

So far, so good.

---

