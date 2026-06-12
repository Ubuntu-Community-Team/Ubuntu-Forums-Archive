---
title: "USB pen-drive for extra swap on low-mem machines"
date: 2008-03-05
forum: Apple PPC Users
---

### Post by stream303 on 2008-03-05
Has anyone tried this on their low-memory ppc boxes?

[http://ubuntuforums.org/showthread.php?t=395435&highlight=readyboost](http://ubuntuforums.org/showthread.php?t=395435&highlight=readyboost)

Seems like it would be ideal for iMacs.

I do know that some low-cost pen-drives have an initially fast amount of ram, and the rest is much slower. so buyer beware...

---

### Post by stream303 on 2008-03-06
It works!

Ok, I don't have this problem because I've got a lot of ram, 1.5 gb to be exact.  But I was more interested in saving older machines from thrashing old hard drives when they are giving a workout to the swap partition.  I'd rather thrash an inexpensive usb-pen drive than have to find and install a replacement hard disk for an early iMac :)

Plus, I didn't want to get dragged into the whole performance issue.  I have a 1 gb Kingston pen drive that is "Ready-boost" certified.  Yawn. :)

1) Inserted the usb pen drive into the system.
2) From the desktop, I just right-clicked it, and UNmounted it.
3) From the terminal, I checked what the device was called

```
dmesg | tail
```

4) It shows up for me as /dev/sdb1
Let's put it to use.

```
sudo mkswap /dev/sdb1

sudo swapon -p 32767 /dev/sdb1
```

5) Check it:

```
cat /proc/swaps
```

6) Since I want to ensure that ONLY the pen-drive is used for swap, (optional) I turned off the standard hard drive swap:

```
sudo swapoff /dev/sda4
```

(the cat /proc/swaps command earlier verified my hard-drive swap as /dev/sda4)

I'll have to look into how to automate this whole thing with the pen-drive permanantly installed during boot, but so far so good.

However, with so much memory on my box, I can't hit my swap.  I'll try harder. :)  But this could be great for saving some old gear from wear and tear.

Managing a large swap like 1gb may not be the best idea on a low-mem computer anyway, so something smaller like 128, 256, or 512 might be about right if you figure in 1 / 1.5 / 2 times installed ram....

---

