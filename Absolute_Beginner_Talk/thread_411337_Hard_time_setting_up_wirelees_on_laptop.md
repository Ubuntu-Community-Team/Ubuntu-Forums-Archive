---
title: "Hard time setting up wirelees on laptop"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by mr32123 on 2007-04-16
Hey everyone,

Recently I just decided to install Ubuntu on my laptop (HP) after a fight with windows xp.  I just need help connecting to my wireless network.  

I know it detects the card because when I go to Device Manager find "PRO/Wireless 3945ABG Network Connection"

I heard to download network manager, but as I'm new to linux i found the page for downloading and was completely baffled by what to download to where and how to install etc...

Someone please help :(  i feel so helpless lol

---

### Post by N Clement on 2007-04-16
I know how you feel...about being hopeless with wireless, but I can try to help you.  Can you go into the terminal and give me the output of the command:

iwconfig

---

### Post by mr32123 on 2007-04-16
OK got it what next?

---

### Post by Maestro23 on 2007-04-16
Might help:

Ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

### Post by mr32123 on 2007-04-16
I checked out that link and I don't really understand what they're talking about

---

### Post by AndrewB on 2007-04-16
you might want to wait a few days. Feisty is coming and it works with Intel's PRO/Wireless 3945ABG Network Connection right out of the box:D

---

### Post by N Clement on 2007-04-16
Andrew makes a good point, but if you do want to try to get it working before then, let me clarify my first post:

1)  Go into the terminal and type the command: iwconfig

2)  The command should spit out a bunch of stuff onto the terminal

3)  Copy-Paste this stuff into the forums so that we/I can see what it says

---

### Post by jdong on 2007-04-16
There is no need for ndiswrapper for the Intel IPW3945 chipset. It has had kernel support since Dapper, and installing ndiswrapper will only make things worse.

The good news is that Feisty Fawn coming out this week will have an easy-to-use Network Manager that allows you to configure wireless networks from a tray icon. Perhaps the best advice right now is to wait for that release :)

---

### Post by mr32123 on 2007-04-16
ah great- almost perfect timing.  I think I'll wait a few days for Feisty.

Thanks for the help

---

