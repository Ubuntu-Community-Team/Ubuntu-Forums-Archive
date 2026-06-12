---
title: "Trying to make network printer work"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by niknak on 2006-03-26
Hi, I'm a confused newbie, 
   I have 3 computers all running windows and recently have installed ubuntu 5.1 as a dual boot. It's great but confusing and it's early days. I'm sure I'd have no problem if i'd connected the printer directly to the computer but I haven't. My printer is a MFC5840cn made by brother. I have a all in one box which contains a adsl modem, router and wireless network. This machine which has unbuntu installed is connected directly via ethernet cable to the router. The printer is also connected like this. I have followed various threads and also posted but it was suggested I start a new thread instead of gate crashing another. I would like to be able to install the printer, I'm not fussed about the scanner or card reader yet, I'll worry about that later but to be able to print is kinda important in the learning curve I'm faced with in unbuntu. Can anyone help?:-k

---

### Post by jjf on 2006-03-26
I'm a noob, so I can't offer substantial help other than to say I'm also looking into installing drivers to print to a brother printer over the network.  In case you're not aware, brother has developed Linux drivers.  Go to this page:

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

And find the Debian drivers for your printer.  My advise (which is only a guess) would be to connect the printer directly to your Ubuntu machine, set up the drivers and test, then plug the printer back into your router and work on accessing it over the network.

---

### Post by marcw on 2006-03-26
If you use one of these guides, You should be able to piece things together:
[http://www.ubuntuforums.org/showthread.php?t=71104](http://www.ubuntuforums.org/showthread.php?t=71104)
[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

Obviously you'll have to change references from the example printers to your own model.  Also, based on what you said in an earlier post, you *must* get the c shell installed first or nothing else will work.  "apt-get install csh" at a command line should do it.

---

