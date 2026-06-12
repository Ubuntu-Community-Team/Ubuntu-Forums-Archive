---
title: "Linux Ubuntu Help Please!!!"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by chris301up on 2007-10-07
I am completely new to the Linux world and am now stumped.

I have installed Linux Ubuntu 7.04 together with Windows XP as dual-boot just in case things go wrong.

Unfortunately I do not know how to install my Mercury card so that I can access the internet.

I have tried to install 'ndiswrapper' but simply do not know how to do it.

Can anyone please advise??

Thanks

---

### Post by williamwade on 2007-10-07
Is it some sort of wireless network card?

can we have model numbers please?

---

### Post by overdrank on 2007-10-07
> **chris301up said:**
> I am completely new to the Linux world and am now stumped.

I have installed Linux Ubuntu 7.04 together with Windows XP as dual-boot just in case things go wrong.

Unfortunately I do not know how to install my Mercury card so that I can access the internet.

I have tried to install 'ndiswrapper' but simply do not know how to do it.

Can anyone please advise??

Thanks

Hi and welcome, please post the output of the command ```
lspci
```
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by chris301up on 2007-10-07
Thanks for your reply.

I have looked into Applications>Accressories>Terminal and it displays the following: chris@chris-desktop:~ $

Don't know if this helps?

The wireless card is a Mercury KOP WL430 PCI Adaptor.

Regards

---

### Post by startherepodcast on 2007-10-07
Hi, just open uphe Terminal like you did, and after that carp with your username  and a $ in it type lspci and hit enter. Some text should come up, select, right click and select copy, then paste what you now cpoied into a new post!

---

### Post by n3tfury on 2007-10-07
> **chris301up said:**
> Thanks for your reply.

I have looked into Applications>Accressories>Terminal and it displays the following: chris@chris-desktop:~ $

Don't know if this helps?

The wireless card is a Mercury KOP WL430 PCI Adaptor.

Regards

what star is trying to say is type lspci after "chris@chris-desktop:~ $".  it should look like this

**chris@chris-desktop:~ $lspci   **    

then  hit enter, copy the information it gives you and paste it in your next reply.

---

### Post by chris301up on 2007-10-07
Have done that and I get the message "command not found"

Must be doing something wrong??

Can I switch between Windows and Ubuntu as it is a bit of a problem keep having to re-boot pc into Windows to access internet???

Could email details if prefered to [email]cj004e0293@blueyonder.co.uk[/email]

Regards

chris

---

### Post by n3tfury on 2007-10-07
> **chris301up said:**
> Have done that and I get the message "command not found"

Must be doing something wrong??

Can I switch between Windows and Ubuntu as it is a bit of a problem keep having to re-boot pc into Windows to access internet???

Could email details if prefered to [email]cj004e0293@blueyonder.co.uk[/email]

Regards

chris

you must be typing it wrong. 

[http://www.bitbenderforums.com/~grogan/kernhowto/lspci.gif](http://www.bitbenderforums.com/~grogan/kernhowto/lspci.gif)

---

### Post by overdrank on 2007-10-07
> **chris301up said:**
> Have done that and I get the message "command not found"

Must be doing something wrong??

Can I switch between Windows and Ubuntu as it is a bit of a problem keep having to re-boot pc into Windows to access internet???

Could email details if prefered to [email]cj004e0293@blueyonder.co.uk[/email]

Regards

chris

Ok I am assuming this is a wireless issue? Or are you using a wired connection?

---

### Post by n3tfury on 2007-10-07
> **overdrank said:**
> Ok I am assuming this is a wireless issue? Or are you using a wired connection?

> **chris301up said:**
> 

The wireless card is a Mercury KOP WL430 PCI Adaptor.

Regards

^^^^^^^^^^^^^^^^^^^^^^^^^^

---

### Post by Daveth on 2007-10-07
having chased it down it is a 
KOB WL430 IE1EE 802.1b Wireless Cardbus/PCI Adapter

manufactured by Mercury computers. It does not look to be here

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

but I'll keep hunting for you

---

### Post by chris301up on 2007-10-07
Ok. I have finally got the details you asked for:

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
00:0a.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
00:0a.1 Communication controller: Rockwell International Riptide HCF 56k PCI Modem
00:0a.2 Input device controller: Rockwell International Riptide PCI Game Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)


Other details from lspci -v | less are:

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 0314
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 1314
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 2314
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 4314
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 7314

Trust this helps???

Chris

---

### Post by Daveth on 2007-10-07
oh, you just beat me to it!  A French Mandriva user posted that it uses the  Realtek 8180L chipset which is the thing we have to drive.

---

### Post by Daveth on 2007-10-07
looks like you can drive that chipset with ndsiwrapper under Debian, so should work here.

[http://www.zoxx.net/notes/index.php/2006/11/24/31-realtek-8180l-with-ndiswrapper-on-debian-gnu-linux](http://www.zoxx.net/notes/index.php/2006/11/24/31-realtek-8180l-with-ndiswrapper-on-debian-gnu-linux)

looks a little invloved though!

---

### Post by ayenack on 2007-10-07
Have a look at this.

[https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L)

Should do the trick.

---

