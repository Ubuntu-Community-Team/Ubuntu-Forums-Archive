---
title: "Connecting to a Windows Network"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by joshuamc on 2007-06-05
I typically have to login to a windows domains before I get on to my work computer. I've just installed Ubuntu and can't seem to get internet access here at work and I think it is because I need to logon to the network. How can I do that?

---

### Post by lazyart on 2007-06-05
You likely have a proxy at work that you need to connect to.  On a windows box go to internet explorer settings>connections>lan settings and note what the proxy address is and give that info to firefox (sorry, can't tell you where ATM but it's in the preferences/settings somewhere).

Once that's entered and you try to browse you should get an authentication window.  Enter your domain\username and password and you should be able to surf.

---

### Post by joshuamc on 2007-06-05
Actually, after some help from a friend, I realized that I need to connect to the network via WPA2 Leap. However, anytime I try to access this type of network, I get an error about my hardware not supporting the security protocol. My gateway is just a few days old though so it should support it.

---

### Post by lazyart on 2007-06-05
It's the driver for your wireless card that is at issue.  Can you give us specs on it?

---

