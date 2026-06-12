---
title: "Linksys WPC54G card and Dapper"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by lwr on 2006-05-26
Here's the situation: I've just installed Dapper on my Dell Inspiron 2500 (I had Breezy on for a couple of weeks beforehand, but other than that, I'm new to Linux). I'm trying to get my Linksys WPC54G version5 wireless card working, but I don't know what I'm doing. All the existing forums have stuff that just goes over my head, and I don't think any of it's for Dapper anyway. If someone could give me a simple how-to type guide, that would be brilliant.

Thanks

---

### Post by dmizer on 2006-05-26
usually i point people here: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29)

but your card is not listed there for several possible reasons:
1) it's too new and there's no documentation on it yet.
2) it doesn't work in linux
3) no one's gotten around to adding it to the list.

i'm going to lay my money on number 2 though, because that particular line of cards has a bad history.  i have the v2 of the same card, and it won't even show in lspci.

if you just purchased it, i suggest taking a look at the above link and exchanging your card for one in the list that works out of the box.

if you're really desperate, you can try ndiswrapper.  there's a good howto here: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

