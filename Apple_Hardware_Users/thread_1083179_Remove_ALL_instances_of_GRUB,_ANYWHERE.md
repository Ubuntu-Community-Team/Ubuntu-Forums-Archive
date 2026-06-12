---
title: "Remove ALL instances of GRUB, ANYWHERE"
date: 2009-02-28
forum: Apple Hardware Users
---

### Post by FendersRule on 2009-02-28
I'm alittle PO'd at the moment, so bare with me.

I have 4 HDDs in my Mac Pro.

2 of them have RAID OSX.

The 3rd use to have a Ubuntu installation with Vista.

The 4th left empty (may have had a windows installation at one point).

Recently, I decided I did NOT want Ubuntu, so I formated the third drive, and installed Windows XP.

However, I am still left with the GRUB screen (it just wants me to push tab) when I try to boot into XP. If I boot from the apple firmware (alt), then I do not get the grub screen. If I boot to XP in OSX (boot device), then I get the grub screen (it just wants me to push tab). I did the whole "fixmbr" thing from the Windows installation CD, but I am still left with the grub screen only when I boot from OSX to XP.

I removed everything but my OSX HDDs, and turned on the Mac Pro. I get a "Grub Hard Drive Error". Restarted. Same thing. Restarted. Held down ALT, then booted into Mac OSX through apple's firmware boot screen. Now it restarts to OSX every time with not grub screen no matter which method.

This makes me believe, that Grub has also "infected' My OSX volume.

If I put my Windows XP HDD back in, and I boot to it from OSX, I just know I'm going to see that Grub screen again. I want it back to the way it was with GRUB completely purged.

How do I get rid of this entirely from my MOSX volume?

---

### Post by FendersRule on 2009-02-28
I put my XP Drive back in, reboot to it from OSX, and I get a "GRUB Read Error".

Restart. Boot into XP from Apple's Firmware, and it goes straight to it. 

In Windows XP, in the boot camp control panel, it seems my OSX drive as "Windows", and my Windows drive as "Windows".

So, it seems like Grub is indeed on my MOSX drive, and I need to get it out.

---

### Post by cyberdork33 on 2009-02-28
there is a thread here about clearing the info in the MBR, but beware of consequences. I am not sure it has been tested in your situation... If you have windows on the same drive, it is much easier (and safer) to just boot the Windows CD into rescue mode and use the FIXMBR command. 

In the future, on a Mac, it is usually more desirable to install grub to the Linux root partition rather than the MBR.

---

### Post by FendersRule on 2009-03-01
The only way of fixing this, is to either hexedit my MOSX partition to clean it of GRUB, or to reinstall OSX.

I went ahead and reinstalled OSX....

---

