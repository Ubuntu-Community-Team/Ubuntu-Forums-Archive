---
title: "Difficulties Starting Ubuntu"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by P235 on 2006-12-11
When Ubuntu is running properly I have no complaints, but the first start of the day is the most difficult one.  After I log in, typically everything will load up properly, but I know better.  I have this habit to open up alsa mixer to tweak the volume so that sound comes through both speakers because the laptop usually emits sound only from the right speaker on the first start of the day.  However, when the alsa mixer window does not appear - which is expected - I restart my computer.  

After the second time I log in, I'll be able to see the top and bottom panels, but none of the applets or menus.  Typically the mouse will freeze and ctrl/alt/backspace is unresponsive so I am left with no choice but to follow the instructions in my siggy link:  alt/prt sc/s, alt/prt sc/u, alt/prt sc/b.  I repeat the process a number of times only to be greeted with a frozen and incomplete desktop.  

For fear that I have to run fsck again I run my live disk, but not without having to reboot a few more times to coax my laptop to run the live disk properly.  After running fsck on /dev/hda2 and /dev/hda3 I learn that nothing is wrong.  It is now, after having coaxed my laptop to run the live disk and having run fsck that I know my laptop will run properly.  Today was exceptionally bad because I can usually get my laptop running within 3 reboots, help?

---

### Post by wpshooter on 2006-12-11
Do you have M/S windows O/S also on this computer ?

Did you check your Ubuntu installation CD's integrity by running the verification function found on the initial Ubuntu boot screen menu before you installed the O/S ?

---

### Post by P235 on 2006-12-11
Ah, sorry, I should have provided more detail.  Only Ubuntu is installed on my [HP Pavilion N5495 laptop]("http://www.if.pw.edu.pl/~kisiel/laptop/hplinux.html").  I did not check my install CD integrity though.  I'll start the check at my next earliest convenience.

---

### Post by wpshooter on 2006-12-11
Not to says that this is your problem in this particular case BUT always checking the integrity of your CD before installing is vitally important.

If your installation CD comes back with Zero integrity errors, then write back and we will look at it further.  If your CD had integrity errors, my advice would be to download and reburn the CD at 4X or less and give the install another try.  If you have to do this I would highly advise getting the **KILLDISK** program and **WIPE** your hard drive completely clean and then reinstall from scratch.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by P235 on 2006-12-11
The CD came back with zero integrity errors.

---

### Post by P235 on 2006-12-11
By the way, I tried checking the logs to see if I could figure something out.  I couldn't find anything there, but my home folder holds a number of "core" files that I cannot open with a simple double click and they appear to be "program crash data".  Two of these files, named "core" and "core.4514", appear to have been created today, but the former has no bytes while the latter has 1.8 MB.  There's even a file with no name.

---

