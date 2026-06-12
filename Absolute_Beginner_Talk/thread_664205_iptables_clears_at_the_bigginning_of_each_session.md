---
title: "iptables clears at the bigginning of each session"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2008-01-10
Every time I reboot my pc the list of blocked ip's in iptables disappears, is this supposed to happen?

---

### Post by dashnak on 2008-01-10
You would have to make a script that ran at boot to make sure that every time you boot, the rules are applied...

---

### Post by nowshining on 2008-01-10
yes

and yes to what dash said

i suggest arno-iptables-firewall found in synaptic - u may have to add the rest of the repositores - system - administration - software sources 

except for soruces of course

it's an easy to use firewall script, has a section/file for creating ur own rules, etc...

there is also firestarter, and guarddog for GUIs that are front ends to iptables and will create a script of ur current rules to start up on reboot, don't worry u won't see an icon in the tray on either, but firestarter can be made to show one on every login/bootup.

---

