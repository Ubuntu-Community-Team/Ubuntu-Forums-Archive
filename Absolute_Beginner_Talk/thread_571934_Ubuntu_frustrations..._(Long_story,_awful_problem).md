---
title: "Ubuntu frustrations... (Long story, awful problem)"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Scarfman on 2007-10-09
Despite the "long story" title, I'll skip the pointless things. I have installed Ubuntu 6.10 onto my new 160GB external HDD. Now, the first time I tried this, I seem to have told the Ubuntu installer to install GRUB to my main HDD (my laptop win XP), and thus, booting from my external was impossible.
So, I installed it again, this time making sure that GRUB installed to the external, AND IT WORKED!!

BUT. Now, without plugging my external into the laptop, it was impossible to start up windows XP due to GRUB error 20 something.

To make things worse, I had no XP boot disk to fix my master boot record.

After about 2 hours of trying to find a boot disk from someone (seems that nobobody gives you bootdisks with your computer anymore), i settled for downloading MbrFix from some sketchy site in desperation. I ran fixmbr in it, and it actually worked! What's more? when i plugged in my external (after arranging my BIOS), the GRUB menu came up!

Oh, I was ecstatic, until I discovered that when GRUB started up, not only could I not run ubuntu due to the infamous error 17, but i could no longer run windows from the GRUB menu, either.



Current condition:

-Xp starts up when external is NOT plugged in.
-When external IS plugged in, the GRUB menu appears, but I cannot run any of the options.
-I am very frustrated due to this being my 5th day wasted trying to get ubuntu installed on a portable external HDD that i can take with me wherever I go.
- I am quite sad, for I fear I may have caused my poor laptop severe damage running that program I happened to stumble accross.

-But, I have learned a bloody lot using command prompt and terminal to fix all this bloody stuff.


Please help.
Pretty please?

P.S. I installed Ubuntu 6.10 from the Live CD

---

### Post by rsambuca on 2007-10-09
First off, I would say that the fixmbr site is not "sketchy", and it won't do harm to your computer.

---

### Post by Scarfman on 2007-10-09
Well that's one less problem :-D

---

### Post by steveneddy on 2007-10-09
didn't you post this same problem earlier as a different user?

---

### Post by Scarfman on 2007-10-09
No, I did not.

This is the first time I posted it, but if someone else posted the same problem, and it was actually solved, a link to that thread may be helpful.

---

### Post by steveneddy on 2007-10-09
Is [this your thread]("http://ubuntuforums.org/showthread.php?t=479550&highlight=boot+external+drive")?

---

### Post by Scarfman on 2007-10-09
Not my thread, but I'll see if any of this helps.

That thread's problem is the first problem I had, but managed to fix myself.

Now I just can't start Linux anymore.

---

### Post by tgalati4 on 2007-10-09
One of the challenges of using an external drive is that the Linux kernel enumerates the drives based on a hardware scan.  If your drive is plugged in then the drives get a certain assignment.  If not plugged in then the drives get a different assignment.  This will certainly mess with the boot process.

Feisty uses a UUID scheme which assigns a code number for each drive discovered and hopefully this keeps the mountpoints and drive assignments in place when external USB drives (or more internal drives) are installed.

Some folks experience problems with this UUID assignment.  The work-around is to wipe all references of UUID from your fstab and use the standard /dev/sda enumeration instead.

Not understanding how drive assignment works will cause fits.  Once you get it, it's pretty simple.  You have to waste a few days of install hell to appreciate how Linux handles hardware.

Windows doesn't have this problem.  Windows is coded such that there are no other operating systems besides Windows.  So it will always look for C: for the boot drive and there can only be one boot partition in the primary drive.

Solution:  upgrade to Feisty and hope that UUID assignment works as it is supposed to or learn how drives are assigned and make appropriate GRUB entries.  Learning GRUB is helpful.

---

### Post by Scarfman on 2007-10-09
Thanks! I'll spend some time learning how to use grub, and understanding all of the drive mounting spiffiness. Sounds like alot of work, but I'm sure it'll be a good learning experience.

And if that gets too frustrating, I'll upgrade. By the time i give up, maybe the ISO will be done downloading (slow internet)

Finally someone who doesn't just criticize my post and actually tries to help.
I appreciate it.
Tyvm

---

### Post by HermanAB on 2007-10-09
The drive assignment is handled by udev.  If you figured the other problems out on your own, then this will be easy and after fixing the USB drive, you can start to grow the junior-guru stubble!

Here is some udev info:
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)
[http://www.gentoo.org/doc/en/udev-guide.xml](http://www.gentoo.org/doc/en/udev-guide.xml)

This is relatively new and really deep Voodoo, good luck!

Cheers,

H.

---

