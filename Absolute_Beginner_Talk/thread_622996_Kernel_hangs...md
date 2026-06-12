---
title: "Kernel hangs..?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Zoiked on 2007-11-25
About every 10 minutes I get to use Linux my whole computer freezes up. I can't do anything, not even CTRL + ALT + BACKSPACE or switch to a different run level. I checked and all my hardware seems to be compatible. 

My Hardware is...
Asus A8R-MX (OEM Board) If you can find a Bios update, that would be great. 
Athlon 64 3500+
1GB Ram

I have had this problem before but I remember it just went away, and recently I reset all my settings in my bios back to default and know I have this same problem. I pretty much tried to change every setting known to man but it just doesn't work. 

Anyone know of a solution? Also, It does this for every distribution I try(Fedora, OpenSUSE, PCLinuxOS, Kubuntu). 

What are some things that I might need to change in the bios(I already know that plug in play needs to be set to no)? 

What happens if I completely turn ACPI off, is that going to effect my hardware stuff? 

Thanks.

---

### Post by Aniongap on 2007-11-27
Try to turn acpi off for first.

Seems like you have 64 bit proc. What kind of linux? 32 or 64 bit?

---

### Post by natehatewindows on 2007-11-27
do you know how to boot acpi=off?

---

### Post by jfinkels on 2007-11-27
Is there anything funky in /var/log/kern.log?

---

