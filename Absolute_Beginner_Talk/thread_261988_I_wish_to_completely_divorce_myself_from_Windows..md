---
title: "I wish to completely divorce myself from Windows."
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by sheldonhoward on 2006-09-21
I am very new to Linux and wish to completely divorce myself from Windows. I was finally able to install Ubuntu 6.06 but am unable to have my wireless adaptor (Airlink AWLL 3026 Wireless USB)recognized.  Is it  possible to use this adaptor or should I give up and buy another wireless USB adaptor.  If so, what is recomended as compatible (i.e., easy to install)with Ubuntu 6.06?
Thank you, you wonderful people who give of your time to help newbies like me.

Dr. Sheldon Howard

---

### Post by Jussi Kukkonen on 2006-09-21
General warning: USB wlan devices are generally speaking bad for your health: they are mostly the cheapest devices available, and that does affect quality. The manufacturers often change hardware without changing model numbers, which makes supporting them even harder. Getting many USB wlan adaptors to work in linux often requires tweaking things that normal people shouldn't even know existed.

Now, since you already have the device (and maybe USB is the only choice) you should of course try it -- You could be lucky and the thing works like charm...

I'm not very familiar with your device, but the situation looks pretty good: there's a project that maintains the original ZyDAS driver here: [http://zd1211.ath.cx/](http://zd1211.ath.cx/) and also a "community rewrite" coming up -- it's included in the 2.6.18 kernel (which will probably be used for Ubuntu 7.04.)

Note that they say debian has source packages available -- that means Ubuntu probably does too. I suggest you use them if they are available: you'll stilll have to compile, but at least the files end up in the package management system.

Remember when I said manufacturers like to change hardware without telling users? Your card seems to have several versions... read the web page, compare the usb id to the id you get in *dmesg* or *lsusb* when you plug it in to find out if the drivers work for you.

---

