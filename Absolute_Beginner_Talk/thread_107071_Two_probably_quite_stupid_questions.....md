---
title: "Two probably quite stupid questions...."
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by rikoshay on 2005-12-22
Hi,

1. I'm new to linux and have been using Ubuntu on my desktop and laptop for about a couple of weeks now and enjoying it short of one annoyance - the wireless on my laptop. 

The laptop is an Acer Aspire 5021 WLMi. I gave up trying to configure the onboard broadcom chipset. Although I could install the driver and detect the hardware with ndiswrapper I found it impossible to find anyway of actually switching the damn thing on: so i moved to plan B. I had a spare Netgear WG511T PCMCIA card lying around which reportedly works 'straight out of the box' with the bundled madwifi drivers. Now I'm sure it does, however the laptop doesn't seem to detecting the hardware even though the card is plugged in and the light flashing (a great improvement on the onboard broadcom which has always remained resolutely dead unless I boot into windows - yuk). I've posted several times and followed every madwifi how to but I'm sure the problem is Ubuntu simply not picking up it's presence. I think I've confirmed this by downloading the drivers and trying to install them using ndiswrapper which tells me the hardware is not present. Do I need to mount the PCMCIA card or something? Please help as I love using Ubuntu but having no wireless is a major downer and my flatmate is laughing at me as I've spent hours trying to get it to work:( 

2. The chip in my laptop is an AMD Turion but I'm using the 386 version of Ubuntu. This is principally because the 64 bit version I downloaded first kept hanging during installation. I also thought the 386 version would be more 'compatible' with various pieces of hardware and software. I quite probably made this up in my head. The desktop is running an Athlon 2400XP and also has the 386 version. Again because of my 'compatibility' idea - which I'm sure is rubbish. Can anyone enlighten me.

Appreciatively,

Rik

---

### Post by derbaschti on 2005-12-22
Hi, I had a similar problem with a PCMCIA wireless card. The problem turned out to be that the card was not present when I installed Ubuntu and was consequently not detected. Although I tried almost everything, the final solution was to reinstall Ubuntu with the card plugged in...

---

### Post by rikoshay on 2005-12-22
Thanks but I've tried that several times and no dice:( Could it be a conflict with the onboard wireless?

---

### Post by fordfan753 on 2005-12-22
I have a WG511 - not WG511T, but I had a bit of trouble with it. It seems that within some netgear models they changed the chipset without changing the model number, or even the look of the card! This is pretty stupid, but if you can't get the madwifi driver to work (and you've modprobed stuff till you can't modprobe anymore :P) it might be an idea to try NDISwrapper with the Windows driver for the card. Yeah, this is probably not the best way to do it, but if it works...

---

### Post by rikoshay on 2005-12-22
I've tried this by installing the card on the windows partition, copying the drivers across and using ndiswrapper. Ndiswrapper installs the drivers but fails to detect the hardware hence my assumption that ubuntu is not recognising that there's a PCMCIA card there. Is there anything I can do to check this?

---

### Post by fordfan753 on 2005-12-22
Take the card out, then sudo dmesg. That will dump what the kernel's been up to into your terminal. Then plug the card in, and run sudo dmesg again. It should say somewhere if it picked up the card, if nothing comes up try 5-10 seconds and try again, because sometimes it can take a while to recognise new hardware.

Also, with it plugged in you can use sudo lspci to see if it's being seen by the kernel.

---

### Post by rikoshay on 2005-12-22
OK here goes. On running sudo dmesg I can't see any reference to PCMCIA or wlan, just the eth0 that I'm running off at the moment. Unplug the card and plug it back in and I get this message at the end:

 PCMCIA: socket d98f1c2c: *** DANGER *** unable to remove socket power

sudo lspci only sees:

Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
(my on board wireless that doesn't work because I can't switch it on) and
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

Any further ideas from the floor?

---

### Post by jimrz on 2005-12-22
do you have a BIOS setting that will disable your onboard broadcom? it appears to be seeing only that and not your netgear card.

---

