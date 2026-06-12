---
title: "Kernel and Gnome question"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-02-12
I just installed the latest kernel, it's something like 2.6.12.10-386 but this isn't the true latest version of the kernel is it ? Isn't it really 2.6.14.1 now ? If so why isn't it in the repositories ? Is it still under testing and is there a debian package for it b/c I really suck at kernel complication. 

My Gnome question:

How can I prevent update notifier from starting with gnome b/c it uses alot of memory on my slow machine. I check for updates every 3 days and I don't need it to run all the time. I tried to remove it from under sessions but it always comes back....any ideas ? Thanx :-)

---

### Post by az on 2006-02-12
[QUOTE=MasterChief1234]I just installed the latest kernel, it's something like 2.6.12.10-386 but this isn't the true latest version of the kernel is it ? Isn't it really 2.6.14.1 now ? If so why isn't it in the repositories ? Is it still under testing and is there a debian package for it b/c I really suck at kernel complication. [/QUOTE]

The kernel version will not change for the release.  If you want the latest kernel, either look for a backported version of it or install the most recent experimental release.  Right now, Dapper runs 2.6.15.  It will become the stable release in april.

---

### Post by xtacocorex on 2006-02-13
[QUOTE=MasterChief1234]b/c I really suck at kernel complication.[/quote]
I hear you there. I've only been able to do it once correctly when I ran Fedora and when I booted into it, I didn't have networking. I've tried since then with Kubuntu, but decided that it should wait when I'm not busy using my computer for solving engineering problems. 

[QUOTE=MasterChief1234]
How can I prevent update notifier from starting with gnome b/c it uses alot of memory on my slow machine. I check for updates every 3 days and I don't need it to run all the time. I tried to remove it from under sessions but it always comes back....any ideas ? Thanx :-)[/QUOTE]

Although I can't say how to specifically do it in Gnome, I know that in KDE you can have it save a session once and then when you log off, it won't save anything to that session. This is what I do since I want certain programs to start up whether I'm on my laptops battery or have it plugged in. This way, it doesn't start the programs multiple times. I just save a clean session once, and then have a bash script read on login to determine my acpi battery status.

So I would close all the programs you don't want saved to a session, then kill the updater thing, then save the session. After that, I'd log off and re-login to see if it worked. 

If I can ever get Gnome installed without it wanting to remove half of my KDE install, I might now more.

Hope this helps some.

---

