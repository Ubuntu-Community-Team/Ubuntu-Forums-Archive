---
title: "My Son Has Left Home!"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by marym on 2007-04-14
My son and heir has left the family castle.  Which means I don't have an on-site IT manager any more.

I am a completely new user of Ubuntu.  I am not a programmer, just a user.  

Belkin 802.11b wireless router will talk to the destop pc(windows), work laptop(windows), daughter's MAC, but has thrown a strop with my laptop.

Has anyone any ideas?

---

### Post by caffienefree on 2007-04-14
Could you please post the output of the following?

sudo lshw -businfo -C network

---

### Post by BarfBag on 2007-04-14
Copy and paste the code caffienefree gave you into the terminal (Applications - Accessories - Terminal).

---

### Post by n3tfury on 2007-04-14
> **caffienefree said:**
> Could you please post the output of the following?

sudo lshw -businfo -C network

lol.

---

### Post by xpod on 2007-04-14
> My son and heir has left the family castle. Which means I don't have an on-site IT manager any more.

I am a completely new user of Ubuntu. I am not a programmer, just a user. 

Brilliant....good on you marym
I think more of us parents need to be learning how these things work:D 
Too many mums & dads out there not got a clue what their young un`s are up to on these things.

Anyway marym...good luck and welcome to the forums

---

### Post by marym on 2007-04-14
> **caffienefree said:**
> Could you please post the output of the following?

sudo lshw -businfo -C network

I got

Bus info        Device      Class       Description
===================================================
pci@03:00.0     eth1        network     BCM4310 UART
pci@05:01.0     eth0        network     RTL-8139/8139C/8139C+
mary@hercules:~$
mary@hercules:~$

---

### Post by caffienefree on 2007-04-14
What if you type:

sudo iwlist scanning

Are any networks detected?

---

### Post by marym on 2007-04-14
Doesn;t look like it.  The screen readds

lo  interface doesn't support scanning
eth1 no scan results
sit0 interface doesn't support scanning

---

### Post by an4rew on 2007-04-14
my mum is more hooked on the net than myself after teaching her how to download tv shows she thinks its great fun :)

of course the when she has a problem i have to fix it!

---

### Post by NeoGreen on 2007-04-14
What brand of laptop do you have?  Have you recently installed Ubuntu on your laptop?

---

### Post by marym on 2007-04-14
It is a Lenovo and it came ready installed with Ubuntu.  The strange thing is, when I took it to my son's house it was working on his wireless no problem.

---

### Post by marym on 2007-04-14
> **an4rew said:**
> my mum is more hooked on the net than myself after teaching her how to download tv shows she thinks its great fun :)

of course the when she has a problem i have to fix it!

Well perhaps we ought to set up a forum for mothers who have been abandoned!

Mind you, I am enjoying learning how to use the system.[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by n3tfury on 2007-04-14
> **an4rew said:**
> my mum is more hooked on the net than myself after teaching her how to download tv shows she thinks its great fun :)

of course the when she has a problem i have to fix it!

lol, hopefully legitimately

---

### Post by disabled_20220313 on 2007-04-21
Hi,

I'm the Son.

The laptop works fine at my house using a 802.11b/g router with WPA the router at my mothers house is a Belkin 802.11b-only.

The laptop is a Lenovo 3000 N100 from Linux emporium installed with Dapper and uses ndiswrapper to get the wireless card to work.

Hope this helps

---

