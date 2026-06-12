---
title: "I lost my Firefox 2 during an xserver problem."
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-11-05
**short version- Firefox 2 doesn't load when clicking on icon after having to fix my xubuntu.


**long version- I was trying to configure my xorg to use Beryl (failed wrong directions) and I ended up having an xserver error that I tried to fix in a wrong way.

What I did, was to do basically the wrong thing first, before figuring out what to do correctly. 

What I did wrong, since I couldn't remove the xserver-xorg and replace it and reconfigure it, was to basically strip down everything by removing and purging xinit, xorg, xserver-xorg, x11-common and then doing a dpkg --configure -a, than a -f install and then doing an install --reinstall of  x11, xorg, xserver-xorg, xinit followed by a dist-upgrade and then and then an install of ubuntu-minimal, ubuntu-standard, and my xubuntu-desktop, and of course a dist-upgrade, -f install, dist-upgrade and then a dpkg --configure -a.

What I did correct (I think) was that after rebooting I still had the xserver error. So I thought about it and then used nano (for my first time while having no gui). I found the original xorg.conf file that had been replaced with xorg.conf~ and overwrote the modified file with the original.

Now my gui works perfectly, but I lost a lot of my packages which is no problem, but my Firefox doesn't load when I click on the icon. I have no idea how to get my Firefox 2 to work since I am new to xubuntu and it just comes with edgy, right. I tried to re-install it using synaptic but that didn't work either.

Thanks,
-c.

---

### Post by po0f on 2006-11-05
crimesaucer,

Open up a terminal and try to run Firefox; if it doesn't work, post the error.

---

### Post by crimesaucer on 2006-11-05
can you give me the exact terminal code, I'm new, do you just write firefox and press enter or is there an open command?

---

### Post by po0f on 2006-11-05
crimesaucer,

It should be just `firefox`, if not try `mozilla-firefox`.

---

### Post by crimesaucer on 2006-11-05
ok, i'm on my windows partiton right now, so I'll try it in a second and get the exact error that was written when I wrote "firefox" in the terminal when it wouldn't start.

Thanks for the help, I'll post back in about 5 minutes with results.

---

### Post by crimesaucer on 2006-11-05
so, this is the error when I put firefox or mozilla-firefox in terminal: Segmentation fault (core dumped)

what now?

Earlier, I did see it say that Firefox would need to be restarted or something, when I was trying to fix things without the gui durring the xserver error.

---

### Post by po0f on 2006-11-05
crimesaucer,

I would suggest reinstalling Firefox, and if that doesn't work... *shrugs*

I don't know where Firefox dumps its core, but if you can find that out, file a bug with either Launchpad or Mozilla.

---

### Post by crimesaucer on 2006-11-05
I tried that already and no luck, I tried with synaptic, and with terminal: sudo apt-get install --reinstall firefox since when I tried to sudo apt-get install firefox, it said that I was already using firefox2's newest version.

I'm not gonna file a bug report because I was the one who messed it up while operating with no gui, and also in root during failsafe mode.

I'm gonna try one more thing, and if that doesn't work, I'll reinstall again.

---

