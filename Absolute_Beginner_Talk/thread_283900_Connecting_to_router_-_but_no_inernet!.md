---
title: "Connecting to router - but no inernet!"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-24
(I'm on Kubuntu)
Hi, just as the title says, I am able to connect to my router's interface, but not to the internet. Right now I'm using a hawking USB adapter (not sure of its model), but anyway this has happened to me since the day I began using MY 'secured' network. I was using an unsecured network before and everything seemed to work nicely.
I'm using a Dlink DI-624 router, and I'm using 
Another thing to add is that I do not really know HOW(!) but sometimes my network did work after a while of just leaving my computer alone. Sometimes I messed with the DNS servers in the Networking window and it worked (but when applying the new DNS server and closing the Networking window took long minutes of waiting). It also annoys me how the DNS server I add get erased after I restart my PC. The tool to connect to WiFi networks in Kubuntu doesn't seem to work either (Network appears, I type password and all settings)

some minutes later after finishing writing the above: I just noticed that I was using gnome's network tool. Either way, I used KDE's but same thing...
I was even editing directly thet /etc/network/interface file and same thing. Let me try messing with the DNS part of the KDE Network settings to see what happens.
Hopefully I'm missing something obvious and I can fix this... Thanks in advance,

Dual Cortex

---

### Post by Dual Cortex on 2006-10-24
:confused: 

Gah... It's almost embarrassing. But everything works now. In fact I'm typing on Kubuntu right now.
I didn't do anything with the DNS settings. I just set it to DHCP, etc., and works fine... (On KDE's network settings which I hadn't tried DHCP on  before)

:-k :-D

---

### Post by Sef on 2006-10-24
Glad u got it up and running.  When I had just gotten my Dell, I moved and could not get internet at my new place.  After going back and forth with the Dell help, I still had no internet. ](*,)   After 5 months, I was just fiddling with my computer, going through the setting when I discovered that my internet settings were set to dial up, and I was on lan.  I changed the settings, and it worked just fine after that.:-D

---

### Post by JayTee on 2006-10-24
if you're on a home network and you use a cable or dsl modem you should usually set your network interface to use DHCP. ISPs often change the IP addresses of their DNS servers. I'm assuming this is for maintenance and updates or because they've restructured and upgraded their network. Usually they'll only bring one of two DNS servers offline at a time but if there is an outage in your area and they updated their addressing and push out new DHCP leases with new addresses for DNS then your computer would not have had them updated if you'd set them statically. If you want though you can still choose to set a static IP address and let your DNS be done dynamically. I use a Linksys router and even with DHCP set on my 3 computers I usually get the same addresses all the time unless the lease period has expired and I shutdown and restart more than one of them at a time.

---

