---
title: "FireStarter blocks Ubuntu Synaptic Request"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by DaemonLee on 2007-03-30
Once, I install Firestarter, it blocks all communication from Canoncial to me, via Synaptic. If it's done through update-manager, it allows it. 


I've tried every way to "greenlight" it, without messing with my outbound traffic permission. I really don't wish to set it on blacklist everything unless permission is given. 

Seems like a pain. 



Any ideas?

---

### Post by 67GTA on 2007-03-30
I had the same problem with no solutions. I think it may be a bug. I uninstalled firestarter. Linux is different from Windows in the fact that all the ports are closed by default and will only open for outgoing stuff. Firestarter is really just a graphical way of managing the iptable(firewall) rules. You should be fine without it as long as you don't manually open any of your ports.

---

