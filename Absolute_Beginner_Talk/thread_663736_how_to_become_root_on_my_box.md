---
title: "how to become root on my box?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by wagner108 on 2008-01-10
how to become root on my box? and install flash.

When I did the install it never gave me the oportunity to set the root
account, but I did not think you had to.

I have 7.04 feisty fawn and I can't install it.
Looks like I need to become root since it can't find the path and everytime
I go to cd it says my username@myname_desktop.
I have flash 9 downloaded from Adobe and when I try to execute it says that it does not support ppc which is my architecture.
Please help?

---

### Post by taurus on 2008-01-10
You would use sudo/gksudo if you need root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by LinuxIsInnovation on 2008-01-10
> **wagner108 said:**
> how to become root on my box? and install flash.

When I did the install it never gave me the oportunity to set the root
account, but I did not think you had to.

I have 7.04 feisty fawn and I can't install it.
Looks like I need to become root since it can't find the path and everytime
I go to cd it says my username@myname_desktop.
I have flash 9 downloaded from Adobe and when I try to execute it says that it does not support ppc which is my architecture.
Please help?

 Simply type "sudo bash" at the terminal to become root..

---

### Post by philinux on 2008-01-10
> **wagner108 said:**
> how to become root on my box? and install flash.

When I did the install it never gave me the oportunity to set the root
account, but I did not think you had to.

I have 7.04 feisty fawn and I can't install it.
Looks like I need to become root since it can't find the path and everytime
I go to cd it says my username@myname_desktop.
I have flash 9 downloaded from Adobe and when I try to execute it says that it does not support ppc which is my architecture.
Please help?

Are you running 64 or 32 bit

---

### Post by PeterJS on 2008-01-10
> **philinux said:**
> Are you running 64 or 32 bit

I'm pretty sure that all PPC is 32bit.

> **wagner108 said:**
> how to become root on my box? and install flash.

When I did the install it never gave me the oportunity to set the root
account, but I did not think you had to.

I have 7.04 feisty fawn and I can't install it.
Looks like I need to become root since it can't find the path and everytime
I go to cd it says my username@myname_desktop.
I have flash 9 downloaded from Adobe and when I try to execute **it says that it does not support ppc which is my architecture.**
Please help?

Back to the matter at hand, It looks like no amount of privilege escalation is going to let you install something that doesn't exist. I don't think there are linux flash binaries for PPC. You might try googling around for hacks to get the Mac plugins to work under linux. Or try installing gnash, it doesn't work well, but it works better than nothing.

---

### Post by bodhi.zazen on 2008-01-10
The preferred methods of becoming root are :

Terminal : ```
sudo -i
```

Grpahical apps : ```
gksu nautilus
gksu synaptic
gksu gedit
gksu firestarter
```and on ...

---

