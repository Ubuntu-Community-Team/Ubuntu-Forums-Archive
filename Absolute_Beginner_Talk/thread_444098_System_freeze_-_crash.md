---
title: "System freeze - crash"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-05-15
My system has crashed a couple of times now.  I believe the issue is from my broadcom internal wireless card and pluging in a proxim card via pcmcia at the same time.  The broadcom card is connected to the network and I am running kismet with the proxim card.  Where can I find crash files to report this?

It also looks like the disk has errors because from a forced shutdown.  Do I need to run fsck disk.  Would this be the right command?  fsck /dev/sda5  - that is where root is mounted.


Details of the cards:
03:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

Thanks

---

### Post by Pragmatist on 2007-05-17
Have you tried duplicating the error in a non-GUI environment?  You can just type: CTRL + ALT F3  This will put you in a virtual terminal.  Then to make sure X (the GUI) is terminated, you would type:
```
sudo /etc/init.d/gdm stop
```One way to ensure this worked, is to look for processes for GDM and X before and after typing the above command.:
```
ps -ef | grep gdm
``````
ps -ef | grep X
```If X is still running, you'll see something like this:
>   root      **4492**  4475  3 08:27 tty7     00:20:25 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 You can kill this process by typing the kill command followed by the process ID number (in bold above. yours will probably be a different number):
```
sudo kill 4492
```The main advantage of trying this experiment is to narrow the possibilities.  If you don't have a problem in a text-only environment, then you know the problem is GUI-related.

---

