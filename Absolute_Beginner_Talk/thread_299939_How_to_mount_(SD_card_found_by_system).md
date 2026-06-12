---
title: "How to mount (SD card found by system)"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by az_s_za on 2006-11-14
I know know next to nothing about my command line, but have come up with the following with help from other posts:

output from dmesg | tail:
> [17179610.432000] Bluetooth: L2CAP socket layer initialized
[17179610.476000] Bluetooth: RFCOMM socket layer initialized
[17179610.476000] Bluetooth: RFCOMM TTY layer initialized
[17179610.476000] Bluetooth: RFCOMM ver 1.7
[17191010.028000] tifm_7xx1: sd card detected in socket 1
[17191087.156000] usb 2-1: USB disconnect, address 3
[17191099.836000] usb 2-1: new low speed USB device using uhci_hcd and address 4
[17191100.008000] usb 2-1: configuration #1 chosen from 1 choice
[17191100.036000] input: A4Tech PS/2+USB Mouse as /class/input/input6
[17191100.036000] input: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.1-1
output from lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:04.0 CardBus bridge: Texas Instruments Unknown device 8039
06:04.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
06:04.2 Mass storage controller: Texas Instruments Unknown device 803b
06:08.0 Ethernet controller: Intel Corporation Unknown device 1093 (rev 02)


I don't see the contents of my SD Card anywhere.  Is this a case of mounting it?  If so, how do I do that?  If not, what can I do?

Thanks.

---

### Post by schrombot on 2006-11-14
```
[17191010.028000] tifm_7xx1: sd card detected in socket 1
```
The kernel knows you plugged in an SD card. lspci is only going to show you the card reader, not the card itself, and I believe it is```
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
```..but I could be wrong. If it works like my system, you will need to mount it.

Try```
sudo mkdir /media/sdcard
sudo mount /dev/tfa0 /media/sdcard
```Do that to see if it will mount correctly.

---

### Post by az_s_za on 2006-11-15
Thanks, I REALLY appreciate you replying.

when I try your suggestion I get:
> $ sudo mount /dev/tfa0 /media/sdcard
mount: special device /dev/tfa0 does not exist

attached is a screenshot of my device manager incase that helps.

Any more ideas?

---

### Post by az_s_za on 2006-11-22
Anyone?  Anyone?

---

### Post by Peepsalot on 2006-11-22
try sda1 instead of tfa0.

If that doesn't work, run this command while the card is plugged in:
```

sudo fdisk -l

```
(that's dash lowercase L not dash one)
It should be listed as a device somewhere in the results.  You just need to find the correct name for it.

---

### Post by az_s_za on 2006-11-22
Thanks for replying.

sda1 didn't work.

fdisk-l doesn't show the sd card either:
> $ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         608     4883728+   b  W95 FAT32
/dev/hda2   *         609        3796    25607610    7  HPFS/NTFS
/dev/hda3            3797        9729    47656822+   5  Extended
/dev/hda5            3797        5884    16771828+  83  Linux
/dev/hda6            5885        6011     1020096   82  Linux swap / Solaris
/dev/hda7            6012        9729    29864803+  83  Linux
Any other ideas?

---

### Post by streeto on 2006-11-22
Do you have the package ivman installed? I takes care of automounting removable media.

---

### Post by az_s_za on 2006-11-22
no.  I'll try that now.

---

### Post by az_s_za on 2006-11-22
Well, I've got ivman installed and I don't notice anything when I insert an SD card.  Should something appear on the desktop, or my home folder or something?

---

### Post by streeto on 2006-11-22
When I insert my PSP in the USB, it gets mounted at /media/psp. Look at /media to see if there is something new. Also, make sure ivman is running, it is not a system service, it must be run by the user at login.

---

### Post by az_s_za on 2006-11-22
I started Ivman with:
ivman -s

then:
ivman

as per the man page.  
Aside from that I have done no config on it.  Is that right?  

Still nothing extra mounted anywhere, including in my /media folder.

---

### Post by az_s_za on 2006-11-22
I don't think we are on the right track here with ivman, as my system has had no problem auto-mounting other devices (cdrom & usb) even before ivman.

---

### Post by streeto on 2006-11-22
Well, I only tried ivman with USB mass storage devices. Perhaps this is not the case of you SD card. Sorry, I don't have any other ideas.

---

### Post by secam on 2006-11-24
Try this:

 Originally Posted by Hugin:

I just wanted to say that this thread has been of great help.
Just did a fresh install of Edgy. To get the SD card to mount I used

sudo modprobe tifm_core
sudo modprobe tifm_sd

and the SD card shows up

adding
tifm_core
tifm_sd
to /etc/modules will have them load at boot

---

### Post by az_s_za on 2006-11-27
FANTASTIC!!!

That has worked perfectly.  Thank you so-oooo much secam (and Hugin)

---

### Post by Louis XVI with a gun on 2006-11-28
> **secam said:**
> Try this:

 Originally Posted by Hugin:

I just wanted to say that this thread has been of great help.
Just did a fresh install of Edgy. To get the SD card to mount I used

sudo modprobe tifm_core
sudo modprobe tifm_sd

and the SD card shows up

adding
tifm_core
tifm_sd
to /etc/modules will have them load at boot

Hello :) 

Oh thanks, my card is now mounted on my NX6125 under Ubuntu 6.10

---

### Post by chikko on 2006-12-04
hey guys!
thanks for all the info!  it really made my TI 6in1 reader to mount!
BUT! - a small strange problem though..
it seems to accept my 128mb card, but not my 2gb sandisk ultraII card..:(
when i push it in, the led just blinks for a second, and then nothing..
any thoughts?

p.s
the 2gb card DOES work when i put it into a simple USB card reader..

thanks!

---

### Post by az_s_za on 2006-12-04
I haven't found a 2gb SD card that has worked properly all the time yet.  The ones I have tried work sometimes, but not always.  This is not just on my computer, but also on my Palm Pilot.

I think the technology is not mature enough yet in 2gb.

Do you have other cards that are smaller than 2gb?  Do they all work?  If so, then maybe you should stick to 1gb cards for the time-being.

---

### Post by noidear on 2006-12-09
Hi
I am still quite new to linux and started using Edgy about 3 months ago, but hope this helps. I have a 2 GB SDCard which is use to swap info and store files between my 2 laptops, a Dell Inspiron XPS Gen 2 and an IBM X40 Thinkpad. Unfortunately neither of the basic Edgy installs allowed me to use the SDCard, in fact both PCs would freeze after I put the SDCard in the slot. However my way around that was to update the kernel and as such I have been running a customised 2.8.16.2 kernel with ubuntu with full SDCard support and    no other problems so far. Ths link I used to do this was [http://www.ubuntuforums.org/showthread.php?t=217657&highlight=how+to+compile+the+2.6.18+kernel](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=how+to+compile+the+2.6.18+kernel)
which is very easy to follow, but if you need any further help, let me know.
Hope this helps:D

---

