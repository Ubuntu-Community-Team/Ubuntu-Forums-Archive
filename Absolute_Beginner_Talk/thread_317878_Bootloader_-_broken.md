---
title: "Bootloader - broken?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by DavidNW on 2006-12-13
Hello, everyone.

I really hope you can help on this one! Okay, I'll try to cut to the chase on this one otherwise it's a long story.

I dual boot Mandriva 2006 and Ubuntu on hard drives 1 and 2 respectively.  Due to me screwing around with file permissions/ownership whilst in Ubuntu I managed to render my Mandriva partition on my first hard drive inoperable, as I could not boot into it!

Anyway, I eventually managed to fully restore the system because I had made a .tgz backup of the whole system!  Great, I thought.  However, and I don't know how, I have somehow managed to knock-out the bootloader menu, that on start-up, allows me to boot into either Mandriva or Ubuntu.  When I power-up the PC now &#8211; it boots straight into Mandriva &#8211; in other words, the bootloader menu has completely disappeared!

Can anyone help me out on how to restore the bootloader option menu so that I can boot into either OS?  I'm really stuck here as I have a lot of good stuff on Ubuntu, and have it set-up just how I want it (tweaks, etc).  

As a last resort, I'm thinking I could fully restore Unbuntu from an archive .tgz file that I backed up to a few days ago, but I'm wondering if this would fix the bootloader?  I'm dreading another Ubuntu re-install - I had everything set up so nicely!!  I really hope I will not have to start from scratch. :sad:

Many thanks,

David.

---

### Post by peterj on 2006-12-13
You need to edit the GRUB menu, 


[http://ubuntuforums.org/showthread.php?t=76652]("http://ubuntuforums.org/showthread.php?t=76652")

Should cover it.

---

