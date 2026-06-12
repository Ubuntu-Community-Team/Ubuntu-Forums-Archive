---
title: "Wireless Card problem for newbie"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by simonfoley on 2006-12-10
I decided to go for Ubuntu as I would love to get linux up and running.  I am no IT pro and have a very, very basic knowledge so please treat me like a fool but...

I have installed Ubuntu without problems and then went to the documentation - Chapter 5 - Internet

I went to system - admin - networking and it is showing that I have a wireless card but I do not get an activate/deactivate button so I assume that the drivers are not working.  So, I install ndiswrapper to solve the problem and follow the steps outlined on page 32 and

[I]simon@simon-desktop:~$ sudo ndiswrapper -i /home/Deasktop.net5211.inf
Password:
Installing deasktop.net5211
couldn't copy /home/Deasktop.net5211.inf at /usr/sbin/ndiswrapper-1.8 line 144.
simon@simon-desktop:~$ ls home
ls: home: No such file or directory
simon@simon-desktop:~$ ls /home
simon
simon@simon-desktop:~$ sudo ndiswrapper -i /home/simon/Desktop/net5211.inf 
net5211 is already installed. Use -e to remove it
simon@simon-desktop:~$  ndiswrapper -l
Installed drivers:
deasktop.net5211        invalid driver!
net5211 invalid driver!
simon@simon-desktop:~$  ndiswrapper -l
Installed drivers:
deasktop.net5211        invalid driver!
net5211 invalid driver!
simon@simon-desktop:~$ 
[/I]

Is what I get.  The modem is 108Mbps 802.11g PCI Adapter **TEW-443PI**from TRENDnet.  I have looked in the wiki for this card.  

I looked here [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and found

RENDnet
	

TEW-443PI
	

Atheros AR5212/ath*
	

?
	

Yes
	

yes
	

Easiest wireless setup I have ever done, Use Ubuntu's network GUI and just add WEP key, enable and activate. Works with both 802.11b&g.
	

So, how do I do this as I am not seeing how to do this?  If the driver is valid, then why can I not activate this and access the net.  I have not changed any settings under the networking tab?

Thanks in advance for any help.

Simon

---

### Post by nickpaton on 2006-12-10
Hi Simon and welcome to the forums & Ubuntu!

Can I suggest that a little knowledge is a dangerous thing LOL!  What the supported cards page says is that your wireless drivers should be already installed by default, so all you need to do is install Network Manager:

[http://www.ubuntuforums.org/showthread.php?t=315860]("http://www.ubuntuforums.org/showthread.php?t=315860")

Or via Synaptic.

Get back with any queries or problems, or even better that you've managed to get it going!

Good luck!  Nick

---

### Post by spd106 on 2006-12-10
Hi, I understand your confusion since the screen shot was from dapper, not edgy. 

Just to check that you have an Atheros based wifi card you can go to System -> Admin -> Device Manager and look at the NIC details. If it is an Atheros card then it should be a simple matter of entering the settings.

You should go back to the networking menu, click on the properties button, then check the enable interface box and enter the settings.

---

### Post by simonfoley on 2006-12-11
reply coming to you from inside Ubuntu- Thanks guys :)

---

