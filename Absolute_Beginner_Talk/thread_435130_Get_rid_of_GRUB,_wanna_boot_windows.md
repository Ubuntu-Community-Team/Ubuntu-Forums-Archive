---
title: "Get rid of GRUB, wanna boot windows"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by trunks14 on 2007-05-06
I've been having problems with my configuration since i installed Ubuntu in my system, the configuration is like this:

-Pri Master HD with Windows, jumper set to Master
-Pri Slave HD with ubuntu, jumper set to Slave

It will randomly boot or not boot, sometimes the POST screen pauses to detect Pri Master/Pri Slave, and sometimes it goes straight to the GRUB menu ¬¬

The problem is definetely with the second hardisk i added when i installed ubuntu, tthat is, the one which is currently set to slave, it's damaged or something since i was using ubuntu and it suddendly froze, not even Windows XP freezes nowadays so... What i want to do is drop the damaged HD, buy a new one and proceed, but right now if i remove the Slave (in which ubuntu is installed) it will complain and not boot, so i want to restablish the microsoft bootloader or something  but i don't know how to do this, help me out please, i don't wanna go through the trouble of repairing my Windows installation with the Windows XP disk X_X

---

### Post by Nekiruhs on 2007-05-06
Xp doesn't freeze? Thats news to me.

---

### Post by mikewhatever on 2007-05-06
Check this out [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
I think the Super Grub or FixMbr.exe should work for you.
> Xp doesn't freeze? Thats news to me.
Never had it freeze too. :)

---

### Post by rygar on 2007-05-06
remove the second hard drive from your system, the one with Ubuntu.

boot to an XP cd.  go into the recovery console, and type "fixmbr"

that should do it.  if it still doesn't work, it's possible that your XP boot sector is corrupt--you can try doing "fixboot" from the recovery console.

---

