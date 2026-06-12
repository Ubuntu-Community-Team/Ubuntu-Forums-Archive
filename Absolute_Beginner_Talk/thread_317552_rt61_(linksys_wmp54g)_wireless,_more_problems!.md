---
title: "rt61 (linksys wmp54g) wireless, more problems!"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by pthickett on 2006-12-12
Guys,

After struggling so bad with getting drivers to work with ubuntu edgy, i decided to try the 64bit version of dapper ubuntu as this is supposed to have the rt61 drivers installed.

It seems to have found the network card fine, and in the network settings program it is listed as ra0. However when i select the properties to set it up it just hangs and wont let me activate the connection. I was wondering if there is a different way i can go about activating and setting up the card to enter my ssid and wep key.

Cheers

Pete

---

### Post by Kobalt on 2006-12-12
Hello, 
you can manually edit the file /etc/network/interfaces and add the configuration items for your connection and interface. To do so, type : 
```
sudo gedit /etc/network/interfaces
```
Then you will see a list of interfaces, where you'll find yours (ra0). Add your essid and wep key so that your interface section looks like this :
> auto ra0
iface ra0 inet dhcp *(if this line differs don't mind it now)*
wireless-essid *your essid*
wireless-key *your wep key*
Save and exit, then : 
```
sudo ifdown ra0
sudo ifup ra0
```

And here you go !

---

### Post by pthickett on 2006-12-12
Cheers mate that sounds useful, i will give it a go.

Just out of interest whats do the 'sudo ifdown ra0' and 'sudo ifup ra0' commands do?

Thanks for your help

Pete

---

### Post by Kobalt on 2006-12-12
*sudo ifdown* deactivates a network interface, *sudo ifup *activates it.
Cheerio :rolleyes: !

---

### Post by pthickett on 2006-12-12
Right... i think i might have broken it! I tried what you suggested, but the strange thing was that in the interfaces file there was no ra0???! there was however a wlan0?!

So in my stupidity i added an ra0 to the bottom, and i wasnt suprised to see that it didnt work! however now i cant get back into ubuntu, it freezes on startup when it attempts to startup the network interfaces... i am thinking i will have to reinstall it, which wont be an issue as it was a fresh install anyway. So what should i have done instead??

Thanks

Pete

---

### Post by pthickett on 2006-12-12
right i have reinstalled ubuntu now, and tried modifying the wlan part of the interface document but it still doesnt want to know. Im really not sure what to do, the drivers look like they are fine, and the device itself seems to be recognised, just having a massive problem with it hanging when i try and activate the wireless card...

---

### Post by pthickett on 2006-12-12
does the card have to show up as a ra0, or is it ok as a wlan0??? im so confused... may try downloading the 32bit version and see if the issue with dapper is only for 64bit...

---

### Post by msak007 on 2006-12-12
Well I'm a little confused about your setup among other things, but I'll try to offer some insight:

1. The title of the thread says that this is a Linksys WMP54G, but the cards is an rt61 - those 2 things contradict. The rt61 is the name of the driver, not the card. Either way if you know you use that driver, then you have a card that uses the RaLink chipset, while the Linksys WMP54G (I have the WMP54GS myself) is a Broadcom chipset based card. The Linksys cards *are* detected, but won't work out of the box. They still need the help of the bcm43xx firmware tool or ndiswrapper to actually load the firmware / driver. This is in contrast to the RaLink cards which should work out of the box. What card brand / model do you have?

2. The card will show up as ra0 if it's an RaLink chipset. My Linksys card, because I had to use ndiswrapper to load the drivers, shows up as wlan0. I have another computer that I put a FoxConn wireless card (which uses an RaLink chipset) in, and that one shows up as ra0. It worked out of the box, all I had to do is add my ESSID and key to access my network.

3. You may not have had to necessarily reinstall the entire OS because it hung at boot. You could've simply booted into recovery mode (one of the options in GRUB when you're booting your machine) and then removed the offending entry from your interfaces file.

So I guess what we need now to help you is:

1. The card's manufacturer / model
2. The output of **lspci** (that's a lower case L)
3. The contents of your **/etc/network/interfaces** file

With that info we might be able to help you out a little more.

---

