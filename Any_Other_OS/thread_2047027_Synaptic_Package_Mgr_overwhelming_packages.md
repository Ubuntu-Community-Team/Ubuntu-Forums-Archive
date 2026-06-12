---
title: "Synaptic Package Mgr overwhelming packages"
date: 2012-08-24
forum: Any Other OS
---

### Post by UltimateCat on 2012-08-24
Hi:;)

I am not sure exactly how many packages that I have in Synaptic but I started going through the long list.  It seems to be an overwhelming amount of packages and I'm not sure where to begin except with apt.

Some packages I was able to determine what they are and what they are for but some I'm clueless and wondered if some are even necessary to have-

What; if anything can you suggest I do?

And Is is normal to have so many packages after a new install?

---

### Post by critin on 2012-08-24
> **UltimateCat said:**
> Hi:;)

I am not sure exactly how many packages that I have in Synaptic but I started going through the long list.  It seems to be an overwhelming amount of packages and I'm not sure where to begin except with apt.

Some packages I was able to determine what they are and what they are for but some I'm clueless and wondered if some are even necessary to have-

What; if anything can you suggest I do?

And Is is normal to have so many packages after a new install?

I'm not quite sure what you mean by 'have' in synaptic.  You do realize that these are not all installed in your system don't you?  Synaptic is a package manager like Software Center, but that will also install the dependencies on the package that you want.  

Unless you're talking about the dependencies list that show after you choose an item to install?  Yes, you will need those unless you're an expert in linux,  I'd install those.

Synaptic has thousands of items to choose from, but they are not all installed.  It's not like the 'Programs' folder in windows that shows what is installed.

---

### Post by oldos2er on 2012-08-24
> **UltimateCat said:**
> Some packages I was able to determine what they are and what they are for but some I'm clueless and wondered if some are even necessary to have-


I'm assuming you're talking about installed packages. Synaptic should show you a description of each package; it would help to know package names to determine if they're necessary or not.

---

### Post by UltimateCat on 2012-08-25
Like you said; when I click on a package Synaptic tells me what it is and that's good but the problem I am running into is that in honesty I really don't understand what some of these applications are for and do I really need them?

 Here are just a few packages that are not installed.

9base, 9menu, aacplusenc, ablly, abicheck, aboot-cross, acidbase, acl2-emacs, addresses.framework-

For example I have a package called  "aggregate" and it's description is ipv4 cidr prefix aggregator. (The detailed description says)  It takes a list of prefixes in conventional format on stdin, and performs two
optimisations to reduce the length of the prefix list.

Again, I can read and write English but this info. is like another language to me and I don't know what packages that are not installed if they should be installed or not.

---

### Post by UltimateCat on 2012-08-25
If this was your circumstances would you Google each and every package?

---

### Post by BigSilly on 2012-08-26
> **UltimateCat said:**
> Hi:;)

I am not sure exactly how many **packages that I have** in Synaptic but I started going through the long list.  It seems to be an overwhelming amount of packages and **I'm not sure where to begin** except with apt.

Some packages I was able to determine what they are and what they are for but some I'm clueless and wondered if some are even necessary to have-

What; if anything **can you suggest I do**?

And Is is normal to have so many packages after a new install?

There's a bit of a breakdown in communications here. What are you trying to begin? Are you trying to figure out exactly what every package does that you have installed, or are you trying to determine what every package available in Synaptic does?

You could Google each and every package and you'll still be none the wiser. You'll probably find exactly the same descriptions. If it's any consolation, I don't know what those things are either. If it's installed, it's because Ubuntu needs it to be installed, not for my direct understanding but certainly for my direct benefit for a stable system.

You'll need to be clearer about what you are trying to achieve. Synaptic shows everything - stuff you have installed and stuff that is available for install. Over the years I've come to know the stuff I need to add manually to a fresh install of Ubuntu. Beyond that it's a programmers domain! Good luck.

---

### Post by MadmanRB on 2012-08-26
Looking at packages in synaptic is intimidating I know as I was intimidated when I first used it.
But over time you learn that most of the apps you see you will probably never use.
This is the main reason why software center was made in Ubuntu to lower to the confusion of what to install.
But this doesnt make synaptic bad as it can install things not listed in software center.
I know its a new OS and you are curious on what to use, but dont dive that deep into it as Debian has a HUGE amount of things to use and with ubuntu being based on debian it inherits that hugeness.

---

### Post by critin on 2012-08-26
> **UltimateCat said:**
> 

Again, I can read and write English but this info. is like another language to me and I don't know what packages that are not installed if they should be installed or not.

You're learning linux and it's not easy, but it's not boring either.  :P

Don't install anything from synaptic  if you haven't been instructed to somewhere.  When you choose a package in software center, synaptic, or on the web, it will either install everything you need or it will plainly tell you what else you need.   You may have to write the details or copy/paste them into synaptic or the terminal (however you prefer).  

You choose the main package and the dependencies usually take care of themselves.

---

### Post by UltimateCat on 2012-08-28
Synaptic can be intimidating but that isn't the problem.

The problem is that I have been inundated with packages; and I'm having difficulty deciding which are necessary to install and distinguish the ones not to install. As mentioned above; I could Google each package.

For example I'm thinking about installing AIDE: Intrusion Detection
But than after the research I did on it AIDE tells you after the fact. (after the breach in security has taken place) And it would have to be ran manually along with having to add info to the config file; which I am not willing to do.
This AIDE application and everything associated with it I have decided to leave it alone-

Obviously; I don't need to install the packages that pertain to gaming for I don't have an interest in them-

What exactly would you do if you had this ridiculous amount of packages?

And why is it that I can not remove the packages that I don't want?

---

### Post by UltimateCat on 2012-08-28
> **critin said:**
> You're learning linux and it's not easy, but it's not boring either.  :P

Don't install anything from synaptic  if you haven't been instructed to somewhere.  When you choose a package in software center, synaptic, or on the web, it will either install everything you need or it will plainly tell you what else you need.   You may have to write the details or copy/paste them into synaptic or the terminal (however you prefer).  

You choose the main package and the dependencies usually take care of themselves.

I needed to hear that; 
```
You choose the main package and the dependencies usually take care of themselves

```

That helped me: Thank you; Critin

---

