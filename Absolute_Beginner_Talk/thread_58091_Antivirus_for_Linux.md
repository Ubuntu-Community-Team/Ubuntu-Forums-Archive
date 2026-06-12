---
title: "Antivirus for Linux"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by spectra1 on 2005-08-18
I am new to linux. Can anyone tell me a what a good antivirus program for linux would be, and how would I download and install this program

---

### Post by soce_32 on 2005-08-18
There are several free and commercial AV solutions for linux - ClamAV, Sophos, Vexira.  However, these are largely aimed at mail or samba servers.  You generally do not need AV software for a linux workstation, but there is a script called chkrootkit that examines your system for telltale signs of common exploits that affect linux.  aptitude search chkrootkit

---

### Post by aysiu on 2005-08-18
[QUOTE=spectra1]I am new to linux. Can anyone tell me a what a good antivirus program for linux would be, and how would I download and install this program[/QUOTE] It's called "you don't need it."

---

### Post by erikpiper on 2005-08-18
That is true. You don't need it. A firewall is a good idea, anti spyware is useless, and so is disk defragmenting software. (Linux filesystem doesn't frag in the first place)

Thought that could be useful to you.

---

### Post by codejunkie on 2005-08-19
[QUOTE=erikpiper]That is true. You don't need it. A firewall is a good idea, anti spyware is useless, and so is disk defragmenting software. (Linux filesystem doesn't frag in the first place)

Thought that could be useful to you.[/QUOTE]
the only way you might need antivirus software in linux is you have a windows computer sharing the same network connection with it and you share files between the two then you could put the windows pc at risk of infection.

---

