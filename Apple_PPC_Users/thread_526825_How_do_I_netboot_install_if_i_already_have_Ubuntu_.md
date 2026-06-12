---
title: "How do I netboot install if i already have Ubuntu on HD?"
date: 2007-08-15
forum: Apple PPC Users
---

### Post by gvigorus on 2007-08-15
Hi. I already run Xubuntu on my Powerbook lombard. I installed this Xubutnu via netboot from OS X where I placed four netboot files to root directory and booted into Yaboot from Open Firmware.

Now, i want to re-net boot, partition everything from the beginning. But i do not have OSX anymore...

How do i do this if I already run Linux? In openFirmware when i type: boot hda3,yaboot it just loads my current Xubuntu kernel and everything else.

Thanks for any help!

---

### Post by pxwpxw on 2007-08-16
You need a small hfs (macos standard) partition somewhere to put the net install images on.
It only needs to be big enough for that (say 30MB). Then you boot yaboot from open firmware, as for the install from the original  macos partition. 

This partition can be -
1.  on the hard disk, using a spare partition if there is one, or by stealing your swap partition if you have one, or by carefully resizing your root partition. Then you leave it there for the next time.

2. On a USB flash stick (or any other external  i suppose, or floppy disks)


The partition needs to be formatted using the hfsutils package you should have installed (see man hfsutils), hformat does the formatting. 

The safest way is to use the USB stick, but some suppliers USB sticks dont work, you may need to try a few . Be prepared to go carefully, because you have to use your existing Ubuntu installation to set it all up. 

The other way is to do a net boot from another computer via ethernet. See the Ubunutu or Debian Install docs.

---

### Post by gvigorus on 2007-08-16
Thanks for the info! This is helpful. The reason I want to reinstall actually is because my current installation gives me error on boot PCI:Cannot allocate resource region so and so. My PCI slot loading Orinoco Wifi card does not work. So, i thought maybe if I reinstall Ubuntu with Orinoco plugged in, it'll get detected and will work. What do you think, is it worth a try? Thanks again.

---

