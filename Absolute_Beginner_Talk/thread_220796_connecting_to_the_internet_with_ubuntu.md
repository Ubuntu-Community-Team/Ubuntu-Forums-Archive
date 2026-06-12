---
title: "connecting to the internet with ubuntu"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Micik on 2006-07-22
I placed internal modem into my computer on which ubuntu linux is installed and want to connect to the internet. How to set-up my dial-up connection step by step?
Thanks

---

### Post by goodfren on 2006-07-22
> **Micik said:**
> I placed internal modem into my computer on which ubuntu linux is installed and want to connect to the internet. How to set-up my dial-up connection step by step?
Thanks
I think you can find the wizard under system - Administration - Nerwork Tools or Networking.

---

### Post by Micik on 2006-07-22
Thanks but that doesn't help me much.
I have modem with conexant chip. In device manager of ubuntu I see that modem as HFC modem, so I think it's OK
I go to Administration->networking, choose pp0 and enter number which I want to dial. It cannot detect modem port so I choose one of existing something tty0 or similar.

Please, I'm new to linux, in windows I create dialup connection and clikc dial to dial number to ISP. Where I can create connection in ubuntu? Where to click dial to strat dialling to ISP?

If I execute this command:
sudo lspci
I get this in response:

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
0000:00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
**0000:00:0d.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)**
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)


As you can see ubuntu see my modem, at least informations about it are same as in Win XP.
How to connect and what program to use?

---

### Post by editrix on 2006-07-22
> **Micik said:**
> Thanks but that doesn't help me much.
I have modem with conexant chip. In device manager of ubuntu I see that modem as HFC modem, so I think it's OK...

If I execute this command:
sudo lspci
I get this in response:

**0000:00:0d.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)**

As you can see ubuntu see my modem ...

Because it can see your modem, it doesn't mean it can *use* it. Have you read the Dialup modem HowTo? 
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

I did a search of the forums on your modem and got 22 hits:
[http://www.ubuntuforums.org/search.php?searchid=6922143](http://www.ubuntuforums.org/search.php?searchid=6922143)
but I didn't read all the posts :-)

---

### Post by Micik on 2006-07-23
Ok guys,
I didn't manage to make my modem work, so interent connection by dial up is out of question. Since I have network card, I want to try to connect my linux machine with win XP machine and to connect to the internet via windows XP machine. Is this possible?
When I connect machine with LAN cable I see my windows computer in network but cannot access it. Also I can ping it.
Please can you explain me or at least give some useful link with explanation how to make coonectio through network between Win and Linux?
Thanks

---

### Post by GuitarHero on 2006-07-23
While I dont think thats the best option... how you would do it is enable the ethernet connection in the network dialouge, choose DHCP under properties also.  It should work on the ubuntu end.  For the Windows part of it you need to bridge the dialup and ethernet connection.  Ive done it with wifi but not dialup.  Look in network connections and select ethernet and dialup, right click and hit bridge.  Then while you are connected on the windows machine you should be on the ubuntu one too!  You may have to enable incoming connections on the windows box too, by setting up an advanced connection with the new connection wizard.

---

### Post by yman on 2006-07-23
hello, I'm new to ubuntu. I have an old laptop on which it is runing. ubuntu doesn't recognize the existance of my LAN + Modem PC card (3com megahertz model 3CCFEM556 B). I tried to connect the external DSL modem via USB, but it didn't work (on the computer side. the modem had all the proper lights on). I tried some of the trobelshooting of the service provider, but it was no use. however, Ubuntu recognized the DSL modem as being an ethernet connection.

another question: I have a desktop with windows XP, How do I create a home network with it and use the internet through it and share files?

---

### Post by yman on 2006-07-27
forward to my first question: in the device manager ubuntu recognizes the existance of the external modem and the LAN card, but doesn't know what they do and how to use them and can't read all of the information about them.

---

### Post by HerbAlpert on 2006-10-22
Yman: There is a problem with your 3COM LAN+Modem card on Ubuntu. But this might give you a clue to how you can work around it:
[http://ubuntuforums.org/showthread.php?t=238073]("http://ubuntuforums.org/showthread.php?t=238073")

---

### Post by sdubois92 on 2006-10-22
why the hell are you using dial up?

---

### Post by Redache on 2006-10-22
> **sdubois92 said:**
> why the hell are you using dial up?

Because not everybody in the world has access to a Broadband ready phone line.

I'll reiterate the point of, just because it's in the Device Manager doesn't mean Ubuntu knows how the thing works, it just knows it's there. Try the HowTo previously posted and see if that works.

---

### Post by laosboyme on 2006-10-22
System>admin>Network tools](*,) ](*,) ](*,) ](*,) I'am so dumb,, maybe it wont work....I'am using my modem ubuntu will auto detect youre modem..we'll Just trying to help.

---

### Post by _duncan_ on 2006-10-22
It's probably a software modem. If that's the case, you will have to find a suitable driver for it, or compile one yourself. Redache gave you a good link to follow. Here are a couple more:

[How to Conexant and Smartlink modems]("http://www.ubuntuforums.org/showthread.php?t=190728")
[linmodems.org]("http://www.linmodems.org")

P.S. I have to warn you in advance that it's not going to be easy. I got mine working, but it's a totally different chipset from your modem so I can't help you with the specifics.

---

### Post by yman on 2006-10-23
> **HerbAlpert said:**
> Yman: There is a problem with your 3COM LAN+Modem card on Ubuntu. But this might give you a clue to how you can work around it:
[http://ubuntuforums.org/showthread.php?t=238073]("http://ubuntuforums.org/showthread.php?t=238073")

[SIZE="4"]thank you for your help - I finally have internet on ubuntu after long miserable months!:-D :-D :-D[/SIZE]

---

