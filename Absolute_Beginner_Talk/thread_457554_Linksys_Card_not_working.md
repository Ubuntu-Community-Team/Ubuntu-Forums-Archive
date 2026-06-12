---
title: "Linksys Card not working?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2007-05-28
Ok...I had my card working at one point...but now it wont work..dont know whats wrong...

Linksys WPC54G ver 2 Wireless card

card has power, but doesnt seem to be seeing a network, even though i am right next to the router, and laptops on the other side of the house are conected wirelessly..

Wep key has been check and rechecked 50 times, and it is correct..

When I look at Network Tools (System>Admin>Network Tools), and select Wlan0, it says no info available for everything. 

Under Network Settings, the Wireless Connection is there, and activated, but still nothing.

Help!

---

### Post by Lapith on 2007-05-31
You'll want to follow these instructions:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The default driver they recommend, wl_apsta.o, didn't work for me. I used the version 2-specific driver from the Intel website:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3DWPC54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230042300B01&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3DWPC54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230042300B01&displaypage=download#versiondetail)
Find the bcmwl5.sys file in the zipped driver download, and plug that in as the <downloaded file> in the command.
(You may also be able to find the same file in the download list at the zless /usr/share/doc/bcm43xx-fwcutter/README.gz step of the instructions.)

I'm struggling through this myself with the same WPC54G v.2 on a Sony Vaio PCG-FX140; I'm to the point where the machine thinks it's connected to my network, shows full bars, but can't ping the router. I feel like I'm just steps away from getting this to work...

---

### Post by kernel tom on 2007-05-31
if it's activated and with the correct network name, and WEP key you should be fine, so check that over

secondly, getting an app like wlassistant becomes very helpful for wireless networking

sudo apt-get install wlassistant

then when you run it

sudo wlassistant

and it will show all availible networks

---

### Post by Kobalt on 2007-05-31
I have a WPC54G v.2 and it's based on an ACX111 chipset and not a broadcom one... You should maybe check out what the *lspci* command gives you.

Anyway, if it turns out to be an ACX111, you must know the opensource drivers only provide support for WEP encryption and not WPA. If you want to enable it, you should use ndiswrapper+windows drivers. See [this]("http://ubuntuforums.org/showthread.php?t=324148") for more info about that.

---

### Post by bladefallcon on 2007-06-04
ok...*lspci* gives me the following output
> 0000:07:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

I am using a WEP, not WPA encryption, and the key is correctly entered. I have had it working in the past...not really sure when it stopped working, as i typically have had it on ethernet cable..

---

### Post by bladefallcon on 2007-06-04
no worrys everyone...i found what i needed...did another search, and found the info i needed. Information i had used once before...but forgot..It seems i will need to do this again after each kernel update, to keep the wireless working correctly..the link i found is below for any interested..

[http://ubuntuforums.org/showthread.php?t=233565](http://ubuntuforums.org/showthread.php?t=233565)

---

### Post by abn91c on 2007-06-04
you may want to check the location for the card, my linksys card is on eth1, wlan0 may not work for you, i tried that on and cant connect, right now im on a sabayon live cd and my card is detected as eth1. its one of the few live distros that I can wireless connect. It would be the same for a HDD install

---

