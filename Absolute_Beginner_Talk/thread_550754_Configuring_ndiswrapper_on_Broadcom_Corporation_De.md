---
title: "Configuring ndiswrapper on Broadcom Corporation Dell Wireless 1390 in Fiesty"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by manishbhardwaj on 2007-09-14
[B]Friends,

i have installed Ubuntu 7.04 on my Compaq notebook v3225 AU. It has got Broadcom Corporation Dell Wireless 1390 wirelass lan card.

I found this post on configuring ndiswrapper.[/B]


WifiDocs/Driver/1390
Broadcom Corporation Dell Wireless 1390

Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card is used in "Dell Inspiron 1501"
How To find out if you're using Wireless 1390

In a terminal, type lspci , which lists the PCI devices in your system. The output might include something like

05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

in which case you've got a 1390. You can find out a bit more information about the driver by typing lspci -n, which in my case includes the line

05:00.0 0280: 14e4:4311 (rev 01)

How To install Wireless 1390 driver to Feisty & Edgy

Get rid of the old ndiswrapper and bcm43xx driver,then restart your computer.

$sudo rmmod ndiswrapper
$sudo apt-get remove ndiswrapper-utils
$sudo su
$sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
$sudo shutdown -r now

Get the latest version of ndiswrapper

$wget [http://nchc.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.42.tar.gz](http://nchc.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.42.tar.gz)

Create a driver directory like "~/.driver", and move ndiswrapper to it. Install new ndiswrapper.

$sudo apt-get update
$sudo apt-get install build-essential linux-headers-`uname -r`
$cd ~/.driver
$tar -zxvf ndiswrapper-1.42.tar.gz
$cd ndiswrapper-1.42
$sudo make uninstall
$make
$sudo make install

Create wifi directory like "~/.driver/wifi",then get R140747.EXE from dell.com

"$wget http://ftp.us.dell.com/network/R140747.EXE"

Or you can pick up the r129832.EXE file from Dell driver disc,and unzip the file.

$cd ~/.driver/wifi
$unzip -a r129832.EXE      # or $unzip -a R140747.EXE
[COLOR="Red"][B]
Install the driver and restart again.[/B][/COLOR]

$sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf
$sudo ndiswrapper -l
$sudo ndiswrapper -m
$sudo modprobe ndiswrapper
$sudo shutdown -r now

You're all set! Try running this to see if your wireless card is functioning properly:

$sudo iwlist scanning

You may get the information like this:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:CE:F7:02
                    ESSID:"lab2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


[B]
I could work out most of the steps except for the one in Red. How do I install the driver from Dell : R140747.EXE.

Which command do i give to install this. It seems to be a Window format.

Any help would be highly appreciated.

Thanks
Manish[/B]

---

### Post by shearn89 on 2007-09-14
If you have unzipped the driver using the command above the red bit, you should have a load of files like ****.inf and ****.sys.
To install these with ndiswrapper, follow the commands BELOW the red bit. They should work provided you've done the bit before.

---

### Post by Acglaphotis on 2007-09-14
[http://blakecmartin.googlepages.com/](http://blakecmartin.googlepages.com/)

In that site there is a graphical tool that does it for you.

Or you could:

```

sudo aptitude install bcm43xx-fwcutter wifi-radar

```

That would install the driver for your card and a wifi manager. This is what i did.

BTW I have the same card as you so dont worry about compatibility.

EDIT:

To answer your question, you need to use a tool called cabextract:

```

sudo aptitude install cabextract

```

---

