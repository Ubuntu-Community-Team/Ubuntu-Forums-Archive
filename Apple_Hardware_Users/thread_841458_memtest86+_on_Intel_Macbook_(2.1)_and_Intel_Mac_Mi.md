---
title: "memtest86+ on Intel Macbook (2.1) and Intel Mac Mini"
date: 2008-06-26
forum: Apple Hardware Users
---

### Post by gmc on 2008-06-26
Hi Folks,

I've run into a bit of a brick wall here and I'm wondering if someone can offer some assistance (or a conformation of my findings). Recently I upgraded my Mac Mini to 2Gb of ram and the system seems to be running perfectly, with one exception. Virtualbox appears to have some issue with the Intel video chipset. The screen periodically flickers and will appear to hang Gnome with either a black or a white (like the boot) screen. Switching to an alternate terminal session works and I'm able to safely restart the system.

Here's the kicker, I thought that maybe one of the new sticks of ram might be flakey, so I tried to fire up Memtest86+ from the grub menu... but it won't run! The system just hangs... So I boot up with my Hardy CD and try memtest from there... same thing... it just hangs the system.

So I try the same things on my 2.1 Macbook.. same problem. 

Can some one test memtest on their Mac and see if they can get it to run, or suggest a way I can test the ram in my Mac Mini?

Thanks
Gord

---

### Post by m_l17 on 2008-06-26
I have the same issue with my mini. I was looking for a solution and came across your thread. If I find a solution will post back.

---

### Post by entangled on 2008-06-29
I have a Mac Mini solo 1.5 (early 2007, upgraded to 2GB) and it has the same problem with video hang up when using virtualbox (and kvm/qemu) in ubuntu 8.04. 
I raised this as a launchpad bug and eventually someone came up with a solution. 
Try to see [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/226272](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/226272).
Otherwise just search launchpad.net for bug 226272.
The problem seems to be that the default 'DRI' option for xserver doesn't work on Mac Mini, so you have to turn it off.

---

### Post by gmc on 2008-06-30
> **entangled said:**
> I have a Mac Mini solo 1.5 (early 2007, upgraded to 2GB) and it has the same problem with video hang up when using virtualbox (and kvm/qemu) in ubuntu 8.04. 
I raised this as a launchpad bug and eventually someone came up with a solution. 
Try to see [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/226272](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/226272).
Otherwise just search launchpad.net for bug 226272.
The problem seems to be that the default 'DRI' option for xserver doesn't work on Mac Mini, so you have to turn it off.

Thank you very much! In all the online information that I found before buying the Mac Mini neglected to mention that (but to be fair it was older info).

The Virtualbox / screen problem / freeze seems to be ok, though I've played with it for a few minutes. As for testing the new ram with memcheck; I plan to try a package called "memtester" from the repo's tomorrow.

Gord

---

