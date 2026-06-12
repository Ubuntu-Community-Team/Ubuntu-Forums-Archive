---
title: "bootup time"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-02-12
I use Ubuntu 6.10 and I have 512+128 mb RAM. Processor 2.7GH.
My Ubuntu takes 3 minutes to boot.
How to shorten the time?
Thanks.

---

### Post by purplearcanist on 2007-02-12
You could try cleaning up the desktop, removing the amount of files in it. (Note: This also works in Windows)

Something is wrong, since it takes less time for my computer to boot Ubuntu (About 2 minutes), and my computer is slower. (Ubuntu 6.10, 128 mb RAM, 666 Mhz processor).

---

### Post by sauravbhaumik on 2007-02-12
my desktop contains two icons (link to hda5 and hda1) and nothing else. Files are not too much. Can you guess the problem?

---

### Post by casaschi on 2007-02-12
I achieved a substantial speedup of the boot process by disabling the network interfaces eth0 and wlan0 in /etc/network/interfaces (just comment those out).
What I think happened is that ubuntu was stuck waiting for something on those interfaces (rather that realizing that the wired ethernet is unplugged and the wlan0 needs wifi-radar to startup the WPA association).
If you do that, then you need a wifi manager like wifi-radar to bring your wifi up...

---

### Post by sauravbhaumik on 2007-02-12
any other suggestion?

---

### Post by Darkspace on 2007-02-12
Do you have any Windows partitions mounted from startup?

My installation took ages looking at my Windows files.

---

### Post by sauravbhaumik on 2007-02-12
Yes, I have two windows partitions.

---

### Post by Darkspace on 2007-02-12
Try unmounting them to see if it reduces boot time.

If that solves it perhaps you could instead mount a specific Windows directory to share files.

---

