---
title: "linksys drivers for wireless card"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by onelove25 on 2005-09-13
hello, i just recently installed ubuntu (gnome) onto my sony vaio notebook. i have purchased a new wireless internet card linksys wireless-G notebook adapter model # WPC54G ver. 3

 ineed some guidance on installing this device. do i need to get the drivers for it?? o r what is the best method of installation. thanks much

matthew

oh on another note, how can i connect my ipod to my curren version of ubuntu. i notice the music program has a ipod link but again do ineed drivers?? :)  :)  \\:D/

---

### Post by atrus325 on 2005-09-14
Ahoy there,

This post looks like it might be of some help:

[http://ubuntuforums.org/showthread.php?t=5645&highlight=WPC54G](http://ubuntuforums.org/showthread.php?t=5645&highlight=WPC54G)

I don't think you'll have too much trouble with this card.  Linksys stuff is usually pretty easy to install.  Have you checked the Linksys website to see if they have built any Linux drivers for the card?  If memory serves, there should be something out there.

J.

---

### Post by poofyhairguy on 2005-09-14
[QUOTE=onelove25]
oh on another note, how can i connect my ipod to my curren version of ubuntu. i notice the music program has a ipod link but again do ineed drivers?? :)  :)  \\:D/[/QUOTE]

> sudo apt-get install gtkpod


put that in terminal

---

### Post by HJB on 2005-09-15
Hi. I just got mine working with WPA and all. Was a bit hectic (also a n00b) but everything runs fine. \\:D/ 

Have a look here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

What worked for me was to install ndiswrapper via synaptic and start the guide at  Install Windows driver.
Get the latest driver for your card:
DriverVer=02/18/2005, 3.100.64.0 (what I used) and it is under the NT folder in the file you need to [download](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Download_C2%26cid%3D1115417109934%26sku%3D1121874577737&pagename=Linksys%2FCommon%2FVisitorWrapper)

Good luck

---

