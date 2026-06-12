---
title: "Kernel 2.6.31 Weird Wireless Behavior"
date: 2009-12-05
forum: Apple Hardware Users
---

### Post by shakty on 2009-12-05
Hi guys, I have updated my system to kernel 2.6.31 and as many of us I've got troubles with my wireless. Unlikely to what I have read recently, where the wireless didn't work at all, now my wireless works partially...and weirdly! That is...I cannot see my wlan any more...interestingly I can see my neighbors' wlans, and I can even connect to an open one, though it does not last long...

I have a macbookpro 5.1, ubuntu 9.10 and kernel 2.6.31-15 generic

My wireless driver is the now the old Broadcom STA-Funk-Wireless, it has always worked perfectly before...I have tried also the B43, but that does not work at all.

Quite perplexed...any clue???


Thanks

---

### Post by shakty on 2009-12-06
Up...please any hint! I am getting mad...

---

### Post by linuxopjemac on 2009-12-06
downgrade your kernel. Go to Synaptics package manager, search "linux-kernel" and install the older one (linux-image-2.6.31-14-generic). It will be added to your Grub entry. I hope this helps for you.

---

### Post by shakty on 2009-12-06
Tried, but no success...I have also a 2.28 kernel available, but this one does not load at all the Broadcom STA driver.

---

### Post by Ostrava on 2009-12-06
I'm having a similar problem. I can connect to a network, but nothing works. I'm back to using ethernet with this for now.

EDIT: It looks like it was the encryption WPA causing the problem. Switching to WEP made my wireless work.

---

### Post by shakty on 2009-12-06
After a few furious attempts I quite messed up things now...it don't have any wireless at all now :)

Thanks for the WEP tip...I will go for ti as soon as I fix the other problems!

---

### Post by techie99 on 2009-12-16
I posted a possible fix here: [http://ubuntuforums.org/showthread.php?p=8505612](http://ubuntuforums.org/showthread.php?p=8505612) . I was having crazy issues.  I noticed on lauchpad that the bcmwl-kernel-source package was using an old version of the driver.  This may work, however it is a binary blob driver so YMMV

---

