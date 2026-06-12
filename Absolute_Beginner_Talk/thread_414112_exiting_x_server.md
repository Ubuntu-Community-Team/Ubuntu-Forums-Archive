---
title: "exiting x server"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by mynameisjohn1234 on 2007-04-19
I am trying to install the driver for my nvidia 7900 gs go, and the installer says I have xserver running. I googled this, and it said I should try ctrl+alt+backspace, which simply logged me off. I also tried ctrl+alt+f1 and ctrl+alt+f2, which brought me to a text menu that didn't close x server. 
Sorry if this is a bad question, This is the first time I have ever used linux.

---

### Post by Awperator on 2007-04-19
I think the command is

sudo /etc/init.d/gdm stop

if you're running gnome. I am noob too, so sorry if this is a case of the blind leading the blind.

---

### Post by mynameisjohn1234 on 2007-04-19
Thank you, that worked but now it says it cannot load the libc kernel header. What woud this mean?

---

### Post by zaza1851983 on 2007-11-03
that means u need to download the libc package. go to System->administration->Synaptic packege manager. The libc6 package should be already installed, if not select it, and then select the package libc6-dev, then press apply, now you have the wanted libc by nvidia. That's as far as I've been,cheers

---

