---
title: "Connecting ROKR E2 on Ubuntu."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Xummoner on 2007-01-24
Hi guys, here I am again with another one of my issues...
Well, let me explain some things before posting my actual question:

I have a Motorola ROKR E2 phone, which can be detected as 3 different devices (USB Modem, USB Net and Removable storage device). In Window$ I could browse my phone files (same structure as Linux with /usr, /bin, /home, and those folders), sounds logical since the phone is powered by java-linux. But on Ubuntu I can only get it to work as a removable storage device.

I need to be able to access my phone files since there are some things I need to configure, but Ubuntu won't detect it in modem or USB Net modes. Again as an example, in windows I would just go to the explorer, type my phones IP adress (got it by typing IP config on windows console thingy) and voila, I could browse thru my phone's files, open them with a text editor and edit them. There was also something called Samba and Telnet, but I can't really tell much about it since I don't even know how they work or what they are.

So, here's my question (finally):

-Is there a way I could make Ubuntu detect my phone? Or being able to see if Ubuntu detects it as something else when I connect it, or if by any chance someone knows what program could I use to browse my phone files...

---

### Post by ewankho on 2007-01-24
I use moto4lin to acces my motorola phone files. I have an old phone, not sure if it will work with your phone.

---

### Post by Xummoner on 2007-01-24
Thanks for the quick reply, I'll try that right away.

Edit.
Just downloaded Moto4lin from sourceforge, but well... How do I install it? 
(I don't even know if it would completely work anyway, since my phone is EZX and not P2K) But I have to give it a try.
It would be better finding a way to access my phone using it's IP adress on the refgular browser (Nautilus?)

Edit 2.
Ubuntu is actually detecting my phone in USB Net mode, I was looking at the device manager and it shows as Motorola USBLAN (just in case that helps).

---

### Post by ewankho on 2007-01-24
I installed Moto4Lin using Synaptic, you could try to install it from there. If it doesn't come out in the search result you may need to add other repositories (universe?).

I looked at the Moto4Lin [wiki]("http://moto4lin.sourceforge.net/wiki/Category:Models") and it seems your phone model has not been tested with the program so...

---

### Post by Xummoner on 2007-01-25
Can't seem to find it on Synaptiic, found another one called Kmobiletools but I can't seem to find a manual or something to configure it well and see if it detects my phone.

The "fun" thing is that Ubuntu detects my phone in it's 3 modes as: Removable storage device, Motorola GSM Modem, and Motorola USBLAN, I'm still trying to figure out how to use 'ifconfig' and see if the console displays my phone's IP adress.

---

### Post by Coburn on 2007-03-28
You might be used to the processes that Windows users call "downloading a driver for your phone" or "installing Motorola PhoneTools".  You have to find, install, configure, and learn to use the programs that let you see and manipulate files on your phone.  

A good place to start is with Synaptic Package Manager.  The standard program you need, moto4lin, is not in the default setup for Synaptic.  You have to "add the universe repository" and then it will show up and you can download and install it.  At least I think it's in Universe.

Rather than my explaining this to you, search the forums for a HowTo on adding repositories.

There are several programs available.  Kmobiletools is more Windows-like, and  works for some things, like syncing your contacts, and moto4lin is more like a file explorer, which works for other things, like pictures and ringtones.  If you want to install games, you have to do it through Bluetooth or get a Java uploader, like from the moto4lin site.

Multisync is developing a plugin that works for Motorola phone, but it is still in development and unsafe.  When it is released, it should have calendar access.  Gammu is a good choice that is slightly better than Kmobiletools for me, but you have to have more experience to install it.  I think it was Gammu that messed up my "drivers" so that the phone won't recharge right through the USB cable.

There is good help for moto4lin on their sourceforge.net homepage.

---

