---
title: "Booting from CD"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by scimitar on 2006-01-04
I have downloaded Ubuntu and burned the cd. It works fine but i cant get it to boot on the machine that I actually want to use it on. It looks at the cd, then just carries on booting windows :( is there someway I can kinda boot it manually or fix this problem?

Regards

Al

---

### Post by Asix on 2006-01-04
That's probably because you haven't burned the boot record on the CD, too. Maybe if you try ISOBuster program, it can help you with that stuff.

---

### Post by Norberg on 2006-01-04
To boot from a cd you must change boot priority to boot from cd before hd, it can often be done when starting the computer by clicking del or F2.

---

### Post by Janzuka on 2006-01-04
Have you selected cd-rom as the first booting device in BIOS? Probably you have, but if you haven't that has to be done.

---

### Post by scimitar on 2006-01-04
Yea i've done all that! That's the weird thing! It works on all my other machines :S

---

### Post by hobbit1983 on 2006-01-04
What BIOS do you have on your target machine - then I might be able to give some more advice.

---

### Post by scimitar on 2006-01-11
It's an older version of this [url]http://www.giga-byte.com/Motherboard/Support/BIOS/BIOS_GA-7IXE_More.htm[\url]

I could flash it but its like version 2 I have on this machine and as i understand it  you're not supposed to skip loadsa upgrades like that?!

From what i can remember it booted from the windows xp cd ok. Any more ideas anyone?

---

### Post by jerrykenny on 2006-01-11
There is an article somewhere on Debian with a solution for this,  it involves creating a boot floppy which will load (or chainload) your cdrom.

Go to debian and try their problem installation help . . . it aught to very relevant, ubuntu is a debian derivative.


I wouldnt flash the BIOS unless really necessary.

---

### Post by johnnymo87 on 2006-01-11
Here's ubuntu's official guide on burning ISOs: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto) [Once you've obtained the CD image, burn it to CD with this guide]

---

