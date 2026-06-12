---
title: "PowerBook G4 PPC Hard Drive Boot (without a cd)"
date: 2013-01-29
forum: Apple Hardware Users
---

### Post by E411 on 2013-01-29
Hi there,

I intend to install ubuntu on a PowerBook G4 through a hard drive boot.

I found [this document]("https://help.ubuntu.com/12.04/installation-guide/powerpc/boot-drive-files.html"), but I am still confused: it says "the installer cannot boot from files on an HFS+ file system". Does this apply to the four files to copy to  the root level of the hard drive  (vmlinux, intidrd.gz, yaboot, yaboot.conf) or to the rest of the files? 

In other words: is it ok to format an HFS partition where to put all the files while the four files above are copied to the root level of my existing (HFS+) partition?

---

### Post by rsavage on 2013-01-30
You need to put the four files where they can be seen from openfirmware and on a partition that yaboot (the bootloader) can work with.  For example, although you can see a FAT16 partition from openfirmware, I know yaboot is pants with FAT and it doesn't work.  
 
Whether this is the same for HFS+ I don't know, but openfirmware and yaboot definitely works with HFS.  
 
When you install the usual thing is to create separate bootloader, root (usually a linux type like ext4) and swap partitions.  The installer will sort it out for you if you've left free space on your drive (i.e. no partition occupying the space).

---

### Post by E411 on 2013-01-30
Hi rsavage,

I decided to go for a usb boot instead. I copied the iso using dd and could locate my usb stick as usb0 through devalias

But none of the booting commands works for me in openfirmware

```
boot usb0/disk@1:2,\\yaboot
```gives me "couldn't locate PARTITION can't open usb0/disk@1:2,\\yaboot"

and 
```

boot usb0/disk@1:1,\\yaboot
```

just "can't open usb0/disk@1:1,\\yaboot"

also tried all the variations like
```
boot usb0/disk@1:2,\install\yaboot
```

the only dir command that doesn't give me "can't open the dir device" is
```

dir usb0/disk@1:1,\
```

output is just

```
ok
```

Any suggestion?

---

### Post by rsavage on 2013-01-31
If you are certain it is usb0 then it is probably the dd command.  Flash devices often don't like it.  There is a link in the booting USB section of the FAQ that links to a thread I wrote about using grub2.  That is the (almost) guaranteed way to do it.  My instructions for booting the mini/alternate are not very good though - see if you can figure it out.  You could alternatively format the USB device as HFS and do like you were going to do in post 1.

---

### Post by E411 on 2013-01-31
I followed the post you mention but for some reason OF would'nt boot from the usb stick (although I found /fat-files in /packages) so I decided to use my hard drive instead.

I moved all the files (ofboot.b, grub.conf, grub.img and the iso) to the first partition of my HD and I could indeed boot ofboot.b with "boot hd:9,\ofboot.b"

grub starts, however, I don't get any menu, just the grub prompt

```
grub >
```Is there something I am missing here?

Edit: from there, could set root and isofile but not sure about the rest as "loopback loop $isofile" gives "unknown filesystem)

---

### Post by rsavage on 2013-01-31
It is set to boot off the first partition, but you are booting hd:9.  At the grub prompt you need to do something like:

configfile (grubdevice,9)/grub.cfg

You'll then have to edit the menu entry to also point to partition 9.

Not sure what you are doing now - is it a live ISO?

---

### Post by E411 on 2013-01-31
> **rsavage said:**
> 

Not sure what you are doing now - is it a live ISO?

It is lubuntu-12.10-desktop-powerpc.iso

Am I doing something weird? 

Was trying to boot on the usb stick but it wasn't working and yaboot won't work on my HFS+ partition.

---

### Post by E411 on 2013-01-31
Dunno if I was doing something funny, but Lubuntu booted somehow. 

So I was indeed booting a live version while I was trying to install it (hence your question I suppose) but now it seems I can install it from there, right?

Graphics look funny though (pixelized) but it seems to be working.

---

