---
title: "help with mac-fdisk in hardy for USB install"
date: 2008-09-08
forum: Apple Hardware Users
---

### Post by brentb21 on 2008-09-08
I have an interesting install issue. I am trying to get a usb flash stick formatted using mac-fdisk. all the live cd's of various linux flavors I've downloaded (knoppix, backtrack, ubuntu hardy, debian) don't seem to contain it. I've attempted to download the mac-fdisk package in ubuntu but am assuming it can't rewrite it to the live cd, so no luck there. I have a macbook pro with osx on it, not able to install any other OS'es on it though and the flashstick, once formatted, will be used to install an undecided flavor of linux on a ibook G3 that has no working cd drive, nor an operating system on it currently. Because of booting the flashstick through the ibooks open firmware method, it has to be formatted with the new world apple bootstrap partition, and as far as I know fdisk and cfdisk don't support this format.

Which linux Live CD is compatible with the macbook pro duo core, and contains by default mac-fdisk?

is there another free app that will format and partition the USB stick to my needed specs?

even better, is there some way to transfer necessary install files to the ibook and do a Hard drive install? (No OS on it at this point)

thanks for all your help.

---

### Post by pxwpxw on 2008-09-09
mac-fdisk does not seem to exist in intel binaries, just tried it for macbook, it is only for ppc (ibook ).

However, you dont really need an apple bootstrap partiton or blessing to boot usb on an ibook from open firmware. just a macos extended (not journalled) or macos standard partition, which you should be able to do to the usb stick from macosx on the macbok pro.
 Then you just 0> boot hd:,yaboot on the usb from ibook openfirmware, 
instead of 0> hd:,\\:tbxi. 

you can also put an install iso file on the usb stick and use hd-media install images vmlinux and initrd to install direct from the iso (and try booting them from open firmware first).

Might also be possible to use firewire target mode between the two macs for transferring files,  not sure about that between macintel and ppc, will try it. Yes that works - between a macbook and a target ibookg4.

---

### Post by brentb21 on 2008-09-09
Thanks for the info, Trying that now.

---

