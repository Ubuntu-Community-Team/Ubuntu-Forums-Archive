---
title: "New User - One Major Question"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by JediLow on 2006-06-02
Well, I've spent most of the night so far working on getting Dapper running (that took a bit...) and I'm pretty happy with it (I'm new to Linux). I'm looking at using Dapper as my main OS to finally get away from Windows but I've run into one huge snag which everything is hinging on right now.

Currently I have a (USB) Asus WL-160g wireless adaptor, I'm not able to find any support on how to get it running or and documentation. Moving my computer to the ethernet line really isn't an option since I'm nursing a broken ankle at the moment. Is there a way that I can get my wireless adaptor to work? The Network option does not display the device, but I can find it under the hardware option. If it won't work with Linux, is there a wireless adaptor that someone can recommend that'll work flawlessly with Dapper (if I go out and buy a new one I really don't want to have to deal with a long install)?

---

### Post by SqRt7744 on 2006-06-02
look on the install CD that came with your wireless adapter for the .sys and .inf driver files, copy them to your desktop.  Now use the package manager (system->administration->synaptic package manger) to install "ndisgtk".  (you will need the network for this, so plug in your computer to the router, just swallow some painkillers first).  This will install the entry "Windows Wireless Drivers" under system->administration (at the bottom).  Use it to install a new driver, select the .inf file you copied to your desktop from the CD.  This will hopefully work.  If it doesn't, then you must grab driver files that are known to work with your device.  There is a list somewhere, but try my suggestion first.

---

