---
title: "Airlink 101 PCI"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by ilikecoffee on 2007-10-23
Just switching from XP to Ubuntu. I've installed 7.04 and Ubuntu doesn't even see my wireless card. (This all worked fine on XP - which I've erased from my hard drive).
All the help threads refer to lines of code. I can't even find a place to type in command lines.
I figure "Absolute Beginners" would have a few answers for me. So, if anyone can explain this as you would to a child, could you help me get up and running?

---

### Post by Daveth on 2007-10-23
Welcome to the Ubuntu forum for starters. The place to type in the commands is the terminal, and this lives in Applications/accessories/ terminal. It is handy to have to hand, so you might want to right click it and  "add this launcher to panel", so it sits there.

Though it is an Airlink, we need to know what chip is inside, so, in your newly acquired terminal, type

```
lspci -v | less
```

from [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

the answer will then take you to 

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101)

and we can progress the issue with you some more.

---

### Post by ilikecoffee on 2007-10-24
okay, Thanks for the help. Found the terminal typed the command and got:

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at c400 [size=256]
        Memory at ed105000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

I checked both references, and apparently the realtek chipset RTL-8185 is supported.

I even downloaded NDISwrapper, but couldn't install it. I feel like a newbie. What should I do now?

---

### Post by Daveth on 2007-10-25
you probably need to run through this page next then

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

assuming there is no native driver for that chip, which is generally the better option (if available).

---

### Post by ilikecoffee on 2007-10-30
Okay, I couldn't get it going from these tips. I installed ndiswrapper, ndisgtk, and copied the winxp drivers and util drivers from the CD to the desktop. using NET8185.inf and "windows wireless" utility, I was able to get the hardware recognized (supposedly).
When I run:

      ndiswrapper -l

It says invalid driver, but hardware present. When I run:


     sudo ndiswrapper -m

It says something about Alias directive. I've downloaded the linux driver for the realtek 8180 chipset (says it would work with 8185), but I have absolutely no idea how to install it. I've tried:

     "tar -zxvy /Desktop/*"

Of course I substituted the file name for "*" and it said invalid. That's the only installation "help" for the linux-based driver, so back to ndiswrapper and the windows driver.
I'm ready to say ubuntu is "u-busto" and go buy XP again, just because, hey, it works! But before I join the flock, is there anyone who can see what I might be doing wrong?

Once again: ubuntu is not seeing my wireless card. It's an Airlink 101 using realtek 8185 chipset (which IS SUPPORTED: [https://www.fsf.org/resources/hw/net/wireless/cards.html](https://www.fsf.org/resources/hw/net/wireless/cards.html) ). I"ve tried all the normal steps and researched through the forums, and still can't get to the internet using ubuntu 6.10, 7.04 or 7.1.

Thanks

---

