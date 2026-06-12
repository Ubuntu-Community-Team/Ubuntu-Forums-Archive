---
title: "Macintosh LiveCD!"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by Phrostay on 2005-11-03
Okay well I've decided to give this linux thing ago:razz: so I tried the i386 of Ubuntu v5.10 LiveCD on my brothers laptop, works flawlessly & I am going to install it soon enough. However I tried the PowerPC LiveCD on my new iMac G5 20" and all I received was a brown screen and I couldn't move my mouse or use the keyboard. I think it was because I burned the disc too fast using firestarter-fx because I did a 2x burn with the i386 disc or maybe Ubuntu doesn't like 64-bit G5 processors?

Is there like a an updater for Ubuntu like the Windows XP software update program? I'm like a real beginner to it all and played around with Linux when I was like 12 and now that i've made the switch from Windows to Macintosh I thought I might as well try out Linux too, I haven't looked back since the switch from Windows:D Oh yeah I'm not too bad with the terminal either I love customizing my shell on OS X (pico .tcshrc).

---

### Post by Qrk on 2005-11-03
Ubuntu does have an updater just like windows update. But its much nicer and more powerful. Ubuntu can update every program you have installed all in one step, whereas Windows is limited to core updates. 

As for your live cd problems... you may want to try a re-burn. Or you can hit ctrl-alt-backspace out of x.org and try to fix it with a 

sudo dpkg-reconfigure xserver-xorg

command typed into the prompt. Ubuntu does run just fine without a GUI, but you may prefer one!

---

