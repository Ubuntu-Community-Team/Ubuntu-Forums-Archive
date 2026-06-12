---
title: "In great need of Xubuntu help."
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Famicommander on 2008-02-15
I tried asking this yesterday in the general forum, but to no avail.

Here are the specs on the computer in question:
AMD Duron @1.3ghz
256MB RAM
32GB free hard drive space
SiS630 integrated video card with up to 64MB shared video RAM
Xubuntu 7.10 Gutsy Gibbon

I just installed it the other day, and the freezing is unbearable. The only thing I've been able to accomplish was installing Xubuntu-restricted-extras. Other than that, it's just been constant freezing.

Directly after the install, I was having screen resolution issues (it wouldn't go higher than 800x600). I fixed this by going to System>Administration>Screens and Graphics and selecting a monitor setting that allowed for a higher resolution (it detected by flatscreen CRT KDS monitor simply as "generic plug and play" and only allowed 800x600 res).

So, I assume all of the freezing is due to a graphics card driver error. I searched the net, and I found this driver:
[http://www.sis.com/download/](http://www.sis.com/download/)
(sub-menu, navigate to Linux->IGP Graphics Drivers->Sis630&SiS730 series)

I downloaded the .tgz file and extracted it on the desktop. I clicked on it, and nothing happened. I right-clicked and selected run executable, and nothing happened.

How can I make this driver install?

Please explain it in very simple terms, if you can. I don't really know anything about terminal.

---

### Post by Famicommander on 2008-02-16
I forgot to mention that of the available 64 MB, I'm currently allocating 16MB.

I have tried allocating 8, 16, 32, and 64MB and I get freezes on all of them.

I've done a RAM check and everything came back fine.

---

### Post by PeterJS on 2008-02-16
Well, I've got some bad news for you. That's not actually a driver. I downloaded it, and looked at it, and it's a precompiled copy of XFree86 with the SiS drivers built in. It's woefully out of date as no one has defaulted to using XFree in over 3 years, it's completely incompatible with modern modular X org. And lastly given it's monolithic nature there's definitely not a kernel driver in there, so even if it wasn't ancient it wouldn't help with stability at all.

---

### Post by ashmew2 on 2008-02-16
Got beat :P

---

### Post by Famicommander on 2008-02-16
> **PeterJS said:**
> Well, I've got some bad news for you. That's not actually a driver. I downloaded it, and looked at it, and it's a precompiled copy of XFree86 with the SiS drivers built in. It's woefully out of date as no one has defaulted to using XFree in over 3 years, it's completely incompatible with modern modular X org. And lastly given it's monolithic nature there's definitely not a kernel driver in there, so even if it wasn't ancient it wouldn't help with stability at all.

What else could be causing the freezing then? It's pretty bad.

---

### Post by PeterJS on 2008-02-16
> **Famicommander said:**
> What else could be causing the freezing then? It's pretty bad.

Don't know, I didn't mean to imply that you mis-diagnosed the problem, but rather that this isn't the solution.

Is there anything in the logs that jumps out and says I'm an error danger Will Robinson! The logs can be found under System > Administration > System Log.

---

### Post by Famicommander on 2008-02-16
> **PeterJS said:**
> Don't know, I didn't mean to imply that you mis-diagnosed the problem, but rather that this isn't the solution.

Is there anything in the logs that jumps out and says I'm an error danger Will Robinson! The logs can be found under System > Administration > System Log.

No, the system log is fine.

I'm currently on my normal Ubuntu rig, so I can't access it now, but I don't recall anything out of the ordinary. It was consistently running at about 8% CPU usage and <100MB RAM usage.

The Xubuntu rig is just a project, but I'd still very much like to figure out the problem.

---

