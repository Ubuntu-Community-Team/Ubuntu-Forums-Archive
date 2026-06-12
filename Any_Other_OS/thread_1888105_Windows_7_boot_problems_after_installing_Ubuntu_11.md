---
title: "Windows 7 boot problems after installing Ubuntu 11.10"
date: 2011-11-28
forum: Any Other OS
---

### Post by whyttedragun on 2011-11-28
First of all, I'm sorry if this has been asked and answered somewhere else.  I used the search and found a couple posts about similar problems but nothing that matches exactly.

I set my computer up to dual boot Windows 7 and Ubuntu 11.10 (the 64 bit version of both).  Ubuntu boots with no trouble at all, but Windows 7 will start to load, get to the splash screen with the Windows logo, then the computer will restart.  Once it has, I select Windows 7 from the boot menu, then "boot normally" from the Windows menu that pops up because Windows didn't successfully start.  Sometimes Windows will finish booting then, and sometimes it takes 3 or 4 reboots before it works.
I tried using the startup repair from my Win7 install disk and reinstalling grub2, but the same thing still happens.
I'm relatively new to Ubuntu.  Is there something I'm missing?  I'd prefer to fix this without wiping the system, but if that's what it takes, that's what I'll do.

---

### Post by Mark Phelps on 2011-11-29
You may need to run Startup Repair as many as three times, to get Win7 booting working properly again.

But ... once you've done that, Win7 should be OK.

Are you accessing the Win7 OS partition while inside Ubuntu?

Are you hibernating Win7 and then accessing either the Win7 OS partition, or another NTFS partition -- from inside Ubuntu?

Either of these last two actions can cause problems with the Win7 OS filesystem.  So, if you are doing these, you need to stop doing them.

Otherwise, you should not be continuing to have problems with Win7 booting.

---

### Post by whyttedragun on 2011-11-29
I'm sorry, I should have said that I did run the startup repair 3 times.  I had seen that suggestion in another thread somewhere, so I tried it.
To answer your other questions, I always completely restart the computer before switching OSs, and I don't access the Win7 partition from inside Ubuntu (I only use Win7 for games - anything else I do in Ubuntu, so any files I need are in the Ubuntu partition).
I'll try doing the startup repair another 3 times, just in case I somehow goofed last time.  I'll post the results when I'm done.

---

