---
title: "No screen output on Asus G75 with Ubuntu 12.04"
date: 2012-06-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by agentplissken on 2012-06-16
Hi,
I'm trying to install Ubuntu 12.04 using wubi on an Asus G75 notebook equipped with a Geforce 670M GTX display adapter.

After I reboot to Ubuntu the first time, I get a black text screen with the cursor flashing at the top left. The installation apparently finishes on the background, once it's done the Ubuntu startup sound plays through the speakers, but no desktop appears.

On subsequent boots I get a solid violet screen, which then gets corrupted with some random pixels, and the startup sound plays again, but again, the desktop fails to appear.

Any suggestions on how to resolve this?

---

### Post by Welly Wu on 2012-06-17
Did you see this:

[http://ubuntuforums.org/showthread.php?t=2000778&highlight=asus+g75](http://ubuntuforums.org/showthread.php?t=2000778&highlight=asus+g75)

Mind you, this person may have installed Ubuntu bare metal on his ASUS G75 with the Nvidia GeForce GTX 660M GPU. You have the higher specification model and you used WUBI.

Did you try a dual-boot configuration? WUBI might be the cause of your problems.

---

### Post by oakstair on 2012-06-17
I have failed installing ubuntu on my new g75 so far. Will try to use the text based installer plus updating video drivers now.

---

### Post by agentplissken on 2012-06-17
Thanks for the suggestions! In the end I resolved the problem by choosing the "ACPI workarounds" boot option for the initial installation, and for further boots, adding nomodeset on the kernel command line.

---

