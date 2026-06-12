---
title: "Networking Help"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by zjgz on 2005-11-20
I just installed Ubuntu on my dell laptop and i need help configureing my pcmcia networking card, it's a linksys WPC54GS and i have absolutely no idea how to make it work, I tried googleing it and looking for drivers but that didn't work right
linux is a lot different from windows, i'm such a linux noob

---

### Post by thomas.mcmahon on 2005-11-20
Hi there,

First of all, don't panic :) Linux can seem confusing to start off with, and it's really frustrating when you can't get networking stuff to work. However it seems that this will be doable!

According to the Ubuntu Wiki's ([https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)) wireless network card compatibility list ([https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)), your card should be supported natively by Ubuntu.

Therefore, all that is really required, is to open up the network administration tool. Your wireless card should pop up there, then all you need to do is click on it and configure it like you would under windows. If you have any problems, just post them and we'll see what we can do.

Good luck :)

---

### Post by danne on 2005-11-20
you can install your card graphically with your windows drivers if you want...
just connect your laptop to the internet with a lan-cable and search for "ndisgtk" in your synaptic packet manager.
once you've installed it you can retrieve the app under "system" > "windows wireless drivers"
open it and simply add a driver by using the ".inf" file from the windows driver.
notice that you have the .inf file stored somewhere it doesn't bother you because you'll have to leave it where it is after you've used it so ubuntu can reload the driver when you reboot...
let me know if it doesn't work!

bye!

---

### Post by zjgz on 2005-11-20
My laptop dosen't have a LAN thingie and whenever i go to the networking config thing it dosen't have it on it, in the device manager it dosen't have it listed, the card isn't broken or anything, the power light is lit up,

---

### Post by sarah_b on 2005-11-20
[QUOTE=thomas.mcmahon]
your card should be supported natively by Ubuntu.

Therefore, all that is really required, is to open up the network administration tool. Your wireless card should pop up there, then all you need to do is click on it and configure it like you would under windows. [/QUOTE]

Yes I have the same Linksys WPC54GS on one of my computers, I thought it would turn into a "NightMare" before I got it connected but it turned out to be so easy it was scary !

---

### Post by sarah_b on 2005-11-20
[QUOTE=zjgz]My laptop dosen't have a LAN thingie and whenever i go to the networking config thing it dosen't have it on it, in the device manager it dosen't have it listed, the card isn't broken or anything, the power light is lit up,[/QUOTE]

Are you using Breeze 5.10 ? Are you using this path: [COLOR="Red"]Systems > Administration > Networking[/COLOR]

---

### Post by Lambert on 2005-11-20
I show this having a broadcom chipset so it won't be supported natively in ubuntu.
[LIST=1]
[*]Card: Linksys #[WPC54GS] [SpeedBooster]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/SpeedBooster"), 54mbps/125mbps -- [link here|List#WPC54GS][LIST]
[*]Chipset: BCM94306
[*]pciid: 14e4:4320 (rev 03)
[*]Driver: Linksys [ftp://ftp.linksys.com/pub/network/wpc54gs_driver_utility_v1.0.zip]("ftp://ftp.linksys.com/pub/network/wpc54gs_driver_utility_v1.0.zip")
[*]Other: Ndiswrapper 0.10rc1 Manual compile. Works fine. Also reports speed up to 125Mb/s. Suspend/Rsume also works great. Great card, hassle freee install.[/LIST] [/LIST]You will need to use ndiswrapper and the windows drivers. They should be on your disk that came with the card or there is a link above to get them from linksys server.

Pop your install cd back in, open synaptic search for ndis and install I believe it's named ndis-utils or ndiswrapper. If this doesn't make sense to you click on the life preserver in the top panel and read through 5.10 getting started noting the section on installing apps.

Once you get ndiswrapper installed follow these instructions.

__[https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29)

If you need more help just use the forum search and type in ndiswrapper. You'll find hundreds of posts about this. Or type in the model number of your card and you can find posts that are limited to your model device.

---

### Post by thomas.mcmahon on 2005-11-20
According to the Ubuntu wiki, an ndiswrapper is not required for this card. Is the info. on the Wiki incorrect?

---

### Post by zjgz on 2005-11-21
well i tried the ndiswrapper thing and it got confusing and woulden't work

---

### Post by aznboi on 2005-11-21
i have the same card and mine works. try this:
sudo apt-get install ndiswrapper-utils
that will download the latest version.
then follow this guide:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)

if u have any questions feel free to ask cuz i went through the same thing.

---

### Post by aznboi on 2005-11-21
i recomend going to the linksys site and downloading the drivers. I did that and my card works great.

---

### Post by sarah_b on 2005-11-21
zjgz, I know the instructions at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver") say not to use the driver rt2500.INF from your Windows CD, but my personal experience is I did use the one from the Windows CD and have not had any problems at all. Hope this would make it less complicated for you if you want to try it.

---

### Post by dustin.kerber on 2005-11-22
I have got a good one for you guys. I am using an acer travelmate 4400 with a broadcom chipset and amd turion 64. According to the list on the ndiswrapper windows driver install list, I should be using drivers for an athereos card from an acer aspire 3023WLMi. Since i didnt think this is right, I went to the dirrectory for the travelmate 4400 within the acer site(nav from [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/)
to
[ftp://ftp.support.acer-euro.com/notebook/Travelmate_4400/driver/winxp/](ftp://ftp.support.acer-euro.com/notebook/Travelmate_4400/driver/winxp/) )

I then downloaded the 80211b drivers and followed the ndiswrapper instructions to install the drivers. Everything appeared to load fine, but the card stil couldn't be seen by ubuntu. I ran dmesg and saw this

[ 2827.972808] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[ 2827.976616] ndiswrapper (check_nt_hdr:145): Windows driver is not 64-bit; bad magic: 010B
[ 2827.976624] ndiswrapper (load_sys_files:456): unable to prepare driver 'bcmwl5'
[ 2827.985975] ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (6); check system log for messages from 'loadndisdriver'
[ 2860.963899] APIC error on CPU0: 40(40)

Looks like I need some 64 bit drivers. I am new to linux, someone please help :(

---

### Post by zjgz on 2005-11-22
I finally figured out how to get ndiswrapper working, well i used lsbcmnds.inf, it says that the driver is present now but it dosen't say anything about the hardware. hmmm

---

