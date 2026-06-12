---
title: "Slow boot"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by laxguy on 2007-09-11
I'm new to linux, and recently installed it on my secondary harddrive. I have a Intel Celeron D 3.46Ghz, 1GB RAM, and decent onboard video. This computer runs Vista quite well with no problems. After I installed Ubuntu, it took over 30 minutes to boot up to the point where I was ready to begin working on things.

I also have another question about my wireless network card. its a Belkin (not sure chipset or anything like that, not sure how to find out) and Ubuntu doesn't seem to like it. I went through one tutorial that I found while i was looking around, but it didn't seem to help at all, and I was wondering if you guys could help with one of more of my problems.

---

### Post by Nolander on 2007-09-11
afew Q?
what took 30 mins to load ur windows or ubuntu? what release of ubuntu ru using?
 
nolander.

---

### Post by moffa on 2007-09-11
The long boot times have to do with your wireless card.

Comment out the wireless card settings in /etc/network/interfaces

If you type iwconfig you'll see which card is your wirless card (could be wlan0, ath0, eth1) and then comment out the 2 lines with a # at the beginning.

---

### Post by laxguy on 2007-09-11
umm, the newest version of Ubuntu, i belive its like 7.04 maybe. and it is the ubnutu that takes 30 minutes to load

---

### Post by laxguy on 2007-09-14
hello, its me again.
i used a guide i found and got my network working so i have internet now, but it still takes close to a half hour to boot. i attemtped to do what moffa said, but it didn't work because in my /etc/network/interfaces, there is no two lines about the one that my wireless card is..so im still looking for help on the boot thing.

my wireless card is eth1 and it only has lines on lo, wlan0, eth0, and ath0....

---

