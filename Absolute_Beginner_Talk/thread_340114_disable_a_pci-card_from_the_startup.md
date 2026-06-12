---
title: "disable a pci-card from the startup"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by RicardoSoe on 2007-01-16
Hi peeps,
I having a problem with my intelligent (i2o) pci-card (A DSP card from TC Powercore). I have surfed on the internet and people have the same problem with other i2o oriented cards.Cause of the fact that I won't use the card with linux, I want to disable/delete/exclude the card from the startup sequence of my Kubuntu setting. I looked the card up with lsmod and dmesg but taking the name from those listings and putting it in the /etc/modprobe.d/blacklist won't work. Can somebody help me with this?

Thanks,

Ricardo Soe

---

### Post by peabody on 2007-01-16
Unfortunately, if the blacklists don't work, the only other thing I can think of trying is to custom compile a kernel with the relevant code for that hardware completely disabled (and no, I'd have no idea where to look in the kernel config).

I take it you're duel booting and using the card in Windows?

---

### Post by RicardoSoe on 2007-01-16
Yeah you are correct,
Because in windows I have the software for it. The reason why I want to disable it is because it hangs the startup of Ubuntu for some time. I haven't had this problem with the 2.4.22 kernel when I was on slackware.

---

