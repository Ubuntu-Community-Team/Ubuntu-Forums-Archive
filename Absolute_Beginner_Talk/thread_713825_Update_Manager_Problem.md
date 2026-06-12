---
title: "Update Manager Problem"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by mikkko on 2008-03-03
i just recently installed ubuntu 7.10 and connected it in the internet.. and it successfully downloaded 196 files for update.. and when it was about to install and the updates, the laptop, went off coz the laptop was burning hot.. what should i do to fix this? coz i need to upgrade my linux.. 

when i click my update manager, it says "Software index is broken. It is impossible to remove or install any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

when i typed the command in the terminal, it said "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

then i tried typing, "dpkg --configure -a", it said "dpkg: requested operation requires superuser privilege"

what should i do? im a total noob at this.. i just started using linux.. i would really appreciate your help guys.. thanks ahead.. ^_^

---

### Post by arochester on 2008-03-03
Use "sudo" to get superuser privilege. The command is > sudo dpkg --configure -a

---

### Post by warbird on 2008-03-03
> **arochester said:**
> Use "sudo" to get superuser privilege. The command is

You'll get asked for a password too, which is your normal account password.

---

### Post by fuzzyk.k on 2008-03-03
or in gui open synaptic , on the left click custom filters then broken and deselect the packages there

you can also try sudo apt-get install -f in terminal

---

