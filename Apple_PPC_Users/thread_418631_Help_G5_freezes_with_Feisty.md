---
title: "Help G5 freezes with Feisty"
date: 2007-04-22
forum: Apple PPC Users
---

### Post by constantinos on 2007-04-22
After install/upgrade  to feisty my machine just freezes and the red light in the front of the machines when you power up/down the machines goes on permanently and the machine becomes un responsive.

root@foobar:/boot# cat /proc/cpuinfo 
processor       : 0
cpu             : PPC970MP, altivec supported
clock           : 1000.000000MHz
revision        : 1.0 (pvr 0044 0100)

processor       : 1
cpu             : PPC970MP, altivec supported
clock           : 1000.000000MHz
revision        : 1.0 (pvr 0044 0100)

timebase        : 33333333
platform        : PowerMac
machine         : PowerMac11,2
motherboard     : PowerMac11,2 MacRISC4 Power Macintosh 
detected as     : 337 (PowerMac G5 Dual Core)
pmac flags      : 00000000
L2 cache        : 1024K unified
pmac-generation : NewWorld
root@foobar:/boot# 


Ive done google searches on just about everything I can think of and the closest article which I came across is @ [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23445](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23445)

I do not think this is related to my problem though.

After much flailing ,I have confirmed that any kernel > 2.6.18.x will experience this behaviour with my machine. As a temporary solution I upgraded my machine to Feisty and before rebooting I compiled 2.6.18.8 and booted from that kernel and am up and running now. There are no dmesg logs no system logs no Core dump. I am sure I am probably not looking in the right places as my sys admin skills are not up to par. Is no one else experiencing this problems with the Powermac G5?

Apple is just not worth it man. Someone sold me the kool aid a while back and now it just tastes bitter.

---

### Post by stmiller on 2007-04-22
I have a powermac G5 dual 2Ghz (two cpus- not dual core) and Feisty is running fine with no problems.
And there is support for those later dual core G5s in the kernel now. Did you do a make g5_defconfig when you compiled your kernel? That should include all thermal modules built in for your machine. Could be that the ubuntu team doesn't have a dual core G5 machine to test their images.

---

### Post by constantinos on 2007-04-23
Yeah when I compiled the 2.18.8 Kernel I compiled with the g5_efconfig parameter. But when I did the same for the 2.6.19 and 2.6.20 it would freeze. I am pretty confident that it might be a sound module that I have seen ifloating in 1 or 2 other threads. I got it working with the 2.18.8 I just dont like to maintain my own kernel . Would have liked to got it working out of the box. But oh well.

---

