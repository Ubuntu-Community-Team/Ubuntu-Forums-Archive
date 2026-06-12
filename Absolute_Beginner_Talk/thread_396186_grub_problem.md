---
title: "grub problem"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by stavpal on 2007-03-29
So, like, I had installed ubuntu for weeks, I pressed Cltl+Alt+F3 a couple of times, the pc froze, I had to reset, and now it doesn't boot linux!
I just get a "GRUB" and doesn't continue to the <select kernel> screen  (2.6.17.11, 2.6.17.10)
I have dual boot xp/ubuntu (xp loader loads grub and from then I load ubuntu). Grub is in the ubuntu partition. What can I do to fix this?
Help!

edit: nevermind, I ended screwing it up and I'm doing a complete re-install. d@mn

---

### Post by be4truth on 2007-03-31
It is better to learn how to fix this type of problems than to reinstall all the time. This is a Windows habit. Reinstalling a system costs you hours of configuration. The problem could have been fixed in minutes. Next time give it a few hours until people can answer your post.
Have a nice day and remember the first 2 years with linux is a challange, then it is fun only. In the end you are in bliss but somehow bored. Enjoy the first 2 years ...

---

### Post by alien21010 on 2007-03-31
Yeah it was probably about a 5 minute fix...  All you probably needed to do was rebuild the /boot/grub/menu.lst file, which could have gotten corrupted, or at the worst case scenario, reinstall grub.

---

### Post by Doug11 on 2007-03-31
Check this out,,should work for you

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by GSF1200S on 2007-03-31
> **alien21010 said:**
> Yeah it was probably about a 5 minute fix...  All you probably needed to do was rebuild the /boot/grub/menu.lst file, which could have gotten corrupted, or at the worst case scenario, reinstall grub.

You know, I got really lucky when I installed Ubuntu... My DVD RAM drive wont burn (had to have my buddy burn the edgy ISO) so I couldnt backup anything on my Windows partition. I wanted Linux so bad, I said screw it and started to install/partition. I actually made a mistake and put the partition slider all the way to the left, thinking 30GB would be partitioned for Linux. I realized that it was reversed (windows would be shrunk to 30GB) and I cancelled. Windows still booted and ran chkdsk, and I installed with the slider in the right place. Ive lost no data on XP, grub loads without a hitch, and Ubuntu is writing this message right now- SOOOOO lucky its not even funny...

I wanted to ask though as "in case it happens later," if I ever boot up and grub fails to load anything, what should be my course of action? Being Navy, im out in the middle of the ocean sometimes with no access to the internet. Can I get grub on disk? Is there some file I could load if Grub crashed (never happened so I dont know)? I think a lot of people could benefit from knowing this...

---

### Post by antoz on 2007-03-31
the link below might be helpfull

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Bigbluecat on 2007-03-31
GSF1200S

What you want is SuperGrubDisk. You can find it here:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Burn an ISO CD or create a grub boot floppy from this.

This together with Herman's site from the previous post will give you all you need to solve any boot problem.

---

### Post by GSF1200S on 2007-03-31
Awesome.. thanks alot. Its good to be prepared for it rather than blindly staring at a command prompt with no internet and no clue what to do... lol

---

