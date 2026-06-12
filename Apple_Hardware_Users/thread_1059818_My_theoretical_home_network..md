---
title: "My theoretical home network."
date: 2009-02-04
forum: Apple Hardware Users
---

### Post by Jaiibee on 2009-02-04
Pretty sure this would be the right place.. Sorry if it isn't.

Ok, so basically I want to connect my Mac G5 PPC to the Ethernet, and then set-up a Wifi network sharing the internet over a WEP encrypted signal (WEP is just there to stop leechers) using my G5.

That way, my iPhone and EEE PC can just connect to my G5 wifi and use the internet via the G5, rather than connect to the router.
If my assumption that the router is preventing Linux computers from connecting to the internet is correct, then this should allow my ubuntu-variant-powered EEE PC to connect to, and download from, the internet (as it's having problems with that at the moment)

So I plug the Ethernet into the G5, turned off airport and WAH-LAH: nothing.


Sigh.. I'm assuming that Macintosh computers have a light on their ethernet when its plugged in, and i dont see the cable being illuminated.

The "Built-in Ethernet" has a green light and it says i'm connected to the internet via built-in ethernet, however I have no internet connectivity once my AirPort has been turned off.

Any idea? We have WPA2 encryption for the wireless, and a Mac filter which I'm sure is only for the wifi. Could I be looking at a failure to connect to the internet because my Mac address isn't on the filter list?
I dont have access to my router...

---

### Post by tiresia on 2009-02-04
If I understand, you have two problems - tell me, if I am right

1. Connecting your G5 to the Internet via ethernet (now you can access internet only wireless trough your Airport)
2. Sharing your Internet connection with another PC (Ubuntu) and with an iPhone

You say, you can't access your router.
What does it mean? You can't access it phisically?
Do you know the IP of your Router? (something like 192.168.0.1)
Do you get an IP for your PowerMac?
Please have a look in System Preferences > Network

---

### Post by Jaiibee on 2009-02-04
> **tiresia said:**
> If I understand, you have two problems - tell me, if I am right

1. Connecting your G5 to the Internet via ethernet (now you can access internet only wireless trough your Airport)
2. Sharing your Internet connection with another PC (Ubuntu) and with an iPhone

You say, you can't access your router.
What does it mean? You can't access it phisically?
Do you know the IP of your Router? (something like 192.168.0.1)
Do you get an IP for your PowerMac?
Please have a look in System Preferences > Network

Sorry I was a little ambiguous about it.
I'm posting off my EEE PC, which is running an Ubuntu variant (gOS). This EEE PC is connected to the internet via the Ethernet, so it isn't a filter issue...

You're right about my problems, however I could solve number 2 by myself if I could work out why i cant connect to the internet via ethernet.
Im sure i've just over looked a setting..

And by not having access to the router, I mean the default admin password was changed without my knowledge, and I can no longer change settings on the router.

---

### Post by tiresia on 2009-02-04
> **Jaiibee said:**
> Sorry I was a little ambiguous about it.
I'm posting off my EEE PC, which is running an Ubuntu variant (gOS). This EEE PC is connected to the internet via the Ethernet, so it isn't a filter issue...

You're right about my problems, however I could solve number 2 by myself if I could work out why i cant connect to the internet via ethernet.
Im sure i've just over looked a setting..

And by not having access to the router, I mean the default admin password was changed without my knowledge, and I can no longer change settings on the router.

There should be on the router a button, to reset it to the original configuration (but then, you must enter again all your data, passwords...)

Anyway, if you can access internet via ethernet with your asus, it means that the ethernet cable is working. 
You should go to 'system preferences' on your mac, and check your connections in 'network'. It should be set to DHCP automatic.

(But it would be important to see the configuration of the router...)

---

### Post by cyberdork33 on 2009-02-04
What is the benefit in connecting to the G5 rather than directly to your router AP?

---

### Post by Jaiibee on 2009-02-04
> **cyberdork33 said:**
> What is the benefit in connecting to the G5 rather than directly to your router AP?

I want to see if my gOS - powered EEE PC will be able to access the internet via this method, as using the router does not prove effective.

Here are my settings, tiresia.

I think I dont have my Wifi on, and I dont know how I would go about turning it on..
iwconfig shows up:

lo no wireless extensions.

eth0 no wireless extensions.

---

### Post by cyberdork33 on 2009-02-04
> **Jaiibee said:**
> I want to see if my gOS - powered EEE PC will be able to access the internet via this method, as using the router does not prove effective.
I would just fix that problem instead, as going through 2 NAT filters will likely give you problems.

For Internet Sharing, you need to go to System Preferences > Sharing and enable Internet Sharing from there.

---

