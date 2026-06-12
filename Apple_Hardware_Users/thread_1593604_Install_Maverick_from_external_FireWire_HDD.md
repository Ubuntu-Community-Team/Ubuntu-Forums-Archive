---
title: "Install Maverick from external FireWire HDD"
date: 2010-10-11
forum: Apple Hardware Users
---

### Post by Die Mensch-Maschine on 2010-10-11
Hi everyone,

I’d like to dual boot my not so old MacBook Pro 1.1 (OS X 10.5 —*let's call it “Old box”) with Maverick. Problem is: it's optic drive is dead (it’s smiling: I can’t even physically insert a DVD in it). My other laptop (MBP 3.1 OS X 10.6.4 —*let it be “New box”) has much trouble with it's optic drive too, so installing it with the old box in target mode is out of the way until I can borrow another box.

I do not have a USB flash drive either. However, I do have a currently useless FireWire external hard disk drive (let it be HDD). So I’d like to make a bootable install disk out of HDD.

Here is what I tried:
[LIST]
[*]I tried to make a boot disk out of HDD using the USB boot disk tutorial from the current Ubuntu download page. The disk appears to be perfectly copied, but it does not appear in the bootable disk list when I boot the machine holding the “option” key.
[*]I tried to copy the latest boot.img + every file from the Ubuntu Installer ISO on HDD. The disk appears as bootable, but won’t boot.
[*]I tried to install GRUB2 on the HDD (from binaries found on these very forums) and to make boot the installer. The bootloader loads, but after choosing a config, doesn’t boot and says something like “You must load the kernel first”. So either it won’t work or I screwed the grub.cfg file — very plausible as I don’t even understand what a bootloader does anyway.
[/LIST]

So would any of you have any suggestion?

---

### Post by tpievila on 2010-10-12
I didn't quite get what you wanted to do. Did you want to make an external hard drive with Ubuntu installed, so that you can run Ubuntu from that? Or do you want to install Ubuntu to the internal hard drive using your external as a replacement since you don't have a optical drive?

When it comes to the first choice, I'm not sure you can. I do know for sure that my 2,1 Macbook refuses to boot legacy OSes from USB stick. Not sure if using firewire or different mactel will make a difference. In my case rEFIt just has this info: "Booting Windows or Linux from an external disk is not well-supported by Apple’s firmware.".

But the second option is possible, and indeed what I have done since my optical drive is fried (damn Apple hardware, even the Apple store tech says this is a common problem, and still they will charge almost 200EUR for a replacement). I created a usb stick with another Ubuntu, then dd'ed that stick onto a partition in internal hard drive in OS X, then booted that partition. Works fine.

---

### Post by Die Mensch-Maschine on 2010-10-12
The second, sorry if that wasn’t clear. I’m gonna try your solution tonight.

> I created a usb stick with another Ubuntu, then dd'ed that stick onto a partition in internal hard drive in OS X, then booted that partition. Works fine.

I currently have no Ubuntu box. So I guess I’m gonna try to dd an img built from an iso. I’m guessing something like ```
dd if=path/to/ubuntu.img of=/dev/rdisk0sN bs=1m
``` would work ?

---

### Post by tpievila on 2010-10-12
Yeah, if you can directly create an img, that works too. I didn't find out how to do it on OS X, all the hints were for Windows and Linux, so I just used another computer running Ubuntu.

The dd command is spot on. I marked the partition bootable in MBR, the type as 07 (0b would work too, I guess, or maybe it doesn't even matter) and booted it in rEFIt.

---

### Post by Die Mensch-Maschine on 2010-10-12
Indeed, installing from a partition of the internal hard drive did work.

Here is what I did:
[LIST][*]downloaded Ubuntu *alternate* iso (it did not work with the desktop edition) from [here](http://releases.ubuntu.com//10.10/)
[*]downloaded and unzipped the matching boot.img from [here](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/hd-media/)
[*][not sure it had any effect] installed rEFIt
[*]partition my hard drive as following: 30GB (current Mac OS X install), 47GB (for Ubuntu), 2GB (first for installer, then swap)
[*]rebooted the machine, updated the MBR using rEFIt tool. Rebooted to Mac OS X.
[*]```
diskutil unmount /dev/disk0sN
```where /dev/disk0sN is the partition on which I created the installer
[*]```
dd if=path/to/boot.img of=/dev/rdisk0sN bs=1m
```
[*]```
diskutil mount /dev/disk0sN
```where /dev/disk0sN is the partition on which I created the installer
[*]copied the Ubuntu alternate ISO (not file from the disk image, the disk image itself) to the Ubuntu Inst partition (the name should have changed).
[*]rebooted, rEFIt proposed to boot from the installer partition
[*]then, it was straightforward.
[/LIST]

Thanks for your help.

---

