---
title: "[SOLVED] Unable to run audio programs"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-03-09
Hi,

So I was trying to get Rosegarden working, and it was complaining about the system timer resolution being too low, and failing to connect to the JACK audio server, so I searched the forums, as you do, and followed some instructions (like installing Ubuntu Studio, install a real time kernel, and some other things).

And after all that Rosegarden still gives these too errors...

Anyway now I can't even open Audacity...
When I click on it in the menu, nothing happens, however when I go onto the System Monitor the Audacity process is listed there, so I'm not sure whats going on...

Also when I try to play a song in Rhythmbox now, the second I click the play button, Rhythmbox crashes.

Please help somebody!

---

### Post by genus_001 on 2008-03-10
Do you have the Jack server still running when you open Audacity or rhythmbox?  That may cause some problems.

---

### Post by dwally89 on 2008-03-11
Ok, I managed to sort all out, turns out all it needed was a restart.

And because I put the GRUB menu as hidden, I didn't notice the new real time entries.

Does having two kernels installed take up alot of space on the HDD?
Approx how big are the kernels?

Thanks

(p.s. Rosegarden now starts without any error messages :-) )

---

### Post by forrestcupp on 2008-03-11
The Linux-image-generic kernel that I have is 63.8 MB.

You can find out the size of something by opening up Synaptic and finding the package that you are interested in, highlight it, and click the Properties button.  It tells you in there what the installed size is.

---

### Post by dwally89 on 2008-03-11
Thanks

---

