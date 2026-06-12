---
title: "Gutsy Boot Problem"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by D-Rick86 on 2008-02-20
Hey all. I ran the Live CD and got Gutsy onto my system (finally!)

Now, when I restarted the computer, GRUB loaded, but then I get a very long line of code that read over and over and over again:

/init: /init: 158: /bin/sleep: not found. (sooo many lines of this)
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules 1s /dev
/init: /init: 158: modprobe: not found
/init: /init: 158: modprobe: not found
ALERT! /dev/disk/by-uuid/ffe039fc-40df-40c4-9641-b751a0030225 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands. 

Then I get a command prompt type thing that reads:

(initramfs)

I am assuming this is where I put in some sort of executable(?)

I have a Gateway Laptop w/ Intel Duo Core @ 1.73ghz, 2GB RAM, 160GB hard drive and a bottom of the line Intel Integrated Graphics Chip.

Any thoughts/suggestions to what I should do next? The CD checked out fine for defects and I'm a super Linux noob. Any feedback would be appreciated. Thanks!

-Derek

---

### Post by maybeway36 on 2008-02-20
Sounds like it failed to mount your root partition.

---

### Post by D-Rick86 on 2008-02-20
So, what should I do now since that happened?

Any suggestions?

---

