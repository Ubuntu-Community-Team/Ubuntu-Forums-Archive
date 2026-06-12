---
title: "Really bad probelm after beryl"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-20
After trying to install beryl i reached the last step to restart the x server. Once i did i saw all these weird graphic errors. I restarted my computer and now i get booted to the command prompt. how can i fix this! It sais Failed to start X server (your grpahical interface). It is likely that it is not set up corerctly

It also sias
X window system version 7.2.0
Release date 22 january 2007
X protocol version 11, revison 0, release 7.2
Build operating system: Ubuntu
Module loader present
Markers: (--) probed, (**) from config files, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (ee) error, (NI) not implented, (??) unknown
(==) log file: "/var/log/xorg.0.log", time : Fri apr 20 22:01:19 2007
(==) using config file: "/etc/x11/xorg.conf

---

### Post by taurus on 2007-04-20
From the prompt, run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by %hMa@?b&lt;C on 2007-04-20
type in the console
sudo dpkg-reconfigure xserver-xorg
follow the prompts.  if you need any more help, dont hesitate to ask

---

### Post by overdrank on 2007-04-20
> **mojo123 said:**
> After trying to install beryl i reached the last step to restart the x server. Once i did i saw all these weird graphic errors. I restarted my computer and now i get booted to the command prompt. how can i fix this! It sais Failed to start X server (your grpahical interface). It is likely that it is not set up corerctly

Hi in the command prompt use the command *sudo dpkg-reconfigure xserver-xorg* and follow the instructions and that should you get you going again! :)

Dang to slow lol

---

### Post by mojo123 on 2007-04-20
When i get to the desired default color depth in bits the command prompt would pop underneath saying something about overwirting ughhhhhhh should i just reinstall

---

### Post by overdrank on 2007-04-21
> **mojo123 said:**
> When i get to the desired default color depth in bits the command prompt would pop underneath saying something about overwirting ughhhhhhh should i just reinstall

It is overwriting the changes you made to the xorg. That is what you want to do!:guitar:

---

