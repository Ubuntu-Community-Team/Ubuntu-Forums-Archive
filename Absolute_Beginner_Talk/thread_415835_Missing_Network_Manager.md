---
title: "Missing Network Manager"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2007-04-20
Just upgraded the laptop to version 7 and I'm looking for the new Network Manager. Add/Remove Programs says that I've got it, but I can't find it anywhere. I've got Network Selector and Wi Fi Radar, but no new Network Manager. Have I done something wrong?

---

### Post by tmasboa on 2007-04-20
Same here, I have no network manager, although my wi-fi does work.

---

### Post by Compyx on 2007-04-20
Go to System -> Preferences -> Session and see if "Network Manager" is checked.

---

### Post by Pobega on 2007-04-20
Try manually running it from a terminal, maybe that will give some better output. Open a new gnome-terminal window and run "nm-applet --sm-disable", and see if it runs. If it doesn't run, post the output of the command.

---

### Post by Charlie Chick on 2007-04-21
Thank you all for your suggestions. I opened System - Preferences - Session and Network Manager is there and ticked. I then tried running the suggested text in the terminal and nothing happened apart from another icon appearing next o the clock. The cursor just flashes at me. Is the new Network Manager supposed to replace Wi Fi Radar? The two appear to do the same thing.

---

### Post by medad on 2007-04-21
The icon that appeared next to the clock, does it have two flatscreens (on behind the other)?  That is your network manager.  Do a left click on it and see if has sensed any wireless routers.  There are a lot of threads on this that you can take a look at for more info on how to get it to work.  It had taken me a long time to get my netgear up and running on my older computer since I was tryng to get some kind of security on it.

---

### Post by Charlie Chick on 2007-04-21
> **medad said:**
> The icon that appeared next to the clock, does it have two flatscreens (on behind the other)?  That is your network manager.  Do a left click on it and see if has sensed any wireless routers.  There are a lot of threads on this that you can take a look at for more info on how to get it to work.  It had taken me a long time to get my netgear up and running on my older computer since I was tryng to get some kind of security on it.

Ah! In fact, I have 2 similar icons next to the clock. One has a white border around the edge of the 'screen' and the other doesn't. Putting my mouse over each, the one with the border says "Wired network connection" and the other, borderless icon says "Network connection: eth0" as I'm currently connected  to my wired router. If I waned to try and connect to one of the wireless networks around me, how would I go about it without using the old Wi Fi icon? What I don't get is the nice picture underneath the clock on the website as a new feature of 7.04.

Thanks for the help.

---

### Post by Charlie Chick on 2007-04-21
Since posting the above, the Network Manager has appeared, just as on the website! As it says, one click brings up everything in range, both wired and wireless.

Thank you to everybody for your help!

---

### Post by blunteyedfool on 2008-06-25
I got here looking for help on my missing network wireless icon. I've since found the issue and being a nice sort of chap, thought I'd let the next person know how I sorted it out. First off, there are two network-type icons, one is the Network Manager, which is a dialog box allowing you to configure your network connections. The other one (which went missing on me) is an icon showing your current actual connections, and those available around the place. This second one is the one you need if you're in a cafe in Brussels, Murdoc Sound or Ibiza. ... This was my missing icon. Trying to find it drove me ab.sol.ut.ely.nuts.I.swear.to.god. Yes, it is hidden in the System Preferences, but it's not Network Manager... it's one of the icons which appears in the Notification Panel. The Notification Panel I had decided I didn't need and removed while thrashing about with my themes. 

So make sure you've got your Network setup, internet working, etc... now, check out the descriptions above from Charlie. Your Network Manager (icon one) is probably there. What you might be missing if you're reading this is the second icon, very very similar (two monitors; colour may vary)

Right mouse click your panel.
Your Add to Panel dialog will/should appear
Scroll Down to 'Notification Area'
Close the Add to Panel dialog
Now, with that sucker added, you'll see - if you're currently connected to the web -- a new pair of monitors. 
Place the mouse over this icon. It will read 'Manual Network Configuration'. Click on it. Select Manual Configuration. Result? You'll get a list of available hotspots or neighbors wifi. 

hope this helps someone out there, saves them from going completely nuts, etc.

cheers

bef

---

### Post by tua03332 on 2008-07-05
Hey, Im running Ubuntu 8.04 and I have no problem connecting through Ethernet, but the wireless refuses to even show up.  I have searched the forums and tried many different things that I wouldn't even know where to begin describing what I've done.  Right now i have the double monitor saying i have a wired connection.  When I left click it simply says, 
Wired Network
Connect to 802.1x Protected Wired Network...
Manual Config.

however I have tried all three options to no avail.  I use verizon fios and have a wpa2 psk encryption.  I know the essid and passphase, however the network does not show up even though it broadcasts.  If i boot this same latop in Vista, I connect no problem.  Is there anyone out there willing to help me?

---

