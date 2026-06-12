---
title: "Evince-Thumbnailer causing 100% CPU Usage?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by SendDerek on 2007-01-07
Hey All!

I have a very fresh install of ubuntu 6.06 (dapper) on my Wife's desktop system (specs at bottom).  I noticed that the CPU was at 100% according to the system monitor.  I ran "ps aux" in the terminal and found that a process called evince-thumbnailer was using 95% of the CPU.  

I then went ahead and ended the process via the system monitor and now everything is back to normal again.  

Like I said.  This is a fresh install (as of this morning) and I installed all the updates when I installed it (including evince).  Is there any reason I should worry about this system process?  Has anybody else experienced this problem?  And how would I go about fixing it?

Thank you in advanced!

System Specs:
P4 2.4GHz
Terminator T2-P Asus Barebone (Intel 865G)
1024MB PC3200 SDRAM
80GB HDD

---

### Post by meng on 2007-01-07
I assume you had a PDF open at the time, and your experience would make sense if it was many pages and graphics-intensive. I believe evince is a bit slow to render graphics in PDFs.

---

### Post by SendDerek on 2007-01-12
What's strange is that I didn't have any .pdf's open at all.  It seems to be gone now.  I just rebooted and it's not there anymore taking up 100% CPU.  Thank you for the reply though.  I think this is resolved for now.

---

### Post by Ruth Lazkoz on 2007-01-30
> **SendDerek said:**
> What's strange is that I didn't have any .pdf's open at all.  It seems to be gone now.  I just rebooted and it's not there anymore taking up 100% CPU.  Thank you for the reply though.  I think this is resolved for now.

Hi,

I have the same problem. Evince thumbnailer takes up 100% CPU (fortunarely) I have a dual core. I get this problem when I go to Nautilus and ask it to open an eps file with Gimp.

If I firts open Gimp and call the file from the menu I do not get the problem, and rebooting is no 
cure.

Any hints?

Ruth

---

### Post by tanemahuta on 2007-04-30
try installing the package gs-gpl (if not already installed) and use galternatives or update-alternatives to change the alternative for gs from gs-esp to gs-gpl. worked for me!

---

### Post by mingotta on 2007-05-27
in my experience, evince-thumbnailer eats up all my RAM and increases my swap space steadily up to an unusable pc state, rather than eating up all my CPU cycles.

---

