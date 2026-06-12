---
title: "Gutsy: MacBook Graphics Card Recognition"
date: 2007-12-29
forum: Apple Intel Users
---

### Post by RelativelyQuantum on 2007-12-29
Just a quick question:

I'm using a black macbook, Intel Core 2 Duo. Upon attempting to activate the desktop effects, I learned that my graphics card doesn't seem to be recognized. Has anyone experienced a similar problem, and have you found a way around it?

Thanks in advance.

---

### Post by alpinesatan on 2007-12-29
hey dude!

are you dual booting or using virtual pc software???

---

### Post by RelativelyQuantum on 2007-12-29
I dual boot between OS X (Leopard) and Gutsy, or at least I did until about ten minutes ago. I was attempting to interface the OS with the macbook's wifi, but somewhere during the reboot something went drastically wrong, and I could no longer boot. Now I have wiped it from my HDD, and reformatted the partitions formerly containing Gutsy. I haven't given up on booting into Edgy, though, even though it freezes at the x server error every time I try to boot into live CD. 

Have you had any luck dual booting?

---

### Post by alpinesatan on 2007-12-30
not yet, ive managed to get airport working tho.
dont know what to suggest to be honest, im new to using my own macbook to dual boot.
Id probably suggest starting from scratch myself, start fresh.

---

### Post by alpinesatan on 2007-12-30
well if your ok with it ofcourse.

boot from osx dvd, use the disk utility to partition your HDD, continue with the install.
install rEFIt, reboot, use live cd to boot up ubuntu, go to partition manager, format the partition that your going to use for linux as ext3 or whatever. and install to that partition.
It should go just fine. I say should.

---

### Post by Dynaflow on 2007-12-30
Your problem with desktop effects may stem from an Intel 965 graphics card, which I've read can be found in MacBooks, and the driver for which currently sucks so badly that it can't play video and run Compiz at the same time.  Compiz has [blacklisted it]("http://wiki.compiz-fusion.org/Hardware/Blacklist"), so you won't be able to make desktop effects run without doing some tinkering and sacrificing video playback, at least until a better driver becomes available.  See [http://ubuntuforums.org/showthread.php?t=620884]("http://ubuntuforums.org/showthread.php?t=620884").

---

### Post by RelativelyQuantum on 2007-12-30
Wow, this really helps! That clears a number of things up for me. I'll check out the link and try to get a few things activated, then post to share my findings. At least I know it can be done, however bad it performs. It's good to see that I'll actually get my beloved Ubuntu back :)

Thanks!

---

### Post by RelativelyQuantum on 2007-12-30
> **alpinesatan said:**
> not yet, ive managed to get airport working tho.

Just wondering, did you use madwifi? I couldn't get that to work.

---

