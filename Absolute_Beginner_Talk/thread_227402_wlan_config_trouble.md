---
title: "wlan config trouble"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by cmfourie on 2006-08-01
I hae a belkin g wlan card based on the rt2500 chip set.
Kubuntu sees my card fine, and so does Suse 10.1

I have been trying to set my card up on ubuntu using ndiswrapper. I get ndiswrapper unpacked and then when I type make it says there is a kernel missing in the module folder or something. I have a loop back thing in the top right hand corner of my screen.

Question: how do I set up my wlan card to work on Ubuntu

All help apprecciated

---

### Post by GuitarHero on 2006-08-01
Is Ubuntu on the same install as Kubuntu(did you install them separately or did you install one and just add the other one as a different session?).  If its on the same machine it should work the same.  If you have Ubuntu and Kubuntu on separate partitions you should know that you can have both on one install.  Just type sudo aptitude install ubuntu-desktop or sudo aptitude install kubuntu-desktop.

---

### Post by cantormath on 2006-08-01
> **cmfourie said:**
> I hae a belkin g wlan card based on the rt2500 chip set.
Kubuntu sees my card fine, and so does Suse 10.1

I have been trying to set my card up on ubuntu using ndiswrapper. I get ndiswrapper unpacked and then when I type make it says there is a kernel missing in the module folder or something. I have a loop back thing in the top right hand corner of my screen.

Question: how do I set up my wlan card to work on Ubuntu

All help apprecciated

ok, if kubuntu/ubuntu sees your card, should need ndiswrapper.  ndiswrapper is the last thing you want to do.. I would probably buy a new card before using that.

so can you connect to the internet with lan line?
if so
make sure you do all the updates.
then go to

System>Administration>Networking
make sure the card is activated.
make the wireless card is your default interface
click on the wireless card and click configure

assuming you dont have wep setup, set key type to hex,
wep blank
Configuration DHCP
click ok

let it finish etc etc.

then open terminal and type 
sudo ifconfig wlan0 (or whatever the card is)
then
sudo iwconfig
what do they say?
ifconfig should show you an ip
iwconfig will tell you what wireless connection you are connected to.

if you are still having trouble getting on the net, try renewing the ip,
type

sudo dhclient

let if finish, if you get a new ip then you should be on the net.

also make sure that you dont have some silly security thing blocking you on the router, ie) wep key or mac address filtering.

another thing,
I installed network manager through the applications>add/remove gui.
I also have waproamd installed and wifi-radar (I just like wifi-radar better).

---

### Post by cmfourie on 2006-08-01
thanks to the person who wrote the following article: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

helped me tons.

only thing now is i cant seem to be able to surf the internet.
i'll see if i can figure it out

thanks for everyone who has given me advice on this forum all credit and appreciation goes to you.

---

