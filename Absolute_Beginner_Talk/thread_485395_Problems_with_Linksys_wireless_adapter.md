---
title: "Problems with Linksys wireless adapter"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Devezu on 2007-06-26
Excuse me for being a noob, but for some strange reason in the latest ubuntu release (7.04), i cannot get it to reach the internet. It is recognised, picks up the wireless signals, but does not connect to them. My adapter is a linksys wireless adapter, with an id of WUSB54GC. Please let me know if i need to supply more information

---

### Post by paradoc on 2007-06-27
Welcome to Ubuntu!

I've got the same system as that.  If you mean Linksys connects in Windows, but not in Ubuntu,hover over
one of the icons top right, it needs your dot in the  the linksys circle (sorry I can't remember the techie terms
at the moment), then a wiggly sort of icon takes a few seconds, and hey presto! you are told you're connected wirelessly, at least, that's what happens in my system.

   If not, please post again,  one of the members is sure to know!

---

### Post by theotherjoey on 2007-08-01
Actually, I've had this a similar problem with this same card and setup. It does connect in Windows, but the probalem in that when I try to connect to my home network (which NetworkManager does in fact detect) it stalls when the progress bar reaches 28%.

I have WEP encryption with a 16-digit key.

---

### Post by hendricks on 2007-08-03
I had the same problem. No matter what I did, I could never get past 28% in the knetworkmanager.  I'm pretty sure that it was impossible to connect. It seems that the default drivers that ubuntu installs for our wireless adapters does not work. Please see this thread I started:

[http://ubuntuforums.org/showthread.php?p=3127959#post3127959]("http://ubuntuforums.org/showthread.php?p=3127959#post3127959")

  --Hendricks

---

### Post by Devezu on 2007-08-07
Hey! I have the solution i found a while back. Here's the Link > 

[http://jefim.wordpress.com/2007/07/24/how-to-linksys-wusb54gc-wireless-and-ubuntu-linux-704-feisty/](http://jefim.wordpress.com/2007/07/24/how-to-linksys-wusb54gc-wireless-and-ubuntu-linux-704-feisty/)

copy and paste! Enjoy. (FYE, i will rewrite these instructions to make them easier)

---

### Post by Jefim on 2007-09-13
> **Devezu said:**
> Hey! I have the solution i found a while back. Here's the Link > 

[http://jefim.wordpress.com/2007/07/24/how-to-linksys-wusb54gc-wireless-and-ubuntu-linux-704-feisty/](http://jefim.wordpress.com/2007/07/24/how-to-linksys-wusb54gc-wireless-and-ubuntu-linux-704-feisty/)

copy and paste! Enjoy. (FYE, i will rewrite these instructions to make them easier)

Hi, I am glad that you found my guide useful. If you have a proposal on how to make the guide cleaned and / or easier - please let me know (here or add a comment on my blog). I gladly accept constructive critics.

Devezu, yes, it is a known problem of this wifi dongle. As stated in my guide, it works without problems with ndiswrapper, so read it and if you have any questions or problems - feel free to ask.

---

