---
title: "Firestarter causing problems"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by gofeddy on 2007-12-11
Hello,
         I have Ubuntu 7.10 installed. Recently I installed firewall FIRESTARTER. But, later I decided to uninstall it through Synaptic. After it got uninstalled, my Internet connection went down. I tried many solutions. But later, I had to reinstall FIRESTARTER again, and had to disable the firewall status to activate my network connection. But, now I have been having problems with it. The firewall behaves unexpectedly and even when I have disabled it, it automatically gets enabled causing the network connection to go down again and again. Now, I really want to just get rid of this application. :mad:
Is there any solution to keep my network connection intact and not be bothered at all by FIRESTARTER?

---

### Post by kpkeerthi on 2007-12-11
First thing. Firestarter is not a firewall by itself. Firewall is already built-in in ubuntu as iptables and is active all the time. So you already had firewall before you ever installed firestarter. Firestarter is just a GUI to IPTABLES. I doubt firestarter causing your network down. The problem could be something else. Are you on wireless? Did you try connecting to your network from other machine/OS when ubuntu is failing? Is your Live CD able to connect  when you think your network is down?

---

### Post by gofeddy on 2007-12-11
I am very confident of the fact that this problem occurred only after I uninstalled Firestarter. I am not connected to any wireless network. The problem is not that Ubuntu is completely failing. Its losing connectivity randomly. But, why is it that even after I have disabled the firewall through Firestarter, it is getting enabled. Isn't that a bug in that case? Firestarter is not behaving as it is told to. And when the firewall is getting enabled automatically, I lose network connectivity.
Is there a solution to completely remove IPTABLES if possible and then reinstall it again or........???
I am a newbie with firewall and stuff....especially with Linux.

---

