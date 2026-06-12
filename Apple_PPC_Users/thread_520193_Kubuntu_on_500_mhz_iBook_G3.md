---
title: "Kubuntu on 500 mhz iBook G3?"
date: 2007-08-07
forum: Apple PPC Users
---

### Post by zbittner on 2007-08-07
I have a rev.A 500 Mhz iBook G3 384 MB RAM, and the question is how well will Kubuntu Feisty run on it? It is currently running 10.3.9 which feels pretty sluggish.

On an unrelated note, is there a PPC kickoff build floating around, and if so would this machine be able to handle it?

---

### Post by stmiller on 2007-08-07
Hey it should run fine. Many people on this forum are using G3 mac laptops with success and will probably chime in. You could also try Xubuntu, or Blackbox window manager which are lightweight. They need very little ram (even 64MB is enough). Video playback of some codecs might be sluggish though, due to the CPU.

---

### Post by bodycoach2 on 2007-08-08
Unless you can install more memory in that machine, I'd run Xubuntu instead. Kubuntu will use more resources, and will run slower in that machine. I'm not sure of the top-end limit on memory, but if you can increase it to 512, that would make a big difference. 

Xubuntu, however, will run nicely in that machine, as it is now.

> **stmiller said:**
> Hey it should run fine. Many people on this forum are using G3 mac laptops with success and will probably chime in. You could also try Xubuntu, or Blackbox window manager which are lightweight. They need very little ram (even 64MB is enough). Video playback of some codecs might be sluggish though, due to the CPU.

---

### Post by daladheri on 2007-08-08
Is Kubuntu Fiesty available for PowerPc? I thought only dapper runs on PowerPcs.

---

### Post by kerry_s on 2007-08-08
prepare for the future, go debian, ubuntu is dropping ppc.

[http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/](http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/)

personally, i would go with the net installer/businesscard iso & do a custom install. If you build it to your needs using light applications that thing will fly.

---

### Post by daladheri on 2007-08-08
Thanks for the suggestion but I will probably get an Intel in the near future. I tried installing debian and it did not work well. I think Ubuntu is the best. Ubuntu has earned a loyal follower.

---

### Post by stmiller on 2007-08-09
> **kerry_s said:**
> prepare for the future, go debian, ubuntu is dropping ppc.


Ubuntu is not dropping PowerPC.

daladheri: Read the Sticky at the top of the forum for a link to Feisty PPC, and be sure to read the PowerPC FAQs (link is below).

---

### Post by Lord Shank on 2007-08-10
Debian can be a little spotty on a G3, I'd stick with ubuntu for now.  I never could get it to save my settings correctly.  The sound driver and the trackpad were always screwing up.  If you install ubuntu, go with Xubuntu, and turn off every bit gui you don't need, no shadows, animations etc, no weather update icons or screen savers either.  You'll need to use the alternate install, or #dpkg reconfigure xserver-xorg to get the graphics to work right.  The graphic are the only problem with ubuntu, damn ATI cards.  Also, unless you like the trackpad tap function do #trackpad notap.  If you don't mind configuring it, open box is cool, but it can be a bit tough to get right with no right click.

---

