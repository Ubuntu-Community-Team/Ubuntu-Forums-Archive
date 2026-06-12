---
title: "NETGEAR 54 Mbps Wireless PCI Adapter WG311 v3 l"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by pravinkharche on 2007-10-26
i use NETGEAR 54 Mbps Wireless PCI Adapter WG311 v3 this card on debian etch but it cant detect the card or any hardware when i type => iwlist scan output is
pearl:/home/pkharche# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

is ther any problem of drivers
please help me:)

---

### Post by mikeyphi on 2007-10-26
Is your card recognised under System/Preferences/Hardware information?

Also try to find out what the chipset is.

---

### Post by Church.Cameron on 2007-11-13
i have the same card and the same problem, and under the hardware info the card is there, but next to status it says status please help i need to get this machine going :( :P 

Thnx

---

### Post by Church.Cameron on 2007-11-13
please help mee

---

### Post by wieman01 on 2007-11-13
What chipset is it?

---

### Post by Church.Cameron on 2007-11-13
all i know is its a dell and its a intel pent 4 i am not certian to much more than that

---

### Post by wieman01 on 2007-11-13
> **Church.Cameron said:**
> all i know is its a dell and its a intel pent 4 i am not certian to much more than that
Well, what chipset is the wireless adapter?

---

### Post by Church.Cameron on 2007-11-13
Atheros chipset

---

### Post by Church.Cameron on 2007-11-13
so i found a driver system that supports the ath chipset, but its complicated system and i have no idea how to get it to go in my ubuntu system, please help me here's the site,[HTML]http://madwifi.org/[/HTML] 
also if there is a better one than this let me know thanks !

---

### Post by TheIrishGuy on 2007-11-13
[SIZE="4"][COLOR="DarkRed"]NetGear WG311v3 (marvell chipset)[/COLOR][/SIZE]

Install Ndiswrapper
```

sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common

```

Download marvell chipset Drivers (i cant find the link where i got em, so i uploaded them to my own webspace)
```

wget http://www.feeditout.com/marvell/wlandrivers.zip

```

Unzip them
```

unzip wlandrivers.zip

```

Load the driver (ini file) (i used the win2k xp drivers)
```

ndiswrapper -i /path/to/ini

```

lets see if it is present
```

ndiswrapper -l
mrv8335 : driver installed
        device (11AB:1FAA) present

```

Save our settings 
```

sudo ndiswrapper -m

```

Start the device
```

sudo modprobe ndiswrapper

```

once the driver has been installed you can remove the unzipped files, as the needed files have been copied elsewhere

```

rm -rvf /path/to/folder

```
[SIZE="5"][COLOR="Red"]note : alwasy be carefull of what you delete, use GUI if unsure[/size][/color]
check this sticky out
[http://ubuntuforums.org/showthread.php?t=611908](http://ubuntuforums.org/showthread.php?t=611908)


Network-manager will make it work automatically in gnome

if you want it on boot, advanced config for terminal usage can be found here

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)




[SIZE="4"][COLOR="DarkRed"]Does not work with madwifi[/COLOR][/SIZE]

Madwifi Netgear Info for WG311
-------------------------------------------------------------------------------------------

Chipset:	AR5212 (b/g)
URL:	[www.netgear.com](www.netgear.com)

Interface:	Mini PCI in PCI carrier. (Can be removed).

Antenna Connector:	RP-SMA.
Device Information:	168c:0013 (rev 01)

Notes:	Rev 01 works fine with Madwifi(ng?) under Ubuntu 7.04 with NetworkManager.
Rev 02 has a TI chip, and is not compatible (Device Information : 104c:9066, Work with ndiswrapper).
[SIZE="2"][COLOR="DarkRed"]Rev 03 has a **Marvell Chip**, and is also **not compatible** (Device Information : 11ab:1faa (rev 03), **Work with ndiswrapper**)[/COLOR][/SIZE]

---

### Post by Church.Cameron on 2007-11-13
> **TheIrishGuy said:**
> [SIZE="4"][COLOR="DarkRed"]NetGear WG311v3 (marvell chipset)[/COLOR][/SIZE]

Install Ndiswrapper
```

sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common

```


i tried this string out and i got E: Couldn't find package ndiswrapper- utils-1.9 

WHATS HAPPENING TO MY UBUNTU :confused::confused::confused:

there has to be something i am not doing right, i have the ndiswrapper- utils package on my desktop. should it be somewhere else? grr....

---

### Post by Church.Cameron on 2007-11-14
also from what i am looking at it says it works if i am reading this right it works with wg311 but not with ndiswrapper. pls let me know if i am not stating this correctly 


[COLOR="Red"]Rev 01 works fine with Madwifi(ng?) under Ubuntu 7.04 with NetworkManager.[/COLOR]
Rev 02 has a TI chip, and is not compatible (Device Information : 104c:9066, Work with ndiswrapper).
Rev 03 has a Marvell Chip, and is also not compatible (Device Information : 11ab:1faa (rev 03), Work with ndiswrapper)

---

### Post by wieman01 on 2007-11-14
I don't know if your adapter is compatible or not, but it is worth the effort. Let's try.

Please open Synaptic (the package manager) and search for packages that looks similar to these:
> ndiswrapper-utils-1.9 
ndiswrapper-common
The version number could be different but these should be available. Once you have installed them, continue to follow the guide.

---

### Post by TheIrishGuy on 2007-11-14
Church.Cameron > 

search for ndiswrapper in synaptic package manager, also update your apt sources

```

sudo apt-get update

```

rev 01 is wg311v1, 

you clearly stated that you have wg311v3

wg311v3 = rev 03

Rev 03 has a Marvell Chip, and is also not **compatible WITH MADWIFI** (Device Information : 11ab:1faa (rev 03), **COMPATIBLE WITH ndiswrapper**)


you shouldn't have to do this, but on the off chance you cant find ndiswrapper

heres a guide to installing it manually
[http://ubuntuforums.org/showthread.php?t=574511&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=574511&highlight=ndiswrapper)

also is synatic pakage manager, go to settings > repositories > and enable the restricted repoitories and reload your package cache

sudo apt-get update


but once again this should not be needed

---

### Post by pravinkharche on 2007-11-23
plz try it

###install ndiwraper for driver

# apt-get install module-assistant
# module-assistant auto-install ndiswrapper
# cp WG311v3.INF WG311v3.sys WG311v3XP.sys /home/jimbo7/temp_dir
# ndiswrapper -i /home/jimbo7/temp_dir/WG311v3.INF
# ndiswrapper -l
# modinfo ndiswrapper
# modinfo usbcore
# modprobe -n -v --first-time ndiswrapper
# modprobe ndiswrapper
# dmesg     or # modprobe -r ndiswrapper # modprobe ndiswrapper
# ifconfig wlan0
# iwlist wlan0 scan


Create an alias into the module configuration file using

# ndiswrapper -m

Then add the line ndiswrapper to the file /etc/modules

# echo ndiswrapper >> /etc/modules

---

### Post by Martin on 2007-12-20
ndiswrapper and the intructions on the thread worked perfectly for WG311GR v3 (German version) on both Gutsy and gOS

---

