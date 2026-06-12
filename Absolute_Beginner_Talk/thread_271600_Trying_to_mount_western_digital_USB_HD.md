---
title: "Trying to mount western digital USB HD"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by bstreet85 on 2006-10-04
Hi,

I'm new to Linux and was trying to mount my USB hard drive, but can't get it to come up. I've tried looking around to see if it's even been detected, but haven't had any luck (could be I don't know right commands, etc). Any help would be greatly appreciated. I'm running Dapper Drake on an IBM T40 laptop.

---

### Post by bodhi.zazen on 2006-10-04
> **bstreet85 said:**
> Hi,

I'm new to Linux and was trying to mount my USB hard drive, but can't get it to come up. I've tried looking around to see if it's even been detected, but haven't had any luck (could be I don't know right commands, etc). Any help would be greatly appreciated. I'm running Dapper Drake on an IBM T40 laptop.

Start by finding your (USB) partition:```
sudo fdiak -l
```

next make or select a mount point, mount.

```
sudo mkdir /media/usb
sudo mount -vfat /dev/sda1 /media/usb -o users,rw
```

To make it permanent, you would need to edit fstab.

[[color=blue]fstab[/color]](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by bstreet85 on 2006-10-04
When I run "sudo fdisk -l" it lists the partitions, but the problem is that the external HD doesn't come up as a partition. I don't think Linux is detecting it.

---

### Post by bodhi.zazen on 2006-10-04
> **bstreet85 said:**
> When I run "sudo fdisk -l" it lists the partitions, but the problem is that the external HD doesn't come up as a partition. I don't think Linux is detecting it.

That would be the problem then. What usb drive (?model number)?

What little I could find on google indicated there was no driver for this USB HD.

? contact Western Digital.

---

### Post by bstreet85 on 2006-10-05
The other thing that bothers me about this is that I used to run Kubuntu, which detected the drive, but when I switched to Ubuntu (my school has someone that supports Ubuntu on staff) I started having problems...

---

### Post by bstreet85 on 2006-10-05
Anybody have any idea if I can look to see if Ubuntu's even reading the USB connection from the drive?

---

### Post by Josey on 2006-10-05
Thats strange. Ubuntu Dapper 6.06 detected my usb western digital 120 gb and threw some new icons on the desktop for it.

It sounds silly but try a different usb port. It's worked for me before :-?

---

### Post by zool2005 on 2006-10-13
> **Josey said:**
> Thats strange. Ubuntu Dapper 6.06 detected my usb western digital 120 gb and threw some new icons on the desktop for it.

It sounds silly but try a different usb port. It's worked for me before :-?

Was that a WD "My Book" drive?

Thanks

---

### Post by Prologue on 2006-10-18
I just purchased a WD My Book 250gig essential. I'm running 6.06 on a HP Pavilion and I just plugged it and Ubuntu mounted it and allowed read/write.

---

### Post by mssever on 2006-10-18
With your drive plugged in, look in /dev/disks/by-id and see if there are any symlinks there that reference your drive. If so, use that to create an /etc/fstab entry. For example, here's a line from my fstab:
```
/dev/disk/by-id/usb-Seagate_External_Drive_SG060608423-part1 /media/EXTERNAL_HD vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 3
```The reason for using the above path instead of /dev/sdb1 (the actual location of the partition) is because the latter can change with removable devices. But the symlinks in /dev/disk/by-id always point to the proper location.

If your drive doesn't appear in /dev/disks/by-id, type ```
less /var/log/messages
``` then hit F (capital F). Watch when happens when you plug and unplug the drive and post anything relevant.

---

### Post by podunk on 2006-10-19
If I boot up with my USB drive pluged in - it isn't detected. So I just unplug it for a few seconds then plug it back in and it comes up and adds icons to my desktop.

---

### Post by Nuibkulnatsu on 2006-10-23
Mounting a drive through the use of the "by-id" link seems to be a good strategy of "mapping" the drive to a constant path.

Altough by doing this I get a second shortcut to the drive on the desktop! Does anyone know why this happen, I need only one shortcut!

---

### Post by monktbd on 2006-10-23
the OP's question is old so i guess it is solved but anyway

> **bstreet85 said:**
> When I run "sudo fdisk -l" it lists the partitions, but the problem is that the external HD doesn't come up as a partition. I don't think Linux is detecting it.

what does 
> lsusb
say when the disk is plugged? does the harddisk show up there?



> **Nuibkulnatsu said:**
> Mounting a drive through the use of the "by-id" link seems to be a good strategy of "mapping" the drive to a constant path.

Altough by doing this I get a second shortcut to the drive on the desktop! Does anyone know why this happen, I need only one shortcut!

the easiest way to have a consistent mounting with gnome-volume-manager is to label the partitions. 
if it is a fat32 partition you can do it under windows or with mtools (maybe gparted as well, dunno?), if it is a ext3/ext2 partition then with e2label.
i have two partitions on my external harddisk and since i gave proper labels i never had a problem of inconsistent mounting, they are always found under /media/mylabel.

---

### Post by Nuibkulnatsu on 2006-10-23
If for some reason I dont want to mount my usb drive, perhaps its unplugged for some reason, and instead I plug in my mp3 player then the mp3 player mounts to the usb drive mountpoint as it is refered to as /dev/sda.

Thats my problem, anyway this is solved by the use of mount by-id.

The thing I dont get is why there are two icons on the desktop!

---

### Post by monktbd on 2006-10-23
> **Nuibkulnatsu said:**
> If for some reason I dont want to mount my usb drive, perhaps its unplugged for some reason, and instead I plug in my mp3 player then the mp3 player mounts to the usb drive mountpoint as it is refered to as /dev/sda.

my harddisk never would mount to the standard names that are given if no label exists. 

in your case the mp3 mplayer would automount to the standard name given by gnome-volume-manager and the harddisks would still have their usual mountpoints denoted by their label. 


> 
The thing I dont get is why there are two icons on the desktop!

because you mount it via fstab (by-id) and gnome-volume-manager automounts it as well, that is what i think.

---

### Post by mssever on 2006-10-23
> **monktbd said:**
> because you mount it via fstab (by-id) and gnome-volume-manager automounts it as well, that is what i think.

According to the pmount man page, if a device is listed in /etc/fstab, it's mounted according to fstab and not the "regular" way. At any rate, I noticed that I have two icons on my desktop, as well. Not a big deal to me since I primarily access that machine via ssh, NFS, and various other servers. But I can see how it could be annoying.

You can see whether the drive is mounted more than once by typing mount at a command prompt. On my machine, the drive is only mounted once, despite the two icons.

---

### Post by monktbd on 2006-10-24
> **mssever said:**
> You can see whether the drive is mounted more than once by typing mount at a command prompt. On my machine, the drive is only mounted once, despite the two icons.

yeah that will probably be the case. dont know if it is at all possible to mount a partition twice.

i just remember having two icons as well for a partition when i put it in my fstab and also have gnome-volume-manager (gvm) stepping in.

i dont remember if both icons were working though.
all i remember is that i solved the problem with naming the partitions. because i dont have an mp3 player i dont know whether that would make an additional problem if i let gnome-volume-manager handle it or if i would need to handle it with the by-id solution. 
i also cannot remember right now if it is possible to remove the  automount possibility of gvm for external harddisk drives in the removeable media manager in the system administration menu.

---

### Post by mssever on 2006-10-24
Can you tell me how to set the label with mtools? The mtools man page assumes knowledge of DOS commands, which I don't have.

---

### Post by bodhi.zazen on 2006-10-24
> **mssever said:**
> Can you tell me how to set the label with mtools? The mtools man page assumes knowledge of DOS commands, which I don't have.

See this link. Near the bottom, in the labels section, is a how-to with mtools.

[[color=navy]How to fstab[/color]](http://ubuntuforums.org/showthread.php?t=283131)

See _FAT (Windows partitions)_ section.

---

### Post by mssever on 2006-10-24
Thanks. It appears that mtools is needlessly complicated (drive letters in Linux???). Oh well.

---

### Post by rdfx100 on 2006-10-28
So did the original poster get the Western Digital to work?

I think I'm having a similar problem with this new Wester Digital MyBook 500GB usb external drive.  It is not recognized, and I can't find a device that it's attached to.

I have several different usb ports, and 'dmesg' gives a similar 1 line response when I plug in the drive:
> [17206784.080000] usb 3-2: new full speed USB device using uhci_hcd and address 4
another usb port:
> [17207029.528000] usb 1-2: new full speed USB device using uhci_hcd and address 2
another usb port:
> [17207378.800000] usb 2-2: new full speed USB device using uhci_hcd and address 5

I think each time I do see a corresponding entry looking at 'lsusb', e.g.:
> Bus 002 Device 005: ID 0928:ffff Oxford Semiconductor, Ltd

However, I can't seem to figure out how to get a /dev/ device associated with it.  There is not an associated link in /dev/disk/by-id/.  Any suggestions?

---

### Post by bodhi.zazen on 2006-10-28
Plug in your usb drive and try by UUID:```
ls /dev/disk/by-uuid
```

Then:```
 sudo mount UUID=<number> <mount_point>
```

---

### Post by rdfx100 on 2006-10-28
There is no corresponding entry in /dev/disk/by-uuid/.  Everything there is for other drives I have.

---

### Post by Snocrash on 2006-11-05
Same problem here....

When I plug my Wester Digital Passport USB drive into my desktop, it does not get mounted.

dmesg gives:

[17180140.896000] usb 7-5: new high speed USB device using ehci_hcd and address 2
[17180162.552000] usb 7-5: new high speed USB device using ehci_hcd and address 3
[17180184.204000] usb 7-5: new high speed USB device using ehci_hcd and address 4
[17180184.740000] usb 7-5: device not accepting address 4, error -71
[17180248.600000] usb 7-5: new high speed USB device using ehci_hcd and address 6
[17180270.248000] usb 7-5: new high speed USB device using ehci_hcd and address 7


and lsusb gives:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:6204 Hewlett-Packard DeskJet 5150c
Bus 001 Device 001: ID 0000:0000  


It is not there. I have tried different ports, no good.

Oddly enough, It works fine on my laptop.


Any more ideas???


Thanks,

Sno

---

### Post by rdfx100 on 2006-11-05
What OS/kernel is on your laptop where it works?  It also doesn't work on my laptop with Fedora Core 4 (kernel 2.6.11-1.1369_FC4).

---

### Post by Snocrash on 2006-11-06
> **rdfx100 said:**
> What OS/kernel is on your laptop where it works?  It also doesn't work on my laptop with Fedora Core 4 (kernel 2.6.11-1.1369_FC4).

Ubuntu Edgy
kernel 2.6.17-10-386
Toshiba Tecra

Desktop is Ubuntu Edgy
But kernel is 2.6.17-10-generic.....maybe that has something to do with it.

I will let you know.

-Sno

---

### Post by Snocrash on 2006-11-08
> **Snocrash said:**
> Ubuntu Edgy
kernel 2.6.17-10-386
Toshiba Tecra

Desktop is Ubuntu Edgy
But kernel is 2.6.17-10-generic.....maybe that has something to do with it.

I will let you know.

-Sno

Nope...still does not work on my desktop.](*,)

---

### Post by Snocrash on 2006-11-10
Well....still does not work on my desktop.

However, I added the sd_mod module to my rc.local file, pluged in the drive and rebooted.

It saw the drive and added it:

[   54.336000] usb-storage: device found at 5
[   54.336000] usb-storage: waiting for device to settle before scanning
[   59.336000]   Vendor: WD        Model: 1600BEVExternal   Rev: 1.02
[   59.336000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   59.336000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   59.336000] sda: Write Protect is off
[   59.336000] sda: Mode Sense: 00 00 00 00
[   59.336000] sda: assuming drive cache: write through
[   59.336000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   59.336000] sda: Write Protect is off
[   59.336000] sda: Mode Sense: 00 00 00 00
[   59.336000] sda: assuming drive cache: write through
[   59.336000]  sda: sda1
[   59.388000] sd 2:0:0:0: Attached scsi disk sda
[   59.388000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   59.392000] usb-storage: device scan complete



But then it dropped it:

[   59.500000] usb 6-2: USB disconnect, address 5
[  102.200000] usb 6-2: new high speed USB device using ehci_hcd and address 6
[  102.340000] usb 6-2: configuration #1 chosen from 1 choice
[  102.340000] scsi3 : SCSI emulation for USB Mass Storage devices
[  102.340000] usb-storage: device found at 6
[  102.340000] usb-storage: waiting for device to settle before scanning
[  102.704000] usb 6-2: USB disconnect, address 6
[  124.620000] usb 6-2: new high speed USB device using ehci_hcd and address 7
[  124.760000] usb 6-2: configuration #1 chosen from 1 choice
[  124.760000] scsi4 : SCSI emulation for USB Mass Storage devices
[  124.760000] usb-storage: device found at 7
[  124.760000] usb-storage: waiting for device to settle before scanning
[  125.132000] usb 6-2: USB disconnect, address 7
[  147.168000] usb 6-2: new high speed USB device using ehci_hcd and address 8


Can't figure out why......

Any ideas???

Thanks,

Sno

---

### Post by rdfx100 on 2006-11-10
So, you just added "/sbin/modprobe sd_mod" to /etc/rc.local ?   It seemed lsmod showed I already had sd_mod installed, but it doesn't work as yours did...

FYI, I tried running EdgyEft from a live CD, and that doesn't find it correctly either :(

---

### Post by Snocrash on 2006-11-13
Mine turned out to be a power problem. My desktop was not putting out enough for the drive.

Had to go get a powered USB hub. Now it works fine.

-Sno

---

### Post by bodhi.zazen on 2006-11-13
Thanks for the update. I'll remember that.

:p 8)

---

### Post by rdfx100 on 2006-11-15
Interesting about the power level... It didn't work for me in 3 different USB ports on my desktop or on my laptop.  So, I gave up and returned the drive.

I instead bought a Seagate 500gb external usb drive, and it works fine right out of the box.

---

### Post by gyskouras on 2006-11-25
i have a mybokk essential 400GB and i've had exactly the same problems mounting it in ubuntu as "snocrash". for a short period the device is being seen and then it refuses to recognize it on none of the USB ports.

snocrash, how do you know it's a power issue? i do not get it since the external hdd is self powered by itself. why should it require power from the USB connection?

did you use a self-powered USB hub to connect mybook external hdd and it worked?

thanks,
-g

---

### Post by gyskouras on 2006-11-25
something i forgot to mention: mybook essential external hdd works perfect in windows on the same USB ports it is not working in linux.

-g

---

### Post by gyskouras on 2006-11-26
Here is the dump I get when Linux tries to recognize the hdd:

SCSI subsystem initialized
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
  Vendor: WD        Model: 4000KS External   Rev: 101a
  Type:   Direct-Access                      ANSI SCSI revision: 04
usb-storage: device scan complete
usb 1-1.2: reset high speed USB device using ehci_hcd and address 4
usb 1-1.2: device descriptor read/64, error -110
usb 1-1.2: device descriptor read/64, error -110
usb 1-1.2: reset high speed USB device using ehci_hcd and address 4
usb 1-1.2: device descriptor read/64, error -110
usb 1-1.2: device descriptor read/64, error -110
usb 1-1.2: reset high speed USB device using ehci_hcd and address 4
usb 1-1.2: device descriptor read/8, error -110
usb 1-1.2: device descriptor read/8, error -110
usb 1-1.2: reset high speed USB device using ehci_hcd and address 4
usb 1-1.2: device descriptor read/8, error -110
usb 1-1.2: device descriptor read/8, error -110
scsi: Device offlined - not ready after error recovery: host 0 channel 0 id 0 lun 0
scsi0 (0:0): rejecting I/O to offline device
scsi0 (0:0): rejecting I/O to offline device
scsi0 (0:0): rejecting I/O to offline device
usb 1-1.2: USB disconnect, address 4
scsi0 (0:0): rejecting I/O to offline device
scsi0 (0:0): rejecting I/O to offline device
scsi0 (0:0): rejecting I/O to offline device
sda : READ CAPACITY failed.
sda : status=0, message=00, host=0, driver=04
sda : sense not available.
sda: assuming drive cache: write through

---

### Post by Omnisuite on 2007-02-09
I'm also having similar problems:
-I have a WD My Book 500gb which is recognized by windows and not ubunut
-It does not show up in "cat /etc/fstab" or "fdisk -l"
-It has its own power
-"dmesg" gives many errors including:

[4294892.231000] usb 5-4: new high speed USB device using ehci_hcd and address 2
[4294892.654000] Initializing USB Mass Storage driver...
[4294892.664000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294892.667000] usb-storage: device found at 2
[4294892.667000] usb-storage: waiting for device to settle before scanning
[4294892.668000] usbcore: registered new driver usb-storage
[4294892.668000] USB Mass Storage support registered.
[4294897.668000]   Vendor: WD        Model: 5000KS External   Rev: 101a
[4294897.668000]   Type:   Direct-Access                      ANSI SCSI revision: 0 4
[4294897.674000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[4294897.674000] sdb: assuming drive cache: write through
[4294897.679000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[4294897.679000] sdb: assuming drive cache: write through
[4294897.679000]  /dev/scsi/host1/bus0/target0/lun0: p1
[4294897.686000] Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
[4294973.758000] usb 5-4: reset high speed USB device using ehci_hcd and address 2
[4294976.822000] usb 5-4: device descriptor read/64, error -110
[4294991.989000] usb 5-4: device descriptor read/64, error -110
[4294992.152000] usb 5-4: reset high speed USB device using ehci_hcd and address 2
[4294995.214000] usb 5-4: device descriptor read/64, error -110
[4295010.377000] usb 5-4: device descriptor read/64, error -110
[4295010.540000] usb 5-4: reset high speed USB device using ehci_hcd and address 2
[4295015.552000] usb 5-4: device descriptor read/8, error -110
[4295020.664000] usb 5-4: device descriptor read/8, error -110
[4295020.832000] usb 5-4: reset high speed USB device using ehci_hcd and address 2
[4295025.849000] usb 5-4: device descriptor read/8, error -110
[4295030.961000] usb 5-4: device descriptor read/8, error -110
[4295031.062000] scsi: Device offlined - not ready after error recovery: host 1 cha nnel 0 id 0 lun 0
[4295031.062000] scsi1 (0:0): rejecting I/O to offline device
[4295031.062000] Buffer I/O error on device sdb, logical block 0
[4295031.062000] Buffer I/O error on device sdb, logical block 1
[4295031.062000] Buffer I/O error on device sdb, logical block 2
[4295031.062000] Buffer I/O error on device sdb, logical block 3
[4295031.062000] Buffer I/O error on device sdb, logical block 4
[4295031.062000] Buffer I/O error on device sdb, logical block 5
[4295031.062000] Buffer I/O error on device sdb, logical block 6
[4295031.062000] Buffer I/O error on device sdb, logical block 7
[4295031.062000] usb 5-4: USB disconnect, address 2
[4295031.063000] scsi1 (0:0): rejecting I/O to offline device
[4295031.063000] scsi1 (0:0): rejecting I/O to offline device
[4295031.066000] scsi1 (0:0): rejecting I/O to offline device
[4295031.066000] Buffer I/O error on device sdb, logical block 0
[4295031.067000] scsi1 (0:0): rejecting I/O to offline device
[4295031.067000] Buffer I/O error on device sdb, logical block 0
[4295031.069000] usb-storage: device scan complete


Any ideas as to what I should try next? Thanks

---

