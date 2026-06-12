---
title: "USB boot vs radeonfb on Intel MacBook Pro 8,2"
date: 2015-02-02
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2015-02-02
On a MacBookPro 8.2, I'm able to boot the daily Desktop image for Vivid Lubuntu AMD64 via DVD but with USB stick it stops early in the process, shortly after the GRUB menu.  

The image starts booting in "insecure mode" and then GRUB comes up and offers several choices. When choosing "Try Lubuntu without installing" it runs for a few seconds and then freezes, apparently indefinitely. There is no way to get to another console with ctrl-alt-f1 or anything else.  

When I edit the boot parameters to take out "splash" and "quiet" I get more information and it stops right after these lines:

[i] [ 7.57234] [drm] radeon kernel modesetting enabled.
 [ 7.575302] fb: switching to radeondrmfb from EFI VGA
[/i]

It does not matter which USB stick try or which of the ports I try it in.  It stops at the same place.  

There is some kind of a work-around for Raring,

[https://help.ubuntu.com/community/MacBookPro8-2/Raring#Booting_from_usb_pen_via_EFI](https://help.ubuntu.com/community/MacBookPro8-2/Raring#Booting_from_usb_pen_via_EFI)

but the steps there seem not to apply to Vivid.  

What can I pass to the kernel to get it to finish booting?

---

### Post by maclenin on 2015-02-09
**Lars Noodén!**

I have been hawking [this guide]("http://ubuntuforums.org/showthread.php?t=2259849") which describes my recent (LiveUSB) xubuntu-to-MacBook install. Perhaps it'll shed a bit of light.... "My" MacBook's video card was nvidia - however, nomodeset deployment or some of the other research I did may lead to your "solution"....

Good luck.

---

