---
title: "Wireless Notebook card (Belkin)"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by schofield0212 on 2007-05-08
:confused: 
I am an absolute beginner to Ubuntu, but not to computers, and need some advice on how to get my Belkin Wireless G Plus Notebook Card to work. I know that Belkin do not support Linux (a pity). I will be installing Ubuntu on a Toshiba Satellite laptop using a dual boot system and it would be great to use wireless with Ubuntu.

---

### Post by AAM on 2007-05-08
there are two ways to get your card working, and both involve installing Ubuntu.
Try plugging the card in when the Ubuntu LiveCD is running and see if it is recognised. You might get lucky!

Then do a trawl of the web and UbuntuForums looking for specific evidence that this card can be made to work with linux. If you find specific information, get a copy and follow it! If you get conflicting information, follow each set of instructions on a clean install until you find something that works.

When you Install Ubuntu the card may be recognised immediately. If not you will need to know whether the card is actually recognised by typing in a terminal
> lsmod Now this is VERY daunting to the uninitiated as it gives a great long list of gobbledy-gook, but you just need to look through from the start and try to work out what is what. You might be able to find a list of native kernel modules on the net (things like islsm, ra, prism54, etc). Sometimes to get your wireless to work you need to blacklist some modules.


If all seems lost and there is no wireless module loaded, then you will need to go the **ndiswrapper** route. This is well documented in many places and included a series of commands as well as alteration to a number of system files. The installation is not hard but the troubleshooting can be a PITA! The steps are to install the ndiswrapper program (this in itself can be a problem if you don't have functioning wireless! (C&E!), then get it to wrap the Windows driver. Both the INF and SYS files have to be in the same directory for this to work (you can hear the voice of experience talking?!). But it's well documented and there's lots of help here.

Hope that gives you an overview of fixing the issue.

---

