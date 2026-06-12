---
title: "Device Manager"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by grossvatti on 2008-03-14
Sorry if this is a re-post of some kind. I was looking under System-Administration for "Device Manager" something that could tell me about the hardware inside my laptop, but no device manager to be found. I am using Ubuntu 7.10

---

### Post by drs305 on 2008-03-14
system, preferences, hardware information. The screen is titled, appropriately, Device Manager

You can get an html-formatted page with lots of system hardware information by running:
```
sudo lshw -html > ~/Desktop/hardware.html
```

---

### Post by TeoBigusGeekus on 2008-03-14
System-> Preferences-> Hardware Information

---

### Post by grossvatti on 2008-03-14
Thanks a whole lot

---

### Post by grossvatti on 2008-03-14
Basic question about root and sudo? I do not understand these things, but I believe root is the root directory and sudo is like administrator privledges. If I sudo something, and it gives me some info or what not am I still in sudo mode, I don't want to mess anything up

---

### Post by danila4m on 2008-03-15
Strange things! I'm trying to set up wireless on my laptop. I know alomost nothing. I go to help page [https://help.ubuntu.com/7.10/internet/C/troubleshooting.html](https://help.ubuntu.com/7.10/internet/C/troubleshooting.html) and read there:
Check for device recognition

   1. Open Device Manager (System &#8594; Administration &#8594; Device Manager).
Now I'm seeking for "Device Manager" topic in forums... =)

---

### Post by iansane on 2008-03-15
hard info
hwinfo
system info
and I think there are others all in synaptic. But no device manager in system>admin

They all tell you lots of info about different things but none of them tells you everything. Like media players, you have to install 3 or 4 different ones instead of one doing it all.

---

### Post by chewearn on 2008-03-15
> **grossvatti said:**
> Basic question about root and sudo? I do not understand these things, but I believe root is the root directory and sudo is like administrator privledges. If I sudo something, and it gives me some info or what not am I still in sudo mode, I don't want to mess anything up

Link:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rustutzman on 2008-03-15
> **drs305 said:**
> system, preferences, hardware information. The screen is titled, appropriately, Device Manager

You can get an html-formatted page with lots of system hardware information by running:
```
sudo lshw -html > ~/Desktop/hardware.html
```

Excellent command! Thanks!

Russ

---

