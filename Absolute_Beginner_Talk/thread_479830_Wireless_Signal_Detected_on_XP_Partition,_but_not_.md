---
title: "Wireless Signal Detected on XP Partition, but not Kubuntu Partition"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-06-20
Hi,

For starters, I work in an area with a very week wireless signal.

When I'm in my XP partition, the signal is picked up and all my internet-accessing programs work.
When I'm in my Kubuntu partition, the signal is picked up by KNetworkManager BUT Swiftfox, Kopete and Amarok tell me that I'm not connected to the internet.

At my house, my Kubuntu partition can access websites and IM protocols easily.

Soooo what's going on exactly?

---

### Post by capecove on 2007-06-20
Well, I would suggest you give us some more detail, things like what the setup is where you CAN'T use the Internet service. This could be quite a few different things really.

---

### Post by Austin_KW on 2007-06-20
> **lazyrussian said:**
> Hi,

For starters, I work in an area with a very week wireless signal.

When I'm in my XP partition, the signal is picked up and all my internet-accessing programs work.
When I'm in my Kubuntu partition, the signal is picked up by KNetworkManager BUT Swiftfox, Kopete and Amarok tell me that I'm not connected to the internet.

At my house, my Kubuntu partition can access websites and IM protocols easily.

Soooo what's going on exactly?

Could be a few things, You will need to check the output of the following terminal commands. If you dont understand, save the output and post the back here
```

ifconfig -a
iwlist scan
iwconfig
cat /etc/resolv.conf

```

And obviously try moving to a area with better signal to eliminate configuration/encryption key issues etc.

---

### Post by lazyrussian on 2007-06-20
ok thanks for that reply - I'll try that on my laptop tomorrow.

Here's the scoop. I'm a medical physics intern surrounded by radiation oncology equipment. The facility is located in the basement of the hospital near a ton of electromagnetic equipment. Cell Phones and most radio-wave emitting equipment aren't allowed. I'm not given access via Ethernet connection because I'm not using a hospital issued computer - they don't feel like buying them for the interns. So I'm stuck using my laptop. I prefer using Kubuntu+Beryl for my research - makes life A LOT easier. But I'm stuck using my XP partition because I can't get on via KDE.

I have a Toshiba Satellite A105-S2101 Laptop with an Atheros wireless card.

I'll test out the method above and post my results in the morning (when I'm back at work).

---

