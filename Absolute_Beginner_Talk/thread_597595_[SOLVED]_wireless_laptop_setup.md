---
title: "[SOLVED] wireless laptop setup"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by jboy012000 on 2007-10-30
Hi All,

Ok so I have bought my-self a nice new laptop and it runs windows vista which I have to say is complete toss sorry for the language, the laptop has an internal wireless card, I would love to install ubuntu 7.10, now when I install it will it automaticlly find my wireless network or will I have to set it up, if so how, are there cammands I have to use or will it work through the administrator controls.

Cheers

---

### Post by New-b on 2007-10-30
what type of card is it?

---

### Post by jboy012000 on 2007-10-31
Good question I am not sure, I do know that it is active all the time my laptop is running i would have thaught ub untuntu would pick the connection up streight away, i wondered if anyone had set one up previosly.

---

### Post by charlatan1978 on 2007-10-31
Hi, I would check in device manager (in Vista) what your card is to see if anyone else has had problems.  My wireless card was a Broadcom BCM4318 which didn't work when I first installed Ubuntu 7.10.  You can also check your card model in the hardware compatability list on this forum which will tell you if it works straight away or if you need to install it using another method.

---

### Post by jingo811 on 2007-10-31
When you run the Gutsy or Feisty LiveCD before installing them to your hard drive does it detect any wireless for you automatically?  If it does then the distro version that can do that should be the distro version you install.

If it doesn't work automatically check in this database to see if your wireless specifications and brand is listed
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

If that database haven't listed your wireless device or have something bad to say about it then your last resort will be NDISwrapper.  See if you device is listed in their list.
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by jboy012000 on 2007-10-31
I have tracked down the type of wireless card my laptop has and its is a "Atheros AR5007EG" card.

Please help

---

### Post by jingo811 on 2007-10-31
Did you try with the Feisty and Gutsy LiveCD's?  Did your wireless work when doing that?

I couldn't find your model number from the Atheros chipset.
**AR5007EG**
[http://linux-wless.passys.nl/query_chipset.php?chipset=Atheros](http://linux-wless.passys.nl/query_chipset.php?chipset=Atheros)
That means you're the Neil Armstrong of your wireless brand :) time for you to go where no man has gone before...

I had better luck finding the model numbers at NDISwrapper though.  But you'll need to give us your Laptop brand and number in order to find a match on their list!
**AR5007EG**
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)

---

