---
title: "slow boot in feisty"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by nymphaeles on 2007-06-05
Booting pauses at about 45-50% bar for a good minute.  I didn't experience the same problem with Ubuntu 6.10 or 5.x.  Anyone has an idea why it behaves that way?
I have a Core 2 Duo 2.0 GHz on a Dell XPS-M1210, which is quite fast for most operating systems.
Thanks.

---

### Post by silkstone on 2007-06-05
It may be because it is looking for network connections that aren't there.

Try...

```
gksudo gedit /etc/network/interfaces
```

and comment out (with a #) all the lines apart from...

auto lo
iface......

and

auto eth0
iface.....

---

### Post by jcronkhite on 2007-06-11
I'm experiencing this on my new hp dv9000 as well.  What I do is turn off the wireless adapter before booting (I have a toggle switch on the front of the laptop to do this) and then turn it on once I'm at the Gnome logon screen.  Seems to work great for me and gets me around the slow boot.  Does your Dell have a switch?  You may have to use FN + F7 to disable wireless on boot.  Then do the same combo (it's a toggle) to re-enable it once you're in X.  I'd be curious to know if this solves your problem.  Good luck!

---

### Post by dragev.ca on 2007-06-11
I tried commenting out eth1, eth2, etc. in /etc/network/interfaces, but that did not solve the problem for me. I found that if I boot to the 2.6.17-10 kernel rather than the Feisty default 2.6.17-16 kernel, the slow boot problem disappears (-11 and -15 kernels are also slow). Now I'm a beginner so I'm curious about what is going on here? Does this behavior mean that my system will never work properly with newer kernel versions, or is this a temporary glitch that will go away in the future?

My computer is a Dell OptiPlex GX110 with Intel PIII 933 MHz CPU and 256 MB RAM.

---

### Post by dragev.ca on 2007-06-11
I should also mention that the boot process pauses at about 0% of the progress bar. Not 45-50% as experienced by  nymphaeles.

---

### Post by dragev.ca on 2007-06-12
As I was looking for a solution to a different problem, I stumbled across a solution to the long pause when booting to 2.6.17-16 kernel. I was not able to boot the Feisty live CD and was getting a  "failed to set xfermode" error, and the [solution to that problem was to add "irqpoll" to the boot options]("http://ubuntuforums.org/showthread.php?p=2635102&mode=threaded#post2635102"). Because this fixed my live CD booting problem, I thought I would try editing /boot/grub/menu.lst by adding "irqpoll" to the boot command, and now I don't experience the pause at the beginning of the boot process anymore!

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=... ro quiet **irqpoll** splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

---

### Post by nymphaeles on 2007-06-12
The boot process pauses about 67 seconds at 35% bar.  A Ctrl+Alt+F1 shows that it is trying to resume from an image???

```


kinit: trying to resume from /dev/disk/by-uuid/11bbxxxxxxx
kinit: No resume image, doing normal boot....


```

Now, I'm not sure if it hangs trying to resume from an image, or it is the next process in the bootstrap sequence that it is trying to do.

I don't see anything related to loading network interfaces yet.  In fact, it goes through loading network interfaces very quickly.

---

### Post by Arasa on 2007-08-07
I have the same issue where it looks for an image.

Did you manage to sort it out?

---

### Post by Sewerraccoon on 2007-08-26
I'm Having the same problem on my older system too (1Ghz P3, 512mb). Both U- and Kubuntu have a long pause with no progress on the bar, and in a minute or so it picks up. I never had this problem with 6.10, and strangely enough xubuntu 7.04 doesn't have this problem at all.

---

### Post by nymphaeles on 2007-10-26
This problem has been fixed in Gutsy.

---

