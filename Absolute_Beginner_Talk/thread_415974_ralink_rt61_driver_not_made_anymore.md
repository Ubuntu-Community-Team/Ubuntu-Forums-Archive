---
title: "ralink rt61 driver not made anymore?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by mills on 2007-04-20
the links from [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo") and [this guide]("http://ubuntuforums.org/showthread.php?t=132980&highlight=ralink+d-link") are supposed to give me the rt61 drivers i need for my D-Link DWL-G510 wireless card but there are no rt61 drivers for linux.
at the [ralink website]("http://web.ralinktech.com/ralink/Home/Support/Linux.html") 

have they been moved?
if they have stopped support for this driver, am i stuffed?
is there an alternative way of setting up wireless?
or do i need a new card?

---

### Post by louieb on 2007-04-20
Feisty comes with the rt61 driver I had to do a little fiddling on my laptop . I'm on my Dapper destop now and don't remember just what I did. Just do a forum search on **rt61**.

---

### Post by mills on 2007-04-20
i've found a few tuts and pages with links to the drivers but they're all dead,

but glad to hear feisty has them, guess i'll be upgrading now then

thanks louieb

---

### Post by col.panic on 2007-04-21
if you go to the [ralink web]("http://ralinktech.com") site you will find a link to linux

It should lead you [here]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

Where you can download  [this]("http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz")


sorry dude just realized when i tried to dl it myself.....  I'm special sometimes

---

### Post by ffxr on 2007-04-21
that link is for the firmware.. col.panic

use the first guide : [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo)

and theres your linux rt61 drivers: [http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz](http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz)


so ```
 wget http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz 
```

instead for the one in the howto (ralink seem to have rearranged their site a little)

---

### Post by ffxr on 2007-04-21
*note

I have updated the community documentation 'how to'  to reflect the change of location of the rt61driver on the ralink website. you should be able to just follow the howto through as normal now..

---

### Post by louieb on 2007-04-21
ffxf, thanks for the link and updating the community doc.
For feisty found a solutition here   [http://ubuntuforums.org/showthread.php?t=392415](http://ubuntuforums.org/showthread.php?t=392415)
the short of it to get the rt61 working in feisty went to System>Administration > Network >Wireless>properties and set my essid

to get it to connect to the router went to the terminal and
```

sudo ifconfig eth0 down
sudo ifdown ra0
sudo ifup ra0

```now when I boot the wireless connects automatically.

---

