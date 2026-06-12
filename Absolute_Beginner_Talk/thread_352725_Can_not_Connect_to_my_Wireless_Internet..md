---
title: "Can not Connect to my Wireless Internet."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Dr. Drone on 2007-02-03
Hello again Ubuntu Members.

Thanks for your help in my last thread, I have now got Ubuntu installed successfully and got the Dual-Boot to work. 

But now I need help on connecting to my Wireless Internet through Ubuntu. I whent into the "Network Manager" thing and my Wireless Card was there (2 cards) and then I entered the name of my Router and entered the code and then clicked "Enabled". After this, I opened the Web Browser to check if everything was working and nope, when I tried Google, it couldn't Connect.

So basically, how do I get Ubuntu to Connect to my Wireless Internet?

Many thanks.

---

### Post by mikewhatever on 2007-02-03
They say, depending on the card, sometimes you it needs troubleshooting. [HERE IS THE GUIDE]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless")
If you can't figure it out, you might want to specify what card it is.

---

### Post by thenetduck on 2007-02-03
You might need to install the windows version drivers. You can do this with "ndiswrapper" Look that up. What kind of wireless card do you have? 

 The Net Duck

---

### Post by Dr. Drone on 2007-02-03
I have a NETGEAR DG834G.

---

### Post by Dr. Drone on 2007-02-03
Any more help?

Sorry for Double Posting, it's just that I have to go in a few Hours.

Also, my friend told me to sudo apt-get my Drivers? What is this and how do I do it?

---

### Post by Dr. Drone on 2007-02-03
ARRRGH.

I can't even get my Windows Media Center to load now, it just restarts once I pick it from the Boot Menu.

Life just isn't going my way today. ='(

---

### Post by Dr. Drone on 2007-02-03
*bump*

I'm sorry for being a complete idiot at this, I thought it would be easy, I was wrong. Same thing happened when I tried Linspire, but the only reason they wouldn't Connect was become Linspire v5.0 can't Connect to Wireless Connections over 11mbps (Mine is 54mbps).

If you could please help me, all I want to know is how to get my Internet working so I can start using Ubuntu. Don't tell me to download Drivers because how am I meant to download Drivers when I can't even get onto the Internet.

Many thanks.

---

### Post by Dr. Drone on 2007-02-04
Any Help?

---

### Post by xSauronx on 2007-02-04
> **Dr. Drone said:**
> I have a NETGEAR DG834G.

that model is a router, not a wireless card. 

what wireless adapter is in your pc or laptop? is it a built-in solution to a laptop? a usb adapter? a pci card? 

did you try googling or searching for the forums for *that* specific adapter (generally if its supported, searching by the model for linux support can get you what you need) 

also, since you *can* clearly get onto the internet, you might have to find what you need from where youre posting and save whatever drivers and documentation you can find to a flash drive or a cd-r

any way you can move the wireless router near the pc and just use ethernet to get started if you need to?

youd get more help if we had some more info to go on, as was already mentioned :)

---

### Post by Dr. Drone on 2007-02-04
Well I can't find out what the Card is because like I said earlier when I try to go into Windows it just restarts automatically. =/

It was a Ralink something or other.

Also, could someone explain to me how to sudo apt-get the Drivers, my friend said that might work.

Also, how do I install ndiswrapper? Will that help?

---

### Post by Dr. Drone on 2007-02-04
Ah, I think I got my Chipset thing, I typed "lspci" in the Terminal and got:

RaLink RT2561/RT61 802.11g PCI

Is this it?

---

