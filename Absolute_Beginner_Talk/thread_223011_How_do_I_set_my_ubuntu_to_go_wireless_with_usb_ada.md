---
title: "How do I set my ubuntu to go wireless with usb adapter??"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Arijua on 2006-07-25
I have a Belkin router and a usb adapter netgear, what do I need to do to connect on my net and go internet?

---

### Post by Washington Irving on 2006-07-25
What is the model of your USB adaptor? Check it's level of support [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

It seems to me that (if it is supported) then it is either a  MA111v1 or a  WG111v1 in which case each has a nice setup guide of which the links are on that page.

Hope you get it up and running painlessly (I had a bit of trouble with a Belkin USB which still isn't working 100%).

---

### Post by Arijua on 2006-07-25
Well it is a NETGEAR WG111T

---

### Post by ORF1000 on 2006-07-27
I got mine to work, but it wasn't that easy. Needed to download and compile the latest version of ndiswrapper (the 1.8 in the Ubuntu repositiories isn't good enough). [URL="https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"]Go here for instructions to download and install the latest ndiswrapper.
[/URL]
Dave

---

### Post by ORF1000 on 2006-07-29
One more thing about the WG111T -- you need to install both Windows drivers -- athfmwdl.inf and netwg11t.inf.

---

