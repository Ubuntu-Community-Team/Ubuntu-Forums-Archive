---
title: "Networking problems"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by maccabbi on 2006-04-08
Okay, I am completly new to Ubuntu. It is the most up to date OS that I can install on my old mac. I have a Comm Slot II de2104 chipset ethernet device. I am not sure that it can work on linux but i have read some people's post where they got certian brands too. This device doesn't have a brand name printed on it. 

I have a cable modem hooked into an airport and the airport hooked int a ethernet hub that runs to my Tam and an IMac. the internet works fine under os 9 on the Tam and os x on the imac. 

Ubuntu wants to use a modle tulip which doesn't work and won't even tun the pc light on, on the hub. I can rmmode tulip and sudo modprobe de4x5 and my activation light comes on and i can ping myself but that is it. 

Any sugestions?

---

### Post by AnRuaRi on 2006-05-07
ok, I want to try and help, but I couldn't understand half of what you were on about,
What's an airport, what's a tulip.....?

I've never used a Mac, but aI would suggest trying the following:

While logged into an Administrator account

click on System -> Administration -> Networking

Enter the users password when requested.

note all the network devices listed.

As an example, on my PC I have 3, Ethernet 0. Ethernet 1, and Modem Conection. The latter 2 are deliberatly deactivated, as I'm not using them.

You should see any networking devices on your computer here.
Ensure that the device you want to use is the only one active.

Now I dont mean just click the "deactivate" button, as this only has an effect untill you re-boot.
Click on any device you're not using, and then click on "Properties"
deselect the tick box "enable this conection" for any devices you're not using right now

Activate **only** the device you're trying to connect to your network with.

If you have a DHCP server (windows equivalent is "obtain IP address automatically") then select DHCP in "Configuration". Otherwise you will need to determine the correct settings and enter them here.

Click OK in this dialogue box, and again in "Netorking"

if you changed anything you would be best to re-boot your computer now (unless you know how to restart the networking deamons yourself)

Get this far, reboot your machine, and see if it's working, then PM me if you need further help.

---

