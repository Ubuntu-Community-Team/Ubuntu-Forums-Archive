---
title: "Netgear WG111v2 Wireless Adapter"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by AshdownMenace on 2008-02-12
Hey,
   Hey guys (and gals) I'm new to the forum and to Ubuntu. I just installed it about 15 minutes ago and I love it so far. My only problem is my wireless adapter. I have read around the forum to see if there are any answers to my question, and there is (well at least I think so). The only problem is that I don't understand how to fix it. Here is my situation.

I have the Netgear WG111v2 Wireless Adapter. When I plug it in, it reads the network that I try to connect to. It tells me to put in the WEP key. After I put the key in, it attempts to connect to my network. It then fails, and asks for the WEP key again. I don't really know how to explain it much more. Thanks in advance.

---

### Post by sennep on 2008-02-12
the WG111v2 sometimes works out-of-box if you set your router to WEP 128bit. If you can't get it working, you probably need to use ndiswrapper (a small program that let's you use the wireless drivers for windows in Ubuntu). See the link in my signature for a guide on how to do it the ndiswrapper way.

---

### Post by jan quark on 2008-02-12
first I would check if the restricted drivers are enabled, if they exist for this card type

go to system> administration > restricted drivers manager
are there any inactive or active drivers for your netgear?

if not try the method explained by sennep

it would be also good if you post the output of these terminal commands
to get some info about your network status

```
iwconfig
```
```

ifconfig
```

```
sudo iwlist scan
```

---

### Post by Berean on 2008-02-14
I too have been having problems, but after installing a variety of wireless apps (system>adminstration>synaptic package manager>search>wireless) I was more confident.  However, it wasn't until I inputted (in Terminal) sudo /etc/init.d/hal restart and pressed enter (you'll have to input your password) that my Netgear WG111v2 gave me a wireless network.  I did have to go to the wireless connection (top right of screen next to the volume icon) and change from "wired network" to "wireless" that I got it to work.  I've also just started using Ubuntu, so if any of this sounds wrong to anyone please let me know.  Otherwise, best of luck to you!

---

