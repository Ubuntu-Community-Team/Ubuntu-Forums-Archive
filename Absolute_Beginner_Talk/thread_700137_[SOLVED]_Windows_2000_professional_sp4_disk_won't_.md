---
title: "[SOLVED] Windows 2000 professional sp4 disk won't install in virtualbox"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2008-02-18
it gets to the part where it installs the network and the virtual machine randomly reboots. I am able to get XP and Vista to install, but I've had very little luck with any Windows OS older than that. 

oh and I'm not using the open source edition

---

### Post by Arthur Archnix on 2008-02-18
I can install Windows 200 Professional SP1 without trouble, I'm not sure why you're encountering errors. I would try two things: First, I would try to disable networking on the virtual machine through the virtual box interface. Do this before trying to install. Then, when it comes to the part of the installation where you are prompted to install the network, choose to customize the install (don't go with defaults) and uninstall all the networking components. You can always install these later if you manage to successfully install 2KSp4.

---

### Post by piratesmack on 2008-02-18
hm I disabled the network adapter and it worked great. My guess is that the driver Windows 2000 was using for my network adapter was causing instability. Thanks

---

### Post by Arthur Archnix on 2008-02-18
No problem. Glad you found an easy workaround.

---

### Post by piratesmack on 2008-02-18
There is only a small problem. After it installed, I reenabled the network adapter and installed guest additions, but I can't connect to the internet. Any advice?

---

### Post by Arthur Archnix on 2008-02-18
Guest additions doesn't have anything to do with networking (from memory). Make sure you've set VB to use your current computer's connection (thus taking advantage of Ubuntu's built in firewall IPtables). I've never tried to setup Windows so that it connects to the internet directly, I always tell it to use the 'host' connection.

Other than that, I've found that when I run into problems with VB a good place to look is the [VB forums]("http://forums.virtualbox.org/viewforum.php?f=7&sid=da80ae5ba14c6cc460552319a5d8addd"). 

Since you've marked this thread as solved I don't think you'll be attracting much attention to it. :) If the problem persists you should open a new thread.

---

