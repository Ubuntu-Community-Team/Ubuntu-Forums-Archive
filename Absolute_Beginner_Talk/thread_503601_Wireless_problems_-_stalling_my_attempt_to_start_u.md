---
title: "Wireless problems - stalling my attempt to start using ubuntu - HELP!"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by chickyd on 2007-07-18
Being a long term Windows boy (who thought he knew his way round a PC pretty well) I've  recently decided to give Ubuntu a go. So, I've installed Wubi which seems to be working fine (from what I've read there is no real issue with speed with Wubi until you start getting more heavily involved so I thought I'd get to know the system this way first before setting up a new partition).

So installation has gone ok. My two issues are as follows (all help offered will be greatly appreciated!):

_Wireless Internet_ - as everything, you need the internet to get Ubuntu going but at this I am failing. Once installed Ubuntu saw my wireless card and listed my network SSID. I clicked on it, typed in my WEP key and nothing happened. After a bit of fiddling with the manual settings I got it to show bars in the top right of the screen - two of which are blue. When i move the mouse over these bars it says 'Connection to wireless network "MY SSID" 50%'... i assumed this meant it was connected but i had no access to the internet. One thing i have noticed is that Ubuntu doesn't prompt me if the password is not correct - i tried a random key and these bars stayed where they were..?.. After a spot of reading this forum I considered it could be a firewall - I don't seem to have Firestarter installed -, I've also read up on ndiswrapper however think (tell me if i'm wrong) that this is for when Ubuntu doesn't see your network card - and mine clearly does! I downloaded it and tried to do something with it last night but as I completely new to the ways of Linux am only really capable of typing things word for word as people tell me into the terminal. I therefore failed to get this going (if this is what I need is it possible to point me to an absolute beginners guide to how to get this working?) If it helps I've also discovered that my network card is recognised at 'ra0' and that the system sees this a 'Unknown Device'. I am using a Belkin wireless network PCI card. 

_Graphics_ - I've clicked on the Desktop Effects and it prompts with you need to enable the NVIDIA driver which I click. It then prompts for a reboot but after this is done nothing seems to have changed and going through the same process doesn't seem to have any effect. I have not focussed on this problem yet though as I clearly see the internet as priority number one!!

I'm sorry to ramble but wanted to get down what I know to help you guys point me in the right direction. Any help you may have will really be much appreciated - I really want to learn linux!!! 

Many thanks!

---

### Post by shearn89 on 2007-07-18
Not sure about the wireless - have a hunt through the "networking and wireless forum" if no help found here. For the desktop effects, if nothing appears to have happened do things look more pretty? fading or effects on windows minimising and things? Windows wobble when dragged?

---

### Post by Gone fishing on 2007-07-18
I have't had any luck with the roaming wireless with feisty - however if I set up the connection manually using the GUI tools and reboot it works everytime.

---

### Post by bedfojo on 2007-07-18
Wireless is often tricky. But if your card is automatically seen by Ubuntu then that is most of the work.

You could try uninstalling network-manager (which I find horribly buggy) and using wicd instead.

Open Synaptic and uninstall completely network-manager.

Then go to the wicd site at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) and follow their instructions to install it (by adding their repository) then using Synaptic to install wicd.

You'll need to add the panel applet to the list in  System > Preferences > Sessions in the "Startup Programs" tab. Click the “New” button. Give it a name ("Wicd" works fine). For a command, enter /opt/wicd/tray.py 

Also remove Network Manager from the same list by unchecking the box for it.

Reboot, then click on the wicd applet to add your WEP details etc.

Good luck.

---

### Post by chickyd on 2007-07-18
Thanks for your help.. I suppose I will have to give a go at replacing network manager to see if I can fix this then.. When I realised last night that in the network setting (i con't remember exactly what it's called) where you see the devices, that my wireless device - ra0 - was called an 'Unknown Device' .. i came to the conclusion that this may be the problem.. from what you guys are saying it isn't, right?

really annoying cause my routers in a different room so without wireless i have no way of having a wired connection - i'll have to try and install this other network manager without the internet which as far as i can tell is when things get difficult (when you can't access the repositries).. if anyone has any other tips they'd be much appreciated!

Also, on the graphics front, nothing changes after a reboot. No nice effects, i can tell the graphics aren't working.. is this something that'll be really easy to fix once the internet is live?

---

