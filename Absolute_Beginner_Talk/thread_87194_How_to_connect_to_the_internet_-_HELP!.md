---
title: "How to connect to the internet - HELP!"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by GabrielWolff on 2005-11-07
Hey!

I got  my modem today, and my ISP doesn't have technical support for linux

Now, I know

1) It's over cable
2) Their IP
3) My user and pass

What next?
I need a dialer, right? Where would I get it from? How to configure it?

Thanx

Gabriel

---

### Post by tonysathre on 2005-11-07
kppp is a linux dialer, use that, i think its under kmenu -> internet

---

### Post by Who on 2005-11-07
People are going to need some more details!

What make/model is the modem. Is it USB, internal, can you connect it to an Ethernet card?
If it is over cable and you have a modem then the odds are you need to connect the modem to the PC with ethernet, configure the modem (use the Windows Tech Support to find out how to do this...it hopefull won't need a Windows app) and then you may be good to go. I'm afraid I have ADSL not Cable. 
Basically, we need more info...

Perhaps look in System-->Administration-->Networing (Or something like that - I'm not on Ubuntu atm) to see whether your modem/ethernet card are detected and configured

Good luck

---

### Post by blastus on 2005-11-07
If its an external cable modem you shouldn't have to do anything to get it to work. All you should need is an ethernet card, plug the modem into it, and that's it. Now, your ISP may have to "renew" your IP address...I'm not sure exactly what that means but it seems like it has to do with assigning a static IP address to your machine. I only had cable Internet access once on someone else's machine and didn't have to do anything to get it to work in Fedora Core.

---

### Post by GabrielWolff on 2005-11-08
Thanx, guys.

It goes like this: I got an Ethernet (called eth0, I think).

The only thing I need is to configure it right (I guess). I need some place I can enter the user and pass, don't I. 

I wasn't able to find the kppp. Where could it hide? I got Ubuntu 5.04.

If I had WIN, I'd just dowload a dialer from the only page it lets me see so far, would install it, enter the pass and user (and maybe server IP or so) and off we go. where do I get that dialer from, or how can I build it?

Thanx

Gabriel

---

### Post by janne5011 on 2005-11-08
system-->administration-->Synaptic package manager--->search  in the package manager (there is a searchfunction) for "kppp",mark it, execute it and you have it installed:)




[QUOTE=GabrielWolff]Thanx, guys.

It goes like this: I got an Ethernet (called eth0, I think).

The only thing I need is to configure it right (I guess). I need some place I can enter the user and pass, don't I. 

I wasn't able to find the kppp. Where could it hide? I got Ubuntu 5.04.

If I had WIN, I'd just dowload a dialer from the only page it lets me see so far, would install it, enter the pass and user (and maybe server IP or so) and off we go. where do I get that dialer from, or how can I build it?

Thanx

Gabriel[/QUOTE]

---

### Post by GabrielWolff on 2005-11-09
I have en external cable modem. I connected with the ethernet cable.

I have managed to activate DHCP, and I got an IP eddress from the modem.

My problem is: Where the f*** do I enter my user and pass to the modem.

All the dialers (incl. kppp) ask for a phone number, which is irrelevant (cable!). I have tried to use PPPoE, which didn't work neither, the modem doesn't support it (I guess)

Thanx

Gabriel

---

### Post by blastus on 2005-11-09
I've never heard of a cable modem requiring authentication. You can usually only use the cable modem that your ISP either provided or sold to you. They know the MAC address of your ethernet card and they can certainly uniquely identify their modems. So they know who you are, so there is no need to require authentication. This is unlike dialup where you can basically use any kind of generic dialup modem and so they require authentication.

---

