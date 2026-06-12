---
title: "Crashes with torrents"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Sunships on 2007-05-04
Hi, I am running Edgy Eft 6.10 Xubuntu, and whenever I try and download using torrents my computer inevitably locks up. The mouse doesn't move, and keystrokes don't work, and the only option is to turn the computer off from the power switch. This effect is not client-specific; I have tried Bittorrent, BitTornado, and ktorrent, all with the same result.

Does anyone have any advice or experience with such a problem?

Thank you.

---

### Post by Pobega on 2007-05-04
What program are you using to handle torrents?

Try using the cli program "rtorrent". Install it by running **sudo apt-get install rtorrent** from the terminal, and then run it using **rtorrent /path/to/torrent**

---

### Post by starcraft.man on 2007-05-04
Ummmmmm..... that sounds very weird. My main source of downloading is torrents, I don't think its anything directly related to Ubuntu. Must have to do with your network set up. Whats your ISP modem and router? How is it set up (connected)? and do you have firestarter installed to configure your firewall?

---

### Post by Sunships on 2007-05-04
I have tried Bittorrent, BitTornado, and ktorrent. I will try your suggestion, thanks!

---

### Post by Sunships on 2007-05-04
Hi  starcraft.man, I am using a Linksys wireless router, connected to a Motorola cable modem. My wireless card is a Belkin FSD6020, which I have had problems with before, but recently decided to work for no apparent reason after I tried Feisty and then re-installed Edgy. I am not using firestarter.

---

### Post by starcraft.man on 2007-05-04
> **Sunships said:**
> Hi  starcraft.man, I am using a Linksys wireless router, connected to a Motorola cable modem. My wireless card is a Belkin FSD6020, which I have had problems with before, but recently decided to work for no apparent reason after I tried Feisty and then re-installed Edgy. I am not using firestarter.

Hmmmm, so when your torrenting your on the wireless connection? Does the same crash happen if you plug an ethernet line in and connect via that? If it doesn't crash then maybe its a wireless issue, if it does, ummm, well we shall have to think abit harder why it crashes... there wouldn't happen to be an error message when the client crashes, ktorrent for instance usually has the crash assitant...

---

### Post by Sunships on 2007-05-04
I just tried ktorrent - the only apparent difference is that it crashed *instantly* - with the other clients there was a variable length of time before it locked up. I will attempt to download using a wired connection now.

---

### Post by Sunships on 2007-05-04
OK, I have disabled my wireless connection, enabled the wired connection, and so far downloading is proceeding as it should, though BitTornado. I suspect it is probably a wireless issue, and will wait and see how it goes. I forgot to mention before as well - no error messages show up when I reboot, although they're probably there to find for someone who knows how to look for them(!).

---

### Post by Sunships on 2007-05-04
OK, it's been 10 minutes now,  a new record! Thanks Pobega and starcraft.man! Your help is much appreciated :)

---

### Post by starcraft.man on 2007-05-04
> **Sunships said:**
> OK, I have disabled my wireless connection, enabled the wired connection, and so far downloading is proceeding as it should, though BitTornado. I suspect it is probably a wireless issue, and will wait and see how it goes. I forgot to mention before as well - no error messages show up when I reboot, although they're probably there to find for someone who knows how to look for them(!).

Hazzah, see, problem fixed :) (Please edit in Resolved to the title of the thread, so others know)

Bit Tornado btw, seems to have problems of late, I dunno why but it doesn't seem to store preferences... stick with Ktorrent.

You are very welcome, you point to problem, we make it disappear like that! :D

---

