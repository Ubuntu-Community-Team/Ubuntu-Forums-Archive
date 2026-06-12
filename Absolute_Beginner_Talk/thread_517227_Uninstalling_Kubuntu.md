---
title: "Uninstalling Kubuntu"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by iAaron on 2007-08-04
Hi!

I've been dual-booting Ubuntu & Kubuntu on my PC and was wondering how to delete Kubuntu so I just have Ubuntu on there? Any help Apprecited. 

Aaron ;)

---

### Post by sad_iq on 2007-08-04
This should help: [http://ubuntuforums.org/showthread.php?t=96048&highlight=remove+kubuntu](http://ubuntuforums.org/showthread.php?t=96048&highlight=remove+kubuntu)

---

### Post by Majorix on 2007-08-04
How do you mean dual booting? Did the two use different partitions for /? Or do you mean that you have them installed together on a single OS? Like, you know, where you select one of the two at the startup menu.

If the latter is the case, simply do this:
```
sudo apt-get autoremove kubuntu-desktop
```

I don't have experience with dual booting so I am afraid I won't be of too much help if you are really dual-booting.

Good luck!

---

### Post by iAaron on 2007-08-04
I've got it so you select one of the two at the startup menu. I'll try that and get back to you soon. 

Thanks both of you. 

Aaron ;)

---

