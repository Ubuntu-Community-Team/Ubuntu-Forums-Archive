---
title: "1min 45sec boot time"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Enalia on 2006-11-11
My boot time has always been very slow... I never bothered to time it though.

I tweaked the daemons that boot on start up but...

it was still slow.

So, I gave in and accepted the fact that it's slow... I have KDE and Gnome installed... would that slow it down?

Just now I timed it...and it's one minute and fourty-five seconds... that's 105 seconds.

Is this normal?  If this is something I have to live with...I might put up with it... if there's ANYTHING I can do, no matter how complicated, i'll do it.

thanks for reading and hopefully responding :)

---

### Post by tipi on 2006-11-11
what are the specs for your pc ?
proc, graphic card, ram etc...

---

### Post by .t. on 2006-11-11
What release are you running. I'm on a Pentium-M 1.6GHz with 1GiB of RAM, a standard laptop 40GiB HDD and an i915 GPU; and I get >30 seconds on good days (and most days are good days).

Do you have prelink, preload and readahead set up correctly? To install prelink: "sudo aptitude install prelink" and edit /etc/defaults/prelink to turn it on. Then run /etc/cron.daily/prelink to do a full system prelink. This will take a while, but it will be quicker in future. If you want, you can search to find out how to have prelink run after every apt operation. To install preload: "sudo aptitude install preload". That's it. Then, finally, profile your boot so that readahead loads the needed files by, at boot time, pressing escape as GRUB loads, then editing the kernel line of the default kernel, removing the option "quiet" (so you can see what's happening), and adding "profile" (to do the profiling).

---

### Post by spd106 on 2006-11-11
You could try profiling your boot process. Just add **profile** to the end of the grub boot line. You only need to do it once and it might get you a few seconds, YMMV.

---

### Post by Enalia on 2006-11-11
It's a laptop.

1GB RAM
ATI Mobility Radeon X1400
Intel Core Duo Processor (not sure of the actual specs here...)


and a neat little glowing alien logo on the top (sorry, had to show off)

I've heard that laptops have slower harddrives... but my windows boots fairly quickly.

---

### Post by DaveBorealis on 2006-11-11
> **Enalia said:**
> My boot time has always been very slow

Have you taken a careful look at /var/log/dmesg for clues?  For instance, ntp can cause delays, especially if there are dns issues.

Dave

---

### Post by Enalia on 2006-11-11
dave b.

not quite sure what I'm looking for... but is there a way to view the boot process?

like, line by line?

---

### Post by DaveBorealis on 2006-11-11
Unfortunately, if I understand it right, the closest you can get to the boot process is dmesg...assuming you've rebooted recently.  Nothing's mounted r/w during the first part of the boot, and it only keeps a small buffer of info to write out later to the logs.

---

