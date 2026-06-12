---
title: "ubuntu 6.10 and 6.4 installers freeze"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by orionsbelt on 2007-02-15
i have a Dell Dimension 2350 and have tried installing both 6.10 and 6.4.  they've both hung at the same spot (black screen, white text instead of the friendly ubuntu graphics).  i'm positive that both CDs are fine (both were burned correctly, tested, and installed on other computers).  i have tried checking memory, checking the CD through the installer, and running the installer in Safe Graphics mode.

i just installed a new 250 GB hard drive, and installed Windows XP successfully on it.  i don't know if this is an issue, but i do have an ATI Radeon 9250 video card installed,but that also didn't give me any problems with the XP install.

so i'm not sure what's going on with the ubuntu installer.  :confused: help?

---

### Post by chuckyp on 2007-02-15
Some things to try would be to hit CTRL+ALT+F1 or F2-F6 see if a text console comes up.

The other thing maybe to try the alternate iso you will get a text mode installer.  During the text installer switching to terminal 4 will show you whats going on in the background i.e. CTRL+ALT+F4

---

### Post by orionsbelt on 2007-02-15
thanks for your suggestions!  it's nice to know people on the forums are so helpful.

it looks like i've got things working, no thanks to my frigging hardware.  first step:  taking out my ATI video card and using the on-board one.  that got me into the ubuntu installer.

then i was having trouble resizing my xp partition.  i trolled around the forums and found this WONDERFULLY helpful post:  [ACK! Can't resize my windows xp partition :(]("http://ubuntuforums.org/showthread.php?t=279494").  to sum it up:  dell has crafty ways of keeping you from resizing your hard drive.  i turned off my "static profile" (instructions on the aforementioned post, on the second page), ran a quick defrag, and viola!  i was able to resize my windows partition.

i was planning to follow the partition setup outlined [here, with FAT32 shared space]("http://psychocats.net/ubuntu/partitioning").  however, when i finished the install and restarted (from my hard drive, not the live cd), there was a grub error (#17).  after a *brief* moment of soul-searching, i decided i really don't need winblows.  i am currently installing 6.10 as my sole OS.

*crossing my fingers and hoping i don't jinx it*

next time, i'm totally building my own computer (minus the ATI video card).

:guitar: 

by the way, does anyone have ideas about why my ATI video card was giving me issues?  thoughts are much appreciated.

---

