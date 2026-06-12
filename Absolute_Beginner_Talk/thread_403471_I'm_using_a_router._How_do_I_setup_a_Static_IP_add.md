---
title: "I'm using a router. How do I setup a Static IP address?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-07
I am connected to a linksys wireless router and that wireless router is connected to a wired linksys router. The wired linksys router is connected to my DSL modem.

How do I setup a static IP address?

I think, it is what I need for video chat for Qnext and WengoPhone. Am I correct?

---

### Post by OffHand on 2007-04-07
Go to System > Administration > Network
Select your connection and click on properties.
From the configuration drop down menu pick 'Static IP Address'.
Fill in an IP address, something like 192.168.1.100
Subnet is usually 255.255.255.0
Gateway is probably 192.168.1.1 (your routers IP address)

---

### Post by dbbolton on 2007-04-07
i don't know if that setup will work. i started a thread about a similar idea [here]("http://ubuntuforums.org/showthread.php?t=340226").

but, i can tell you how to set up a static IP. first go to System > Admin > Networking. select Wireless connection, and click Properties. under Connection Settings, Configuration, click the the drop-sown menu and select Static IP. then, fill in the IP address and gateway. subnet mask is probably just 255.255.255.0 or something.

---

### Post by OffHand on 2007-04-07
You can find out your router's IP address with the following command:

```
route -n
```

If you're not sure about the output, post your results.

---

### Post by Xoanan on 2007-04-07
I have a linksys router and a cable modem;  The first thing I had to do was to configure the router itself.  IN order to do that, I went it the router&#347; menu and for a Linksys, I typed in the router&#347; IP address into the browser.  

From there, I set things up through the router menu.  

I don know how works on DSL, but with cable modem, it took a little playing to get the router and the modem to talk to one another.  What I finally did to make it work was this

1. Unscrewed the coaxial cable from the modem(leaving everything else plugged in.

2. I went into the router menu and I renewed the ip address for the router(it was previously picking 0s.  After renewing, I got a 192.... ip address).

3.  Then I screwed the coax back and renewed the router ip address again.  After that , both my XP and Xubuntu were online.

---

