---
title: "Ubuntu PPC DVD won't boot powerbook"
date: 2005-05-02
forum: Apple PPC Users
---

### Post by muzza on 2005-05-02
Someone gave me a copy of the UbuntuPPC DVD, the one with the 'main' repository included.

I think the DVD was burned on a PC.  Would that cause it to not boot?

I remember seeing an option to make a CDDVD bootable the last time I used Toast.  (I don't have access to OSX at the moment as I've installed UbuntuPPC over it.  I couldn't work out the partitioning, so I formatted the whole disk) Is it possible to burn a bootable Mac DVD on a PC?

BTW, I eventually installed Ubuntu PPC from another CD, but I still want to make the DVD  bootable.

---

### Post by Len on 2005-05-05
If the image was burnt without modification it *should* boot on your Powerbook. Is the DVD readable by the computer? And (sorry, stupid question but to be sure) are you sure it is the PowerPC DVD? Actually I never have seen a downloadable DVD here on the mirrors, at least not for PPC, but then again I didn't look at them for a while...

You can try holding the 'alt' key if you power on your mac. It lists all bootable disks and let you choose one. The Linux CD should have a cool penguin over it and be selectable. Your Linux partition will also be listed.

---

### Post by muzza on 2005-05-05
The DVD exists.

Here is the URL; [http://cdimage.ubuntulinux.org/dvd/current/](http://cdimage.ubuntulinux.org/dvd/current/) 

I'll try holding down the alt key as you suggested, but I already know that it won't boot up.

Do you think that I could re-burn the dvd with maybe toast,but ensure that it is marked as 'bootable'?  Or would the boot information be lost now?

---

### Post by Bug on 2005-05-06
I think it's the option key on an Applekeyboard. But that only works with open firmware (New World) machines. 

If you can't boot it directly fromt he DVD, you can always copy over the kernel and the ramdisk from the DVD to you System folder, grab bootx, and use bootx to boot it up. Or yaboot if you have a new world machines.

Bug

---

