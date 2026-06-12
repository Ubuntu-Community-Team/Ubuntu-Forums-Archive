---
title: "Boot message: Setting up resolvconf..."
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-08-26
During system start I get the message: **"Setting up resolvconf....failed"**.
I don't have obvious difficulties running Ubuntu 6.06 64-Bit PC, but I want to make sure everything is ok. Can anybody tell me how serious this is, because with Synaptic Package Manager I figured out that the package "**resolvconf"**is not installed at all.

---

### Post by NetworkGuy on 2006-08-26
Are you referring to resolv.conf?

I've seen that message also, but I do don't have any problems.  Maybe someone can enlighten us as to why this happens.  :)

---

### Post by scxtt on 2006-08-26
i've had resolvconf installed on my box when i **aptitude install mailx**, as well as postfix and some locking program ... it was seriously f'ing up the way my nameservers were resolved (basically my /etc/resolv.conf was overwritten w/ NOTHING) ... so what i'm saying is - if the resolvconf package is installed, do an **aptitude remove resolvconf** and get rid of it! - i did, and mailx is working fine (it wasn't when resolvconf was installed and i would reboot) ...

---

