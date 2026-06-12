---
title: "Defrag? Clean? Registry?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by gvgerman on 2006-09-27
As a long-time Windows user, I understand from time-to-time I have to remove the "junk" files, defragment the hard drive, even clean and defrag the registry.  Do I need to do any of this or anything like this with Ubuntu?
Thx,

---

### Post by dmizer on 2006-09-27
nope.

---

### Post by wieman01 on 2006-09-27
No defrag, no cleaning of registry, perhaps a bit of disposing of junk files:

[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by elchinovi on 2006-09-27
Hello gvgerman!
I'm pretty new to the Linux world, but I think that I can safely say that all that "cleaning up" is no longer necessary...
Forget abour messing up the registry, because there is not one to mess up, and the files are neatly managed, so no need to defrag, but I'll let the more experienced ones tell you the right thing, but I might be right on the spot!
Thanks!

---

### Post by kent41 on 2006-09-27
you could clean up disk with
```

sudo apt-get clean 
```

---

### Post by shat on 2006-09-27
Welcome to the joy that is the world of Linux!

Linux began as a multi-user system, where Windows was first based on a single user.  The linux filesystem therefore better allocates data in your file system, so that defragging is unnecessary, and you wouldn't have to worry about fragmentation at all as long as your partition isn't full.  There was a good link that explained this concept really well, but I don't have it off the top of my head.

Linux sort of has a "registry", but the only reason you would want to tidy things up is because you have leftover configuration files- you don't need anything to "scan" or "sweep", because you aren't going to get any viruses.

The most you could possibly want is a good [free] firewall.

Correct me if I'm wrong, I've only been a user for a few months, but I'm loving it!

---

### Post by xpod on 2006-09-27
Your Ubu will run a system check every 30 boots which is about all it needs to keep itself in decent shape i think...no more reg`s or defrags:D

---

### Post by dmizer on 2006-09-27
> **shat said:**
> The most you could possibly want is a good [free] firewall.

actually ubuntu comes with iptables (your firewall).  it's just not configured.  so you don't need a firewall, you need a front end for configuring it.  you can use a number of different tools.  the most common of which is firestarter.

but just like a multitude of other tools in linux (network manager, synaptic, nautilus just to name a few) firestarter is merely graphical front end for running command line tasks.

---

### Post by Brunellus on 2006-09-27
Please have a look at the advice on [this page](https://wiki.ubuntu.com/CriticismFAQ#head-710379069c57682b4c113fa8680f19fb8598f9f8).  Linux does things very differently from windows in this regard--and the difference is definitely for the better.

---

### Post by shat on 2006-09-27
I found the site about fragmentation that explained it the best for me [here]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

---

### Post by xpod on 2006-09-27
S**t shat ...im still seeing little zeros before my eye`s...lol

---

### Post by gvgerman on 2006-09-27
Thanks, All.
Special thanks to wieman01 who has helped me before.

---

