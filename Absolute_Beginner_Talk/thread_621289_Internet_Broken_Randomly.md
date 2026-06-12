---
title: "Internet Broken Randomly"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by darkness5723 on 2007-11-23
Hey all, today my computer randomly stopped connecting to the internet. The most recent changes to my computer were: Installing Azureus last night, and then installing VLC. Other than that NOTHING was changed at all. I was just surfing around (secure) websites and then all of a sudden.. no more internet.

I'm using Ubuntu 7.10, Onboard LAN card.. have never ever had a problem with it. Its a dedicated line run directly to the router which is then run directly to the cable modem. 

Cannot ping anything (not even my router I don't think). I can see the local windows network that I'm on as well.. this is a very strange problem. I checked all the diagnostic utilities... 
ifconfig gives me 0 errors,dropped,overruns for both eth0 and lo.


when I type route -n it says everyting is using eth0, but if i try to shutdown eth0 it says eth0 isnt properly configured. 

Sorry about vague information.. I would copy+paste but obviously I cannot.. help me someone!

---

### Post by popch on 2007-11-23
If you can see other computers on your LAN but not the router, I would think that the router does not work. 

ETH0 not being properly configured could possibly be caused by the connection making use of DHCP which would not be available because the router is down.

Can the router be pinged from the other PCs on the LAN?

---

### Post by darkness5723 on 2007-11-23
err.. yea i have the internet.., every other computer (6 of them) in the house works fine.. including this laptop im on which is running feisty. everything is working fine except my PC.

---

### Post by popch on 2007-11-23
> **darkness5723 said:**
> 
Cannot ping anything (not even my router I don't think). I can see the local windows network that I'm on as well..


From your earlier post. What I think a bit confusing is that you claim to 'see' the windows network. How do you 'see' it, if not by pinging?

Being a simple minded person, I suggest next that you check your ethernet cable. Are both sides firmly plugged in? Do the lights on the router and on the PCs NIC indicate that the connection is taking place?  Are you quite certain that the Ethernet cable is not damaged by placing furniture on it or by rodents having eaten the insulation or by some other physical means?

---

