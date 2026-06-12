---
title: "Booting from Live CD problems"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by zantzinger on 2007-03-13
Hi
I downloaded and burned the ISO of Ubuntu 6.06. I then restarted my laptop (Dell 8100, PIII 1GHz, 512MB, 40GB, XP Pro SP1) and then didn't know which option to choose. I chose "Start or Install Ubuntu" and after some files were loaded the computer hung on a blank screen. I forcibly switched the laptop off and tried again, this time choosing "Start from Safe Graphical Mode" (or something like that) and after the same start I got these messages:

...
loading hardware drivers...
hw_random: RNG not detected
BUG: soft lockup detected on CPU #0!


I don't have Ubuntu installed on my system as yet, but I thought I could boot from the CD and check it out.

By the way, I also tried the "Check CD for errors" and no errors were found.

I did not try "Boot from first hard disk".

Any help would be really appreciated.

---

### Post by raidlost on 2007-03-13
Try a distro called simply mepis the live cd boot is very close to most debian based linux and I have had no problems booting numerous laptops with it

as for an install --- you may need to use the laptops recovery disks to prepare a partition for Ubuntu first, don't forget the swap

---

### Post by zantzinger on 2007-03-18
Mepis works like a dream. Thanks so much

---

### Post by Kobalt on 2007-03-18
You could have managed to boot from the Ubuntu disk with the 'noapic nolapic' boot options though ...

---

