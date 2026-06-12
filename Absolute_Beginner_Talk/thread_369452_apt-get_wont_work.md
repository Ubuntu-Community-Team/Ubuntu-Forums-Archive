---
title: "apt-get wont work"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by birddseedd on 2007-02-24
mike@toshiba:~$ sudo apt-get install gaim
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gaim
mike@toshiba:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
mike@toshiba:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package alien

can it be because of my repositories? im not sure where to go to add them, nor what ones i need to add?

---

### Post by chggr on 2007-02-24
To change your repositories:

System -> Administration -> Software Resources.
Under the Internet Tab, check everything
Under the Internet Updates, check Important Security Updates, Recommended Updates, Proposed Updates.

You can customize these settings according to your needs.

---

### Post by robophred on 2007-02-24
System->administration->software resources
doesnt appear in my Feisty Hurd 4 install (I don't have the administration menu).  I found it in System->Control Center, then selecting "Software sources"

---

### Post by Perfect Storm on 2007-02-24
Feisty is in development and it's advisable if you are new to Linux _not_ to use Feisty.

---

### Post by birddseedd on 2007-02-24
i installed both alien and synaptic using the adept package manager that comes with kubuntu.
problem is. i still cannot find and install somethign called madwifi

i have a madwifi.rpm. but cannot get it ton install.

without it i cannot connect to wifi

---

### Post by robophred on 2007-02-24
> **Artificial Intelligence said:**
> Feisty is in development and it's advisable if you are new to Linux _not_ to use Feisty.
Only problem with that is that the older versions wouldn't recognise my keyboard.  I prefer the bleeding edge software anyway, and I don't mind if it randomly decides to fail horribly.

---

### Post by Perfect Storm on 2007-02-24
Okay, it was just a friendly warning ;)

---

