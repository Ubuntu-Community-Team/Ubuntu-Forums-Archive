---
title: "how do i clean cache?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by richieboy on 2007-01-24
when using update manager and add/install what command do i use to clean the cache?  do apt-get clean and aptitude clean clean out those files?

thanks,
rich

---

### Post by %hMa@?b&lt;C on 2007-01-24
yes, it is the same cache, aptitude clean will do the trick

---

### Post by ardchoille42 on 2007-01-24
When you download packages for installation, they are held in /var/cache/apt/archives unless you've set Synaptic to delete them after installation and you use Synaptic to install those packages. If you use apt-get install or aptitude install, you can use "sudo apt-get clean" or "sudo aptitude clean" (they both do the same thing) to delete them.

---

