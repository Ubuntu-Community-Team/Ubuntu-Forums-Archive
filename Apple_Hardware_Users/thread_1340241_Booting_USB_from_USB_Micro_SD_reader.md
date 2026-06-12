---
title: "Booting USB from USB Micro SD reader?"
date: 2009-11-28
forum: Apple Hardware Users
---

### Post by saleop on 2009-11-28
OK, soo... I put the 32bit version of the ubuntu install iso on a USB micro SD using [these instructions.](https://help.ubuntu.com/community/Installation/FromUSBStick) Everything went well until I tried to boot from the usb device, when the only boot option that showed up when i held down the alt key was my hard drive. Not really knowing what I was doing, I installed reefit, but it didn't acknowledge the device either. So what gives? Is it simply because it's a micro SD reader that I can't boot from it? Or is there something that I am missing?

I am using an early-2008 black intel Macbook with leopard v 10.5.8 btw, if you're wondering.
[ ]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by mrtomservo on 2009-11-28
In my experience it's likely the hardware you're using.  Like you said the card reader might just not work for booting.  I've tried booting off of MANY usb devices.  Usually memory card readers (CF/SD/etc) don't boot well in my experience.  If you can, try to boot using something else on USB and see if it finds it, preferably a thumb/flash drive.

---

### Post by saleop on 2009-11-28
I've burned it to a disk, but I get an "Uncompression Error - System Halted" message and it just freezes. NOW what could be the problem?

---

### Post by eltonw on 2009-11-28
> **saleop said:**
> OK, soo... I put the 32bit version of the ubuntu install iso on a USB micro SD using [these instructions.]("https://help.ubuntu.com/community/Installation/FromUSBStick") Everything went well until I tried to boot from the usb device, when the only boot option that showed up when i held down the alt key was my hard drive. Not really knowing what I was doing, I installed reefit, but it didn't acknowledge the device either. So what gives? Is it simply because it's a micro SD reader that I can't boot from it? Or is there something that I am missing?

I am using an early-2008 black intel Macbook with leopard v 10.5.8 btw, if you're wondering.


I am using an older (2005) Powerbook PPC, but this should work on your machine. Load the SD card (i.e. is should be visible in Finder. 

:arrow:Go to System Preferences, System, Startup Disk, (:!:the SD should be visible among the the systems listed: HD, Network, etc.) [FONT=Palatino Linotype][COLOR=DarkOrange]Highlight the SD, then select Restart.[/COLOR][/FONT]

Your machine should now reboot from the SD card.;)

HTH,
with cordial greetings from Montreal, CANADA.

---

### Post by saleop on 2009-11-28
I've tried this, and the SD card doesn't show up in the menu.

---

### Post by sgosnell on 2009-11-28
You may have a corrupt .iso, or the burn to the microSD card could be bad.  It happens all too frequently.  I've booted my laptop many times from a microSD reader, so it shouldn't be a problem.

---

### Post by saleop on 2009-11-28
But my macbook isn't even recognizing the micro SD reader at all. It shows up in finder and on my desktop, but it doesn't appear in the list of bootable drives. nor does it appear when pressing alt/option at boot. Doesn't that mean that there is something wrong with the device and not the burned image? or maybe something's wrong with my macbook?

---

### Post by linuxopjemac on 2009-11-29
Booting from USB is not supported by Apple. The only viable option is Firewire.

---

### Post by tom4everitt on 2009-11-29
> **linuxopjemac said:**
> Booting from USB is not supported by Apple. The only viable option is Firewire.

I see this statement a lot on the forum. What is the origin of this idea? I have installed OS X on my current macbook pro, as well as I've booted linux systems from usb.

And dear Google seems to agree with me :) :

[http://www.tuaw.com/2006/02/08/intel-macs-can-boot-from-usb-drives/](http://www.tuaw.com/2006/02/08/intel-macs-can-boot-from-usb-drives/)

---

### Post by linuxopjemac on 2009-11-29
you might indeed be successful with a GPT formatted USB drive:

[http://rentzsch.com/tidbits/intelbasedMacBootIncompatibility](http://rentzsch.com/tidbits/intelbasedMacBootIncompatibility)

---

### Post by tom4everitt on 2009-11-29
As long as you have rEFIt installed, my experience is that it's possible to boot any bootable USB. Perhaps the article is referring to native usb-boot support. Otherwise it is way off track, I have booted Unetbotin-formatted usb:s without problem.

---

### Post by saleop on 2009-11-29
Thanks, guys. I finally did get Ubuntu installed, but not from USB. I used a burned DVD+R. I still never figured out how to get this thing to boot from my USB micro SD reader, though :\

---

### Post by tom4everitt on 2009-11-29
Okay, good that the DVD worked, sad that the USB didn't.

I checked the guide and it simply says to dd the .iso onto the usb. I'm not entirely sure whether this is a working way. Usually you need to use a program for for putting .iso-files on usbs, such as unetbootin, liveusb-creator or similar (ubuntu has one installed per default, accessible from system->administration).

As I understand it, .img-files are better suited for dd-ing onto a usb. They're not always available however.

---

### Post by garlicsalt2 on 2009-12-13
> **saleop said:**
> OK, soo... I put the 32bit version of the ubuntu install iso on a USB micro SD using [these instructions.](https://help.ubuntu.com/community/Installation/FromUSBStick) Everything went well until I tried to boot from the usb device, when the only boot option that showed up when i held down the alt key was my hard drive. Not really knowing what I was doing, I installed reefit, but it didn't acknowledge the device either. So what gives? Is it simply because it's a micro SD reader that I can't boot from it? Or is there something that I am missing?

I am using an early-2008 black intel Macbook with leopard v 10.5.8 btw, if you're wondering.
[ ]("https://help.ubuntu.com/community/Installation/FromUSBStick")

I can answer the question about whether Macs support USB Booting.

Intel-based Macs SHOULD support USB Booting, although I don't have one to try it.
PowerPC (pre-2006 models) ONLY support booting from FireWire or internal hard drive, and even then if using firewire, it needs to have a certain chipset.

Also, from the post quoted above, it sounds as though the OP is copying the iso file to the SD card. This would have the same effect as burning the iso file to a cd. My brother tried something similar with an Ubuntu ISO image on a pc, then called me up 'cause he couldn't get it to boot This will surely FAIL.

Also, in order to boot from an external drive on a PC you need to have a bootloader on that drive. I'm not certain how it works on an intel Mac.

--Aaron.

---

