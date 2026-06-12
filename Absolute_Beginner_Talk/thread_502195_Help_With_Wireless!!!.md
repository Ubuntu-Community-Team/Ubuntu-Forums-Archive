---
title: "Help With Wireless!!!"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-07-16
i needed help with wireless when i first installed ubuntu, and i got my card (broadcom bcm4318 ) working under ndiswrapper, but everytime i turn it on (the computer is a laptop), i have to disable (using fn +f2) and enable the wireless card for it to work, is there any way to make live happly, or do i have to live with it? maybe a way to make the hardware restart of the card happen automaticly?

---

### Post by linuxwizard on 2007-07-16
May be something here that will help

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29)

---

### Post by ITdrummer on 2007-07-16
Well,    I too am new to linux and for 2 weeks i battled with my broadcom chipset, belkin wireless card.  I could get it working but the functionality of it was very buggy and unreliable.  I was informed by one of the more experienced ubuntu users that broadcom chipsets on wireless cards have horrible support in Linux/Ubuntu.  I know this is a little drastic but i would recommend getting a wireless card with either an Atheros or Prism chipset, as they are nothing short of "plug-and-play" in Ubuntu.  I Bought a d-link DWL-G650 108Mbps wireless card and it was miraculously easy. 

Im not sure if you are in the market for a new card, but i would definately recommend getting a card with one of those chipsets.

Hope my advice helps.

---

### Post by kevin11951 on 2007-07-20
i would get a new card (if its not to much money) but i dont know what to get for my laptop... specs are:
Dell B130
and Broadcom BCM4318 wireless card fits in it... thats all i know about the slot.

---

### Post by ITdrummer on 2007-07-21
do you have integrated wireless or a wireless card via pcmcia?  Just do some research on the internet and find out what cards use the prism and atheros chipsets.  My card has 108Mbps capabilities, runs great, and it only cost me $43.  Go for it, you will be happy you did.

---

### Post by kevin11951 on 2007-07-21
i have intergrated wireless, but i dont know what to look for... is it mini-pci?? also is intel "plug and play"? here is a pic of my wireless card, what can you tell me from that? [IMG]http://ubuntuforums.org/attachment.php?attachmentid=38788&stc=1&d=1185074111[/IMG]

---

### Post by ITdrummer on 2007-07-23
I will admit, i know little about integrated wireless with Linux.  Maybe someone else with a little more knowhow could chime in...?  sorry

---

### Post by mlentink on 2007-07-23
The picture looks like a built in card. But that shouldn't be too much of a problem, because you should be able to disable it in bios-setup. I agree with ITDrummer: get yourself a PCCard (PCMCIA) Wireless with Atheros or Prism chipsets. Getting those to work is a no-brainer

---

### Post by ITdrummer on 2007-07-23
> **kevin11951 said:**
> also is intel "plug and play"? 

If your using a broadcom chipset....absolutely not.  Broadcom chipsets are horrible in Linux.

---

### Post by pearlie on 2007-07-23
Nah - that's a minipci card - you can just reef it out and throw another one in, it's easy-peasy.  Unplug your power cord and remove the laptop battery.  See the little chrome clips that hold on to the divots on the side of the card?  Pull them outwards a little with your thumbnail, and the card will pop up.  Pull off the white wire - by the connector, not the wire - and you should be able to pull your card right out of the socket.  Make sure you only touch the edges of the card, and you should really use a static-control wristband or take other measures to make sure that you don't impart a static charge to the card.  Do the same thing in reverse with your new card.  

Here's a link to the [man page from Dell, with pictures]("http://support.dell.com/support/edocs/systems/ins1300/en/sm/upgrades.htm#wp1084976").

---

### Post by urvaksh on 2007-08-03
Kevin, can you please tell me how you got the card to work with ndswrapper. I have a DWL-G650M card. It works in windows, but it won't in Ubuntu.
I tried downloaded the driver from the disc using ndswrapper. It says the driver is downloaded, but it doesn't indicate it and none of the lights on the card light up.
If anyone else can help me on this as well, I'd appreciate it.

---

### Post by anfractuosities on 2007-10-15
[QUOTE=Ii would recommend getting a wireless card with either an Atheros or Prism chipset, as they are nothing short of "plug-and-play" in Ubuntu.  I Bought a d-link DWL-G650 108Mbps wireless card and it was miraculously easy. 
.[/QUOTE]

I have a belkin f5d9010 with an atheros chipset, and am having a hell of a time...I need much help

---

### Post by urvaksh on 2007-10-17
I still haven't been able to get my DWL-G650M to work with my cable modem when booted into Ubuntu. It works fine when I'm in Windows.
Will someone please tell me in simple english what I can do to fix this.
Thanks

---

