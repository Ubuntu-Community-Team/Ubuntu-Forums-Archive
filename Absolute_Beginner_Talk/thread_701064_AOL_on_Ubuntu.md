---
title: "AOL on Ubuntu"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-02-18
So I am trying to switch my mom over from XP to Ubuntu so that I don't have to worry about her cold-booting everytime I leave Ubuntu up (XP dual boot), but one program that she relies on is America Online 9.0 (Yes, I hate AOL with a passion, but she still uses it for email and a few other things). Is there a way to get it to run on Ubuntu?  I tried calling AOL about it, broke their phone tree when it prompted the question Press 1 for Windows, Press 2 for Mac, and when I used the getHuman database to get someone, they asked what OS I was using and I kept it simple and said "Linux," to what I first heard a human-like expression of "wait, what's that?," then reverted back to their robotic line prompt on how to talk to a customer.

But yeah, I tried Wine, the AOL install booted me out, and cannot seem to find a way to get a OS X emulator to be able to run the Mac version of AOL on there. Oh, I'm using broadband, so I don't need a dial-up client, just the AOL software.

---

### Post by spiderbatdad on 2008-02-18
you could use vmware...put xp there and run aol...a lot of work for a funky service.

---

### Post by spacefreak86 on 2008-02-19
Okay, I looked for it on Synaptic and couldn't find it. Is it hiding somewhere?

---

### Post by Jay Jay on 2008-02-19
How do you want to connect to AOL, via an Ethernet router modem? If so, go [here ]("http://www.jarviser.co.uk/jarviser/linuxether.html")for an excellent guide that should get you up and running fairly quickly. If you're using a USB modem - click [here,  ]("http://www.jarviser.co.uk/jarviser/linuxusb.html")you'll find things slightly more difficult, but not impossible.

I suppose it all comes down to your connection route to the modem.

---

### Post by steveneddy on 2008-02-19
Uhhh - why don't you just go to [AOL.com]("http://www.aol.com/") and check your mail there.

Seems easy to me.

Why do you have to install something to check e-mail on AOL?

I remembered an old AOL screen name and signed on after not using for over 6 years.

I looks kinds like Yahoo mail, so maybe this is the answer.

The mail link is at the upper left of the screen.

---

### Post by spacefreak86 on 2008-02-19
I realize that my mom could just as easily just go on aol.com and enter in her password (if she's remembered it) and all that, but for god only knows what reason, she is determined to be tied to an archaic browser. Granted, I see her on my firefox more often (which I'm grateful for, but also maybe b/c I've deleted all the easy shortcuts to IE on the windows computers), but she still likes that AOL interface for some reason. As such, the interface can only be accessed through, yeah, the AOL software. 

Ubuntu is fine for me, because I don't mind learning the commands and all that, despite preferring the GUI system. One suggestion for it to be more "out of the box" would be those hardware / software installer wizards that come with Windows and occasionally Mac. I realize its open source and non-commercial (one of the great points of it), but Joe User typically relies on those wizards because they just don't want to be bothered with the technical details.

---

### Post by spiderbatdad on 2008-02-19
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)
this is vmware player...i think it is still in syanaptic, but I tink you also need vmware workstation...no longer free. I did this a few years ago. It worked. It was cool running a virtual machine...I could do all kinds of things to my Ubuntu virtual install without affecting my actual installation.

---

### Post by spiderbatdad on 2008-02-19
update: vmware server is in synaptic...the vmware player will act as a frontend.

---

### Post by steveneddy on 2008-02-19
> **spacefreak86 said:**
> I realize that my mom could just as easily just go on aol.com and enter in her password (if she's remembered it) and all that, but for god only knows what reason, she is determined to be tied to an archaic browser. Granted, I see her on my firefox more often (which I'm grateful for, but also maybe b/c I've deleted all the easy shortcuts to IE on the windows computers), but she still likes that AOL interface for some reason. As such, the interface can only be accessed through, yeah, the AOL software. 

Ubuntu is fine for me, because I don't mind learning the commands and all that, despite preferring the GUI system. One suggestion for it to be more "out of the box" would be those hardware / software installer wizards that come with Windows and occasionally Mac. I realize its open source and non-commercial (one of the great points of it), but Joe User typically relies on those wizards because they just don't want to be bothered with the technical details.

Maybe it's time for your mother to learn something new.

Sit down and teach her about Firefox and show her AOL.com and save the password so she won't have to remember it.

Old dogs _**can**_ learn new tricks.

:D

---

### Post by jrusso2 on 2008-02-19
Seems like instead of using Vmware you should be able to do the same thing with Virtual Box.  AOL has free software for broadband you can use if you don't use a modem to dial up to AOL

---

### Post by spacefreak86 on 2008-02-19
> **jrusso2 said:**
> Seems like instead of using Vmware you should be able to do the same thing with Virtual Box.  AOL has free software for broadband you can use if you don't use a modem to dial up to AOL

I got the following error with VirtualBox:


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Um, help?

---

### Post by spiderbatdad on 2008-02-19
I just installed the vmware-server from synaptic...did the registration, and its ready for an operating system...simple took five minutes. didn't even bother with vmware-player. the server put itself in system tools

---

### Post by Hmarroqu on 2008-02-19
> **steveneddy said:**
> 

Old dogs _**can**_ learn new tricks.

:D


Damn....not the right choice of words i think.


> **spacefreak86 said:**
> I got the following error with VirtualBox:


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Um, help?

[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/) 

*** Works on Gutsy also.

---

### Post by spacefreak86 on 2008-02-19
Following in to the letter, I get this message when I click on Settings in VirtualBox:

Failed to access the USB subsystem:


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

---

### Post by stchman on 2008-02-19
> **spacefreak86 said:**
> So I am trying to switch my mom over from XP to Ubuntu so that I don't have to worry about her cold-booting everytime I leave Ubuntu up (XP dual boot), but one program that she relies on is America Online 9.0 (Yes, I hate AOL with a passion, but she still uses it for email and a few other things). Is there a way to get it to run on Ubuntu?  I tried calling AOL about it, broke their phone tree when it prompted the question Press 1 for Windows, Press 2 for Mac, and when I used the getHuman database to get someone, they asked what OS I was using and I kept it simple and said "Linux," to what I first heard a human-like expression of "wait, what's that?," then reverted back to their robotic line prompt on how to talk to a customer.

But yeah, I tried Wine, the AOL install booted me out, and cannot seem to find a way to get a OS X emulator to be able to run the Mac version of AOL on there. Oh, I'm using broadband, so I don't need a dial-up client, just the AOL software.

AOL is not available for Linux.  There is the PENGAOL dialer, but that is about it.

I can think of no good reason to use AOL.  If you want email then AOL.com has FREE email addresses.  Pidgin is a multi protocol IM client.  You can get everything else.

One way to wean people off AOL and Windows is to not help them when they have problems.

---

### Post by spacefreak86 on 2008-02-19
> **stchman said:**
>  I can think of no good reason to use AOL..

I agree. I'll see if I can get her to switch to the internet-based mail client from AOL to get her email. I could care less though, I've got my yahoo and college email account.

---

### Post by stchman on 2008-02-19
> **spacefreak86 said:**
> I agree. I'll see if I can get her to switch to the internet-based mail client from AOL to get her email. I could care less though, I've got my yahoo and college email account.

Yes, you can get free email accounts from Yahoo, Hotmail, and AOL.  As a matter of fact, MyYahoo and MyMSN can act as a homepage for weather, email, news, TV listings, etc.

I forgot, there is a use for AOL.  My buddy uses it to meet girls over IM.

---

### Post by SunnyRabbiera on 2008-02-19
Well if she is familiar with firefox then tell her that firefox is available on linux too.
Honestly you should tell her that no matter how much she likes the interface of AOL she has to adjust and know how risky using AOL is as its based on IE.
It will be a learning process, but I was able to ween my relatives off of AOL

---

### Post by Jay Jay on 2008-02-19
> **stchman said:**
> Yes, you can get free email accounts from Yahoo, Hotmail, and AOL.  As a matter of fact, MyYahoo and MyMSN can act as a homepage for weather, email, news, TV listings, etc.

I forgot, there is a use for AOL.  My buddy uses it to meet girls over IM.

Really, does he meet any nice ones? :)

---

### Post by stchman on 2008-02-20
> **Jay Jay said:**
> Really, does he meet any nice ones? :)

He just meets girls.  That is all I am going to say about them.

---

