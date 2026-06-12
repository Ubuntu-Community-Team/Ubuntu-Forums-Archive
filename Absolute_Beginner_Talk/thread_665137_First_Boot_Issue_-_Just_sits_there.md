---
title: "First Boot Issue - Just sits there"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by curlyt on 2008-01-11
Hi all,

I've gotten Gutsy Gibbon installed on my old desktop here.  Had to use the alternate CD, but everything went OK, reformatted to use the whole drive.  On reboot, I see the Ubuntu logo and orange scroll bar, which fills up, then the screen goes to black.  Then my computer sits there forever, no loading at all.  I took "quiet" and "ro nosplash quiet" out of the boot commands and repeated -- now I see all of the components loading up and everything seems to go OK.  It gets to the end, and then the screen goes black again and we play the infinite staring game, which I always lose.  Sometimes the hard drive is grinding away, sometimes it's quiet.  Any thoughts?

Thanks!

---

### Post by phidia on 2008-01-11
when you get the black screen press the Ctrl+Alt+F1 keys. You should get a command line (CLI) try typing "sudo startx" without the quotation marks. You can post the output here.

---

### Post by curlyt on 2008-01-11
I'm not sure when to hit Ctrl + Alt + F1.  There's no response from the blank screen.  Doing it earlier takes me through the bootup steps but then dumps me back to the blank screen without the chance to type in "sudo startx".  I can get to a grub> command line, but it doesn't recognize "sudo startx."  

Thanks again.  I've been very impressed with this community.

---

### Post by phidia on 2008-01-11
Since you used the alternate cd image can you pop that cd back in and try rescue a broken system? ( language to that effect)

---

### Post by curlyt on 2008-01-12
OK, here's what I get when I run "sudo startx" after alternate install disc > restore a broken system > "executing a shell" on partition 1:

warning: process set to priority -1 instead of requested priority 0
... [skipping some standard looking stuff] ...
using config file: "/etc/x11/xorg.conf"
(EE) intel(0): cannot read V-BIOS (3)
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) intel(0): AGP GART support is not available.  Make sure your kernel has agpart siupport or that the agpart kernel is loaded.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
No screeens found
IO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after ) requests (0 known processed) with 0 events remaining.

---

### Post by phidia on 2008-01-12
I should have asked this before-what gpu/grahpics card are you using and posting the rest of your hardware specs wouldn't hurt either. What version of ubuntu are you using?

---

