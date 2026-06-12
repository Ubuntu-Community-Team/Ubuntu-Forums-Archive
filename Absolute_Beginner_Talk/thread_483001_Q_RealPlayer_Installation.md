---
title: "Q: RealPlayer Installation"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by chudq on 2007-06-24
I have downloaded RealPlayer package (RealPlayer10GOLD.bin). I changed it to executable after that. Then I double click on it, a folder RealPlayer was created with all binary files and other related files. 

So far so good.  can launch realplayer.bin by double-click on it. However, I could not get it to work when I click on a realplayer link in my firefox, such as BBC radio ([http://www.bbc.co.uk/mediaselector/check/worldservice/meta/tx/summary5min?size=au&bgc=003399&lang=en-ws&nbram=1&nbwm=1](http://www.bbc.co.uk/mediaselector/check/worldservice/meta/tx/summary5min?size=au&bgc=003399&lang=en-ws&nbram=1&nbwm=1)). The following is a message I got:

```
The page at http:[www.bbc.co.uk](www.bbc.co.uk) says:
Could not find an appropriate hxplay or realplay in the system path to use as an embedded player.

```
I think I have to set my realplayer in a path. How can I do that to make it work?

By the way, my realplayer folder is at home/Downloaded/Firefox/RealPlayer

---

### Post by mali2297 on 2007-06-24
I suggest you install it via the terminal with root privileges. If you got RealPlayer10GOLD.bin in your home directory, type this in the terminal:
```

sudo ./RealPlayer10GOLD.bin

```
... and just answer the questions you get (choose the default if uncertain).

After this, you will find Realplayer in the Program menu. Hopefully, BBC will also find it.

---

### Post by chudq on 2007-06-24
Great, that works! Thank for your information!

---

### Post by ginestre on 2007-06-25
I have  a related problem- that I can't find a linux version of the real player on their site. I've just spent an hour following links on their site and so on but all I get back to is either the Helix player, which doesn't work with the BBC, or a commercial version of the Real player for windows. I'm feeling frustrated and very stupid.  If you could tell me where you got the file I would be very grateful!

---

### Post by mali2297 on 2007-06-25
Realplayer can be found here: [http://www.real.com/linux]("http://www.real.com/linux").

Also, check out [http://ubuntuguide.org]("http://ubuntuguide.org"). There you can find things like how to install Realplayer among many other things.

---

### Post by ginestre on 2007-06-25
> **mali2297 said:**
> Realplayer can be found here: [http://www.real.com/linux]("http://www.real.com/linux").

Thank you. I must have been going blind- like, when you're looking so much you just don't see.

---

