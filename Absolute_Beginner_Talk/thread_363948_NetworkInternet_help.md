---
title: "Network/Internet help"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Ayanla on 2007-02-17
I have two window's XP PC's that connect to the internet via cable broadband. We use a Netgear network splitter, and both connect fine.

I have a third computer running Ubuntu.

If I plug the Ubuntu box into the splitter, one of the window's boxes will lose connection (not always the same one) No matter what series of resetting the router, rebooting, and plugging/unplugging I do, only two computers can be connected to the internet at once. The two window's machines, or one windows machine and the ubuntu machine.

I'm a networking idiot. Is it because I'm using a splitter versus a router? Is it something I'm setting up wrong?

My computers are not networked in the sense that they can see each other, share files, etc, they just both plug into the splitter and connect to the internet. That's all I'd like the ubuntu box to do as well.

Any ideas?

---

### Post by Ayanla on 2007-02-17
Heh, it would seem I'm an idiot for installing edgy as my first Ubuntu experience. I wasn't aware it was a test build. I think I'm going to try to get rid of edgy and install dapper and see if that makes any difference. Nothing like playing with an entirely different OS to make you feel like an idiot.

---

### Post by rccharles on 2007-02-17
> **Ayanla said:**
> I have two window's XP PC's that connect to the internet via cable broadband. We use a Netgear network splitter, and both connect fine.

I have a third computer running Ubuntu.

If I plug the Ubuntu box into the splitter, one of the window's boxes will lose connection (not always the same one) No matter what series of resetting the router, rebooting, and plugging/unplugging I do, only two computers can be connected to the internet at once. The two window's machines, or one windows machine and the ubuntu machine.

I'm a networking idiot. Is it because I'm using a splitter versus a router? Is it something I'm setting up wrong?



Could you provide the model number of your splitter.

What is the model number of your router?

Robert

---

### Post by Ayanla on 2007-02-17
Ok, so it wasn't the distro that caused it. I still have the same problem with 6.06. As soon as I get a connection on the Linux machine, one of the Window's machines fails to connect.

My modem is one provided by the cable company, a Motorola Surfboard model SBV5220. The splitter is a Netgear FS605, fast ethernet switch.

Like I said, networking is my absolute weakest point. Any help is greatly appreciated.

Setup is like this:

Cable Modem ~>Splitter ~> 3 PCs

Splitter is supposed to support up to 5 connections.

I do not have a router.

---

### Post by Ayanla on 2007-02-17
Well this is frustrating. I simply can't figure out what I'm doing wrong. The Ubuntu computer connects to the internet fine, both windows computers connect fine, and any combination of two connect fine, but it's impossible to get all three of them to connect at the same time.

Maybe I should just do away with Linux and put windows on the third box too :(

---

### Post by abuntoyoutoo on 2007-02-17
> **Ayanla said:**
> Maybe I should just do away with Linux and put windows on the third box too :(

Before you do that, try connecting all three computers, and enter the address [http://209.85.165.104/](http://209.85.165.104/) If this works (it will open the Google homepage), then Ubuntu is possibly creating a dns or ipv6 problem (which is fixable :)).

Also, it could be a good idea to check the settings of your splitter to see if anything is amiss.

To do that, open an Internet window and enter the address [http://192.168.1.1/](http://192.168.1.1/) This address usually leads to a login screen. Once logged in, it will have various options which can be changed to adjust the connection. Be careful though, as you don't want to put the wrong settings in and stop the internet working on all computers! Read the manual first.


Good Luck (I had heaps of problems with Internet when I started too :()

---

### Post by rccharles on 2007-02-18
> **Ayanla said:**
> Ok, so it wasn't the distro that caused it. I still have the same problem with 6.06. As soon as I get a connection on the Linux machine, one of the Window's machines fails to connect.

My modem is one provided by the cable company, a Motorola Surfboard model SBV5220. The splitter is a Netgear FS605, fast ethernet switch.

Like I said, networking is my absolute weakest point. Any help is greatly appreciated.

Setup is like this:

Cable Modem ~>Splitter ~> 3 PCs

Splitter is supposed to support up to 5 connections.

I do not have a router.

Please note, I am not a networking expert.  I'd say that I am a knowledgeable networking user.

The term splitter is confusing.  I believe it is an analog not a TCP/IP digital term.  In your case, you have a switch.  So, you have:

Cable Modem ~>Switch ~> 3 PCs

From what I read in:

SBV5220 Digital Voice Modem 
[http://broadband.motorola.com/catalog/productdetail.asp?ProductID=463](http://broadband.motorola.com/catalog/productdetail.asp?ProductID=463)

Netgear FS605
[http://www.netgear.com/Products/Switches/DesktopSwitches/FS605.aspx](http://www.netgear.com/Products/Switches/DesktopSwitches/FS605.aspx)

You are missing a router.  The Netgear FS605 article indicate that you need to attach it to a router before going to the internet.  The Digital Voice Modem article doesn't mention that it includes a router.

While I do not know a way of proving this, I suspect that your ISP is allowing you to connect two computer to the internet not three.  Do not know how one of your active computers gets bounced.

You need:
Cable Modem ~> Router ~>Switch ~> 3 PCs

Perhaps you can borrow a router from a friend and see what happens.  Also, you could post a question in  Networking & Wireless:

[http://www.ubuntuforums.org/forumdisplay.php?f=136](http://www.ubuntuforums.org/forumdisplay.php?f=136)

Please note, I am not a networking expert.  I'd say that I am a knowledgeable networking user.

Robert

---

