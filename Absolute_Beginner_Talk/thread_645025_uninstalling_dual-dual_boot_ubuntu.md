---
title: "uninstalling dual-dual boot ubuntu"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by AlanRick on 2007-12-19
I had a dual boot system (MSTBOOT) which started different installations of win 98 SE (on a 2  hd pc).
Then I installed ubuntu which added another dual boot (grub) in front of mstboot.

I probably should have selected an advanced option during install to avoid installing grub, adding ubuntu to the mstboot menu instead. But it's too late now.

Anyway - having 2 boot menus is  a hassle (despite setting time-outs in both) and I'm not sure if I'm ready for ubuntu yet anyway so I'd like to go back to what I had before and retrying later.

But I'm a bit worried about the mbrs since the dual-dual boot is unusual.

I'm pretty sure that all I need to do is replace disk one with the disk image that I'd created with ghost before the ubuntu install and that will overwrite the mbr to what it was previously.

But  I'm worried that since some of the old windows installations were on the 2nd drive, where ubuntu was installed, everything is probably all squished up on that drive and the mbr pointers from drive 1 (c: ) will no longer match the boot routines on drive 2. (I don't have a ghost image of drive 2).

1. Am I right in thinking that restoring the drive 1 image will enable that to work as before?
2. Will drive 2 installations also work even though ubuntu was squeezed into the last partition (reducing that partitions size)?
3. Can I leave recovering the ubuntu disk space until after I've restored the ghost image?

Hoping someone has experience of a similar setup,
Alan

BTW: There's some excellent posts out their on de-installing, including this:
[URL="http://ubuntuforums.org/showthread.php?t=508927"] but I'm not sure if they apply to this dual-dual boot situation.

---

### Post by Fritzed on 2007-12-19
The windows boot menu isn't really a boot loader, it doesn't exist in the mbr.  If you would like to restore the windows boot loader, than the best way is to use the microsoft recovery console from the windows installation disc, but you will be left without the ability to start ubuntu.

Having two boot menus won't cause any problems, even if a bit awkward.  My best recommendation would be to modify the timeout for the windows menu in the windows boot.ini file.  This will at least shorten the delay.

---

### Post by AlanRick on 2007-12-20
Thanks Fritz,
But MSTBOOT is not the windows boot menu. It's a shareware that really boots different windows installations on my hard disks - very similar to grub.
I'm pretty sure the microsoft recovery console would delete the mstboot configuration so I won't do that.
I'll have to live with the time-out work-around for the moment and research ubuntu a bit more in case I can reduce the partition size through one of the tools.
Alan

---

### Post by meierfra on 2007-12-21
> I' m pretty sure the microsoft recovery console would delete the mstboot configuration 

It will not.   If you use "fixmbr" from the recovery console, only the MBR will be changed.  msboot will not be touched.   So after "fixmbr" you should  be able to  boot directly to the "msboot" menu.
(But if you decide to keep ubuntu, you will have to find a way to add ubuntu to the "msboot" menu)

---

