---
title: "No Network Connection"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by orbeus on 2007-07-18
Hi

My first problem with 7.04 is I can't connect to the internet with the wired connection. The wired network drop-down is greyed out. I have Fedora on another drive and that connects fine...

I'm running on a Shuttle PC SS31T with 2 x SATA II drives and Intel core 2 E4300. 

TIA

ps. more post to come sadly... :(

---

### Post by loserboy on 2007-07-18
does
```
lspci
```
show your card?

---

### Post by orbeus on 2007-07-18
Yup.

Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter (rev01)

Get the same problem when I boot from the CD...

O

---

### Post by loserboy on 2007-07-18
is the "wired connection" listed when you go to Syatem>Administration>networking ?

I'm normally on a computer that runs edgy, but if I remember right feisty tries to do all the networking automatically, which is nice but sometimes doesnt work and you have to switch to manual configuration and play with some stuff

---

### Post by orbeus on 2007-07-18
It is there... 
When I go to properties it says Enable Roaming Mode should it not say Enable This Connection??


I did have all this working on a SS21T without having to do anything, as you say it sets itself up automatically.
Also Fedora has no issue...

Thanks for your input btw.

O

---

### Post by Amplidude on 2007-07-18
> When I go to properties it says Enable Roaming Mode should it not say Enable This Connection??

I've had a similar problem ( which I haven't solved yet) but no, it shouldn't say enable roaming mode (whatever that is). click on the box to stop the roaming mode and teh rest of the box should un-grey. Fill in the requires IP etc.

---

### Post by orbeus on 2007-07-18
Unfortunately roaming mode is already unchecked...

O

---

### Post by loserboy on 2007-07-18
well it's obvious that you know your way around, but I have to ask, in the Networking window is "wired connection" checkmarked

this might sound stupid, but even if it is, try unchecking it then checking it again.

---

