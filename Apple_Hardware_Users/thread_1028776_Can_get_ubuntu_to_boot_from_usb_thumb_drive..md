---
title: "Can get ubuntu to boot from usb thumb drive."
date: 2009-01-02
forum: Apple Hardware Users
---

### Post by redex64 on 2009-01-02
Hi, I have a problem booting ubuntu from my thumb drive on my new Macbook (aluminum).

I used unetbootin to put the .iso file on the thumb drive.

When I plug the drive into my windows machine it boots into ubuntu, but I can't get the same result on my mac.

---

### Post by pxwpxw on 2009-01-02
> **redex64 said:**
> Hi, I have a problem booting ubuntu from my thumb drive on my new Macbook (aluminum).

I used unetbootin to put the .iso file on the thumb drive.

When I plug the drive into my windows machine it boots into ubuntu, but I can't get the same result on my mac.

Intel Macs will only boot MacOSX boot.efi form external.
Earlier Macbooks can also boot grub.efi.

---

### Post by cyberdork33 on 2009-01-05
> **pxwpxw said:**
> Intel Macs will only boot MacOSX boot.efi form external.
Earlier Macbooks can also boot grub.efi.
In other words, booting from external drives does not work without some other software and configuration.

---

### Post by shivathreya on 2009-01-06
I installed refit on my MACBOOK PRO 1,1.

Created an ext3 USB disk.  I use this disk to install kubuntu intrepid.

Installed grub using the following command.

sudo grub-install --root-directory=/media/sdc1 --no-floppy /dev/sdc


Manually edited USBDISK/boot/grub/menu.lst

# menu.lst - Customized for Kubuntu Live Desktop 6.06
#		MJW 8 Jul 2006

default		0
timeout		3
color white/blue yellow/blue

title		Kubuntu Live Desktop (Persistent)
root		(hd0,0)
kernel		/casper/vmlinuz boot=casper persistent ramdisk_size=1048576 root=/dev/ram rw quiet splash--
initrd		/casper/initrd.gz
boot

title		Kubuntu Live Desktop
root		(hd0,0)
kernel		/casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash--
initrd		/casper/initrd.gz
boot

title		Kubuntu Live Desktop (Safe Graphics Mode, Verbose Startup)
root		(hd0,0)
kernel		/casper/vmlinuz boot=casper xforcevesa ramdisk_size=1048576 root=/dev/ram rw --
initrd		/casper/initrd.gz
boot

title		Memory Test
root		(hd0,0)
kernel		/install/mt86plus
boot

Copied files from KUBUNTU CD to the USBDISK.

Reboot.

Refit will detect the new GRUBBED USBDISK.

Shiva

---

### Post by pxwpxw on 2009-01-06
> **shivathreya said:**
> I installed refit on my MACBOOK PRO 1,1.

Created an ext3 USB disk.  I use this disk to install kubuntu intrepid.

....

Copied files from KUBUNTU CD to the USBDISK.

Reboot.

Refit will detect the new GRUBBED USBDISK.

Shiva

Amazing, I will try it on the MacBook2,1

Nope. refit sees it ok, but then the usual error about externals.
Maybe only for the MBP 1,1 ?
However, I note in another thread 
 [http://ubuntuforums.org/showthread.php?t=1030439](http://ubuntuforums.org/showthread.php?t=1030439)
a MacBook air installed from a usb drive?

---

### Post by rapsball4 on 2009-01-06
I'm looking to do the same thing, also a MacBook 2,1.  I don't want to touch my current OSX installation at all, but would like an Ubuntu on a USB drive to carry around for it.  Ideally, although I'm not sure if its possible, I'd like it to automatically boot into Ubuntu if the jumpdrive is in and automatically into OSX if it isn't.

---

### Post by cyberdork33 on 2009-01-06
> **pxwpxw said:**
> Maybe only for the MBP 1,1 ?
Well, this ties back to the orginal "boot from external" thread where some claimed they could boot from USB.  They seem few and far between though

---

### Post by pxwpxw on 2009-01-07
> **rapsball4 said:**
> I'm looking to do the same thing, also a MacBook 2,1.  I don't want to touch my current OSX installation at all, but would like an Ubuntu on a USB drive to carry around for it.  Ideally, although I'm not sure if its possible, I'd like it to automatically boot into Ubuntu if the jumpdrive is in and automatically into OSX if it isn't.

For a MacBook 2,1 (like mine), you can use grub.efi if you settle for i386 and no agp.

---

### Post by emmary on 2009-01-07
Mini Tripod and Digital Camera Tripod Wholesale  
TRADESTEAD supply cheap, high quality of mini tripod, digital camera tripod. Mini tripod is known for its usability, Lightweight, portable, extensible, especially design for those times when size matters. These mini tripod and digital camera tripod can easily fit into your pocket, briefcase and backpack. As digital camera and video camera has long be people's daily company, keep a mini tripod at your around is necessary.

1 year warranty for all the digital camera tripod and the mini tripod TRADESTEAD offers. High quality, sleek design, and nicely crafted body, couple with the feature of the cheapest price make our digital camera tripod and mini tripod be customer's favorite. 

Our digital camera tripod and mini tripod will be your nice travel companion. Carry a ultra-lightweight mini-tripod wherever you roam. It's small enough to fit in your pocket, and perfect for setting up at a moment's notice while traveling. It is perfect for Small Digital, APS, Point and Shoot and small digital cameras.

The mini tripod and digital camera tripod are sell at the bottom price, so we do have Minimum Order Quantity requirement for most of them. Among several of the mini tripods, this model: 2-Segment mini tripod, is best selling and be highly recommended.

Related Categories: Digital Cameras | Digital Camcorders | Digital Photo Frames | MP4 player | Camera Tripod

---

