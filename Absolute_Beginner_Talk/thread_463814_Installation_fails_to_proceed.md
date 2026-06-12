---
title: "Installation fails to proceed"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by salalejo on 2007-06-04
I'm new to Linux, just want to try it out.  Attempting to install Ubuntu 6.06 on Compaq Presario SR1222NX with specifications here: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00256286&lc=en&cc=us&dlc=&product=437888#N380](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00256286&lc=en&cc=us&dlc=&product=437888#N380)

Install is pretty quick until it gets to the desktop looking thing (someone tell me if that's actually what its called).  I click on the install icon and it takes about 10 minutes for a window to appear.  I get to a window that says install on top with what is supposed to be asking me for my language.  After 30 minutes, its still there.  The CD is still making sounds, no clue what is going on.  Tried using Ubuntu 7.04 but it gave me the same results.  Hardware issue?

---

### Post by salalejo on 2007-06-04
Just a second ago, a list of languages ust showed up but I don't have any option for "OK" or "Continue" or anything of the nature to indicate that I should continue.  Now what, should I play another (half-hour) waiting game?

---

### Post by mlentink on 2007-06-04
Your Compaq has 256 MB of memory, which is pretty basic. BUT...
It also has an integrated video board, which uses part of your RAM. That brings your memory under par. I'd try adding memory before anything else.

---

### Post by jvictor on 2007-06-04
Does your CD/DVD drive work correctly on windows ?

---

### Post by salalejo on 2007-06-04
Disc drive(s) (both of them) were working fine.   I burned Ubuntu 7.04 on it.  However, this install of Ubuntu 6.06 that's currently running was burned on another computer running Windows Vista Business and I made sure the MD5 checksum thing matched like it said on the website.

---

### Post by pappapump on 2007-06-04
Also, keep in mind that for some reason the install hangs if you don't click something on the selection screen, even if its already selected.
Thats happened to me a lot.

---

### Post by salalejo on 2007-06-04
Now that the languages popped up, I selected English ever so slowly and then clicked on "Forward" (ever so slowly).  Now its just kind of hanging there, CD drive is making no sounds.  Is this very bad?

---

### Post by candtalan on 2007-06-04
> **salalejo said:**
> I'm new to Linux, just want to try it out.  Attempting to install Ubuntu 6.06 on Compaq Presario SR1222NX with specifications here: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00256286&lc=en&cc=us&dlc=&product=437888#N380](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00256286&lc=en&cc=us&dlc=&product=437888#N380)

Install is pretty quick until it gets to the desktop looking thing (someone tell me if that's actually what its called).


You are first booting and then running the 'Live CD' - this is the desktop looking thing. The Live CD is fully functional, and runs (albeit slowly) in RAM. You have the minimum recommended RAM for Live CD use, so it should work. You mention it gets to this stage quickly. In your machine  (P4 2.9GHz 256MB ram) that is expected. In a machine I have - a PIII 450MHz 394MBram, the Live CD takes 6 minutes to get to the desktop. 

Following clicking on the install icon on my PIII machine it takes one and a half minutes to get to the first Install window, a Welcome and Choice of Language.

> **salalejo said:**
> 
  I click on the install icon and it takes about 10 minutes for a window to appear.


(The language choice window?) I have sometimes had an MD5sum check ok in one machine, but the CD still gives trouble in another apparently normal machine. I would suggest that you use the target machine and your chosen Live CD, and using the actual CD choose the  'Check CD for defects' from the live CD boot menu. This will verify that your machine and CD data are ok together. If you get a problem, try burning the CD more slowly than the maximum speeds. I use half rated speeds or I sometimes get trouble.

good luck

---

