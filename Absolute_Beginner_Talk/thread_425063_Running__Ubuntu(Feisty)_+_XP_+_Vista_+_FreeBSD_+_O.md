---
title: "Running  Ubuntu(Feisty) + XP + Vista + FreeBSD + OSX simultaneously in virtualization"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by whee on 2007-04-27
I want to run Ubuntu(Feisty) + XP + Vista + FreeBSD + OSX simultaneously in virtualization and/or multi-boot.
But i'm wondering how to do this.
Also for multi-booting there's one thing i'm worried about.
When one wants to dual-boot Ubuntu + XP, one has to install XP first and after that Ubuntu, if one does it the other way around, then XP will overwrite the boot sector of a hard disk?
So if i wanted to install all those OS's, should there be a particular order in installing them? So that for example GRUB won't be broken because other OS installs will overwrite the boot sector of a hard disk?
How would one go about doing something like this, both running all those OS's simultaneously in virtualization and multi-booting them. And all this with good stability?
Can anyone shed some light on this?


PS: With virtualization i don't mean running it inside VMware on top of another OS, but hardware virtualization. The kind where you have running multiple OS's on a machine with no  host OS.

PPS: I'm not yet sure about OSX though, maybe i'll scrap that one.

---

### Post by Cypher on 2007-04-27
To do this, you would install XP first, followed by Vista which should get you the dual-boot option between those  two. Then install FreeBSD (having never installed it, i don't know what it does for booting) and then Ubuntu with GRUB will boot them all..

How exactly are you planning on doing the hardware virtualization?? You cannot have two OS' running on a single machine at the same time without one acting as the host OS with software virtualization.

I can understand multi-booting Ubuntu + XP + Vista, but why FreeBSD and OSX?

---

### Post by NyteGeek on 2007-04-27
You would need a heck of a machine to even make that worth doing. Why do you even want to? Is there a practical purpose to this?

---

### Post by sailor2001 on 2007-04-27
I was under the impression you could only have four os's...... might be wrong........I doubt you can run vista dual with xp as microsoft doesn't like anything to run with it.......I would think that vista would wipe out xp...

---

### Post by gohanssjn on 2007-04-27
> **sailor2001 said:**
> I was under the impression you could only have four os's...... might be wrong........I doubt you can run vista dual with xp as microsoft doesn't like anything to run with it.......I would think that vista would wipe out xp...

You can run both.  I did for a while.  You just have to be careful with your installs.

---

### Post by whee on 2007-04-27
Well the reason for doing this is i need the OS's for various tasks.
For example i plan to do 3D art on Linux. But want to do video editing on OSX. With Vista i want to run new games and XP i intend to use for legacy software. FreeBSD i want to use for running a server on.
The machine i intend to do this all on will be either the next AMD(Barcelona) true quad-core or Intels new quad-core(Penryn) which will be released later this year.
The machine will probably have 4GB of DDR3 ram and a Geforce 9.
I don't know how hard running so many OS's will be on that kind of hardware though. I guess i'll just have to experiment with that kind of setup first.

---

### Post by Cypher on 2007-04-27
OK..just so we are all clear..you intend to buy a quad-core based system, but realize that that does not mean that you can run 4 OS' on each of those cores simultaenously. You would have to run each of the OS inidividually. That being the case, I can understand your reasoning for Ubuntu, OSX (you could do 3D here as well, why bother with Ubuntu??), XP and Vista..but a FreeBSD server? Doing what? You'd have to reboot back into one of your other OS' to perform you other tasks, so it doesn't make sense to me..

Unless the AMD or Intel chip is going to come with some sort of a BIOS that will allow you run your OS' simultaenously, I think you'd probably want to drop FreeBSD and maybe Ubuntu from that list..

---

### Post by whee on 2007-04-27
> **Cypher said:**
> OK..just so we are all clear..you intend to buy a quad-core based system, but realize that that does not mean that you can run 4 OS' on each of those cores simultaenously. You would have to run each of the OS inidividually. That being the case, I can understand your reasoning for Ubuntu, OSX (you could do 3D here as well, why bother with Ubuntu??), XP and Vista..but a FreeBSD server? Doing what? You'd have to reboot back into one of your other OS' to perform you other tasks, so it doesn't make sense to me..

Unless the AMD or Intel chip is going to come with some sort of a BIOS that will allow you run your OS' simultaenously, I think you'd probably want to drop FreeBSD and maybe Ubuntu from that list..

I was under the impression that Xen and/or KVM were able to run most of these OS's(including FreeBSD) simultanously through some sort of hardware virtualization or hypervisor, as new CPU's from Intel and AMD support these type of features.
The reason for using FreeBSD as a server simultaneously while for example working in Ubuntu or Windows is that suppose i would be gaming in Windows and Windows would crash, then FreeBSD would still be up and running and people would still be able to access my server.
FreeBSD is known for it's uptime/stability when it comes to running servers.

This screenshot shows basically what i'm trying to accomplish, but without a host OS and different OS's that i listed earlier:
[http://www.cl.cam.ac.uk/research/srg/netos/xen/screenshots/snapshot2.png](http://www.cl.cam.ac.uk/research/srg/netos/xen/screenshots/snapshot2.png)

---

### Post by Cypher on 2007-04-27
OK..so Xen or KVM or VMware all require some sort of a host OS running and they they provide the virtual machines to run various OS'. In the case of Xen, they call the host machine as Domain 0.

Regardless, all of these require you to get into a single OS, then launch the other virtual machines and the OS' they are configured to run. What you are seeking is some sort of a BIOS-level program that will launch multiple OS' without the host OS and I don't think that's possible.

---

