---
title: "Install problem: P II 400Mhz, ASUS, 256Mb, 10GB"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by bando on 2007-03-12
I tried installing Ubuntu 6.10 (also 6.06) on my Pentium II 400Mhz custom PC with ASUS motherboard and 10 GB memory. I have not updated the Bios since 2000. This PC used to run Win 98 successfully with a single partition. Thus I believe the Bios has large HD (> 1GB) support.
My Ubuntu installation seems to be successful, but when it asks me to reboot, the machine hangs with the "Loading Linux" message. I accepted all the defaults during install. The bootloader is GRUB.
I can boot from the CD.

If the above info is not sufficient to diagnose the problem, then please tell me how to partition the drive during installation (I did not se any option for this) so that / is mounted on a partition less than 1GB. (what should be the partition sizes?)
Then I will try the install again.

Thanks for any help or suggestion.
bando

---

### Post by Brendantb on 2007-03-12
Hi, with those specs you should have has no problem with installing Ubuntu on that laptop. That the live cd runs is a good indicator. 

I have a similarly aged laptop from toshiba, with only 196mb of ram, so I run Xubuntu on it. My bios is version 1.50. There are three partitions in the setup, with / on a four gb partition. 

You might want to check, if you haven't already done so, that the ISO was properly burned.

If that is okay, you might want to try to install from the alternative CD, in text mode. 

Finally, with such low specs on the laptop, you might want to consider a lighter window manager than Gnome/metacity. Xubuntu comes with Xfce, but there are others such as fluxbox and ICEwm.

---

### Post by bando on 2007-03-13
Thanks Brendan,
I will try the text mode install.
bando

---

