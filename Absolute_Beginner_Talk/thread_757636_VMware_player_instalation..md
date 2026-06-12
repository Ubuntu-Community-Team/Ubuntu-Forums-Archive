---
title: "VMware player instalation."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by mosheshp on 2008-04-17
Hello everyone!

all I'm trying to do is to install ubuntu with windowsXP as an option.
(I have E2160 CPU , and now I've installed Ubuntu 7.10 amd64.

I tried to install Vmware player from the ADD\REmove programs, and it told me that this software isn't supported to this kind of (amd64).
I searched for updated version and (I think) I found it here:
[http://packages.ubuntu.com/feisty/amd64/vmware-player/download](http://packages.ubuntu.com/feisty/amd64/vmware-player/download)

now, when I'm trying to open it by the G Debi... and it says:
"Error: Dependency is not satisfiable: vmware-player-kernel-modules"

I Tried to install some "kernel modules" of that software, but it didn't work,

it gave me very similar error.

How can I instal that software?
Thanks A Lot.
I don't want to leave Ubuntu, I love it!!!
Moshe

---

### Post by Sef on 2008-04-17
Not all cpus support virtualization.  There is documentation on it.  If I find it, I will post it.

---

### Post by mosheshp on 2008-04-17
hey! thanks a lot, I'll try to find out about that.

does it mean that I Won't be able to install vmware player on my PC?
can there be other reason?

---

### Post by Hendrixski on 2008-04-17
Yeah. Virtualization depends on two things, CPU's and kernels.  The Linux kernel has THE best virtualization configuration out of any system (for example, you can dynamically add cpu's, change the amount of ram, etc. etc.) so it's not that.

If your CPU isn't supported by VMWare you can try Xen, or Qumu and they might work? maybe?

if none of those will work with Linux, then they sure as hell won't work on Windows.

---

### Post by Hendrixski on 2008-04-17
Also, we use VMWare server in my office quite a lot, and we avoid vmware player like the plague.  Maybe that might work better for you?  It's equally inexpensive (free of cost even though it's not Free software)

---

### Post by mosheshp on 2008-04-17
Thank you all!!!

you ARe good!  I'll try it out.

you helped me a lot! :)

---

### Post by philoakley on 2008-04-17
Hi

Not sure if this helps but I have installed VMware player on my Ubuntu amd64 box following the instructions from here:

[http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710](http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710)

I downloaded the 64 version but it said that it was incompatible and to use the i386. I downloaded the i386 version and it installed fine.

Sorry I am a bit of a newbie.

---

