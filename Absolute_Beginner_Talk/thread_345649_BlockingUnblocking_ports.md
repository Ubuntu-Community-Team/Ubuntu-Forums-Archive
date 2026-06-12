---
title: "Blocking/Unblocking ports?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-01-24
Hi,

I want to enable certain specific ports.  Where's the file that will allow me to do it? 
Do I have to reboot after modifying it?

Thank you.

---

### Post by x1a4 on 2007-01-24
Nevermind, found it.  It's /etc/services

---

### Post by x1a4 on 2007-01-24
Oops, jumped the gun a bit.  /etc/services is NOT it.  I'll just do what I need using iptables.

---

### Post by kosmic on 2007-01-24
If you want to block/Open Ports the way to go is with ***iptables***, if you prefer a GUI you can use Guardog or Firestarter but if you want to learn the best way is using the 'cli' :)

---

### Post by x1a4 on 2007-01-26
> **kosmic said:**
> If you want to block/Open Ports the way to go is with ***iptables***, <snip> but if you want to learn the best way is using the 'cli' :)

That's what I'm doing now.  I got a few good HOWTOs, printed the *iptables* and *ipchains* man pages and am doing a lot of reading.  In the meantime I used GuardDog.

---

