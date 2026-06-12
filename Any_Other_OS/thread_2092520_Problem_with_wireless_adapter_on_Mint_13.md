---
title: "Problem with wireless adapter on Mint 13"
date: 2012-12-08
forum: Any Other OS
---

### Post by LadyA on 2012-12-08
I have just installed Mint 13 (Mate) and the Ausus wireless adapter connected right away, but when I try to go on the internet it disconnects. What do I have to do to make it stay connected?

---

### Post by pissedoffdude on 2012-12-08
We're going to need more info.  What's the model of your wireless card?

Give us the output of one of the following, depending on if its an internal or usb card:

```
lspci
lsusb
```

Let us know what kernel your running by: 
```
uname -r
```

Did you have to install restricted drivers for it, and is this a problem only on secure (WPA or WEP) wireless networks?

---

### Post by wetland on 2012-12-08
Same Idea as POD / Asus What?

At the command prompt...


```
lspci
lspci | less
lspci | grep -i intel
lspci | grep -i wireless
```

When I enter the last line I get for example...

04:05.0 Network controller: Atheros Communications Inc. AR9227 Wireless Network Adapter (rev 01)

what do you get?

---

### Post by LadyA on 2012-12-09
Thankyou, pissedoffdude and wetland for responding to my problem. I burned a new disk and reinstalled mint 13. Now the wireless is working fine.

---

### Post by wetland on 2012-12-13
Glad to hear you got it working... Goodluck!

---

