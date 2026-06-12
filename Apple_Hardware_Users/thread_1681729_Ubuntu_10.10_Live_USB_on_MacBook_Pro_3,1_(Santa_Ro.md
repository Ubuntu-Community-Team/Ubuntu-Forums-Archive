---
title: "Ubuntu 10.10 Live USB on MacBook Pro 3,1 (Santa Rosa) problems"
date: 2011-02-04
forum: Apple Hardware Users
---

### Post by ipatch on 2011-02-04
Alright, I have had the past few days off due to inclement weather which has allowed me time to try and create a Ubuntu 10.10 Live USB for my MacBook Pro 3,1.  I thought surely this has already been done, and it was as simple as burning the ISO to a partition on a thumb drive (USB SD or uSD card).  Well, several days later and more snow on the ground, and I still have not booted a complete Ubuntu 10.10 system.  I have tried all sorts of walk-throughs and HOW-TOs but have had no success yet so I decided to piece together a way to get this done, and this is what I have done so far.

These are the steps I have taken to try and create a bootable Live USB of Ubuntu 10.10:


[LIST]
[*]Completely wipe/format the SD card in GParted and set the partition table to GPT, [_[COLOR=Blue]pic[/COLOR]_]("http://ipatch.penguinmilitia.net/?attachment_id=600")
[*]Created 4GB ext2 partition, with a label of *LINUX*, [_[COLOR=Blue]pic[/COLOR]_]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/02ext2partition.png")
[*]Created *EFI* directory in the root of the *LINUX* partition, and then created *boot* within *EFI*, [_[COLOR=Blue]pic[/COLOR]_]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/03createEFI.png")
[/LIST]
[I]*Note: The **EFI** directory must be [FONT=Courier New]EFI[/FONT] and not [FONT=Courier New]efi[/FONT] in order be seen in the boot selection menu for rEFIt because the ext2 partition is case sensitive.
[/I]
[LIST]
[*]Copied the contents of ISO (Ubuntu 10.10) to the root directory of the *LINUX* partition, [_[COLOR=Blue]pic[/COLOR]_]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/04copyISO.png")
[*]Mounted the *efi.img *located within the Ubuntu 10.10 ISO  and copied the *bootx64.efi* to [FONT=Courier New]LINUX/EFI/boot/ [_[FONT=Verdana][COLOR=Blue]pic[/COLOR][/FONT]_]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/05copybootx64EFI.png")[/FONT]
[*][FONT=Courier New][FONT=Verdana][COLOR=Blue][COLOR=Black]Copied the *grub.cfg* to [FONT=Courier New]LINUX/EFI/boot/[/FONT][/COLOR][/COLOR][/FONT][/FONT]
[*][FONT=Courier New][FONT=Verdana][COLOR=Blue][COLOR=Black][FONT=Courier New][FONT=Verdana]Added the following to *grub.cfg* on the *LINUX* partition: [URL="http://ubuntuforums.org/showthread.php?t=1284974"][COLOR=Blue][U]source 
[/U][/COLOR][/URL][/FONT][/FONT][/COLOR][/COLOR][/FONT][/FONT]
[/LIST]
```
[FONT=courier new]menuentry "Live USB Ubuntu 10.10"{[/FONT]
[FONT=courier new]    search --set -f /ubuntu-10.10-desktop-amd64.iso[/FONT]
[FONT=courier new]    loopback loop /ubuntu-10.10-desktop-amd64.iso[/FONT]
[FONT=courier new]    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.10-desktop-amd64.iso vga=773 persistent[/FONT]
[FONT=courier new]    initrd (loop)/casper/initrd.gz[/FONT]
[FONT=courier new]}[/FONT]
```
[LIST]
[*]Copied *ubuntu-10.10-desktop-amd64.iso* to the root directory of the *LINUX* partition.
[/LIST]

[LIST]
[*]Restarted, rEFIt loaded *bootx64.efi* from the *LINUX* partition on the  SD, and a Grub prompt displayed, but menu entries did not appear.
[*]Renamed the stock 10.10 *bootx64.efi *to *BOOTX64.efi*
[*]Restarted, renaming the *bootx64.efi *yielded the same results.
[*]Added the following lines to the *grub.cfg*
[/LIST]
```
[FONT=courier new]# This is the default GRUB2 configuration file, grub.cfg[/FONT]

[FONT=courier new]# Timeout for menu[/FONT]
[FONT=courier new]timeout=20[/FONT]
[FONT=courier new]default=0[/FONT]
```
[LIST]
[*]Restarted, the above lines yielded the same results, i.e. the menu entries did not display.
[*]Copied *BOOTX64.efi* from [_[COLOR=Blue]source[/COLOR]_]("http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick") and relocated the stock *BOOTX64.efi*
[*]Restarted, and the grub menu entries loaded with new *BOOTX64.efi*
[*]Made the following changes to g*rub.cfg*
[/LIST]
```
[FONT=courier new]# Custom menuentry #2 added 4FEB11[/FONT]
[FONT=courier new]menuentry "Live USB Ubuntu 10.10" {[/FONT]
[FONT=courier new]    fakebios[/FONT]
[FONT=courier new]    root=hd0,1[/FONT]
[FONT=courier new]    linux /casper/vmlinuz root=/dev/sda1 video=efifb agp=off[/FONT]
[FONT=courier new]    initrd /casper/initrd.img[/FONT]
[FONT=courier new]}[/FONT]
```
[LIST]
[*]Restarted, selected *Live USB Ubuntu 10.10*, but an error message displayed saying file not found.
[*]I was then presented with the menu entries again, I selected the *Live USB Ubuntu 10.10*  again, and then text/output started to scroll across screen, but then  soon stopped, and computer fans began to spin at full speed.
[/LIST]
[COLOR=Red]I will have a picture of the text output momentarily. [/COLOR]

---

### Post by ipatch on 2011-02-04
**PICTURES**

[LIST]
[*]rEFIt boot screen, [[COLOR=Blue]pic[/COLOR]]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/01-rEFIt-bootScreen.jpg")
[*][COLOR=Blue][COLOR=Black]GRUB displaying menu entries, [[COLOR=Blue]pic[/COLOR]]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/02-grub-bootScreen-good.jpg")[/COLOR][/COLOR]
[*][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]First message after selecting *Live USB Ubuntu 10.10 - loopback*, [[COLOR=Blue]pic[/COLOR]]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/03-loopBack-error-file-not-found.jpg")[/COLOR][/COLOR][/COLOR][/COLOR]
[*][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]Grub menu entries reappear then select *Live USB Ubuntu 10.10 - loopback* again, and kernel panic, [[COLOR=Blue]pic[/COLOR]]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/04-loopBack-kernelPanic.jpg")[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]
[*][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]Kernel Panic, selecting *Live USB Ubuntu 10.10 - hd0,1 *[[COLOR=Blue]pic[/COLOR]]("http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/06-NONloopBack-kernelPanic.jpg")[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]
[/LIST]

I think I am pretty close to getting this system to boot.  Any thoughts?

---

### Post by mu3en on 2011-02-05
18 hours ago, i somehow reached exactly the same final state as you also on a macbook 3.1, except on an internal drive.

as far as i can tell (ls command in grub menu) the panic seems to come from not being able to read the protective MBR correctly.

i used:
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

and then made sure to tweak the EFI Graphic Protocol as here:
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

which actually seems to work as expected right up until it spits the same error sequence: [http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/06-NONloopBack-kernelPanic.jpg](http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/06-NONloopBack-kernelPanic.jpg)

but i note now that the grub.enbug.org site states: " EFI booting is broken in grub 1.98 ".

so now i'm thinking maybe we need to build 1.99 as it suggests?

would be great to get some confirmation before doing so but guess i'll try anyhow.

---

### Post by srs5694 on 2011-02-05
> **mu3en said:**
> 18 hours ago, i somehow reached exactly the same final state as you also on a macbook 3.1, except on an internal drive.

as far as i can tell (ls command in grub menu) the panic seems to come from not being able to read the protective MBR correctly.

i used:
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

and then made sure to tweak the EFI Graphic Protocol as here:
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

which actually seems to work as expected right up until it spits the same error sequence: [http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/06-NONloopBack-kernelPanic.jpg](http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/06-NONloopBack-kernelPanic.jpg)

but i note now that the grub.enbug.org site states: " EFI booting is broken in grub 1.98 ".

What you're seeing is a Linux kernel panic, which means that GRUB has successfully loaded the kernel; however, the kernel is unable to locate your root filesystem. A few lines up from the end, it includes the following clue:

```

VFS: Cannot open root device "sda1" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
0b00        1048575 sr0 driver: sr

```

No other possible root partitions are listed. This suggests to me that the kernel isn't able to detect your hard disk for some reason. The most likely cause is that your initial RAM disk, which holds drivers for most disk devices, isn't being loaded correctly. You might check the initrd line in your /boot/grub/grub.cfg file, and be sure that a matching initial RAM disk file exists.

OTOH, if the initial RAM disk weren't loading, it's a bit puzzling that the system was able to detect the optical disc (the sr0 device). Perhaps it's simply a bad specification of the Linux root device. (Note that's the device specified on the "linux" line with the "root=" option, *not* the device specified by the "set root=" option.) You can specify your Linux root device either with a Linux device filename (as in "root=/dev/sda5") or via UUID (as in "root=UUID=43d1353d-6174-4ed4-be30-c24b4cba3d8e"). Try changing which you use. Also, the error message includes a comment that it can't open "sda1" as the root device. It's very unlikely that /dev/sda1 would be your Linux root device, since that would normally be your EFI System Partition (ESP). (This assignment isn't mandatory; the ESP *could* be something else; but the ESP is usually /dev/sda1.) If your grub.cfg is specifying "root=/dev/sda1" and if your Linux root (/) partition is something else, you must correct that problem.

A more unlikely possibility is that there's something strange about the ESP (which *is* normally /dev/sda1, as just noted). The EFI specification says it must be a FAT32 partition. I've heard of Mac users re-doing the ESP with HFS+, and the Mac's version of the EFI can handle this; but there's a slim possibility that the Linux kernel is flaking out when it sees such a configuration. This seems like a long-shot possibility to me, though.

Note that I'm suggesting direct editing of /boot/grub/grub.cfg, which is contrary to the usual way of doing things with GRUB 2. If you get your system to boot by direct editing of grub.cfg, you'll need to either keep it working by manually editing after every automatic change or alter the scripts in /etc/grub.d to implement whatever change you instituted to get the system to boot.

---

### Post by ierpe on 2011-12-18
Any joy? I'm still not able to boot ubuntu on a usb stick on the macbook 3.1... :-/

---

