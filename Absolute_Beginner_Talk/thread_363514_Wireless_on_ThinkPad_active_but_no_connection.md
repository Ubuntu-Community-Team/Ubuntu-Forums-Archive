---
title: "Wireless on ThinkPad active but no connection"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by lacrumb on 2007-02-17
I have an IBM ThinkPad R31 with wireless included.  Ubuntu reports this as an Intersil corp. Prism 2.5 Wavelan.
The wireless connection is eth1 and is active.  The Interface properties has Enable this connection checked.  ESSID is what is used with my D-Link Dl-524 wireless router and I have put in the WEP.

Connection setting is DHCP.

I can access the internet through eth0 as a wired connection to the same router.

I am new with Linux and am not a programmer.

---

### Post by in_flu_ence on 2007-02-17
Have you tried pinging your router and see if there is a connection to at least the router?

How about configuration within the router? Does it permit you to access it?

Also I remember that some router does not permit u to type in plaintext in WEP (You have to check that out 'cause i read it somewhere myself but I don't have the problem here) and you have to type in the hex code (or something) for WEP.

THat's the usual problems that I have seen and I have myself encountered.

---

### Post by lacrumb on 2007-02-17
With WinXP I can enter the WEP in plain text.

I will have to ask my son about access to the router as he is the one that set it up for me.

I tried to ping various address and was successful at 192.168.1.1 but nowhere else.  I think that this is the gateway address but will have to talk to my son.

Thank you

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

