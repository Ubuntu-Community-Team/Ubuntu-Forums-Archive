---
title: "System info and messages"
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2005-05-16
I was queried about these questions and I wasn't totally sure where to find the information. I figured I'd ask here first and then play around in Linux and find out first hand

First thing, I was asked was "where do you go to find out how many processors are in a system?"
Second thing, where are the network files (I thought they were in /etc/..somewhere) and where/how do you check the system messages?

---

### Post by Stormy Eyes on 2005-05-16
[QUOTE=TheAnonymousx]First thing, I was asked was "where do you go to find out how many processors are in a system?"
Second thing, where are the network files (I thought they were in /etc/..somewhere) and where/how do you check the system messages?[/QUOTE]

For CPUs, try **cat /proc/cpuinfo | less**. What network files are you talking about? Hosts and DNS files? Look at **/etc/hosts** and **/etc/resolv.conf** respectively. Ubuntu does try to auto-config your network via DHCP, though. As for system messages, are you talking about logs?

---

### Post by TheAnonymousx on 2005-05-16
Yeah, it'd be the logs. Sorry for the lack of vernacular knowledge.

---

### Post by somuchfortheafter on 2005-05-16
if your in hoary... applications / system tools / system log ... i think anyways....

---

