---
title: "confusing (for me) internet problem"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by Who_Knows? on 2005-08-02
All right, here's my problem.
I have just installed Ubuntu 5.04 a few days ago and I cannot figure out how to make my dial-up internet connection work.  I have been reading similar forums on here to try to find out what is wrong but nothing I've tried has worked for me.  Windows works just fine with it.

I have an internal  US Robotics 56K Voice PCI modem with the 2976-OEM number.
In XP it is on COM 3 so in Ubuntu that should be /dev/ttyS2 right? (I have also tried 0, 1, 2, and 3 and also /modem but those don't work either)
I used pppconfig-create a new connection to create a connection with the default name of 'provider'.  All of the information is correct that I can tell but when I type 'pon' or 'sudo pon' nothing happens.  I went through the system-administration-networking panel and entered the same information there but it still won't do anything when I click on 'Activate'.  I added the modem manager utiltity to my toolbar, but it has the exact same information as the networking panel and when I click activate there it asks me if I want to connect so I click connect and again nothing happens.  I have turned on the modem noises even so I should hear it connecting as well.  Also, when I click activate through the networking panel it immediately changes to active and the deactivate button lights up but I still cannot connect through Firefox and the Modem monitor says that I'm not connected.

So I'm wondering, is this a driver problem? I have looked for linux drivers for my modem but can't find any.

I obtained my information on how to set up a connection from the Ubuntu Wiki at [https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29) 

'lspci' gives the following information about my modem:
0000:00:0a.0  Serial controller: 5610 56K FaxModem 56K Faxmodem Model 5610 (rev0 1)

Any help you could give me would be appreciated.

---

### Post by neilbain on 2005-08-03
I might have got this very wrong but my understanding is that the USR PCI modems implement many of their functions in software (i.e. the driver).  Checking the USR web site confirms they only provide Windows drivers.  My guess is that your modem is not supported under linux.

A google search for appropriate USR linux drivers has drawn a blank... Sorry

Neil

---

### Post by ubuntp on 2005-08-03
Yes most PCI modems are basically software modems. You have the hardware to get the signal in your computer but that's basically it, the rest is done in software.

---

