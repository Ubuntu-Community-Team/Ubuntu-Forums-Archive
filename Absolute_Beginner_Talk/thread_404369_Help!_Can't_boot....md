---
title: "Help! Can't boot..."
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Sidhe on 2007-04-08
Hey, I am sort of new here, but I'd really appreciate if someone bothered tossing me a hint anyways... I've googled far and wide for this, to no avail.

The problem is that I can't get into Ubuntu after upping it to Edgy Eft. When the OS boots, I hit alt+f1 and get to "login lucy:" (lucy being the name of my computer), and then the screen goes blank, offering no responce. I've come across the same problem on the forum here, but unluckily there was no answer there.

I had the exactly same problem on the Dapper Drake 6.06 LTS edition, but that was resolved by using an older Kernel on the boot list. If I try doing that now, the kernels either do the same as described above, or output "kernel panic" and freeze.

I've tried to run dpkg-reconfigure on the xorg, since I thoguht the error might be there, but obviously it did not work. Also, I boot into the recovery console without trouble.

Any help will be greatly appreciated. I really dont want to be stuck with window$. >.>

Thanks in advance,
-Sidhe.

Edit: Solved the issue - thanks to all who contributed.

---

### Post by Austin_KW on 2007-04-08
Did the upgrade change you xorg.conf, are older versions saved in  /etc/X11. Or can you boot from CD and compare you current xorg.conf with a working one.

---

### Post by Sidhe on 2007-04-09
Nevermind, figured it out. X-) The villain was my ATI graph card that refused to start correctly. Had to switch xorg.conf to boot with VESA and then install fglrx when I got in.

Thanks for answering anyways.

---

