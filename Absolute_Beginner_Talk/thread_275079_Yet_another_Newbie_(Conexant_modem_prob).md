---
title: "Yet another Newbie (Conexant modem prob)"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by dyingsun on 2006-10-10
Hi everyone, I've come to lose my Forum Virginity (be gentle with me:neutral: )

I have a Dell Desktop, pretty standard stuff, 512 MB RAM, 2.4gHz, pre-installed with XP Home on a 40 gig, and I've just installed Ubuntu (bought a second 80 gig hard disk just for Ubuntu to colonise) and everything's been running sweet..I was almost disappointed not to have to put in an all-nighter just to get it up and running! I'm a complete linux newbie...I can sort of move around a little, and have installed a few bits and pieces, but I really don't know my kernels from my corncobs.

I was using the updating thingy, and downloading some obscene number of packages over my pathetic dialup connection, and I rebooted when prompted...and wvdial no longer works and can't find /dev/modem. I've tried ln -s and so on, and still isnt working...it's a Conexant chipset, using the (free, slow version)Linuxant HSF driver. I've tried and tried to resurrect it using all the techniques I can google, and it's just not coming back online. AM I getting the syntaxes wrong, should I be linking to the port or the driver (it's COM 3 under XP), so should I be linking to ttyS2 or just re-installing everything? Installing the modem drivers and dialer was very confusing; hoping to avoid re-installing them! 

Can anyone tell me why /dev/modem has carked it, and how I can get it back? Sorry if I'm covering old ground, I guess I just don't really understand the problem.

Thanks, in advance,
DS

---

### Post by _duncan_ on 2006-10-11
Hi. It's possible you inadvertently upgraded to a newer kernel while updating the system. So you need to compile the modem driver again to work with the new kernel.

Note that you need to install the linux-headers package that matches the new kernel before compiling.

---

### Post by dyingsun on 2006-10-12
Ah, now I get it! (where's the "blush" smiley?)

I forgot the driver had to match the kernel version; all I had to do was uninstall the old, install the new...goddamn it, wasn't even a seriously technical, frightening issue, just a stupid oversight :) It's now up and running, with a paid-for driver so I'm rocketing along (comparatively speaking, anyway).

Thanks for your reply Duncan, I'd probably still be wallowing in XP trying to pick up the pieces if you hadn't replied!

This Ubuntu thing's really sweet...the power...the power...the power....::twisted:

Thanks again mate,
DS

---

