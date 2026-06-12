---
title: "WD 60gb Passport Automatic Mounting Failures!!"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by fabianvas on 2008-04-01
Hello Ubuntu Community!

Recently I gave Windows Vista the boot off of my laptop and have started using the most recent version (at the time I downloaded) of Ubuntu Gutsy Build 7.10.  Over the past several days I have been using this forum to help relieve some of the compatibility issues with my hardware (such as wireless card, etc) and I'm hoping you guys can pull through and help a beginner out on this one.  Recently I sat down with my WD Passport 60 GB hard drive (FAT32) and plugged it into one of my USB drives and after reading all the forums about hot-plugging external devices into Ubuntu I figured it would have worked but to my dismay Ubuntu didn't recognize the drive.  So to help those of you who have the time to look at this thread this is the list of methods I went through to help alleviate the problem (with a small caveat of a minor success but that didn't last long).

1)  A number of threads here and elsewhere stated that a quick fix is going into the terminal and typing gconf-editor to rid the mount options under 'vfat' of the 'usefree' option.  Much to my surprise this actually worked however only for one use.  After unmounting my drive by right clicking and 'unmount' and plugging it back in, the computer failed to recognize my hard drive.  Adding the 'usefree' option back in, restarting the computer, and removing it again doesn't work either (as some posts suggested).

2)  With my hard drive plugged in I typed in the dmesg | grep usb command in the terminal and came up with the following information:

    xxxxx@xxxxx-laptop:~$ dmesg | grep usb
[    3.688000] usbcore: registered new interface driver usbfs
[    3.688000] usbcore: registered new interface driver hub
[    3.688000] usbcore: registered new device driver usb
[    3.764000] usb usb1: configuration #1 chosen from 1 choice
[    3.868000] usb usb2: configuration #1 chosen from 1 choice
[    4.268000] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    4.408000] usb 2-4: configuration #1 chosen from 1 choice
[   15.716000] usbcore: registered new interface driver uvcvideo
[  165.344000]  [<f88856c2>] usb_hcd_irq+0x22/0x60 [usbcore]
[  165.344000] [<f88856a0>] (usb_hcd_irq+0x0/0x60 [usbcore])

Because of my beginner status I have no idea what any of this stuff means or what it may imply about the status of my external hard drive.  Additionally, I issued the lsusb command in the terminal and came up with the following:

Bus 002 Device 002: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

ALSO, with my WD Passport Plugged in I issued the gedit /etc/fstab command as suggested by others to check on the status of the hard drive being present or not.  The following is the contents of that file.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3ab51728-6190-4db7-a76d-7260c6a365e3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6bad5c1f-e782-4ec7-b4e0-382578758b52 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I issued the fdisk command to check on the current devices on my computer.  The threads had mentioned that with the hard drive plugged in, it should show up here.  Anyways, here is the contents of that command;

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

AND FINALLY, I issued the sudo fdisk -l command and came up with the following information (my external hard drive is plugged in):

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc202b441

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris


Some other posts have stated that it could be that the gnome-mount manager is out of date but it appears that that program is up-to-date on my machine.

So, I hope I covered my ground well enough but that is my situation.  I know that this subject has been beaten to a dead horse in countless forums but I was never able to find one that had the same situation as I have been having.  No matter what command I entered it was never able to detect that my WD Passport had actually been plugged in.  The only time it had worked was when I had removed the usefree command in my mount options but that no longer works I'm afraid; it was a one time only deal.  I also noticed a lot of people manually mounting their drives but like I had mentioned I have not been able to get the computer to recognize that a drive is actually in place, so it seems that the only drives present are those of my internal hard drive and their partitions (I would much rather prefer to have my external hard drive automatically mount).  The computer I am using is an HP dv6000 laptop that had a clean install done with Ubuntu (if that is of any use to anybody :). 

This is my last and final BIG configuration issue (as of now anyways) and the one factor that is preventing me from taking windows completely off my other machine (my WD Passport works fine on my Windows OS).  If anyone could possibly walk me through the steps of getting this resolved I will be beyond grateful.  Thanks! :-)

---

### Post by mrsteveman1 on 2008-04-01
I don't see the kernel recognizing that a device is even connected.

Fdisk -l should show a device with a total byte count of 60- somthing, and it isn't there.

The kernel dmesg buffer should also be showing a usb-storage device recognized, and it isn't.

I have the exact same drive, the silver thing with the blue light on it right? My guess is the drive isn't being powered enough with the cable/port/hub you are using unless you know it is ok. Can you hear the drive itself spinning?

Without enough power i believe these drives click a little bit but never actually spin.

If the drive is in fact spinning but the kernel can't see it something else is wrong.

---

### Post by ugm6hr on 2008-04-01
> **mrsteveman1 said:**
> Without enough power i believe these drives click a little bit but never actually spin.

If the drive is in fact spinning but the kernel can't see it something else is wrong.

Indeed.  I have the same device - and it works great on my new laptop.

My old laptop used to take a variable amount of time to power this device (initial clicking sound).  But leaving it plugged in for a few minutes used to fix that problem.

This is unlikely to be a problem with Ubuntu, but one of power management to USB.  I know some Macs do not supply enough power to USB to use these drives.

Out of interest - did it work on this laptop with Vista?

---

### Post by fabianvas on 2008-04-01
mrsteveman1-

Thanks for the reply!  You know due to how late it was when I posted the last message I had miseed probably a useful piece of information.  I had plugged in my hard drive a second time and clicked on 'computer' and the icon for my WD Passport was actually present but missing from the desktop.  I clicked on it and an error message popped up saying "bad super block could not mount volumn vfat" or something very similar to that.  Could it be that my hard drive is corrupted enough that Ubuntu has a difficult time recognziing it?  As it sits, my external seems to be getting enough power.  It is running without the ticking of the hard drive as you had suggested.  Is there any particular update that I could to get it fixed.  I also have a USB stick that my computer doesn't recognize either.  

P.S.  Could I possibly reformat my external or USB stick to linuxes ext3 format or is it a different issue all together.  Thanks again for the help!

Ugm6hour-

The hard drive did work with Vista on my laptop but every once in awhile there was a time where it might not have been supplying enough power.  I have three USB drives and the one located by my ac adapter plugin would actually never work on my hard drive.  The other USB's located by my ethernet plugin would work but with the occasional issue of the computer not recognizing.  All I would have to do is just unplug and plug it back in again.  As the post above stated it appears that the hard drive is getting enough power.  Thanks!

---

### Post by ugm6hr on 2008-04-01
> **fabianvas said:**
> P.S.  Could I possibly reformat my external or USB stick to linuxes ext3 format or is it a different issue all together.  Thanks again for the help!

Bad superblock sounds like a hardware issue.

A reformat may fix things temporarily, but I'd be wary about relying on the data - make sure everything is backed up.

And yes - you can use GParted to format the drives in whatever format you want (My WD Passport is 2 partitions - vfat and ext3).

---

### Post by Duck2006 on 2008-04-01
When you used it did you do a safe remove?

---

### Post by fabianvas on 2008-04-01
Duck2006-

I'm pretty sure I did a safe remove.  All I did was just right click on the external and click unmount.  Something tells me that I have an issue with the physical USB ports.  I have a dual boot set up on my desktop of the same version of Ubuntu and Windows XP Pro and my external is actually recognized just fine on the desktop.  Could their be a possible linux update of my USB ports that I could download?  As you can tell I'm completely in the dark on this stuff being that I have just started with ubuntu so any help is appreciated!  Thanks again!

---

### Post by compiledkernel on 2008-04-01
Hmmmm, you know I had some similar issues with 2 of the seagate freeagent drives I have, and it took a little sdparm magic to make them happy. Im not sure if that would be the case here or not.

---

### Post by mrsteveman1 on 2008-04-01
Is this drive actually formatted with FAT32/vfat?

I have seen ubuntu setup some fstab entries for drives that weren't actually connected, which then failed later because the filesystem listed was wrong. For instance, the hardy beta setup an fstab entry for /dev/sdb using the iso9660 filesystem, why i don't know, but then when i connected my iPod it failed to automount because it was trying to mount it like a CD, and said something similar to the error you got.

Check the filesystem for sure, you don't HAVE to format with ext3, fat32/vfat will work fine for most things unless you need huge files.

When it DOES give you that superblock error, what is in dmesg?

---

### Post by fabianvas on 2008-04-01
Hello Everybody:

So I had decided to start over from scratch and reinstall Ubuntu.  This had actually worked!  So I plugged my external hard drive into one of the USB ports several time:s and it had read each time.  BUT when I switched USB ports and plugged it in I got the error that "/dev/sdb1 could read superblock" so as per request of mrsteveman1 I issued the command dmesg with this error and here is the last remaining lines of the output that has to do with my usb external drive:

[  334.692000] handlers:
[  334.692000] [<f88856a0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  334.692000] Disabling IRQ #7
[  336.000000] Clocksource tsc unstable (delta = -88947173 ns)
[  638.524000] usb 2-2: USB disconnect, address 4
[  638.524000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  638.524000] end_request: I/O error, dev sdb, sector 63
[  638.532000] FAT: unable to read boot sector

Also the dmesg | grep usb command came up with new information 

[    3.660000] usbcore: registered new interface driver usbfs
[    3.660000] usbcore: registered new interface driver hub
[    3.660000] usbcore: registered new device driver usb
[    3.752000] usb usb1: configuration #1 chosen from 1 choice
[    3.856000] usb usb2: configuration #1 chosen from 1 choice
[    4.256000] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    4.396000] usb 2-4: configuration #1 chosen from 1 choice
[   16.432000] usbcore: registered new interface driver uvcvideo
[  115.544000] usb 2-2: new high speed USB device using ehci_hcd and address 3
[  115.676000] usb 2-2: configuration #1 chosen from 1 choice
[  115.780000] usbcore: registered new interface driver libusual
[  115.800000] usb-storage: device found at 3
[  115.800000] usb-storage: waiting for device to settle before scanning
[  115.800000] usbcore: registered new interface driver usb-storage
[  120.800000] usb-storage: device scan complete
[  153.364000] usb 2-2: USB disconnect, address 3
[  167.724000] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  167.856000] usb 2-2: configuration #1 chosen from 1 choice
[  167.856000] usb-storage: device found at 4
[  167.856000] usb-storage: waiting for device to settle before scanning
[  172.856000] usb-storage: device scan complete
[  334.692000]  [<f88856c2>] usb_hcd_irq+0x22/0x60 [usbcore]
[  334.692000] [<f88856a0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  638.524000] usb 2-2: USB disconnect, address 4

I'm hoping that since something had actually been recognized that this error might be a little more useful.  I hope you guys will be able to make sense of it.  Thanks again!

---

### Post by mrsteveman1 on 2008-04-01
If you were leaving the drive connected when those disconnect/reconnect errors happened, something is wrong with the drive or perhaps its not getting enough power and is cycling on and off.

In particular, usb 2-2 should not be disconnecting over and over unless you were unplugging it.

Also this:

```
[ 638.524000] end_request: I/O error, dev sdb, sector 63
```

This is completely independent of the filesystem used, it can't read sector 63 on the drive for some reason.

Plug the drive directly into a USB port on the computer with either the USB cable that came with it, or one that has thick conductors (some of them specify the wire gauge using AWG on the casing of the cable, smaller number is better).

---

### Post by fabianvas on 2008-04-01
Hello to everybody who helped out!  Well, I think I might have it working for at least a little while anyways.  I used Gparted to reformat my external hard drive and I gave it the FAT32 file system.  I then went into gconf-editor and deleted the 'usefree' options unde vfat of the storage folder.  I restarted my computer and plugged in my hard drive and it had mounted it fine on both usb ports.  I did this several times with success.  So i'm hoping that the combination of reformating my hard drive and deleting that usefree option will do the trick from now on.  Thanks everybody who took the time to help out!

---

