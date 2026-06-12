---
title: "What to do when system hangs at boot?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by echo15 on 2007-03-21
I just installed Ubuntu 6.06 in an old PC and am trying it out. I'm a total linux newbie. I installed a wireless card (Edimax with RT2561 chipset) and used the network admin GUI which I found out I shouldn't have done (from another thread).  After using the network admin GUI, my system hangs during boot.  I had to reinstall the system since I didn't know how to fix it.

Anyways, if I'm going to start playing with Ubuntu, I'm probably going to do something wrong again which might cause another hang at boot.  So I wanted to know, how do you get into the system if it hangs during bootup to try and fix it?

Thanks!

---

### Post by kidders on 2007-03-22
Hi there and welcome,

Many Linuxes have taken to using pretty splash screens that hide what's going on while your system is booting. If you're doing a lot of messing around, and are afraid of provoking boot-time problems, you could disable it in /boot/grub/menu.lst, or maybe add a new "splash-less" menu option for yourself. Failsafe boots don't use splash screens.

If you can see boot-time messages, you can often get an idea of what's causing the problem, and whether waiting another 30 seconds would be worthwhile ... which is often the case with networking problems.

Something else you can learn about is "chrooting". Technically, you don't actually need to *boot* a Linux environment in order to use it. If you make a mess and break your box, you can easily boot from a CD and enter your Ubuntu environment from there, using a short sequence of commands. Once inside, you can tweak whatever is required to fix your problem, as though your box had booted *itself* up.

I know this is very general advice, but general solutions never fail! :-P

**Edit:** I forgot to add a reassuring "don't worry". After a while, you'll get pretty used to the way Linux does things, and you'll just *know* what sorts of tweaks are likely to cause problems, and which ones aren't. In the grand scheme of things, booting problems are pretty rare, but it's always useful to have a trick to get out of them.

---

