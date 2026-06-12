---
title: "Xubuntu boot problems?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by paku on 2007-03-14
So as I said in another post my duel cpus fried and I am stuck with a p2 128mb I had sitting in my closet. I installed Xubuntu 6.10 Alternate CD last night. When I try to boot into it it loads the Kernal and gets to the text that asks for my login.... but before i can enter my login the screen goes black. Now i am using a gForce card, so i tried rebooting with just my onboard vid card, and when it gets to that same point, the screen looks all fuzzy... but i can tell the cpu is working, its not locked up and it seems like its a video problem of some kind... Any tips? Thanks all. I have tried getting Ubuntu/Xubuntu working on this computer since last friday with no avail... if I dont get it tonight I guess i'll have to reload XP :(.

---

### Post by taurus on 2007-03-14
Go into the BIOS and disable the onboard video card since you want to use the nVidia.  Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default and use **vesa** as a driver for your graphic card.

Then, reboot with

```
shutdown -r now
```

---

