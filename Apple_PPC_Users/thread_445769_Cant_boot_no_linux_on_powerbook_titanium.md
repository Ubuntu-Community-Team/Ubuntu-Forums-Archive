---
title: "Cant boot no linux on powerbook titanium"
date: 2007-05-16
forum: Apple PPC Users
---

### Post by vlaad on 2007-05-16
Installed Ubuntu 7.04 alter on PB titanium 550mhz,. Installation went fine in text mode but when try to reboot system goes to X and screen goes all colors wierd and then goes black. Tried ctrl-alt-F1 to log in text console, but then get black screen flickering. 
Tried video=ofonly, the same problem with the screen.
Tried rescue, the same...
Tried with installing Ubuntu 5.04 & 6.06, Xubuntu 6.10, Fedora Core 6, but all the same - no way that i could boot at all. 
CD-s are ok since installing on other machines went without problems.
Ideas?

---

### Post by Abandon on 2007-05-16
What other machines? Same architecture? A Powerbook Titanium comes with a PowerPC processor and the latest editions with a intel processor.

Could it be that you install a 386 architecture on a PPC box? If so, use the PPC version. Mind the differences (yaboot)

---

### Post by vlaad on 2007-05-16
The same architecture, PPC. Everyhing works fine on my powermac b&w 300mhz.
The problem is graphical system X (i guess), but the thing is i cant even login in console to try to fix xorg.conf...

---

### Post by stmiller on 2007-05-16
I have a 15" TiBook 867Mhz. I can post my xorg.conf if that helps. I did not have any problems, and Feisty worked automagically with my display.

To repair the xorg.conf file you can boot into single user mode by typing this at the yaboot prompt:

Linux single

---

### Post by gpi on 2007-05-18
Hello , 

I have some time flickering screen with console mode as well as with xorg display...
The flickering starts after the kernel loading (when the (K)Ubuntu image is shown).
For me it is a problem of compatibility with the kernel... 
Notice that I had the same problem with Debian ( kernel 2.6.18 )...

Stop the machine, wait a minute and boot again... for me that solve the problem (temporarily).
Regards,

geoffroy

---

### Post by vlaad on 2007-05-19
no luck for me & linux on pb titanium 550.
the list goes like this: Ubuntu 5.04, 6.06, 7.04, Xubuntu 6.10, Fedora Core 6, Yellowdog 4...
all working fine on desktop G3.
must be something with the graphic card (ati rage 16mb)?
giving it up...

---

