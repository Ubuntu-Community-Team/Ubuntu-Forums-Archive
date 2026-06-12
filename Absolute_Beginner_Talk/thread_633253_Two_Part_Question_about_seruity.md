---
title: "Two Part Question about seruity"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by dnice on 2007-12-06
Does anyone know how to get the firestarter, started??? And is that all i would need to protect my pc with the ubuntu OS? I do have automatrix but i dont c firestarter.

---

### Post by Dr Small on 2007-12-06
Firestarter is only the GUI (Graphical User Interface) of Iptables, your firewall. Firestarter only configures your firewall, so no need to have it running. But, to get it running, look under System > Administration > Firestarter, or type:
```
gksudo firestarter
```

Your ports should be closed by default, and you will be safe.
As for Automatix, here is their support forum:
[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

Also, here is a good security thread by bodhi.zazen:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Dr Small

---

### Post by dnice on 2007-12-06
Thank you very much for the information. So with this there is no need for avast ir any other system security right?

dnice

---

### Post by vikram on 2007-12-06
security is not installing one app or another just as locking your front door is important but of no use if you have the backdoor open.

security is multi layer fiire wall is important but also ensure that you only install from trustworthy sources, run programs as root with caution, allow minimum permissions  required, disable unsed services, patch systems regularly etc.

---

### Post by banewman on 2007-12-06
The greatest security threat to an OS is the person controlling the keyboard and mouse.
Ubuntu is shipped "with safe settings" as default - so be careful of what you open or download is the best advice. :)

---

### Post by dnice on 2007-12-06
Thank you for the update guys. i will take your advice

---

