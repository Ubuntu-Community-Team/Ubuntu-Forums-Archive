---
title: "Wireless connection issues in OS X"
date: 2009-02-26
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2009-02-26
It's odd that I should come here to try and sort this bug out, but I understand Linux a lot more than I do OS X. Here's the deal:

Every so often I have this incredibly aggravating problem in when I'm Mac side. I can connect to my wireless router, which has WPA2 encryption fine. The Airport indicator says that I am connected, however I can't access the internet, and when I look at the network settings in system preferences it tells me that I have an internally supplied IP address. I can plug my ethernet cord into the router and everything works fine, but I have no idea what to do about this wifi thing.

I've tried disabling/reenabling the card. I've tried putting it to sleep/waking it up. I've tried rebooting. None of those options have worked.

But I spend very little time in OS X, and sometimes I'll switch over and it will work fine. There must be something I'm missing. Any help would be greatly appreciated.

---

### Post by gtcoffee on 2009-02-27
That is an issue of Leopard DHCP.
There is no fix patch yet.

What you can try is go to 
"System Preferences" -> "Security" -> "Firewall" -> choose "allow all" (the first one). Once you selected it, you should have the correct ip. (This trick work for my G4)

GOOD LUCKY!

---

### Post by Rog-Mahal on 2009-02-27
I'm running Tiger (10.4.11), and I don't see any firewall settings under the Security tab. Is there another way to access those settings?

---

### Post by Speed Demon on 2009-02-27
I dont run OS X, but ran Leopard on a friends Mac for a few days, and its in Sys Pref's network thingy - set it to Static and set IP Gateway and DNS instead of DHCP

---

### Post by Rog-Mahal on 2009-02-27
Well, I'll try that next time, but I am running Tiger. I was hoping there would be some kind of fix, that just sounds like a workaround. Any other thoughts?

---

### Post by gtcoffee on 2009-02-28
Ops..didn't notice you were talking about Tiger.

for Tiger try this:
1. Turn AirPort off
2. go "System Preferences" -> "Network" -> select "AirPort" and then "Configure..."
3. if "By default, join: " is "Automatic", choose "Preferred networks" instead
4. now delete the network that you couldn't get the ip
5. apply now
6. Turn on the AirPort, connect to your network and retype the password

hopefully it will assign the right ip
Good Luck

---

### Post by Rog-Mahal on 2009-02-28
Thanks for the reply, I'll give it a try next time I am OS X side.

[EDIT:] No good, I still can't connect. Windows and linux computers have no problem connecting to this network. My Macbook doesn't have a problem when I'm running Ubuntu. It has been able to connect to this router before. I don't get it!

---

### Post by Rog-Mahal on 2009-02-28
Well, in fiddling with things I've found that if I connect to the router, unplug it, and then plug it in again I get an ip and can connect to the internet, does that make sense to anyone?

---

### Post by cyberdork33 on 2009-02-28
> **Rog-Mahal said:**
> Well, in fiddling with things I've found that if I connect to the router, unplug it, and then plug it in again I get an ip and can connect to the internet, does that make sense to anyone?
sort of. When you restart the router, it restarts the DHCP server, and it likely tries to reassign IPs. 

It sounds like the Mac is not accepting the IP when you "connect" for some reason.

---

### Post by Rog-Mahal on 2009-03-15
I'm still having this issue with new routers in new locations. It seems like there is some kind of problem related to connecting to the router in Ubuntu and then switching over to OS X. Resetting the router works, but that's a real pain. Could it have something to do with DHCP leases and the computer having the same MAC address for both OSes? Has anyone had a similar problem? What about another place to look for a fix? Would calling tech support be useful? I'm reticent because I've heard that Mac people freak out when you say you're dual booting with refit.

---

