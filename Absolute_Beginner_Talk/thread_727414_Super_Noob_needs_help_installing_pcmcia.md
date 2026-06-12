---
title: "Super Noob needs help installing pcmcia"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by phelix17 on 2008-03-17
Hi all,

I've just recently installed Ubuntu 6.10 for PC and it's running very good on my older sony vaio laptop. I want to use my netgear fa411 mobile adapter. I found the drivers from netgear, and they include a  linux 6.1 folder, as well as a 6.2 and a 7.0.

In the 6.1 folder there are the following files:

88790.c
88790.h
88790_cs.c
config
config.mk
copycfg
makefile

I'm clueless as to what info I need to get to where. I'm a former windows user with no programming skills. Is there a way to get this installed simply? Here is a link to the driver: [http://kbserver.netgear.com/products/FA411.asp](http://kbserver.netgear.com/products/FA411.asp)

any help would be appreciated.

thanks

---

### Post by phelix17 on 2008-03-17
one time bump. Help!

---

### Post by theRightNee on 2008-03-17
have you tried installing with ndiswrapper?

---

### Post by phelix17 on 2008-03-17
> **theRightNee said:**
> have you tried installing with ndiswrapper?

I have no idea whatsoever what that means. Is there a step by step faq anywhere that would tell me what that is? I've looked at the terminal one time, but I have yet to attempt anything on it.

---

### Post by bwang on 2008-03-17
Look at this page: 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) 
for ndiswrapper instructions.

---

### Post by ugm6hr on 2008-03-29
It is likely you don't need to install the driver at all.

What is the output from the following commands:
```
lspci
lshw -C network
ifconfig
```

Is there a readme on the linux driver disc?

---

