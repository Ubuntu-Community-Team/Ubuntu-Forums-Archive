---
title: "SliTaZ - Unetbootin/Mutilbootusb gives me &quot;trying to unpack rootfs image as initramfs"
date: 2012-04-20
forum: Any Other OS
---

### Post by AlexOnVinyl on 2012-04-20
Basically it gives me that message everytime, using both programs, using cooking version and core - What seems to be the issue?

I am running a Compaq CQ60 with 3GB of RAM - so I cant imagine it being a RAM issue..

My computer has 3GB of ram and is a dual processor - do you think this is just a result of a bad setup of the iso? or something worse? Hardware related?

-------

ALSO: I did manage to get Kanotix to work - would that be good enough to use as say a recovery distro incase if my Ubuntu goes down?

---

### Post by oldfred on 2012-04-21
To reinstall grub2 with v1.99, you really need the save version of Ubuntu to use the two line easy mount and install commands.

But, I think you can always chroot into an install and then you are using the current version.

I create my own multiboot USB with grub2. I think your MultiBoot uses grub4dos and I am not familiar with the details.

I think this grub2 entry was working for me, but I see I had to edit the entry (old one is the # commented out)

```
 menuentry "slitaz " {
  set isofile="/boot/iso/slitaz-3.0.iso"
  loopback loop $isofile 
  linux (loop)/boot/bzImage rw root=/dev/null lang=C kmap=us screen=1024x768x16 autologin noprompt noeject
  initrd (loop)/boot/rootfs.gz
#  linux (loop)/boot/bzImage isofrom=$isofile boot=live quiet vga=791 noeject noprompt
}

```

---

### Post by AlexOnVinyl on 2012-04-23
> **oldfred said:**
> To reinstall grub2 with v1.99, you really need the save version of Ubuntu to use the two line easy mount and install commands.

But, I think you can always chroot into an install and then you are using the current version.

I create my own multiboot USB with grub2. I think your MultiBoot uses grub4dos and I am not familiar with the details.

I think this grub2 entry was working for me, but I see I had to edit the entry (old one is the # commented out)

```
 menuentry "slitaz " {
  set isofile="/boot/iso/slitaz-3.0.iso"
  loopback loop $isofile 
  linux (loop)/boot/bzImage rw root=/dev/null lang=C kmap=us screen=1024x768x16 autologin noprompt noeject
  initrd (loop)/boot/rootfs.gz
#  linux (loop)/boot/bzImage isofrom=$isofile boot=live quiet vga=791 noeject noprompt
}

```

Tried this command today:

```
dd if=nameofiso.iso of=/name/of/device
```


and it says "Missing Operating System"

- any other ideas?

I gave up with SLiTaz

---

### Post by Elfy on 2012-04-23
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by oldfred on 2012-04-23
Only some ISO support the dd method to install. You normally have to use Unetbootin or pendrive to extract, install and load a boot loader to the device.

With grub2 you can install grub2 to the device, copy the ISO to a folder, and add a loopmount entry. But again only some ISO support this method.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub4dos
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by snowpine on 2012-04-23
SliTaz has its own USB installer called TazUSB. Check  it out, works much better than Unetbootin in my experience!

[http://hg.slitaz.org/tazusb/raw-file/tip/doc/tazusb.en.html](http://hg.slitaz.org/tazusb/raw-file/tip/doc/tazusb.en.html)

---

### Post by AlexOnVinyl on 2012-04-23
> **snowpine said:**
> SliTaz has its own USB installer called TazUSB. Check  it out, works much better than Unetbootin in my experience!

[http://hg.slitaz.org/tazusb/raw-file/tip/doc/tazusb.en.html](http://hg.slitaz.org/tazusb/raw-file/tip/doc/tazusb.en.html)

TazUSB? Is it specifically for SliTaz or other images as well?

---

### Post by AlexOnVinyl on 2012-04-23
> **oldfred said:**
> Only some ISO support the dd method to install. You normally have to use Unetbootin or pendrive to extract, install and load a boot loader to the device.

With grub2 you can install grub2 to the device, copy the ISO to a folder, and add a loopmount entry. But again only some ISO support this method.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub4dos
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Gah MultibootUSB is a pain in the ****, but I suppose its an option.

---

### Post by oldfred on 2012-04-23
I just like grub2 and used it for a while on my flash drives. But now with several hard drives I find using grub2 to loopmount an ISO from one drive to install to another makes for very fast installs. It is the same process where ever you have the ISO and use grub2 to loopmount the ISO.

Hard drive:
Direct boot on hard drive - drs305:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by AlexOnVinyl on 2012-04-23
> **oldfred said:**
> I just like grub2 and used it for a while on my flash drives. But now with several hard drives I find using grub2 to loopmount an ISO from one drive to install to another makes for very fast installs. It is the same process where ever you have the ISO and use grub2 to loopmount the ISO.

Hard drive:
Direct boot on hard drive - drs305:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I know how to setup MultibootUSB, no issues there, the only question I have is can it work with windows iso files as well?

---

### Post by oldfred on 2012-04-24
Windows ISOs are not directly bootable, you have to install the ISO to the flash drive with Windows software.

I tried making a Windows repair flash drive, but could not get it to install correctly from Ubuntu. I was able to make a CD and use the repairCD to copy itself to a flash drive. The repair files were tiny on a large flash drive and I wanted to see if I could then install grub2 into the Windows FAT32 partition (had to make sure not to have two /boot folders). It worked and then I shrank the FAT32 partition, created another and then used grub2 to boot several other repair ISOs so on one flash drive I have Windows repair tools and Linux repair tools.

---

### Post by snowpine on 2012-04-24
> **AlexOnVinyl said:**
> TazUSB? Is it specifically for SliTaz or other images as well?

For SliTaz (as you'd have learned by clicking the link :)).

---

