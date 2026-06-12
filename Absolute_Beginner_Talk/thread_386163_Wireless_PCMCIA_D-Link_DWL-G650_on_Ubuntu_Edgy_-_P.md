---
title: "Wireless PCMCIA D-Link DWL-G650 on Ubuntu Edgy - Problems :-("
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-03-16
Dear all

first of all... I am a noob when it comes to Linux. Please forgive me. If you have problems with chemistry I can help you back... but not with Linux....I installed it only one week ago on an external hard drive and I am playing around till the point I will feel comfortable to throw Windope into the garbage

I just plugged a PCMCIA Wireless adapter: D-Link AirPlus DWL-G650 H/W Ver:B5 F/W Ver:2.54 Made in China
The chipset should be an Atheros or something like that.
Edgy seems to recognize the card immediately (I see the card in the device manager and I see the wireless connection tab in the Administration>Networking GUI software)
The problem is that when I click on the Properties button for Wireless Connection and I check on "Enable Connection", as soon as I close the window the connection is not enabled anymore.
I have followed the guidelines of the help (installing the windows drivers with ndiswrapper-utils 1.8 from the liveCD) to no avail. Still doing the samee thing. And the funny thing is that the two LEDs on the card are blinking in syncronous. as if the card would be active.

Please help me with this since I can't connect Linux in my work network otherwise my netad is going to strangle me. And here in Toronto we have a wonderful free downtown-wide broadband wireless connection....

My laptop is an ECS G732 - ATI Radeon Mobility 9000 - 1 GHz RAM - 30GB HD

Kernel: I wouldn't know which version I have but I downloaded the iso image for edgy less than a week ago so I guess is the most updated version.

Cheers

Cippa Lippa

---

### Post by Griffiss on 2007-03-16
It sounds as though your drivers are installed fine - it may be an issue with network encryption. After installing ndiswrapper, my wireless didn't work until I found this howto: [http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)

Or you could try installing Network Manager. I didn't do that but it seems to be an oft-cited application for wireless problems.

---

### Post by SactoBob on 2007-03-16
The hardware compat. list [http://doc.gwos.org/index.php/D-LinkWireless](http://doc.gwos.org/index.php/D-LinkWireless) shows that your card works with the madwifi driver (in the restricted modules package).

Since you are good with madwifi, you don't need or want to be doing anything with ndiswrapper.  If you have installed a Win driver for your card with ndiswrapper, you should remove it, because you don't want two drivers fighting over your card. You should confirm that you have the madwifi driver by searching in the Synaptic Package Manager since it may not be installed by default, but probably is if your card was recognized.

You might try installing network-manager-gnome and see what it shows after clicking its icon in the upper right of the screen (after rebooting).  If your card is active, it should show all available connections and walk you through connecting.  You have to reboot after installing network-manager-gnome.

I like network-manager-gnome for my laptop since you just point and click on the network you want.  If you have connected before on that network, you don't have to do anything else.

---

### Post by Griffiss on 2007-03-16
This thread:
Edgy upgrade made Atheros wireless stop working
[http://www.ubuntuforums.org/showthread.php?t=290231](http://www.ubuntuforums.org/showthread.php?t=290231)

suggests that there are problems using madwifi in Edgy, and that using ndiswrapper solved them.

Also, if the device is working (check by inputting **iwconfig** in the terminal, and post results if you need someone to help you decipher the output), then is there any advantage to changing to madwifi at this stage?

---

### Post by SactoBob on 2007-03-16
I don't think that there are any general problems with Edgy and madwifi.  That is what I am using (Wistron Atheros + madwifi on Edgy)this very moment  - it worked out of the box with madwifi installed.  

The compat. chart does list one chip that won't work, but the specific card you have is listed as ok with madwifi.  I personally find madwifi very easy to install and very reliable.  I have another cardbcm43xx using ndiswrapper, and that is good too,

But if you use ndiswrapper, better blacklist the madwifi module since you don't want two drivers fighting over the same device.

You could use lspci (assuming a pci or pcmcia card) to get more info on the chip.
lsusb if it is a usb card.

If you want a slightly less portable solution that doesn't need ANY drivers and is sure fire and will provide you with 4 ethernet ports, look at this for $60 (better reception than any card I know, but consumes more power) [http://www.newegg.com/Product/Product.asp?Item=N82E16833162168](http://www.newegg.com/Product/Product.asp?Item=N82E16833162168)

---

### Post by Cippa Lippa on 2007-03-17
Dear all

can you point me where I can see how to remove the ndiswrapper drivers and make sure that I have the madwifi? Sorry guys for being so noob...
And remember I have no internet connection at all via Linux
I am going to install now network manager gnome  after having downloaded all the dependencies.....

Thanks guys. Hope this kind of stuff wil be solved soon by the devs because this is freaking scary for people coming from Windows. 

Thanks a lot guys

Cippa


> **SactoBob said:**
> I don't think that there are any general problems with Edgy and madwifi.  That is what I am using (Wistron Atheros + madwifi on Edgy)this very moment  - it worked out of the box with madwifi installed.  

The compat. chart does list one chip that won't work, but the specific card you have is listed as ok with madwifi.  I personally find madwifi very easy to install and very reliable.  I have another cardbcm43xx using ndiswrapper, and that is good too,

But if you use ndiswrapper, better blacklist the madwifi module since you don't want two drivers fighting over the same device.

You could use lspci (assuming a pci or pcmcia card) to get more info on the chip.
lsusb if it is a usb card.

If you want a slightly less portable solution that doesn't need ANY drivers and is sure fire and will provide you with 4 ethernet ports, look at this for $60 (better reception than any card I know, but consumes more power) [http://www.newegg.com/Product/Product.asp?Item=N82E16833162168](http://www.newegg.com/Product/Product.asp?Item=N82E16833162168)

---

### Post by Griffiss on 2007-03-17
You can use System > Administration > Synaptic Package Manager to remove ndiswrapper. Scroll down or search for ndiswrapper. The green boxes indicate that a package is installed. Click the green box, select 'Mark for removal', click the 'Apply' button on the top.

I don't know about madwifi - have you tried searching the forums for it? or searching for your card type?

---

### Post by Cippa Lippa on 2007-03-17
I am about to give up guys, I mean I installed all the dependencies for the network manager, network manager gnome and wpa supplicant and i rebooted. No error messages whatsoever. At reboot the software appears as installed from the Add/Remove Program but is not available as a launcher so I can't launch it.
In addition to this very frustrating situation the PCIMCA card is not doing anymore the synchronous lights that it does when is properly recognized. I guess one of the dependencies I installed screwed up the driver of the card or something like that.

I mean I am a total noob but this seems to me worse than Windope. Especially considering nobody seems to understand rationally how to get these wifi cards to work - because in that case I could just read something , study and get it to work. I mean it shouldn't be magic.

Ok sorry for the burst of anger. I really love the principles of linux but these things make it unapproachable by most people - including me, it seems :)

anyway, if it happens to you to have a great idea on how to solve this problem please let me know. Consider that I have dual-boot windope-Ubuntu Edgy and that I can connect to internet only via windows.

Thanks so much guys, you are really great. I just need this last piece of equipment to work and then I am indipendent... I just need a d*mned  Internet connection... pfffff....

Cheers

Cippa

---

### Post by Cippa Lippa on 2007-03-17
Dear All

I am proud to announce I have a F*eaking AWESOME connection from my UBUNTU Edgy with the D-Link G650. It was just sufficient to uninstall the network manager and the network manager gnome and to uninstall also the ndiswrapper utils and common. In addition I had to name the network in the Networking GUI interface. 

The network was picked up in the background

This is AWESOME. The only bad part is that I can see nowhere if I am connected or not... not to read to to get the hang of this via terminal... since network manager seems to screw up everything.

With this I can confirm that the D-Link G-650 card I am using (the H/W and F/W numbers are in my first post in this thread) works on the latest Ubuntu Edgy more or less out-of-the-box... but only if you are not a TOTAL noob like me

Cheers guys - happy S.Patrick day and ... YOU ROCK!

Cippa

---

### Post by Griffiss on 2007-03-17
Glad to hear it Cippa :)

There must be a more elegant way, but the way I tell if I'm connected is to try to open an internet page in the web browser

---

