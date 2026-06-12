---
title: "Wireless problems"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Hunterkiller5150 on 2007-06-01
Hello all,

I am trying to get my wireless to work on my laptop.  I have been searching through the forums with no luck and am currently using fwcutter to attempt to connect.  I can see my network, but it will not get an ip, i have temporarily disabled all the security on the network just to see if i can connect but i still can't.  PLEASE HELP!!!

---

### Post by kernel tom on 2007-06-01
alrighty, depending on which distro your using the location of Network Settings is in different places... but you probably know where that is

enable ur wireless connection by clicking the check box by it, entering your network's exact name, and choosing automatic (dhcp)

try this with no security on ur router

if that works great!

if not.. do you have a wired connection?

if yes, download wlassistant

sudo apt-get wlassistant
then run it as root
sudo wlassistant

this will help set up and configure ur network card, conect you, and save ur settings (WEP keys as well)

good luck

---

