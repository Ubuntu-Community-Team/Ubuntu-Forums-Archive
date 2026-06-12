---
title: "Internet connection shareing"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by Braynid on 2006-05-26
Hello,
I relize that this topic has been discussed over and over again, and i to have read manny posts of this sort but it seems that i cannot have it done.
I have tried usig iptables but it won't work
I have Ubuntu on a computer, and another WinXP. eth2 is my internet and eth1 is my lan.
Could you pease teach me how to do this other than settup squid?
Thanks for your understanding! 
I am sorry again for spamming you again with this kind of thread.

---

### Post by Braynid on 2006-05-26
I do not have firestarter or anything of the sort

apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter

I have tried:
# iptables --flush
# iptables --table nat --flush
# iptables --delete-chain
# iptables --table nat --delete-chain
# iptables --table nat --append POSTROUTING --out-interface eth2 -j MASQUERADE
# iptables --append FORWARD --in-interface eth1 -j ACCEPT
# echo 1 > /proc/sys/net/ipv4/ip_forward

I work as root.The above are commands that I try from a HOW-TO, I have tried to follow the one on this forum but i get

apt-get install dnsmasq ipmasq
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dnsmasq

---

### Post by Braynid on 2006-05-26
It seems that now I have broke it completely... i don't know how but now there is no ping reply between the two computers...
Any suggestions will be highly appreciated

---

### Post by Koech on 2006-05-26
I think the problem could be that you have not enabled all repositories, but I am not sure it's the only problem. Try that or try using synaptic to get them for you.

---

### Post by Braynid on 2006-05-26
Hmm.. i don't know what you mean by repositories, nor do i know how to enable them...

---

### Post by Koech on 2006-05-26
I think the problem could be that you have not enabled all repositories, but I am not sure it's the only problem. Try that or try using synaptic to get them for you.

---

### Post by Koech on 2006-05-26
Repositories are listed under /etc/apt/sources.list and are the list of https the program apt-get or synaptic uses to get Ubuntu updates and open source software. A good tutorial on  this is [here]("http://ubuntuguide.org/#repositories"). Be free to ask more.

---

