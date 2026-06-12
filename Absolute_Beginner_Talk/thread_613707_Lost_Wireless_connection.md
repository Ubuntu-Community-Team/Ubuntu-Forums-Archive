---
title: "Lost Wireless connection"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by LisaM on 2007-11-15
I have a Dell 1420N laptop that came preinstalled with Ubuntu 7.04.  After upgrading to 7.1, I discovered that I had lost sound, SD card access, DVD drivers, etc.  I followed some advice to re-install linux-backports-modules and things went from bad to worse!

Now I have no wireless connection.  I cannot access the internet from the laptop, and am writing this from my old Windows box.  When I go into System > Administration > Network   there is no listing choice now for Wireless Connection. 

How can I add it back?  I can live without sound, SD cards, and the DVD.  I CANNOT live without a connection to the Internet!

Thanks!

---

### Post by surian on 2007-11-15
I guess the first thing to do would be to see if Ubuntu actually still sees the card.  Depending on what kind of card this is, you can find out by opening up a terminal and running "lspci" or "lsusb".   Then look through the output and see if you find your card listed there.  I did a little research and your network card is an Intel 3945 802.11a/g card.  So, run those commands and see if you find a listing that looks like that.

If you do, then Ubuntu can see the card but doesn't know what to do with it.  If that's the case, you could try to get it working again with "ndiswrapper".  I'm not sure if you're familiar with ndiswrapper but if you aren't you can look up the details about it at their homepage: [http://ndiswrapper.sourceforge.net]("http://ndiswrapper.sourceforge.net").  I've also looked up your particular card on their wiki page and it seems like people were able to get the card to work with a little tinkering.  You can look up your card on their wiki: [Here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")

As for the SD and DVD drives, you may want to look through your lspci output to see if they are still being recognized by Ubuntu.  I'm not exactly sure how you could get them back.

Hope this helps a little.

---

### Post by Inxsible on 2007-11-15
since you bought the laptop with pre-installed Ubuntu 7.04, you may want to contact the Dell Support and ask them why an upgrade screwed up your system.

Also you can perform a clean install of Gutsy(7.10) and see how it goes.

---

### Post by LisaM on 2007-11-16
Thanks for your help.   I ran lspci and found the entry for an Intel PRO/Wireless 2945ABG network connection (rev 02) and I think this is probably for my card.

When I tried to run ndiswrapper, the message says that this program is not installed.  How can I install it on the laptop without a connection to the Internet?

Thanks!

---

