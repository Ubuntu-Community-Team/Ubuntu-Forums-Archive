---
title: "Wrong wireless protocol being used"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-07-15
I'm trying to connect to my wireless network
Its being picked when I scan for networks
And i've turned my encryption off
But its still not woking
I think that it might be using the wrong protocol, beause when i scan for networks, it says Protocol: IEEE 802.11b but when i enter iwconfig I get IEEE 802.11g
Could this be the problem?
Does anyone have any ideas what could be?
Thanks :)

---

### Post by reset3x on 2007-07-15
> **tartarian said:**
> I'm trying to connect to my wireless network
Its being picked when I scan for networks
And i've turned my encryption off
But its still not woking
I think that it might be using the wrong protocol, beause when i scan for networks, it says Protocol: IEEE 802.11b but when i enter iwconfig I get IEEE 802.11g
Could this be the problem?
Does anyone have any ideas what could be?
Thanks :)

G is backward compatible with B and A... So thats not an issue... If you're trying to use Network Manager that may be the problem... Try doing a manual configuration of your NIC through System/Administration/Networks... If that works it would be a good idea to re-enable the security on your router...

Hope this helps....

---

### Post by tartarian on 2007-07-16
I'm not using network manager I'm running Xubuntu and I've no internet connection to download it with. 
I've been trying to manually input my network settings but it still doesn't work (using iwconfig and by editing my interfaces file)
Please Help!

---

### Post by reset3x on 2007-07-16
> **tartarian said:**
> I'm not using network manager I'm running Xubuntu and I've no internet connection to download it with. 
I've been trying to manually input my network settings but it still doesn't work (using iwconfig and by editing my interfaces file)
Please Help!

Why not use the GUI in System/Network? You can get more infomation about iwconfig by opening a terminal and entering:

```
man iwconfig
```

and make sure you've gotten everything right....

---

