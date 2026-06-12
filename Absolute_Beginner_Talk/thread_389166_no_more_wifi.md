---
title: "no more wifi"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by chefjames on 2007-03-20
I recently upgraded to Edgy from Dapper.  Upon doing so my wireless card was no longer detected.  I could just go back to Dapper, but where is the fun in that?  In Dapper my card just worked.  I did nothing to make it work.  I went to the local coffee shop and the "Network Manager" utility scanned and found the wi-fi hotspot and I connected just fine.  Now I get nothing.  No card detected, no network detected, no connection to the internet.  If I look in the device manager the card seems to be there, but I can do nothing with it.  It is a TP-Link TL-WN510G pcmcia card.  My Linksys USB wireless adapter doesn't work either.  Oddly it shows up as two separate devices in the "Network Manager".  Any help and guidance would be appreciated.  Many thanks in advance.

---

### Post by KenSentMe on 2007-03-20
As i can tell from your story, the wireless network connection is listed in your network manager, right? Maybe you could install this package: networkmanager-gnome. It's an easy to use tool, especially if you want to connect to different wireless networks.

---

### Post by chefjames on 2007-03-21
Thanks KenSentMe.  I tried the networkmanager-gnome thing.  It did not help.  I got a nifty little icon at the top of the screen that says no network connection when the cursor is on it, but that is all.  I am most interested in getting the pcmcia card to work.  There is a "howto" for the USB device that I could follow, but I really want to use the card.  I will post my question in the networking forum.  I think I need to give a lot of technical info that they can tell me how to get.

---

### Post by sunexplodes on 2007-03-21
sorry, posted in the wrong thread.

---

### Post by KenSentMe on 2007-03-21
Can you post the contents of the file /etc/network/interfaces ?

---

### Post by thefoolisme on 2007-03-21
I was having wifi problems, and someone suggested to me to install WiCD.  So I uninstalled Network Manager and installed WiCD.  I didn't even have to tinker with it.  It just works.  I don't know if it's better or worse than Network Manager, I just know it worked for me.  :-)

---

