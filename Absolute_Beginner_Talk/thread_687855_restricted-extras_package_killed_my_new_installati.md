---
title: "restricted-extras package killed my new installation"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ajeannotte on 2008-02-04
i've had Ubuntu running on my 2 home PCs for 6-8 months now. for kicks, i thought i'd give Kubuntu a go since i use a lot of their programs (amarok, k3b, ktorrent, etc...)

Problem:
after installation i install my favorite programs (nvidia driver, vlc) and the restricted extras. i've pretty much got my system down for a fresh install since i'm doing it a lot. i like to play around with things so i find i do fresh installs a lot. never had a problem with Ubuntu.

as soon as i install the ubuntu-restricted-extras package and install it, it blows up. package manager gives me an error message about not being traceable... or something close to that (i'm not in front of it right now)... and when i try to open the package manager again (or apt-get) it tells me that it's already in use. even after i reboot it's still in conflict. 

if i try to have it resolve it's own conflict it blows up again. 

so far the thing i've tried are:
- 5 or so fresh installs (at least)
- installing restricted extras first
- updating system first
- tried both ubuntu-restricted-extras and kubuntu-restricted-extras
- used 'top' to try to find which processes are active and killing them
- tried it on both computers
     - AMD 5600+ X2 / nvidia 7900 GT
     - AMD 4200+ X2 / nvidia 8500 

i'm buggered. this problem is past my limit of usefullness.
right now i've got it installed on a separate partition, all my favorites installed, amarok with mp3 support, vlc plays all video formats that i need (haven't found any video it won't play yet), firefox with flash, but i did it withough using the restricted extras package.

i suppose i really don't need help as it's running, but it would be nice if i could just go to the restricted-extras and have it not ruin my fresh install. if i didn't have as much spare time as i do right now i'd have given up on kubuntu without even giving it a try.

maybe this post should be a bug report, i don't know. feel free to move it to the correct location mr/miss administrator.

---

### Post by jken146 on 2008-02-04
If you are running Kubuntu, install the **kubuntu-restricted-extras** package.

---

### Post by Blutack on 2008-02-04
Can you type
> sudo apt-get install ubuntu-restricted-extras
into a terminal and post the output please?

---

### Post by ajeannotte on 2008-02-04
uh..... no. 
if i install the restricted-extras package it ruins my beautifully running system.

---

### Post by ajeannotte on 2008-02-04
> **jken146 said:**
> If you are running Kubuntu, install the **kubuntu-restricted-extras** package.

i tried both restricted packages. i tried the jubuntu one first a few times and then tried the ubuntu one since it had never failed me using ubuntu.

---

### Post by Blutack on 2008-02-04
Fair enough! :)
Best bug report it then.

---

### Post by ajeannotte on 2008-02-04
> **Blutack said:**
> Fair enough! :)
Best bug report it then.

ok. what's the official method for that? i've never looked around here too much ... except finding methods to bend ubuntu to my will.

---

### Post by Blutack on 2008-02-04
Go here:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
It should tell you all you need to know.  Thanks!

---

### Post by benc123 on 2008-02-04
You can post a bug report [here]("https://bugs.launchpad.net/")

Or you could post the output Blutack asked for earlier

Benc

---

### Post by ajeannotte on 2008-02-04
ok, i've logged a bug following the link that you both provided (same link).

cheers.

---

