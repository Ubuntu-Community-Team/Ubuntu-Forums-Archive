---
title: "Dual Booting Ubuntu and Windows XP on a Macbook Pro (no Mac partition)"
date: 2010-07-04
forum: Apple Hardware Users
---

### Post by alas-poor-yorick on 2010-07-04
I have an old Macbook Pro (1,1) that I want to dual boot in XP and Ubuntu 10.04 Lucid. I had been dual booting OSX and Ubuntu, with rEFIt. Today I deleted the mac partition, after backing everything up of course.
It booted from the XP cd, formatted the partition correctly, but would not boot. ("Windows could not start because the following file is missing or corrupt: <Windows root>\system32\hal.dll. Please re-install a copy of the above file.")

Now it won't boot from any cd (xp or several versions of Ubuntu), holding down alt-option only displays a hard disk labeled Windows (and no cd), holding down c doesn't work, rEFIt does not come up, and I don't know what to do. How can I get it to boot from cd, and/or boot into any partition correctly?

Thanks. Sorry if this is already somewhere - if it is I couldn't find it.

---

### Post by alas-poor-yorick on 2010-07-05
Bump? I miss my computer... :(

Update: I tried to boot from the mac cd, but now it won't eject and holding down alt-option does nothing.

---

### Post by alas-poor-yorick on 2010-08-01
Well, it seems that my CD drive was broken. Had I been able to boot from CD, I think the solution would have been to boot from a rEFIt cd, install rEFIt to the EFI partition, boot into Ubuntu, and configure grub to boot Windows. What I ended up doing was opening up the computer to get the cd out, and then reinstalling ubuntu via usb cd drive. I haven't been able to set up a windows partition because the computer will not consistently boot from even a usb cd drive, but virtualbox works well enough for my purposes.

---

