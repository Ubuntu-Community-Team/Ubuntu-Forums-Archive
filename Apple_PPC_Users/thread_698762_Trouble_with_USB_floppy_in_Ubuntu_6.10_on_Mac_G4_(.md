---
title: "Trouble with USB floppy in Ubuntu 6.10 on Mac G4 (PPC)"
date: 2008-02-16
forum: Apple PPC Users
---

### Post by Dudewhoa on 2008-02-16
Hi, after hours of searching the Internet and reading posts, and experiencing with the SUDO MKDIR, SUDO MOUNT and SUDO FDISK commands, I am still unable to get my USB Floppy to work on my system. As a reminder Its a New World Mac G4 (PPC architecture.) The information I read thus far, as I am thinking to believe, is that everything I read is related to x86 and vfat? Have I missed something already posted? Can someone please show me what i missed.

I went into device manager in Ubuntu and the USB floppy _***IS***_ recognized. I even hot plugged it to verify the icon for it would disappear and reappear, when unplugged and plugged in respectively into the keyboard.

Which also makes me ask, does it matter if i plug the drive into the keyboard (where all previous experimenting was done) or on the back of the machine itself?

If the moderator believes this is a double-post of someone else's then I apologize in advance as I could not find (or at least understand) enough information to get this to work.

THANKS!
(p.s. I am a noob...and so far I know more about Ubuntu than Mac OS to give you an Idea on my level of expertise... Just a matter of finding the right packages and how to do stuff. Any terminal command lines, or anything else,  to get the floppy to work will be greatly appreciated!)

---

### Post by stream303 on 2008-02-16
I'm using Feisty, and this is what works for me.  When using floppy drives, I like to treat them like hard drives, that is put in the floppy before you attach it, and leave it in the drive when you unmount it.  Sometimes this isn't necessary, but it is an old habit here.

With my teac usb floppy, after it gets attached I mount it to the /mnt directory like so:

**```
sudo mount -t vfat /dev/sdb /mnt
```**

now cd to /mnt and do whatever you need to do.

When you are done, be sure to cd OUT of the mount, just cd'ing to home will do

Then to unmount it, 

[B]```
sudo umount /dev/sdb

```[/B]
remove device.

Lets see if this works for you on 6.1

It works fine in the gui, but this is the cli way to do it.

If you have more than one hard drive, *take a look at the tail end of dmesg when you attach the floppy *and you may have to change it from /dev/sdb to /dev/sdc and so on.

---

### Post by stream303 on 2008-02-16
As a side note, if you want to manually mount a usb-key from the commandline it is similar, but you have to specify the partition number as well on the key aka:
[B]```

sudo mount -t vfat /dev/sdb1 /mnt
```[/B]

similarly, to unmount you have to specify the partition #1 once you are cd'ed out of the mount directory:

**```
sudo umount /dev/sdb1
```**

Sometimes you might have to play with the partition number - I had to use sdb4 once on a weird usb key.

---

### Post by Dudewhoa on 2008-02-16
OK, here's what I did.

s010608@s010608-desktop:~$ sudo mount -t vfat /dev/sdb /mnt
Password:
mount: special device /dev/sdb does not exist
s010608@s010608-desktop:~$ 
s010608@s010608-desktop:~$ sudo mount -t vfat /dev/sdc /mnt
mount: special device /dev/sdc does not exist
s010608@s010608-desktop:~$ 

Perhaps there's something missing from the FSTAB. hold on...let me get that...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=9bb28a33-df2b-482b-8abe-68f4464269bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=4cff0bbc-c7c2-4172-8954-6474d516c6cd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

what a mess. That's exactly how it is in my fstab. I hope the info's easy enough to read!

The machine has 2 IDE fixed disks, HDA and HDB. I am still yet to figure out how to SUDO MKFS the HDB. It does have a FAT32 partition on it now. But, right now I'd like to get the floppy to work first...my SUDO FDISK info:

/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           78921876 @ 2018     ( 37.6G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                1494346 @ 78923894 (729.7M)  Linux swap

Block size=512, Number of Blocks=80418240
DeviceType=0x0, DeviceId=0x0

s010608@s010608-desktop:~$

---

### Post by stream303 on 2008-02-16
This might help.  Just be very careful with fdisk!

To see what is currently mounted, just type **mount** without any parameters.

So you have a second hard drive, and also a floppy drive, and you want to be able to mount the floppy, and then format the second hard drive later?  Let's get the floppy working first.

For simple file copying, you shouldn't need to format the floppy, and just leave it as is with the microsoft format on it.

When you attach the usb floppy with the floppy in the drive beforehand, what does

```
dmesg | tail
```

show?  This will give you an idea of what /dev/sdX should be, with X being what dmesg is turning up.

If the floppy is in the older microsoft format, you may change the filetype:

```
sudo mount -t msdos /dev/sdc /mnt
```

(sdc is an example, dmesg will guide us)  Maybe later we can tackle the second hard disk format.

Do you have a gui available?  GPARTED can come in handy for the second drive  (not that we can't do it from cli, but it's good to know...)

---

### Post by Dudewhoa on 2008-02-16
Here's my MOUNT info

s010608@s010608-desktop:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-12-powerpc/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
s010608@s010608-desktop:~$ 

here's that DMESG | TAIL. That's a pipe between the two commands, right? Because It doens't show anything about any DEV's. Looks like network info.

s010608@s010608-desktop:~$ dmesg | tail
[ 1518.060620] eth0: Pause is disabled
[ 2149.257658] eth0: Link down
[13653.605801] eth0: Link is up at 10 Mbps, half-duplex.
[13653.605815] eth0: Pause is disabled
[24328.757502] eth0: Link down
[25117.154037] eth0: Link is up at 10 Mbps, half-duplex.
[25117.154050] eth0: Pause is disabled
[25162.753735] eth0: Link down
[25297.153224] eth0: Link is up at 10 Mbps, half-duplex.
[25297.153239] eth0: Pause is disabled
s010608@s010608-desktop:~$ 

trying that SUDO MOUNT with microsoft fs....

s010608@s010608-desktop:~$ sudo mount -t msdos /dev/sdc /mnt
Password:
mount: special device /dev/sdc does not exist
s010608@s010608-desktop:~$ 

As for GUI I have GNOME desktop, I think that's what's It's called. Through my research i found about that GPARTED in the Synaptic and it worked flawlessly. Just no file system on the drive.

---

### Post by Dudewhoa on 2008-02-16
Please pardon my double post, but, I discovered this when I typed DMESG with no parameters:

[34766.394884] usb 2-1.3: new full speed USB device using ohci_hcd and address 5
[34766.545008] usb 2-1.3: no configuration chosen from 1 choice

Does anyone know what this means?

---

### Post by Dudewhoa on 2008-02-17
OK Check this out: I just discovered this command that will show some important information regarding the USB Floppy disk:

s010608@s010608-desktop:~$ lsusb
Bus 002 Device 005: ID 0644:0000 TEAC Corp. Floppy
Bus 002 Device 003: ID 05ac:0204 Apple Computer, Inc. 
Bus 002 Device 002: ID 05ac:1002 Apple Computer, Inc. Apple Extended Keyboard Hub [Mitsumi]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c402 Logitech, Inc. Marble Mouse (2-button)
Bus 001 Device 001: ID 0000:0000  
s010608@s010608-desktop:~$ 

As you can see, the USB Floppy is Device 5 on Bus 2. Now all I need to find out is how to "DEV" it. Because MOUNT will always come up with "DEV does not exist" so I'll let you guys know when I get more information on this...so maybe just a few more hours of searching and reading...lol

---

### Post by stream303 on 2008-02-17
Well, I'll be honest and say I'm stumped too, although it appears that the big problem is not device specific, but might be automounting.  Normally there's not much need to manually configure fstab these days.

Don't tell anyone, but at this stage, I think the fastest road to recovery would be to reinstall. 

Maybe someone else can spot something.  I commend you on your willingness to dive in with the cli and not be tossing the box through the window. :)

---

### Post by Dudewhoa on 2008-02-17
It's quite fun, really. It must come from my x86 PC building background I got so many years ago and all that Microsoft Windows trouble shooting I did back then. Yip, Windows can also be a pain in the @$$ despite what the "lovers" say. So at this point I could either reinstall, or manually configure fstab. I'd rather go the long way around and find out what is causing this. Then you can look back at this thread if you ever get another box and put the usb floppy over there and have this kind of trouble.

It must be fstab. Now I have to find out WHAT to put in fstab. Thanks for the info.

---

### Post by Dudewhoa on 2008-02-17
Take a look at my fstab now.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /dev/sdb1 	/mnt/floppy	auto  rw,noauto,user,sync  0       0
# /dev/fd0 	/mnt/floppy	auto  rw,noauto,user,sync  0       0
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=9bb28a33-df2b-482b-8abe-68f4464269bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=4cff0bbc-c7c2-4172-8954-6474d516c6cd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

As you can see, I added both, fd0 and sdb1 so just in case one of them didn't mount, I could try the other. but now I am STILL getting the DEV doesn't exist message on both. Even when I log in as root and use the FDMOUNT command, still doesn't work!!

I am starting to think that re-install is the best choice, as stream suggested. Unless of course if anyone else out there has something that we haven't thought of yet. I'll give this thread a few days, see if anyone posts.

Right now I feel like playing that same GNOME game. (GNOME desktop Ubuntu 6.10.) Maybe ideas will jump in my head while I do that.

---

### Post by Dudewhoa on 2008-02-17
An idea just came to mind regarding this whole setup I got goin' on here:
Before, I mentioned I couldn't mount my second fixed disk as well. Take a look at what I recently did:

s010608@s010608-desktop:~$ sudo mount -t ext3 /dev/hdb1 /mnt/test
Password:
s010608@s010608-desktop:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-12-powerpc/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /mnt/test type ext3 (rw)
s010608@s010608-desktop:~$ 

There's the second disk listed on the bottom line, which was successfully mounted. But, however, /DEV/HDB1 is **NOT** listed in fstab!!! So now I'm thinking to myself, "WTF!?" There has got to be something I need to load, in synaptic or elsewhere, that will make this flippin' floppy show up as a DEV.

1. Logging into ROOT and typing FDMOUNT in the terminal will return a "FD0 does not exist."
2. Floppy Is USB so perhaps it may need to be mounted as a SDB. (like a SCSI disk)

system did NOT crash when I modified fstab under ROOT

---

### Post by Dudewhoa on 2008-02-17
I found some more articles and I have come to the conclusion, that, in order to get this drive to work is that I must have:

kernel SCSI support

(go figure, /DEV/**_SDB_** for USB floppy!?!?) So, I guess that means I either need to recompile the kernel, or

Re - in - stall

Interesting. Yip. OK...

BRB!

---

### Post by Dudewhoa on 2008-02-20
Re-install didn't work. I even added an Adaptec AIC-2940UW (vintage?) host controller to the box before I reinstalled. That was it, i've been at school, really hadn't set any time to working on this box further than that. Without doing any searches to make certain about this statement: I think this USB floppy (TEAC FD-05PUW) doesn't work with this distro. (All this work over a stinkin' floppy drive...)

---

### Post by stream303 on 2008-02-20
Ok, didn't know that your drives never worked.  What is the exact model of your G4 mac?

[http://www.everymac.com](http://www.everymac.com)

When adding / removing hardware from a Mac, I've heard it is best to zap your pram, and possible do a smu/pmu reset before install.

Is your controller actually mac-compatible?

You may want to try installing with the least amount of peripherals attached, and attach them afterwards.

You could also try the "alternate" install of Feisty.

Secret: what you're learning is actually more important than getting that drive working. :)

---

### Post by Dudewhoa on 2008-02-20
Oh, the scsi card worked like a charm. I plugged the USB drive into my windows box, but since my windows box is very old It didn't install the drivers for it automatically, It just recognized it. I added he scsi card and the Seagate ST410800N so Linux could actually see some "SD" disks. As for the mac, It looks exactly like the one in this picture:

[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_733_qs.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_733_qs.html)

I looked at the configuration listed on that page, and it very closely matches the box. Differences include someone upgrading the RAM,  (before I got the box) and this one is a model M8493.

But what you mentioned sounds like some good things to try. This is, after all, the first Mac I've extensively used since the monochrome green Mac with the 2 - 5/1/4" floppy drives I used in high school (In 1993); so learning curve, certainly.

---

### Post by paxswill on 2008-02-20
Could it be that for the floppy to operate properly, it needs to be plugged in to a normal, powered USB port? As far as I know, most of the hubs in Apple keyboards are unpowered. Try plugging the drive in the back of the computer, and see if that helps. Also, if you didn't have SCSI disk support, wouldn't all USB flash drives not work as well?

---

### Post by stream303 on 2008-02-21
I'm also getting confused on what the hd is, and what card it is using.

If it is the original apple hd card, I believe that your model of Mac is limited to no more than 128gB partition for *nix.  At least for the boot and root partitions if you go custom.  Call it 125gb to be safe.

---

### Post by Dudewhoa on 2008-02-21
HDA is the fixed disk that came with the unit. My friend gave me another IBM 40G and I put that one in and that is HDB. The external (I disconnected it for now, it sounds like a turbine engine and drives me nuts to let it run all the time) SDA is the Seagate 5/1/4" drive (was) connected to the Adaptec 2940. You guys know what you get when you type DMESG so I only put in parts of it: (This is after I swapped the mouse and the floppy as paxswill suggested, there are only 2 USB ports on the machien itself, and the keyboard is a USB model. I'll try to mount the floppy again after this post.)

s010608@s010608-desktop:~$ lsusb
Bus 002 Device 005: ID 046d:c402 Logitech, Inc. Marble Mouse (2-button)
Bus 002 Device 003: ID 05ac:0204 Apple Computer, Inc. 
Bus 002 Device 002: ID 05ac:1002 Apple Computer, Inc. Apple Extended Keyboard Hub [Mitsumi]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0644:0000 TEAC Corp. Floppy
Bus 001 Device 001: ID 0000:0000  
s010608@s010608-desktop:~$ dmesg
[   36.131209] ide0: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
[   36.131242] Probing IDE interface ide0...
[   36.419502] hda: IBM-IC35L040AVVA07-0, ATA DISK drive
[   36.699495] hdb: IC35L060AVV207-0, ATA DISK drive
[   43.424620] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   43.424636] Uniform CD-ROM driver Revision: 3.20

the USB floppy:

[ 1879.048574] ohci_hcd 0001:10:18.0: wakeup
[ 1879.431833] usb 1-1: new full speed USB device using ohci_hcd and address 3
[ 1879.682986] usb 1-1: configuration #1 chosen from 1 choice
[ 1880.025247] usbcore: registered new driver libusual
[ 1880.153995] Initializing USB Mass Storage driver...
[ 1880.155242] scsi1 : SCSI emulation for USB Mass Storage devices
[ 1880.156501] usb-storage: device found at 3
[ 1880.156510] usb-storage: waiting for device to settle before scanning
[ 1880.156545] usbcore: registered new driver usb-storage
[ 1880.156554] USB Mass Storage support registered.
[ 1885.155874] usb-storage: device scan complete
[ 1885.178876]   Vendor: TEAC      Model: FD-05PUW          Rev: 3000
[ 1885.178907]   Type:   Direct-Access                      ANSI SCSI revision: 00

The SDA drive:

[   58.411141] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   58.411150]         <Adaptec 2940 SCSI adapter>
[   58.411153]         aic7870: Wide Channel A, SCSI Id=7, 16/253 SCBs
[ 1901.659272] sd 1:0:0:0: SCSI error: return code = 0x8000002
[ 1901.659288] sda: Current: sense key: Medium Error
[ 1901.659295]     Additional sense: Unrecovered read error
[ 1901.659309] Info fld=0x19
[ 1901.659314] end_request: I/O error, dev sda, sector 24
[ 1901.659323] Buffer I/O error on device sda, logical block 3

(This is because I disconnected the SCSI drive)

Ok...editing the post...could you guys check to make sure I am typing the command correctly?

s010608@s010608-desktop:~$ sudo mount -t vfat /dev/sdb /media/floppy
Password:
mount: special device /dev/sdb does not exist

---

### Post by Dudewhoa on 2008-02-22
Umm, guys...I got it to work. This is quite a long story, but I'm going to tell it anyway:

I was minding my own beeswax, OK? then this dialog pops up on the upper right corner of the screen where the clock was telling me that updates are available for my system. OK. click on it. Download updates. no prob. Then there was this option to upgrade to version 7.04 Feisty Fawn, or something in that matter, within the updates dialog box. OK. Let's do that. Downloads, sets up packages and all that, OK. Need to reboot system. Great. I reboot. Now it's telling me that the X System failed to load and gives me the option to examine the version, make sure I go to wiki.x.org and make sure I have the latest version and all that, then It gives me no choice but to use the command prompt. Ok, I didn't really feel like finding out how to access the Internet from the command prompt, so I just said, 'I guess, whatever, I'll just reinstall the version I had on it before.'

Put the disc in and booted from HDC (the CD-Rom.) and I was running the live version. Here's the good part: when the installer gives me the option of choosing which device I'd like to install Ubuntu on, It gave me 3 choices: first and second fixed disks HDA and HDB, or SDA the floppy. So I was like :cool: and did a quick check in terminal: SUDO MOUNT -T VFAT /DEV/SDA /MEDIA/FLOPPY and it worked for the first friggin' time. (and I WAS typing it right.) =D> When I did that, a floppy disk icon popped up on the desktop. What's that? double click on it, light on the floppy comes on and showed the contents of the disk I had on there. It was friggin' sweet knowing the damn thing actually works with this box!

So after I got the system installed (again) the effect was permanent. Floppy works. I suppose Stream and Paxs both get credit for that...I reinstalled the system with the floppy plugged into the box, not the keyboard, and It worked. But somehow my mouse works great when I plug it into the keyboard, It's just a Logitech Marble Mouse. Ironic, huh.

It would appear as Linux in general treats USB storage devices as SCSI devices, hence the "SDA" name for the external floppy. So with the Adpatec 2940 card installed in the box, Linux automatically loads USB support as well. This is good news.

---

### Post by stream303 on 2008-02-26
Wow I just went through this on a friend's machine.  I don't know how he did it, but be sure to check the prefs

System > Preferences > Removable Drives and Media

and check that the system will mount and optionally browse the media when detected.

---

### Post by Dudewhoa on 2008-02-28
Ah, those were already enabled when I checked. Alternatives to those choices would be making sure media is in the drive before you plug it in. I also just confirmed that your friend did not plug the drive into the keyboard, like I was doing. This same thing also applies to the USB Zip 250 (yeah, who uses those anymore...? Well, me since I still use floppy disks) I just tried. Something like those, as well as other big *** items like HP office jets and fixed disks I can rest assured that they will not work if you plug them into the keyboard.

I also tried plugging the floppy into a hub connected to that same port on the box with no transformer, and "/dev/sda did not exist." So with that being said, it's only obvious that the USB ports on the keyboard are generally used for small things that don't require a transformer like mice and those stick-of-gum sized drives that can hold 1 or 2GB's of data on them. So In order to use everything else, a USB hub with the transformer is required. Unless, of course, you have more than 2 USB ports on your box.

---

