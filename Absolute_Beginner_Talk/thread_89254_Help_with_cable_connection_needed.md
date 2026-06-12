---
title: "Help with cable connection needed"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by Aryxa on 2005-11-12
Hi There :)

I have installed Ubuntu and I am having problems getting my head around getting connected to the net. 

I know I am supposed to download BPAlogin from [unbuntu]("http://packages.ubuntu.com/breezy/net/bpalogin"). The only problem is, I do not know which one I need for Ubutu 5.10 or how to go about instaling it.
This program is for my cable log in to my ISP here in Australia. I see posts from others were not helpful.

I am fairly sure my network card/cable modem is working as if I do a "ifconfig" it picks up my IP address and mask etc for eth1.
and in the system monitor I appear to be recieving information and not sending any at all.

I am hoping there is other Bigpond users around who have gone through this too help me. I would be very greatful.

It's a bit of a blow considering all my hardware is working perfectly, my floppy disc drive even works!!! (doesn't on windows)

---

### Post by adwait on 2005-11-12
Well if the software you are talking about is the software of your ISP, then you will have to ask them for a linux version of it. Ask them if there is any way you can log on from linux with or without using that software.

---

### Post by stilus on 2005-11-12
To install bpalogin, just go to System > Administration > Synaptic package management and do a search for bpalogin. You should find it easy to install it through the interface. I can't help you with the exact configuration of the tool itself, as I am almost literally on the other side of the world. From what I found through google (search for bpalogin ubuntu) things seem fairly straight forward [http://forums.whirlpool.net.au/forum-replies-archive.cfm/412903.html]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/412903.html"): 
"[...] you need to put your username and password into /etc/bpalogin.conf by running **sudo gedit /etc/bpalogin.conf**. Then start it [**/etc/init.d/bpalogin start** (or **restart**) ] and it should connect up fine, provided that your ethernet card is working and that your modem is plugged in ready-to-go."

Anyway, good luck and Have Fun!

---

### Post by Aryxa on 2005-11-12
Thank you Stilus, I already found the forums not long after I posted this. 
I did a search and I found it, and I had installed it following prompts from those forums and I seemed to be logged in, yet I was not connected. I then found a command to type in to login and I am typing from Unbuntu now :)

Thanks for being a help :KS

When I have time, I will post a thread for bigpond users and my finds today, maybe it will help them ;) (Or if anyone reads this, pm me or reply as I have subscribed to it)

---

