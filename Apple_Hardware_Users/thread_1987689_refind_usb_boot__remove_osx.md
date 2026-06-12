---
title: "refind usb boot / remove osx"
date: 2012-05-26
forum: Apple Hardware Users
---

### Post by sasasasasasa on 2012-05-26
I have a problem with kubuntu 12.04 on my mba 4.2

What I want is to migrate from dual boot with macosx/kubuntu to single boot kubuntu.

kubuntu is working fine and I have deleted my osx partitions and I wish to resize my linux partition to use the disk space.  I could just have a new partition easily enough but resizing is what I want.

I install rEFInd on my efi boot partition from linux and it boots linux A-ok even without the macosx partitions.  

My problem is it does not seem to want to boot from a USB drive (rEFInd does seem to see the USB drives) so I cannot move my "/" partition over the space freed up by osx deletion.

Booting with the alt key gets the EFI boot loader which offers me "windows" when I have a bootable USB key plugged in.  Problem if I choose this it thinks for a while then says "boot error".

The bootable usb disk was made with unetbootin and the kubuntu 12.04 +mac image here: [https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

This worked fine for the initial install.

So, could anyone tell me:

Using rEFInd (or otherwise) how to boot from the usb key? 
Alternatively any suggestions as to how to move the partition you've booted from!

Ta

---

### Post by sasasasasasa on 2012-05-26
Ok fixed in part - I was the script from here:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

To create the boot disk - then booted press the ALT button and selected the "windows" option which did boot to ubuntu.

Now I'm just waiting for gparted and we'll see it the machine will boot...

---

### Post by sasasasasasa on 2012-05-26
yep that all seems fine now - fully converted from dual boot to single boot linux.

---

