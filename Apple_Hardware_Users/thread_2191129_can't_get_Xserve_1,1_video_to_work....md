---
title: "can't get Xserve 1,1 video to work..."
date: 2013-12-01
forum: Apple Hardware Users
---

### Post by tangles on 2013-12-01
Hi,

I've managed to install Ubuntu on an Apple Xserve 1,1 using [christophersmart.com's blog]("http://blog.christophersmart.com/2009/07/23/linux-on-an-apple-xserve-efi-only-machine/") but I can't get video up... :mad:

The blog uses a net-install approach which I couldn't get to work because I think the paths have all changed now.
Anyway, I got around that by downloading the 12.04 alternate image and used the kernels on that with christophersmart.com's Grub to get it to boot and install.
The text-based installer worked a treat – had video all the way through the process, and I purposely skipped the boot loader section in case it tried to install the 64bit Grub into place and wipe out my efforts with the 32bit Grub that's needed.

I've got an old 60GB SSD drive sitting where the optical would normally be now, which gives me 3 Sata bays to play around with ZFS, however I'd like to get the GUI up if possible.

The 60GB SSD was initially prepared with OSX so that it had the GPT label and partition that the xserve's EFI insists on using. The driver is partitioned as:
sda1 (the ~200MB EFI partition formatted as FAT32)
sda2 (/ 25GB and is ext4)
sda3 (swap 16GB)
sda4 (will be zfs ZIL 5GB, currently HFS)
sda5 (will be zfs cache 5GB, currently HFS)

Even though the xserve has 32GB of RAM, I only gave the swap partition 16GB. Was this a foolish thing to do? otherwise I'll have to get a bigger SDD and start over.

sda1 contains the 32bit Grub2 and the kernels. Here is the grub.cfg I'm using to boot:
```
set timeout=10
set default=0
menuentry "Linux Boot" {
        fakebios
        linux /efi/boot/vmlinuz-3.8.0-33-generic root=/dev/sda2 ro vga=normal video=efifb irqpoll agp=off noefi
        initrd /efi/boot/initrd.img-3.8.0-33-generic
}
menuentry "Install Ubuntu" {
        fakebios
        linux   /install/vmlinuz  priority=low vga=normal video=efifb file=/cdrom/preseed/ubuntu.seed quiet --
        initrd  /install/initrd.gz
}
```

When the xserve boots, the video stops displaying output right around when the swap is setup.
Other than that, I can ssh into the xserve and do what I need to do.

In an effort to let updates potentially fix the issue, here is what I've done so far:

```
$lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise
```

(I figured I'd get ZFS involved as part of the update:)

```
$sudo add-apt-repository ppa:zfs-native/stable
$sudo apt-get update
$sudo apt-get dist-upgrade
```

which also upgraded my kernel from 29 to 33

```
$ls /boot/
abi-3.8.0-29-generic     config-3.8.0-33-generic      initrd.img-3.8.0-33-generic  System.map-3.8.0-29-generic  vmlinuz-3.8.0-33-generic
abi-3.8.0-33-generic     grub                         memtest86+.bin               System.map-3.8.0-33-generic
config-3.8.0-29-generic  initrd.img-3.8.0-29-generic  memtest86+_multiboot.bin     vmlinuz-3.8.0-29-generic
```

So I've moved the new kernel into sda1 and I'm able to boot with the new kernel, but unfortunately the 279MB's worth of updates did not fix the video.

I've attached [ATTACH]248220[/ATTACH] dmesg and the last line I see that is rendered on the screen is entry [1.686150]:


christophersmart.com's blog suggests to edit/include the following into /etc/X11/xorg.conf:
```
Section "Device"
        Identifier      "fbdev device"
        Driver          "fbdev"
EndSection
```
which hasn't made any difference for me...

The xserve has the mezzanine card installed which is an ATI X1300 GPU. It has a Mini-DVI port on the rear only and so I'm using an Apple MiniDVI to DVI display adapter to drive the Monitor.
The Monitor is an old HP 1740, 4:3 aspect ratio with native resolution of 1280 x 1024.
When the Xserve boots, Grub and then the boot sequence rolling text is rendered at 1280 x 1024.

I'm savvy with vi and moving things around with the terminal, but I got no clue past that when it comes to X11.
I'm not really able to find any more info about it when googling, I guess that's fair enough considering the xserve's age and scarcity.

I hope I've provided more-than-enough info for someone out there to simply go... "ahhh.... do this..."

Thank you,

Raoul.

---

### Post by bapoumba on 2013-12-01
Moved to Apple Users.
(I moved your other thread to Jail, BTW, a forums area where we keep things out of view).

---

### Post by tangles on 2013-12-01
Thank you bapoumba,

I wasn't sure where to place this because my issue is with X11/GUI...

---

### Post by bapoumba on 2013-12-01
> **tangles said:**
> Thank you bapoumba,

I wasn't sure where to place this because my issue is with X11/GUI...

You're welcome. They are people around here who are familiar with running Ubuntu on Apple hardware. I do know MacOS and machines as I use them at work but have no experience running Ubuntu on them.

---

### Post by tangles on 2013-12-02
So..

I appended "nomodeset" to my grub.cfg line:
linux /efi/boot/vmlinuz-3.8.0-33-generic root=/dev/sda2 ro vga=normal video=efifb irqpoll agp=off noefi

So now the startup gets further down the track, but I see nothing but a white garbled "dots/lines" on the screen, and the odd "orange" flicker every now and then around restarts.

because the GPU is an X1300, (i.e. legacy) I've found a [post]("http://ubuntuforums.org/showthread.php?t=1988027") that suggests to remove/purge all ATi drivers and just use the  install xserver-xorg-video-radeon package.

I've done this, but am not seeing anything different when restarting.

lspci -nn | grep VGA definitely can see the X1300 GPU...

Would it be that I'm running Grub2 version 1.96 that's causing this?  (compiling Grub 1.98, 1.99, 2.00rc2 for 32bit EFI is not going well for me though... )

Also, the[ Ubuntu Radeon page]("https://help.ubuntu.com/community/RadeonDriver") lists the X1300 as fully supported with a clause after the list of: "... equires Ubuntu >= 12.10 or updated package ..."
I've fully updated my install so I"m ?assuming? I qualify?

I'm now trying to configure/make a newer 32bit Grub2 for the Xserve to see if this is actually the problem, but I'm hitting a snag with not being able to [grub-mkimage as I don't have the sh.mod installed]("http://blog.christophersmart.com/2009/07/23/linux-on-an-apple-xserve-efi-only-machine/") (see Jens' post by searching for "cannot stat sh.mod"
Not sure where to find this file now so hopefully someone can guide me soon...

Raoul.

---

