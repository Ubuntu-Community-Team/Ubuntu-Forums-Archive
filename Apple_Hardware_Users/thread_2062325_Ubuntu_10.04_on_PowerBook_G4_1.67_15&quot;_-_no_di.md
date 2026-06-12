---
title: "Ubuntu 10.04 on PowerBook G4 1.67 15&quot; - no display after install"
date: 2012-09-24
forum: Apple Hardware Users
---

### Post by theDole on 2012-09-24
Dear forum
I am trying to bring my girlfriends old G4 over to the bright side, it is however resisting somewhat.
I have done a live cd install (with GNOME and everything working fine in the "live cd mode") but after reboot and cd-extraction the display just shows black.
I tried following some other threads and fixes but it seems to be small differences on everything that makes it not work for me.
The computer model is:
[http://everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_1.67_15_hr.html](http://everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_1.67_15_hr.html)
I am trying to install Ubuntu 10.04 and to be precise I get to see some splash screen distorted flickering before the great darkness.
Any ideas?

---

### Post by theDole on 2012-09-25
Right, I sorted it! :D
Re-installed from the live cd using yaboot command "live-nosplash-powerpc" (I think, one of the options that appear if you TAB at the second boot prompt).
After that completely hassle free install, boots like normal. 
Yay!

---

### Post by 2blue on 2012-09-26
I`m glad to see things are working out. I am afraid you are probably making a mistake installing 10.04 in stead of 12.04, which is the long term supported and still kept up for several years (Used to be three years, but I think 12.04 is five !!). There have been tons of updates on 12.04 and it is running happily now.

---

### Post by theDole on 2012-09-26
Well, this one is not going to do that much actually and as much as I would like to use the latest shizniz I really don't like unity, sorry :S
I have read that old computers supposedly should be able to run newer versions of Ubuntu but in my own experience that should be taken with a pinch of salt. And we are talking about a fairly old and slow machine here (everything is relative).
Also I learned on 10.04 not so long ago and I am comfortable with it.
Thanks for caring!

---

### Post by 2blue on 2012-09-26
You are correct in assume Unity can be slow on older hardware. Some of later G4s and G5s with higher specs should be able to handle it. However, there is an option to go for the newer release with a different desktop environment, like Lubuntu or Xubuntu. I have Lubuntu running fine on a 1.42GHz popwerpc cpu. 10.04 is still supported so no big worries really ;-) 

12.10 is Beta 2 now, maybe mere mortals can test it out by now.

---

### Post by theDole on 2012-09-28
Damn you 2blue, now you got me to go over the whole installation trouble shooting routine all over again :D installing Lubuntu 12.04 as we speak, seems to run much smoother than even old Gnome on my machine.
So far one problem down, probably several to go.
Any tips on installing vpn-plugins for the network manager? In ubuntu the PPTP is installed by default but not in Lubuntu it seems..

---

