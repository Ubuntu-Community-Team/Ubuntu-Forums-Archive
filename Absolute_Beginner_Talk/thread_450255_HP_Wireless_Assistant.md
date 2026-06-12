---
title: "HP Wireless Assistant"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Eganrak on 2007-05-21
I just recently installed Ubuntu 7.04 on my HP Compaq nx7400. The notebook has an inbuilt wireless receiver which on my Windows XP partition uses the program HP Wireless Assistant software to run.

A friend of mine has given me software to install so I can use it, however it asks me to run commands. Since I am new to the Linux interface, I do not know how to do this.

Could someone please explain how this is possible?

---

### Post by overdrank on 2007-05-21
> **Eganrak said:**
> I just recently installed Ubuntu 7.04 on my HP Compaq nx7400. The notebook has an inbuilt wireless receiver which on my Windows XP partition uses the program HP Wireless Assistant software to run.

A friend of mine has given me software to install so I can use it, however it asks me to run commands. Since I am new to the Linux interface, I do not know how to do this.

Could someone please explain how this is possible?

Hi this may helps some
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Good luck!:popcorn:

---

### Post by Eganrak on 2007-05-21
The first part of the installation contains this in the INSTALL file.

```
Lines beginning with % can be run as any user.  Lines beginning with # 
must be run as root.

First, we build and install the ieee80211 subsystem.  You can obtain 
the latest ieee80211 subsystem from http://ieee80211.sf.net.  We 
recommend version 1.1.12 or newer:

	% tar xzvf ieee80211-1.2.16.tgz
	% cd ieee80211-1.2.16
	% make 
	# make install   <--- You may need to be root
	% cd ..
```

I tryed to enter the first command, however it errored.

---

