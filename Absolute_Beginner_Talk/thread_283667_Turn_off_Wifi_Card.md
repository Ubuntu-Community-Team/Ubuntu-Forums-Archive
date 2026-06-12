---
title: "Turn off Wifi Card"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-24
In Windows, when I disabled my wifi card, it would also turn it off. I was wondering how I can turn off my wifi card on Ubuntu. Even if I disable wireless internet, the card is still on. How can I turn it off to save battery? Thanks! This is an internal card.

---

### Post by SendDerek on 2006-10-24
Well, if you're in gnome, you can totally disable the wireless adapter by following these steps:

System -> Administration -> Network Settings -> Highlight the card and click "Deactivate"

Although, now that I think about it... I don't know if that actually turns off the card (it might, but I don't know).  Sorry I can't be much more help.

If you're using a laptop, is there a switch that can turn it off?  I know most laptops do have it.

Are you looking at turning it off to save on battery power?

---

### Post by amitroy5 on 2006-10-24
I take my computer to school, and my Dell Inspiron E1405 does not have a button to turn it off. Thus,  I need time for when it will not be on. However, using System -> Administration -> Network Settings -> Highlight the card and click "Deactivate" does not turn it off. It just disables access to it.

---

### Post by LinuxGuyInVA on 2008-06-25
What you need is to do this, assuming your wireless interface is eth1 (as mine is on a Dell Latitude D610):

> sudo iwconfig eth1 txpower off

Similarly, to re-enable it, type

> sudo iwconfig eth1 txpower on

You can check if it's enabled or not by just running iwconfig (with or without sudo); the third line should include "*Tx-Power=off*" if the power ("radio") is really off on the wifi card.

I know this is almost 2 years after you asked, but hey, this forum entry came up when I googled the question, so it makes sense to put the answer here :-)  

This is for Hardy Heron; however, I suspect iwconfig hasn't changed much over the last several versions of Ubuntu.

---

