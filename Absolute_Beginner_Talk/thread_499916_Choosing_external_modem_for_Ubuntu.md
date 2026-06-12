---
title: "Choosing external modem for Ubuntu"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by resander on 2007-07-13
I have Ubuntu 7.04 on a Pentium III, 700MHz PC with 256MB ram, which has a winmodem D-Link DFM-562IS HSFi PCI Modem and chipset Conexant SFi-CX11251-11.

Ubuntu does not support this Conexant chipset. I have read that people have had great difficulties in getting the driver (not on the distrbution) for this installed and working, so I am thinking about buying an external modem.
I have managed to find two:

  -  D-Link WebCruiserDFM-560EL (serial db-9)     ($30)
  -  D-Link DU-562M 56Kbps V.92 / V.90 USB Modem  ($34)

My computer has a 9-pin male socket at the back and USB ports too, but I don't know if the USB ports are USB 1.1 type of ports required by the USB modem.

Q1.  I have never bought an external modem before, but image it would come with a driver CD for Windows. If so, is there a corresponding driver for Linux that I would need to find, download and install?

Q2.  Do both external modems (serial & USB) work with Ubuntu 7.04?

Q3.  if so, is there a good reason to choose one rather the other?
     (price not important) For example, if people have reported 
     problems with the USB modem, then I would prefer the serial
     even if it supports V.90 only, i.e. which is the safest bet?



The info below is copied from [www.villman.com](www.villman.com) online store:

D-Link WebCruiserDFM-560EL  (about $30)

This is a competitively priced external box-type analog modem, designed especially to let PC users inexpensively "Cruise the Web." The modem connects to the serial COM port of the PC, desktop as well as notebook PCs equipped with a standard 25-pin serial COM port can use this modem to connect to the Internet.

The modem connects PCs to the normal telephone line to send data, faxes and logon to the Internet. Desktop and notebook PCs and other devices requiring only normal WAN speed (such as Internet gateways and SOHO routers) may also use these modems.

These modems provide V.90 K56flex standard 56Kbps speed. They perform V.42bis & MNP 2-5 data compression and error correction for fast and reliable transmission/reception.

Full duplex speaker phone, fax send/receive are supported.
 
Model Number 	DFM-560EL
Ports 	1 RJ-11 (to phone line),
1 RJ-11 (to phone set)
1 DB-9 serial
Cables 	Copper telephone wires
Speed 	56Kbps
Host Interface 	 Serial COM
Modem Type 	External analog modem




D-Link D-Link DU-562M 56Kbps V.92 / V.90 USB Modem  (about $34)

The D-Link DU-562M modem is a V.92/V.90, 56Kbps analog modem designed for home and small office users.

Very compact and lightweight, this modem can be plugged into any telephone port to provide desktop and notebook computers with a dial-up connection to the Internet. Connection to the computer is through a USB 1.1 port.

Features:

    * ITU-T V.92/V.90 standard Analog modem
    * Receive rates up to 56Kbps, transmit rates up to 48Kbps
    * Fax mode with transmit and receive rates up to 14.4 Kbps
    * Supports Telephone Answering Machine (TAM) and voice annotation through provided software
    * Supports Quick Connect (QC), PCM Upstream, V.44 data compression and 

Modem on Hold
    * DTMF and pulse dialing
    * Connects to computer through USB 1.1 port
    * Compact design

---

### Post by Bartender on 2007-07-13
Googled DFM560EL.  Apparently never sold in the U.S., so I wasn't getting much in the way of useful hits
[http://www.murga-linux.com/puppy/viewtopic.php?t=18698&sid=2357eca3e635f50b33a7e8f9db6b3fab](http://www.murga-linux.com/puppy/viewtopic.php?t=18698&sid=2357eca3e635f50b33a7e8f9db6b3fab)
Sounds like this guy got it working in Puppy, but he says wvdial was not working so that doesn't make me feel very confident about it...
The other modem looks like even less likely to work, but again, not sure - most hits were in another language :(

Once you understand the ways to ask Linux to look for an external modem, and know where it's likely to be found, it's pretty simple - you hook it up and it either works or doesn't.  The driver CD will of course be Windows oriented.
I've got this weird Boca 56K modem model MD56SEE, apparently it's a Swedish version (?).  I plugged it into the Linux PC, it was seen on the ttyS0 port, and it worked.  I got it working in Windows too, but had to tell Windows to treat it as a "Standard Modem" and it didn't want to do that...

What else do you have in the way of external modem choices?  I've got 4 external modems right now, all bought used because so many people have moved on to cable, DSL, fiber, and satellite.  I don't know how it is where you live but used is certainly the cheaper way to go if that option is viable.

---

### Post by ieee488 on 2007-07-13
If I had to choose, I would choose the one with the DB9 connection.

I bought a used Actiontec external modem on eBay last year, and it worked.

You might want to give eBay a try.

---

### Post by Bartender on 2007-07-13
Agreed.  If you knew nothing else about the modems, the serial connection is at least a good indication but not a guarantee.

---

### Post by Warren Watts on 2007-07-14
I bought a used Serial 56K V.92 External modem at the thrift store for less than three dollars and it worked perfectly.  

Since it is a full-blown modem and not a software "winmodem" it doesn't even require any drivers.  

Since I got DSL it's just a paperweight.  If you are interested in it, I would be willing to ship it to you for the cost of shipping.  Even with the power supply and cable, it can't weigh more than about three pounds, so I would imagine it wouldn't cost much to ship.

I'm not out to make a profit here, I'd just like to see it put to good use.

Send me a private message if you are interested.

---

### Post by resander on 2007-07-14
Many thanks for your advice.

I have just ordered the serial D-Link DFM-560E from [www.villman.com](www.villman.com) in Manila. It will be delivered in about a week. Will post here when I know the outcome.

I live in the Philippines and D-Link is very popular here, especially for internal winmodems. An internal D-Link winmodem is about $8-10. An unbranded winmodem can be picked up for as little as $6.

There are not many external modems here, only the two that I found plus US Robotics (too expensive - $80).

Again, many thanks.

---

### Post by Bartender on 2007-07-14
Hi, Warren -
That's nice of you to offer selling your external.

How far are you from these guys?
[http://www.colug.net/](http://www.colug.net/)

Betcha somebody there could use it...

---

### Post by Warren Watts on 2007-07-14
I have a good friend who is active in COLUG.  

I personally have never been to one of their meetings tho.

---

### Post by grlfrend on 2007-07-19
I saw this post because I have been reading in earnest everything I can find about dial-up modems for Linux. I ordered a Dell E510 desktop with Ubuntu installed and am expecting it any day now. Getting online will be top priority, so thanks for your post! It seems from the specs. you provided that I'll need to know what kind of port(s) the Dell E510 has before I can proceed with purchasing a modem, and I don't. It is not as though I haven't been trolling like mad on line for info., and I have two Ubuntu books on order, but in part because I'm new to this and not terribly tech-savvy, I'm still trying to get clear on how to proceed. Can anyone help?

Thanks!

---

### Post by Bartender on 2007-07-19
I don't know if the Dell has a serial port or not.  You can tell us in a few days!  If it does I'd go shopping on craigslist or ebay for a used 56K US Robotics serial modem.  [This]("http://www.newegg.com/Product/Product.aspx?Item=N82E16825137104") is the cheapest new serial modem I've found. 

The new [Zoom 3095]("http://www.marketwire.com/2.0/release.do?id=749607&sourceType=6") USB modem looks pretty cool.

---

### Post by davidsrsb on 2007-07-19
The situation with usb modems went from bad to worse when smlink sold their modem chip business to conexant. This is a usb chipset, actually made by ST, called pegasys and used in many brands. They had Linux support before the trasnsfer. Since the transfer you cannot get drivers, even for Windows. There never was a Vista driver publically released. Linux support is actually better than Windows support now as we have some unmaintained drivers in the repositories

---

### Post by grlfrend on 2007-07-22
Thanks, Bartender.

I am on a borrowed machine; hence the delay in acknowledging your most helpful response.

---

### Post by Bartender on 2007-07-23
> **grlfrend said:**
> Thanks, Bartender.

I am on a borrowed machine; hence the delay in acknowledging your most helpful response.

No prob, all of us losers on dial-up gotta stick together.  Might as well point out my [work-in-progress]("http://ubuntuforums.org/showthread.php?t=480717").

---

### Post by autocrosser on 2007-07-23
I have been using a older Zoom USB modem for several years now--I'm not at home, but I can supply a fair amount of info in about 8/10 hours. I got the Zoom off of eBay for less than $20USD.

---

### Post by cebobbitt on 2007-07-23
Hi there, I too am stuck in the doldrums of dialup. I am using dapper and have been using Ubuntu for right at a year now. I got my hardware modem at Best Buy for about 60 bucks and it has done a really good job. Its a ModemBlaster by Creative and is hooked up to a serial port on ttySo. When I first got it, I opened up the network tool that comes with Ubuntu and it detected it from the get go. Hey Warren Watts, does that offer apply to everyone? I hope you have good luck with getting connected. Good Day

---

### Post by Bartender on 2007-07-23
autocrosser -
Looking forward to your next post.  I'm keeping a 3-ring binder just on dial-up stuff.  Have a short list of functional external modems and would like to add to it!  Did you take a look at the Zoom 3095?

cebobbitt -
6.06 was the last version of Ubuntu where the dial-up part of the Networking GUI worked.  Don't let that scare you off from upgrading - it's just that you'll have to do some things a little [different]("http://ubuntuforums.org/showthread.php?t=480717").

---

### Post by resander on 2007-08-02
My D-LINK DFM-56EL external modem now works with Ubuntu 6.10 (the mouse did not work on 7.04).

Here is how I installed it:

1.  downloaded Gnome-ppp using another computer. Copied to CD.

2.  inserted CD in CD-drive on Ubuntu PC.
     An icon representing the CD becomes visible in the Ubuntu window.

3.  double-clicked on CD icon to install gnone-ppp.
     The installer puts the Gnome dialer in the same
     submenu as Firefox, Evolution mail etc

4.  click GNOME PPP submenu item and enter Username, Password
     and telephone number (in my case from a prepaid Internet card)

5.  Click Setup button at the bottom of the GNOME PPP dialogbox.

      Select device from dropdown list

          /dev/ttSy0  corresponds to Windows COM1
          /dev/ttSy1  corresponds to Windows COM2

      Select device type from dropdown list: 'Analog Modem' in most cases

      Select modem speed: 57600 for a 56K modem

      Leave all other settings as they are. Close Setup

   Click Connect button on GNOME PPP dialog and you will hear
   the modem connect signalling.


I had one hardware problem. The serial port did not work, so took the PC to the repair shop. It turned out the serial port clashed with the internal modem that was left in the PC (there was an IRQ conflict). The serial port worked after the internal modem had been removed. I don't know if this was by unlucky chance on my PC, or, if this would be a common problem.

I also borrowed two US Robotics Sportster modems, a  28.KB and a 33.3 KB. Both worked, after I had changed  the modem speed setting in the GNOME PPP dialog to 28800 and 38400 respectively.

---

### Post by Bartender on 2007-08-02
thanks, resander - 
We need more "it worked!" posts like yours, with the steps laid out for newer users to read and understand.

---

### Post by autocrosser on 2007-08-11
Sorry to not have got back before now--been busy with fussin' with the Gibbon--

Let's see--usefull USB site--modems & much more:
[http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)

Init Strings:
[http://www.inka.co.uk/graphical/modems.shtml](http://www.inka.co.uk/graphical/modems.shtml)

The "best" modem site on the net:
[http://www.xmodem.org/index.html](http://www.xmodem.org/index.html)

The Linmodems site:
[http://phep2.technion.ac.il/linmodems/](http://phep2.technion.ac.il/linmodems/)

These sites have helped me more times than I can count!!!

Anyway--these are the ones I turn to if I have a problem--

---

### Post by koolkatkiwi on 2007-08-12
> **Warren Watts said:**
> I bought a used Serial 56K V.92 External modem at the thrift store for less than three dollars and it worked perfectly.  

Since it is a full-blown modem and not a software "winmodem" it doesn't even require any drivers.  

Since I got DSL it's just a paperweight.  If you are interested in it, I would be willing to ship it to you for the cost of shipping.  Even with the power supply and cable, it can't weigh more than about three pounds, so I would imagine it wouldn't cost much to ship.

I'm not out to make a profit here, I'd just like to see it put to good use.

Send me a private message if you are interested.

Hi Warren. I'm in NZ so shipping would be too high, and besides, you've probably already found a home for this modem. But, can you tell me the exact make and model, its specs? I can go looking for it on our local Ebay equivalent and may be able to pick one up. The modem issue seems crucial with Linux.

Cheers,
Kath.

---

### Post by Warren Watts on 2007-08-12
It's a GLOBAL VILLAGE TelePort 56K/V.92 Model 6250

It was marketed for use with a Mac, and it came with a round mini-DIN cable, but the modem itself has a standard 25 Pin "D" RS-232C connector.  I just purchased a 25-9 pin serial cable and it worked perfectly.

For whatever reason, the Global Village Website is down at the moment, but here's the link:

[Global Village | Macintosh Modems | TelePort 56K V.92 Modem]("www.globalvillage.com/products/macmodems.html")

Hope this helps!

Warren

---

