---
title: "2 Dapper Drake Kernels represented in /boot?"
date: 2006-10-23
forum: Apple PPC Users
---

### Post by MonolithTMA on 2006-10-23
I was doing some troubleshooting and found that I appear to have two kernels represented in /boot.


ls /boot

abi-2.6.15-26-powerpc         initrd.img-2.6.15-27-powerpc

abi-2.6.15-27-powerpc         System.map-2.6.15-26-powerpc

config-2.6.15-26-powerpc      System.map-2.6.15-27-powerpc

config-2.6.15-27-powerpc      vmlinux

initrd.img                    vmlinux-2.6.15-26-powerpc

initrd.img-2.6.15-26-powerpc  vmlinux-2.6.15-27-powerpc

monolith@DualG4:/boot$ ls /boot

abi-2.6.15-26-powerpc         initrd.img-2.6.15-27-powerpc

abi-2.6.15-27-powerpc         System.map-2.6.15-26-powerpc

config-2.6.15-26-powerpc      System.map-2.6.15-27-powerpc

config-2.6.15-27-powerpc      vmlinux

initrd.img                    vmlinux-2.6.15-26-powerpc

initrd.img-2.6.15-26-powerpc  vmlinux-2.6.15-27-powerpc


When I do: uname -r

I get: 2.6.15-26-powerpc

So I know it's the one that is loaded, but can having the other one there cause any problems?


The issues I'm having can be read about here:

[http://ubuntuforums.org/showthread.php?p=1651378#post1651378](http://ubuntuforums.org/showthread.php?p=1651378#post1651378)

Thanks in advance, for any info. :)

---

### Post by Peter76 on 2006-10-23
It is normal to have 2 kernels; one is an old one ( from before an update ) and one is the latest. You can boot the old on from the yaboot prompt by typing old.

Now the weird thing is that you are not running the latest version ( not .27, but .26 ). I remember this was a problem a while back with some people; do a search on the forum to find out how to solve

---

### Post by christhemonkey on 2006-10-23
You have updated your kernel to -27 but upon reboot not selected the newer one from the GRUB menu.

This is not a problem, you can easily have multiple installed kernels.

---

### Post by MonolithTMA on 2006-10-23
I know I can choose *old* from yaboot, I've done that in the past. The thing is, I just installed from scratch and I know I did not choose *old*.

---

### Post by christhemonkey on 2006-10-23
Ack sorry, neglected to look at the forum title,
dont know anything about macs sorry,
The GRUB thing doesnt apply.

Someone else should help from here sorry.

---

