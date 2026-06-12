---
title: "help performance!??"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-02-28
Hey I have a box with an 8gig partion and I want to improve performance with things like processes,read speed and termianal commands I should run periodically. I also want to gain an intimate knowledge of the linux kernal and I think learning things like this certainly help.
Also I want to learn about prosesors. More so than the basic pipline stuuf. I want to learn about instruction sets and drivers in the kernal any ideas?

---

### Post by marufaberlin on 2008-02-29
The best thing you can do is get real deep in the source code of the kernel.

---

### Post by kellemes on 2008-02-29
> **exneo002 said:**
> Hey I have a box with an 8gig partion and I want to improve performance with things like processes,read speed and termianal commands I should run periodically. I also want to gain an intimate knowledge of the linux kernal and I think learning things like this certainly help.
Also I want to learn about prosesors. More so than the basic pipline stuuf. I want to learn about instruction sets and drivers in the kernal any ideas?

Yes, the best way to get started is to start using [Gentoo]("http://www.gentoo.org/"), you'll be much more inspired to learn things like this.. It has a tremendous environment to help you compile custom kernels and every other package that's part of your system.
Also tweaking your system up to the extreme is a peace of cake with gentoo.
The [Gentoo forums]("http://forums.gentoo.org/") has a wealth of information for folks like you having a hunger for knowledge. ;-)

---

### Post by kerry_s on 2008-02-29
> **exneo002 said:**
> Hey I have a box with an 8gig partion and I want to improve performance with things like processes,read speed and termianal commands I should run periodically. I also want to gain an intimate knowledge of the linux kernal and I think learning things like this certainly help.
Also I want to learn about prosesors. More so than the basic pipline stuuf. I want to learn about instruction sets and drivers in the kernal any ideas?

you can do that on any distro, just pick one your comfortable with. compile your own kernel, tweak settings, etc...

if you want to start slow you can install debian base and work from there.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

to get the base install, when it comes to package selection, uncheck both.

if you install X
apt-get install xorg (what-ever-else)

example:
apt-get install xorg fluxbox mc
exit  <-to get out of root
log in as your user
startx

---

### Post by exneo002 on 2008-02-29
k so should I go to the 64bit kernal or would that screw up my alsa config and my apps

---

### Post by kerry_s on 2008-02-29
i think you should start with regular 32, alot of stuff is not 64 compatible yet.

---

