---
title: "Alternatives to Ubuntu's Wireless Configurator?"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by Harimwakairi on 2006-01-19
Though as a new user I'm quite happy with most of Ubuntu experience thus far, I must say that the little network configuration utility is driving me crazy.  I have a notebook that I take to work and school and switching from network to network is neither simple nor predictable.

Often the utility shows me multiple networks with the same SSID (FSU's campus wireless umbrella often shows seven entries with the same ID, for example, sometimes with little key icons on a few of them while the rest are blank).  The list will also show networks I know are encrypted with no key icon, and those that I know are open with it.  I have no idea how the profiles work.  Often I will join a wireless network, surf a little, and then when I hit OK to leave the network configuration dialog which had been sitting open, the wireless connection will stop working, even though I hadn't altered anything in the dialog.

Is there an alternative to this utility?  What are the command line tools I could use?  Is there a command line tool that will show what ipconfig does on a Windows machine?  I've used iwconfig, but it doesn't show IP information or anything else DHCP hands out.

I have not installed ndiswrapper or the graphical tool for it that is available through synaptic.  I read that ndiswrapper was for using Windows-based wireless drivers, which is not my situation.  Is this incorrect?

When I set up my box initially, I told the installer to use my wireless network chip as the primary interface.  Was this a bad idea?  It certainly slows my bot down, as the notebook waits sixty seconds while starting the network interface.

I know this is a rambling post with a lot of questions, but I'd appreciate any advice.  I've looked through these forums and the help that came with Ubuntu but without much success.

---

### Post by davmac on 2006-01-20
As an alternative to Windows' ipconfig, try ifconfig.

It might also be worth trying KWifiManager. I only used it briefly but it struck me as ideal for the roaming wireless user.

Hope this helps,

Dave Mac

---

### Post by d1337 on 2006-01-20
There are several ongoing projects that are addressing the difficulties that folks are experiencing with wireless.  There are also several packages available that may or may not help (Wifi-radar and KWiFiManager as davmac mentioned).  I only connect at home and at work with my laptop so I am not well versed in how to.

Something else helpful, when you are booting your notebook and it hangs at network or syncing clock, hit ctrl-c to skip.  First few times you'll think it's a pain, but after that it'll become second nature.

d1337

---

### Post by obiyoda on 2006-01-23
Just like ctrl-alt del became second nature in windows ;) joking aside I plan on trying kwifimanager to see if it solves the same above issues I have

---

### Post by Harimwakairi on 2006-01-24
If I'm running regular Ubuntu, am I able to use apps that start with k?  I was under the impression that the k* nomenclature meant the app was built for KDE and therefore unusable for me with my Gnome system.

---

### Post by d1337 on 2006-01-25
I'm pretty certain that you can run at least most apps that begin with K (KDE apps).  However, when you apt-get install them or grab them with synaptic, you will likely bring down a bunch of libs and whatnot with them.  I think both of the apps from above are available through the Add Applications under the Applications menu.

d1337

---

