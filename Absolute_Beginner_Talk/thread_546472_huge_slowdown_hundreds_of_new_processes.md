---
title: "huge slowdown hundreds of new processes"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by yeastpuppet on 2007-09-08
not sure what happened, but I've had a huge slowdown in my system and my process manger is STUFFED with hundreds of apport, apt-cache, lsb-release and sh processes all of which are 0 bytes.  

Any ideas of what might have happened?  I grab all my updates from the package manager.....

Thanks yp

---

### Post by some_random_noob on 2007-09-08
Maybe you've been playing around a bit too much with updates/downloads? ... user error?

I never download any updates, and my computer runs perfectly. It's best if you leave things the way they are in most cases.

---

### Post by yeastpuppet on 2007-09-09
I only update when I get a notification

---

### Post by asmoore82 on 2007-09-09
> **yeastpuppet said:**
> not sure what happened, but I've had a huge slowdown in my system and my process manger is STUFFED with hundreds of apport, apt-cache, lsb-release and sh processes all of which are 0 bytes.  

Any ideas of what might have happened?  I grab all my updates from the package manager.....

Thanks yp

have you used Automatix??

---

### Post by yeastpuppet on 2007-09-09
No, I've heard too many bad things - Any idea what any of those files are?  apport?  sh?

Enough for tonight, I'll hack away tomorrow!

Tnx!  YP

---

### Post by asmoore82 on 2007-09-09
> **yeastpuppet said:**
> No, I've heard too many bad things - Any idea what any of those files are?  apport?  sh?

Enough for tonight, I'll hack away tomorrow!

Tnx!  YP

apport: [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)
sh: sh is the name of the default system **shell** on all UNIX systems.
this generic name is used so that scripts will be **portable**.
on Ubuntu, sh is a symbollic link to the **dash** shell.

---

### Post by tgalati4 on 2007-09-09
How much RAM do you have?  If you installed a bunch of updates simultaneously, then it is possible that you experienced a "Fork Bomb".  When low on RAM, extra housekeeping processes are spawned to keep up with the workload.  These forks are small and many and can bring a system to a crawl until the workload is reduced.

---

### Post by FuturePilot on 2007-09-09
This sounds like possibly a fork bomb. But I've never heard of a fork bomb from updates:confused: Usually fork bombs are carried out as DoS attacks.

---

### Post by yeastpuppet on 2007-09-09
I have a gig of RAM and Ubuntu has it's own drive.  

Never heard of a fork bomb.  Does anyone know what an apport file is?

Thanks!

---

### Post by jvc26 on 2007-09-09
Is the apport file to do with when a process/application crashes apport gathers initial information about the crash. From a look at the Ubuntu Wiki [here]("https://wiki.ubuntu.com/Apport") would explain what apport is.
Il

---

### Post by fannus on 2007-09-22
I'm having this exact problem, I have a lot of apport, apt-cache, and lsb_release processes spawning, and also lots of random segfaults.  As I understand it, apport spawns whenever a program crashes.


If you try running in recovery mode, you won't spawn a bunch of apport processes (because it doesn't have so many things starting up and then crashing).

My best guess is that my install got corrupted somehow, either by something in a recent ubuntu update, a hard drive crash, or my system got rooted.  I'm tempted to just reinstall from scratch.  If anyone has this and has fixed, I'm all ears

---

