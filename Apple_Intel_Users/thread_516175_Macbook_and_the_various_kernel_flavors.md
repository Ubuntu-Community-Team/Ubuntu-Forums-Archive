---
title: "Macbook and the various kernel flavors"
date: 2007-08-02
forum: Apple Intel Users
---

### Post by mdh on 2007-08-02
Hi Mac Linux users,

I am wondering whether you guys are running the *-generic kernel package or the *-386 version?. My default ubuntu install on my *macbook* installed the 2.6.20-15-generic package and I recently updated to 2.6.20-16-386 version and all of a sudden my wireless network stopped functioning. I switched back to the 2.6.20-16-generic and wireless came back to life. I am wondering whether mac users are supposed to use to 386 version at all?!

Another question on the kernel flavors, since *macbook* has a core duo processor shouldn't we be using *-686 flavor, isn't the 686 kernel flavor targeted at the dual processor machines?. If we stick to *-386 or the *-generic flavor would we be taking a performance hit?

---

### Post by cyberdork33 on 2007-08-02
> **mdh said:**
> Hi Mac Linux users,

I am wondering whether you guys are running the *-generic kernel package or the *-386 version?. My default ubuntu install on my *macbook* installed the 2.6.20-15-generic package and I recently updated to 2.6.20-16-386 version and all of a sudden my wireless network stopped functioning. I switched back to the 2.6.20-16-generic and wireless came back to life. I am wondering whether mac users are supposed to use to 386 version at all?!

Another question on the kernel flavors, since *macbook* has a core duo processor shouldn't we be using *-686 flavor, isn't the 686 kernel flavor targeted at the dual processor machines?. If we stick to *-386 or the *-generic flavor would we be taking a performance hit?

generic is a metapackage for the 686 version.

If you want more kernel performance, compile your own. There is a thread with instructions in this forum. 

BTW, if you change your kernel you may have to reinstall the modules needed for other hardware, like audio, isight, etc.

---

### Post by mdh on 2007-08-02
cyberdork33, thanks for the reply about 686. Actually, I botched up my initial question, I should have asked shouldn't macbook users be using SMP kernel because macbook has dual processors. I got all got confused between 386, 686 and SMP. Now, to the performance part of the question how much of a difference you will see as an end user between an SMP kernel and a 686/386 kernel running on a dual processor machine.

---

### Post by cyberdork33 on 2007-08-02
> **mdh said:**
> cyberdork33, thanks for the reply about 686. Actually, I botched up my initial question, I should have asked shouldn't macbook users be using SMP kernel because macbook has dual processors. I got all got confused between 386, 686 and SMP. Now, to the performance part of the question how much of a difference you will see as an end user between an SMP kernel and a 686/386 kernel running on a dual processor machine.

I believe smp is enabled in the kernel config for the generic kernels. There used to be a separate kernel available, but I don't see it anymore which leads me to believe that is has merged. Look at the thread for compiling your own kernel, and you can config any options your want.

---

### Post by benanzo on 2007-08-02
cyberdork is right, the **-generic** kernel has SMP enabled by default if it detects a dual-core CPU on boot.  (no special kernel.)  You can literally take the **-generic** kernel and install it on *any* 32-bit Pentium-class (AMD included) machine and it should run just fine, hence why it's the default kernel for almost every Ubuntu installation.  The downside to this is that there's a lot of unnecessary overhead because *so many* configs are enabled for hardware or technology that us Mac users simply don't want/need/have.

You are guaranteed to notice a significant decrease in boot time and improved overall performance if you follow Dirk's [HOWTO]("http://ubuntuforums.org/showthread.php?t=442941") for compiling a custom kernel for the Mac.

Good Luck!

---

