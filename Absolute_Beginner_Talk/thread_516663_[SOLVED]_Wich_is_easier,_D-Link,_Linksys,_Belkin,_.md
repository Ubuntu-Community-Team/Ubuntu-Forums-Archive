---
title: "[SOLVED] Wich is easier, D-Link, Linksys, Belkin, or Netgear"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-08-03
So im bout to purchase a new wireless card for my desktop.
Our home network is set up with WPA security, wich from reading all the different brands appears to be common enough.

But i've heard of numerous wireless problems like
Chipsets - i know broadcom is out, and i keep reading RT is a bit tricky... wich cards use wich chipsets
WPA - any clue with cards are easiest to set this up with... i would prefer to not have to deal with ndiswrapper
Driver Support - Any of those work out of the box?

So ultimately, i want recommendations, possibly a list of what brands use what chipsets, experiences, everything to help me determine wich card to buy... they are all similarly priced, and if this was an xp machine i would just buy the linksys, but really want to avoid wasting 50.00 on a card thats gonna go straight to my junk pile of parts

---

### Post by rbprogrammer on 2007-08-03
not sure if i can help, but i have a:
[LIST]
[*]d-link air plus g54 (dwl-g510)
[*]and a
[*]link sys wireless g (wmp54g)
[/LIST]
and they both work on my feisty install on my desktops right out of the box

---

### Post by p_quarles on 2007-08-03
My Intel Pro/Wireless 3945 ABG worked with one of the restricted drivers included in the default installation. It supports WPA, too. 

Couldn't say much about cards I haven't tried, but here's a link that may be helpful:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Hospadar on 2007-08-03
well you should look[ here]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") for a nice howto, and that page also links to a nice big list of cards with some useful info.  If you can find a card that's on the list and works very well right off the bat.  I was able to get the rt73 driver for my linksys wusb54gc working pretty easily as soon as I built it myself.  I had to do a little blacklisting and hunting around on forums but in the end once i figured out what I needed to be doing it wasn't bad.

I hear though that WPA is particularly nasty, so I would try and find a card that has been reported to work well ahead of time.  If you have the option to change your home network to WEP, I would strongly suggest it.

As for figuring out which chipset a card might have, you can often find it on the manufacturers website, or by poking through the driver files, generally the driver files will be named after the chipset.  Also I'm sure there are probably some good sites out there that list wifi cards and their chipsets/linux drivers.  Furthermore a website like newegg might list the chipset on the specsheet for a card.

---

### Post by ugm6hr on 2007-08-03
Given manufacturers change their range frequently, and then change the chipset within a specific range at random intervals, it is pretty difficult to know what to recommend.

Find a card you like the features on, and then google it to find the chipset, then come back here with details (or search some more) to see whether it will work out-of-the-box.

I've found that the most comprehensive list of wifi card chipsets is actually here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)
I find it amusing that I use the ndiswrapper documentation to see if it will work with linux drivers :popcorn:

---

