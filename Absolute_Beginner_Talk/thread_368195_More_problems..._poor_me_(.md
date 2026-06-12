---
title: "More problems... poor me :("
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by tbasherizer on 2007-02-23
Now, this isn't so much an Ubuntu problem as it is a VMWAre or WinDoze problem, but I just managed to install winxp on my vm, and I'm aching to play halo on it, and I don't want to join the VMWare forum just for one question. I installed halo correctly, but when I start it up, it says that hardware acceleration is disabled, and to run dxdiag. I run dxdiag, and find that I need to install the drivers for my video card, a GeForce 5500. The thing is, I've tried every windows version of the drivers, and none of them work! I need some help dudes. My gaming score depends on it.


Thanks,


tbasherizer

---

### Post by drarem on 2007-02-23
You can go to #VMWARE    irc channel I believe.. to ask those 'quick' questions..

The VMWARE player does not support a video adapter, just the basic svga thingy.. I'm not sure if VMWARE server does or not..  of course that is when I run vmware player on windows  primarily and running ubuntu on it.

---

### Post by orb9220 on 2007-02-23
> it says that hardware acceleration is disabled

I believe drarem is right. Vmware does not support high end gaming requiring acceleration.
Could be wrong but I remember reading in forums here.

---

### Post by sloggerkhan on 2007-02-23
I think there is a beta somewhere of a VMware that has hardware accel, but the regular one doesn't support it so far as I know.

---

### Post by HereInOz on 2007-02-23
Exactly right.  If you check in your system information, you will find that you are running a very basic video setup with about 16MB RAM.  VMware Server creates a virtual video card - it does not directly address the machine video card.

Sorry to dash your hopes.  Looks like you are stuck with a dual boot situation.

---

### Post by tbasherizer on 2007-02-23
NNEEEEIIINNN!

Meh, I can just make a 4 GB windows partition purely for halo and photoshop. Does anyone know if I can access a hard drive both in VMWare and through an OS?

---

