---
title: "Wireless problem"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by OneEyedMan on 2007-04-09
Hello all!

I recently inherited a Dell Inspiron 8500 laptop from work. I figured it might be a nice place to throuw Ubuntu on, since I'm not using it for gaming, just general surfing and documents. I got the partitions set up and dual-booted it with the current XP installation without a hitch. My problem came in setting up the wireless.

The laptop has a Dell Truemobile 1300 wireless card inside, and while the onboard netowkr card works fine, the wireless does not. I'm enough of a newbie at this that I'm confused as to how to troubleshoot it. I've checked the various documentation, but I've gotten myself good and lost with all of the instructions.

Could some kind soul please tell me where to start? The laptop does detect that there is a wireless card there, but does nothing, even when I disable the ethernet card and activate the wireless. My router broadcasts the SSID, but it simply can't find it. As for further information, I'm afraid I don't know where to start to find it. This is the first time I've run into a hardware/network issue on ubuntu, and I've never needed to dig into this area before.

Thanks!

Jeff

---

### Post by siciliancasanova on 2007-04-09
Which version of Ubuntu are you using?

---

### Post by richardward101 on 2007-04-09
[THIS]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") should help you out, its from the official ubuntu wiki; post back here if you run into trouble, and good luk!

---

### Post by danbh on 2007-04-09
Hey mate, I'm a bit of a newbie with ubuntu too.  But, i do know a few things that may help a little.  

Here are some commands:
ifconfig (general networking command, like ipconfig on windows)
iwconfig (wireless networking command)
ifup
ifdown

ubuntuguide.org is a good website to checkout.  Look for ndiswrapper.  It may help.

I would also suggest trying out ubuntu feisty.  There is a new integrated wireless gui.
For that, run this command (i believe):
update-manager -d

In fact, I highly recommend feisty.  I think making wireless easier was one of the goals of the project.

Hope you found something useful.

---

### Post by OneEyedMan on 2007-04-09
> **siciliancasanova said:**
> Which version of Ubuntu are you using?
Sorry, I'm using 6.10.

jeff

---

### Post by OneEyedMan on 2007-04-09
Thanks to everyone who replied. I'm aware from the laptop for now (at work), but I'll try some of these ideas when I get home.

Jeff

---

### Post by siciliancasanova on 2007-04-09
What you need to do is follow the above posted Wireless Guide to find out what wireless card you have and the chipset.  Then search that chipset on the forums or in google and you should find someone else with the same wireless card and the procedure they went through to get it installed.

---

### Post by punzak on 2007-04-09
Or you could just try installing the beta of fiesty fox which is what I did.  After weeks of unsuccessful tweaking and frustration, everything worked perfectly on startup without having to do anything.

---

### Post by siciliancasanova on 2007-04-09
I searched "Truemobile 1300 Feisty" on google and no problems were listed.  So if you choose to follow the above suggestion, either everyone with that card had a perfect installation, or you are going to be the first with a very long thread in the forums to get your card working.

Even if you decide to upgrade.  I would recommend figuring out how to install it on 6.10.  When it comes to hardware, especially wireless devices and drivers, this is one area where you don't want to be 100% reliant upon a GUI.

---

