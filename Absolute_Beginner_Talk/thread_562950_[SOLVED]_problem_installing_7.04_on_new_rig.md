---
title: "[SOLVED] problem installing 7.04 on new rig"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by ubunoobie on 2007-09-29
Hey everyone... ok, here is the problem I am having. I just built a new desktop and tried to install 7.04 on it. I got this message after the first graphical screen from the live cd (where I selected "install/boot"):

[     23.725990] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[     23.905030] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot w
ith apic=debug and send a report. Then try booting with the 'noapic' option
[     23.905074]

Can anyone tell me what this means and what I need to do?

My specs are:
- Asus M2N mobo
- Asus EN8400GS
- Seagate HDD (from an older Dell, with XP already on it)
- Lite-On DVD-ROM/CD-RW combo
- AMD X2 4400 Brisbane
- Transcend 2GB RAM

I don't think I'm having hardware compatibility issues... I've looked at the compatibility lists, and I'm pretty sure I'm clear. Anyway, let me know if I need to provide any other details. Thanks!

---

### Post by Pumalite on 2007-09-29
Try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by southernman on 2007-09-29
It appears (perhaps wrongly so) to me, that APIC is disabled in the BIOS for some reason. Either by default (which shouldn't be the case on newer hardware), or by you.

If after confirming APIC is indeed on in your BIOS, when booting the cd again, press "e" and add "ith apic=degug" to the first kernel line and report the errors here, as well as filing a bug at launchpad. Then do the same thing but add "noapic" to the first kernel line.

I WAS WRONG! (TM) :p

---

### Post by southernman on 2007-09-29
Just so you don't feel alone, I curiously searched the first line of your error at google and [here are the results]("http://www.google.com/search?q=MP-BIOS+bug%3A+8254+timer+not+connected+to+IO-APIC&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

---

### Post by ubunoobie on 2007-09-29
Thanks a lot, you guys.... I looked at those other threads linked through the google search and simply disabled apic in my BIOS and now it seems to be booting, I'm about to install now. I shoulda known to do a google first, lol...thanks anyway!

---

### Post by southernman on 2007-09-29
> **ubunoobie said:**
> Thanks a lot, you guys.... I looked at those other threads linked through the google search and simply disabled apic in my BIOS and now it seems to be booting, I'm about to install now. I shoulda known to do a google first, lol...thanks anyway!

No worries on not searching Google first. It was help you sought, and help you got... directly or indirectly makes no difference. 

Glad you got it solved though. Mind marking your post as solved so other helpers don't come by to later realize it's working for you. Thank you

---

