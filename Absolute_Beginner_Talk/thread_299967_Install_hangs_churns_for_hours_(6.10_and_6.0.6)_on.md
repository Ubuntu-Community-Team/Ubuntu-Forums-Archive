---
title: "Install hangs churns for hours (6.10 and 6.0.6) on Compaq Presario 305"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by scobb99 on 2006-11-15
Am trying to love Ubuntu, which booted from CD all the way to a lovely desktop on my IBM NetVista desktop. But oh what a problem it is on my Compaq Presario (Celeron, 128Mb RAM, currently running Win 98) laptop. Both 6.10 and 6.0.6 will boot, start install, then chug away with blank screen for hours (really, I watched X-Men 3 and came back and it was still chugging).

The CD just keeps churning. At one point the screen was flashing sheet lightning until I pressed a key (a bit like Storm). Only way to stop this process is to remove battery. I can use the Off button, but when I turn it back on, it starts off again, churning.

Any suggestions?

Stephen

---

### Post by schrombot on 2006-11-15
Here, try the alt install, you need at least 192 MB of ram for the live cd installer. [http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/ubuntu-6.06.1-alternate-i386.iso](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/ubuntu-6.06.1-alternate-i386.iso) download that and when you boot, use text mode install.

---

### Post by scobb99 on 2006-11-15
Thanks a bunch...the alt install is going much better. I did not notice the RAM limit on the other package.

---

### Post by moshuptrail on 2006-11-15
On a similar size machine I also noticed that the install was much, much slower when I used ext3 partitions than when I used ext2.  I'm not recommending ext2.  I eventually used ext3 and let the install run for hours.   Once installed, it seemed to run okay, but 128M is the bare minimum for Ubuntu.  Expect it to be pretty sluggish.

BTW don't try Edgy.  Stick with 6.06, Dapper.  More stable.

---

### Post by jimrz on 2006-11-15
> **moshuptrail said:**
> On a similar size machine I also noticed that the install was much, much slower when I used ext3 partitions than when I used ext2.  I'm not recommending ext2.  I eventually used ext3 and let the install run for hours.   Once installed, it seemed to run okay, but 128M is the bare minimum for Ubuntu.  Expect it to be pretty sluggish.

BTW don't try Edgy.  Stick with 6.06, Dapper.  More stable.

Gnome or KDE will definitely be slugish. suggest using a lighter weight window manager try xubuntu-desktop from Synaptic or something like IceWM or fluxbox, should yield way better performane on your machine

---

### Post by scobb99 on 2006-11-18
Thanks for the info mushuptrail and jimrz, and the suggestions for post-install improvements. It did eventually install on the 305, with sound and wifi both active (strangely it overlooked the internal wired Ethernet connection but accepted the Buffalo PCMCIA wifi card like a charm. 

You are right about sluggish performance. And it looks like I need to tweak power on/off/standby settings (darn think won't shut down right now). BUT I am still darned impressed with Ubuntu and this box will be a handy web browser for somewhere like the kitchen. Also proves you can make a very useful machine out of a box that is not going to seel for more than $50 on eBay. 

In that same vein I used the alt-install tip I got here to install Ubuntu on an old iMac G3. That was also slow but went very well. Again, this is a sub-$100 box that does word processing, spreadsheets, web browsing, with tunes. Impressive.

Thanks again for the input.

---

