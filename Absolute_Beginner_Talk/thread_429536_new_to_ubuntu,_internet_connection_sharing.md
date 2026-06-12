---
title: "new to ubuntu, internet connection sharing"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by ex4n on 2007-05-01
Hey guys
First off, im a real linux noob, just installed ubuntu yesterday to give it a go as im really sick of windows xp.

So far i love it, as i was installing it, everything just worked, and once the installation was done, drivers and software already installed, i didnt have to do anything, my internet connection was even already set up, i could update/browse straight away.

Anyway, my problem is that i want to set up the same internet connection sharing i had with windows XP. I have 4 nnetwork ports on my computer, 1 is plugged into the ADSL modem, one into my other computer, one into my laptop and one into my Xbox.

With windows XP is just kinda set it all up for me, i know a little bit about TCP/IP etc. but not alot.

I installed firestarter and tried to get it to share to atleast 1 other connection but it keeps saying eth1 is not ready, check the settings or internet connection, i know my internet is fine (eth2) because im writing this now.

The computer i want to connect to is running windows ME, at the moment setting up the sharing here is my biggest concern, i can work at the other two later.

I think i need to set up some kind of DHCP but i really dont know how to go about it, or what software/settings i will need either end.

Any advice appreciated, thanks.

---

### Post by lamalex on 2007-05-01
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

your box that ubuntu will be connecting to is the server. It's not as easy as windows but my no means difficult. if you need any help ask!

---

### Post by ex4n on 2007-05-01
thanks for the reply.
the link you gave me seems (to me :)) to teach linux to linux internet sharing, any help with getting it to work linux to windows me? if im wrong here please help me out :)

---

### Post by lamalex on 2007-05-01
I'll search around, the other option is just switch their locations which is imo your best choice, put the more secure OS against the internet and make it almost a HW firewall for the windows pc

---

### Post by lamalex on 2007-05-01
found some more info: your current set up will probably work except windows doesn't have any DHCP server, it works windows-windows due to some funky MS junk, if you manually set up your linux box it should work, so set a static ip, set up dns servers, gateway, ip, subnet all that junk.

---

### Post by ex4n on 2007-05-01
sorry, i think i didnt make myself clear.

the computer that is recieving the internet connection is my linux box, but i need to share it with my windows box.

---

### Post by lamalex on 2007-05-01
> 
The computer i want to connect to is running windows ME
then use that wiki page! looks like you have to configure your windows box by hand which should be easy enough. I don't know windows well so I can't tell you how off hand. You should also install a dhcp server on the linux box and have the windows pick up dhcp from it.

---

### Post by ex4n on 2007-05-01
thanks i will give it a go, this is all new to me im just used to setting an ip address and letting windows do everything for me.

---

### Post by snappynuts on 2007-05-03
ok for about 2 weeks now I have been trying to get internet connection sharing working between my ubuntu box which has the internet and my XP box.  I installed firestarter, speciffied eth0 as my internet connection and my eth1 wireless card as my local area connected device.  My local area network device is a wireless card that is ad-hoc to the XP wireless card.  I can't even get the firestarter to start.  It says "cannot start, eth1 not ready".  Under network settings, the wireless card is enabled DHCP.  I installed dhcp3 but the dhcp3 server will not disable and enable, it says fail both times in the terminal window whenever I try and assign listening ip.  I have no ieda why the dhcp won't stop then start again, but I'm assuming this is why internet connection sharing isn't working.... because my wireless card is not getting an IP.

if someone could help me through this I would greatly appreciate it.

---

### Post by heatpumpcontrol on 2007-05-04
Hey there,
I have firestarter and though I am new myself to ubuntu, I believe what you have to do is make sure that firestarter is set to 'creat a new dhcp'  under Firewall, Network Settings in  preferences. Now make sure that you have Enabled ICS and Enable DHCP for the local Network. 

On your windows machine, under Network settings, select your wireless card properties. Under TCPIP settings, double click on it, and at the bottom deselect the Obtain DHCP Automatically, Now in the fields, enter an ip from the default range in firestarter. and find out what IP your Ubuntu machine is because that has to be entered as your default gateway. Enter that twice. Click OK twice.

Right click on My Computer and select manage. Under services you can now restart your DHCP and DNS services by right clicking them and selecting restart. If your machine doesn't pick up the service then try restarting your Windows machine.

Before you do though, just to be sure on your Linux machine, go to system, administration, system monitor and hmm, I don't see it. DHCP is not there,... just reboot your Linux machine to make sure you are resetting your wifi card's DHCP. 

Good luck
HPC

---

### Post by snappynuts on 2007-05-16
ok..... I understand this and thank you for the response.  My problem is whenever I try and turn on Firestarter, it tells me that my Eth1 is not ready and to check that it is connected.  Eth1 is a wireless card on my computer and I would like it to connect to the Wireless card on my other Windows machine.  I just can't get the firewall to start.  I can see how it would say that Eth1 is not ready.... because it is not connected to anything.... but thats why I need Firestarter to start, so it will get an IP and also give an IP to my Windows machine......  

anyone know what I am getting at here?  I really would love to get this working.

---

### Post by nickpaton on 2007-05-16
Whenever I set up Firestarter I use the following steps using the Wizard:

Detected Device is the one you want to use at the present time, you have to change this each time you go from wired to wireless LAN.  For instance I am currently on wireless Eth1, so on Firestarter Eth1 is selected.

Dial out and DCHP boxes deselected

Forward

Enable Internet Connection Sharing deselected (most of that screen blanked out)

Forward

Start Firewall

Save and quit.

Whilst setting up the whole network I would now suggest you disable (stop) the firewall.  Note that when it is stopped you must minimise it NOT shut Firestarter down or else it will restart again.

Once you've got everything working you need to set the Policies so that you can access the Windows PC with the Firewall enabled.

This [HOWTO]("http://ubuntuforums.org/showthread.php?t=202605&page=30#298") goes into this in a bit more detail.

One thing I will say is that you need to have static IP addresses for all this to work.  This can be done by asking your router to reserve IP addresses for each PC.

Also when setting up a file sharing between windows and Ubuntu PC's  I use [this]("http://ubuntuforums.org/showthread.php?t=202605") excellent HOWTO from Stormbringer which has worked for me ever since Dapper.

---

