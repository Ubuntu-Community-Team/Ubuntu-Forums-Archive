---
title: "Wireless Problems?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2006-12-31
So I heard I might have some problems with wireless internet if I plan on using Ubuntu. Is this true? The computer I want to install Ubuntu on is connected to the internet via a wireless router. Will I need to setup anything complicated right after installing Ubuntu to connect to the internet?

---

### Post by wireddad on 2006-12-31
The problem you may run into is the compatibility of your wireless card.  Try it with the livecd to see if it works first.

---

### Post by VoXoM on 2006-12-31
Hmmm.. I'm not home atm but yesterday when fooling around with the liveCD there was no internet connection, though I thought it was normal.

---

### Post by wireddad on 2006-12-31
Do you have both RJ45 and wireless?  Check to see which one is active under Ubuntu.  I had to do the same...disabled one, change the setting, and all good.

---

### Post by VoXoM on 2007-01-01
> **wireddad said:**
> Do you have both RJ45 and wireless?  Check to see which one is active under Ubuntu.  I had to do the same...disabled one, change the setting, and all good.

How?

---

### Post by l951b951 on 2007-01-01
> **VoXoM said:**
> So I heard I might have some problems with wireless internet if I plan on using Ubuntu. Is this true? The computer I want to install Ubuntu on is connected to the internet via a wireless router. Will I need to setup anything complicated right after installing Ubuntu to connect to the internet?

To help isolate my problems, I plugged my newly installed Ubuntu laptop into the router directly.  That way I could download updates and any packages I needed to get my wireless working.  

That being said, I beat my head against the wall for several hours trying to get my wireless working.  Finally I installed one of the Ubuntu official network connection managers (not sure which one it was off the top of my head) and it magically started working.  I could not be happier with the way it's working now.

---

### Post by VoXoM on 2007-01-01
> **l951b951 said:**
> To help isolate my problems, I plugged my newly installed Ubuntu laptop into the router directly.  That way I could download updates and any packages I needed to get my wireless working.  

That being said, I beat my head against the wall for several hours trying to get my wireless working.  Finally I installed one of the Ubuntu official network connection managers (not sure which one it was off the top of my head) and it magically started working.  I could not be happier with the way it's working now.

Well, I'm trying to get Wireless working on a desktop computer. I can't really move it to plug it in the router.. Currently dual-booting with Windows, now posting on Windows.

---

### Post by Tomosaur on 2007-01-01
Unless you tell us the name and model of your hardware, it's going to be difficult helping you. There are many ways to get wireless internet working, but without the basic information, it's hard to suggest anything.

---

### Post by Atomic Dog on 2007-01-01
When you click System-->administration-->Networking does the wireless adapter show up?  If yes then install Network manager [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

If it does not show up then you will need the make and model of the card.  Then so a search of these forums and see if people have gotten it to work with an experimental driver or using ndiswrapper.  You will likely find instructions on how to set it up.  Once done you can then use Network Manager to connect to your wireless network.

---

### Post by VoXoM on 2007-01-01
> **Tomosaur said:**
> Unless you tell us the name and model of your hardware, it's going to be difficult helping you. There are many ways to get wireless internet working, but without the basic information, it's hard to suggest anything.

I'm on the Ubuntu 6.10 edgy eft version. It's a netgear router with a belkin network card.. That's pretty much everything I know.

---

### Post by l951b951 on 2007-01-01
> **VoXoM said:**
> I'm on the Ubuntu 6.10 edgy eft version. It's a netgear router with a belkin network card.. That's pretty much everything I know.

Can you post the model number of the Belkin.  If you can't see it physically on the adpater, can you get any information about it from the device manager in windows?

---

### Post by VoXoM on 2007-01-01
> **Atomic Dog said:**
> When you click System-->administration-->Networking does the wireless adapter show up?  If yes then install Network manager [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

If it does not show up then you will need the make and model of the card.  Then so a search of these forums and see if people have gotten it to work with an experimental driver or using ndiswrapper.  You will likely find instructions on how to set it up.  Once done you can then use Network Manager to connect to your wireless network.

No. There is only Wired Connection and Modem Connection.

As for the Windows device manager, it says "Belkin Wireless Pre-N Notebook Network Card".

Sorry if all this sounds dumb to you, everyone once didn't know anything about something.

---

### Post by l951b951 on 2007-01-01
> **VoXoM said:**
> No. There is only Wired Connection and Modem Connection.

As for the Windows device manager, it says "Belkin Wireless Pre-N Notebook Network Card".

Sorry if all this sounds dumb to you, everyone once didn't know anything about something.

You don't have to apologize.  I'm a newbie, too.  I'm just very interested in helping get your wireless working because of my recent wireless troubles.  It is very frustrating.

Does your card look like this  [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=184399]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=184399")

---

### Post by VoXoM on 2007-01-01
> **l951b951 said:**
> You don't have to apologize.  I'm a newbie, too.  I'm just very interested in helping get your wireless working because of my recent wireless troubles.  It is very frustrating.

Does your card look like this  [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=184399]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=184399")

Yea its exactly this one if im not mistaken.

also, btw, just by curiosity I went to see Network Manager in the program list and it said it didnt support my type of computer (i386). Will this cause me a problem?

---

### Post by garwaymatt on 2007-01-01
I dont know if you are proficient with the command line, as it would help to find out the actual networking chip on the card. To do this, go to accesories, the terminal. You need to enter the command lspci, and then press enter. If you copy this data and post it up here then it would make it easier to find the drivers

---

### Post by VoXoM on 2007-01-01
How can I get a file I saved on Linux to Windows? I saved what lspci gave me but can't find a way to access it.

---

### Post by VoXoM on 2007-01-01
> **garwaymatt said:**
> I dont know if you are proficient with the command line, as it would help to find out the actual networking chip on the card. To do this, go to accesories, the terminal. You need to enter the command lspci, and then press enter. If you copy this data and post it up here then it would make it easier to find the drivers

nicolas@nicolas-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0d.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
02:00.0 Ethernet controller: Airgo Networks Inc Unknown device 0001 (rev 01)
nicolas@nicolas-desktop:~$

---

### Post by VoXoM on 2007-01-01
Still can't figure out what to do.

---

### Post by VoXoM on 2007-01-01
bump

---

### Post by wireddad on 2007-01-02
02:00.0 Ethernet controller: Airgo Networks Inc Unknown device 0001 (rev 01)

It definitely looks like it does not recognize your card.  Hopefully someone can direct you to a fix.

---

### Post by wireddad on 2007-01-02
How about this:  [http://gpl.airgonetworks.com/](http://gpl.airgonetworks.com/)

---

