---
title: "Total Newbie wants to install 7.04"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Wobbler on 2007-06-26
Okay, wanting to install 7.04 on a Sony Vaio PCG-GR300P.  Pentium III 1.13 GHz, 256 MB Ram.  The LiveCD boots and runs flawlessly.  When I double click on the Install icon, I get a window which should let me choose my language and begin install, but instead I get a gray box with "Install" in the title bar.  The CD drive spins continuously and never seems to load anything.  I ran the disk check and everything was OK.  Any ideas on how I can get past this?

---

### Post by ugm6hr on 2007-06-26
Do you have a shared graphics memory laptop?  If so - it may be that the memory taken up by the graphics card has reduced the system RAM to below 256MB (which is the minimum to install from the LiveCD).

Might be worth trying the Ubuntu AlternateCD (or Xubuntu LiveCD if you want to try that).

---

### Post by murmelhunter on 2007-06-27
There is indeed an issue if you system have 256 MB RAM during the normal installation process.

The graphical installer is using quite a lot of ram and can not swap files temporarily to the hard disk since this feature only is working once feisty is installed.

But there is a solution

When you boot from the CD select from the option menu: install in text mode.

The installation will run with a reduced graphical and more text based interface.

This interface is very straight forward and quite logic,just follow the instructions I did even with this interface a dual boot set up.

Once the installation is complete you have will feisty smoothly with all graphical features.

The solution works also for computer with 128 MB of RAM, did an installation on an old compaq notebook and it worked also. ( just a bit slow)

Good luck and enjoy

---

### Post by Wobbler on 2007-06-28
Thank you both for the help.

Just to note from murmelhunter's post below: Install in text mode is not something I was able to take advantage of as this is an option from the Alternate CD, not the LiveCD.:D

---

