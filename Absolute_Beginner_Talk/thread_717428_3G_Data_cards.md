---
title: "3G Data cards"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Newbie_DBN on 2008-03-07
Hi all

First things first, I'm well how shall we put this new to ubuntu and linux and yeah like most people here come from a very strong Windows backround which doesn't help much here.

Anyway straight to the problem. I wanna install Ubuntu 7.10 on my laptop but I have a Novatel E620 3G data card which appears to be to supported by Linux. So the question is does anyone know how to get it to work with Ubuntu?

Thanks
Newbie

---

### Post by jago25_98 on 2008-03-07
I don't know. Haven't got one.

But I can give a tip.

- tell them if it's usb or pcmcia
- if usb do `lsusb` and see what linux calls it. if pcmcia do lspci and pcmcia tools stuff beforehand to make it look like a pci card as if it were a desktop

-> then search for that, both google and in kernel source (aka drivers)

---

### Post by candtalan on 2008-03-07
3g - my actions - what I think I did. It is still working ok after an upgrade to gutsy 
(Note - this is written from experience in UK only)


Dated 30-6-2007
kubuntu 7.04 feisty
updated to date 30-6-2007

use a pcmcia vodafone card with t-mobile pay as you go sim which has some prepayed amount already topped up. (note I used martins pages - see below - to get some details [APN] otherwise I could not connect)

run kubuntu, then plug in the pcmcia 3g card,
terminal as user:
candt@bluedell:~$ ls /dev/ttyUSB*
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2

this verifies that the card is using these devices. I read that /dev/ttyUSB1 is not used, and
/dev/ttyUSB0 is used for data.

kppp configure:
followed
martins pages:
[http://www.net42.co.uk/os/linux/tmobile_datacard.html](http://www.net42.co.uk/os/linux/tmobile_datacard.html)
(kppp section)

needed to disable the existing network connection interface (eth0) using 
systtem settings>network settings
select  item then disable)

note that I got sucessful kppp connections even with the network not disabled, but could not get the browser working ion the internet (eg google)
(later note - this disable is not necessary  with gutsy)

===================
see:
[http://www.net42.co.uk/os/linux/tmobile_datacard.html](http://www.net42.co.uk/os/linux/tmobile_datacard.html)

Martin's pages > Operating Systems > Linux >
Using T-Mobile UK's 3G Datacard Under Linux
Affordable mobile broadband comes to the UK - and it works with Linux:
setting up the Option Globetrotter GT Fusion+ under Kubuntu 6.10 Edgy Eft.
Background

As of January 2007, several UK cellphone operators are well into the roll-out of new 3G networks to complement their GSM networks. GSM coverage is generally excellent (with just the occasional bad spot where those misguided NIMBY's have succeeded in maximising handset radiation!). 3G coverage remains patchy outside larger towns, but since 3G handsets and datacards can switch between 3G and GSM modes as necessary, the 3G user should get good coverage one way or the other.

Both GSM and 3G - also known as UMTS - can offer GPRS Internet access for your laptop, but 3G is a lot faster: download speeds of over a megabit are possible in HSDPA mode, although this is quite rare at the moment, and upload speeds are rather slower. Hopefully, operators will keep most of the voice traffic on GSM, leaving 3G free for high-speed data applications.
Pricing

Up to now, GPRS data services have been pretty pricey, in terms of connection fees, monthly line rental and data charges (typically £1 per megabyte). The good news is that T-Mobile UK now offers a tariff called Web N Walk Plus. This is available as an optional extra for their pay-monthly GSM and 3G phones, or you can buy it on its own and receive a free Cardbus datacard (with no connection fee to pay up front). For a fixed monthly fee you get up to 3 GB of GPRS data transfer per month on their GSM and UMTS networks, plus access to TMUK and BT wi-fi hotspots. VOIP and SKYPE calls aren't allowed on the 'Plus' tariff, but there is a more expensive 'Max' tariff that allows them. More info at [www.t-mobile.co.uk](www.t-mobile.co.uk).

One thing to watch is roaming charges for GPRS data when abroad. At the time of writing, these were £7.50 per megabyte for T-Mobile customers, and £10.00 per megabyte for Vodafone customers. Roaming data charges are not included in your bundled megabytes (if any).
Use Windows First

Before running the card under Linux, it is probably sensible to install the Windows drivers and test out the service. This is straightforward, but it is worth following the instructions! At the time of writing (January 2007), it was best to install the TMUK driver disc *before* inserting the datacard into the cardbus slot, otherwise Windows XP would guess incorrectly and auto-install the wrong drivers (which you'd then need to remove using Device Manager).

My datacard and SIM were already activated on the network, following credit checks at the time of purchases, there was no need to ring up to get it working. The Windows software that came with the card is quite nice - it makes it easy to swap between UMTS, GSM and Wi-Fi hotspots. You can also enter profiles for WEP or WPA protected Wi-Fi networks.

Occasionally, whilst in use under Windows, my card starts flashing two pink LEDs in quick succession. The card seems to have crashed at this point, as it's necessary to remove it, stop all the Windows software and start again, sometimes with a full reboot. I should probably ring TMUK and ask them whether this is a known issue or just a duff card. Perhaps a new firmware update will solve this: I already took a "mandatory" update offered when I first installed the TMUK Windows software. Keeping up with any new updates may be a good reason to boot Windows occasionally.
Getting 3G Working Under Linux

The TMUK datacard comes with drivers for Windows and MacOSX, but not for Linux. No problem!

First to identify the type of card. My card is labelled "OPTION wireless technology: GT Fusion+". Apparently GT stands for Globetrotter. Inserting this into the cardbus slot under Linux, the command lspci shows a new device:

	04:00.2 Network controller: Option N.V. Unknown device 000c

A quick Google reveals a great site at [www.pharscape.org](www.pharscape.org) where you'll find the Nozomi GPL driver, which supports various 3G cards made by Option. There are some great forums there too, where you'll find lots of help. I also tried visiting the manufacturer's website at [www.option.com](www.option.com) but it wasn't all that useful.

Taking the latest Nozomi driver (see the Pharscape forums), it should be straightforward to build the driver. This worked for me on Gentoo (kernel 2.6.15) and on Kubuntu 6.10 Edgy Eft (kernel 2.6.17-10). If you have problems - or if your data card is a different model - then go and look on the Pharscape forums for help.

sudo make && make install should build and install the kernel module. Then pop the card in, and you should see a message in /var/log/messages:

	Jan 28 17:54:23 maladict kernel: [17338817.308000] pccard: CardBus card inserted into slot 0
	Jan 28 17:54:23 maladict kernel: [17338817.308000] nozomi 0000:04:00.2: Init, cards_found: 1
	Jan 28 17:54:23 maladict kernel: [17338817.308000] nozomi 0000:04:00.2: Card type is: 2048
	Jan 28 17:54:23 maladict kernel: [17338817.308000] PCI: Enabling device 0000:04:00.2 (0000 -> 0002)
	Jan 28 17:54:23 maladict kernel: [17338817.308000] ACPI: PCI Interrupt 0000:04:00.2[A] -> GSI 18 (level, low) -> IRQ 185
	Jan 28 17:54:23 maladict kernel: [17338817.308000] nozomi 0000:04:00.2: Nozomi driver nozomi_tty
	Jan 28 17:54:23 maladict kernel: [17338817.616000] nozomi 0000:04:00.2: Version of card: 3
	Jan 28 17:54:23 maladict kernel: [17338817.616000] nozomi 0000:04:00.2: Initialization OK!

The driver automatically creates some new serial ports:

	# ls -l /dev/noz*
	crw-rw---- 1 root dialout 241, 0 2007-01-28 17:54 /dev/noz0
	crw-rw---- 1 root dialout 241, 1 2007-01-28 17:54 /dev/noz1
	crw-rw---- 1 root dialout 241, 2 2007-01-28 17:54 /dev/noz2
	crw-rw---- 1 root dialout 241, 3 2007-01-28 17:54 /dev/noz3

Running minicom should confirm that /dev/noz0 really is a modem. Type: AT (return) for the response: OK.  But you can't dial voice numbers.
Using the Nozomi Linux Driver with KPPP

So far so good. With access to the datacard working as /dev/noz0, it's time to bring up PPP. Using the KPPP utility from the Kubuntu desktop ("K" / "Internet" / "KPPP Internet Dial-Up Tool"), it should be simple to create a new PPP dialup connection.
.........................................................
.........................................................

    * Start KPPP and press 'Configure...'.

    * Under 'Accounts', press 'New' and [manually] create a name for the 3G/GPRS connection [i used fusion3g].

    * Enter [add] the telephone number to dial as *99***1# (dial first profile on data card).

    * Press 'Customize PPPD Arguments' and enter [add] the argument novj (THIS IS IMPORTANT or the link will not start!).


Modem 'Device' tab:
    * Under 'Modems', add a new modem. [I used fusion] In the modem Device tab, set the port to be /dev/modem from the drop-down menu. Make a symlink from /dev/modem to /dev/noz0. [I did not do this, from the modem device dropdown menu I chose /dev/usb/usbtty0 which I knew existed  after checking as noted above][and connection speed set to 460800]

Modem 'Modem' tab:
    * Under the modem's 'Modem' [properties] tab, press 'Modem Commands', 
and in 'Init String 2' you need to enter: AT+CGDCONT=1,"IP","general.t-mobile.uk" - note that it is .uk not .co.uk. If you're using a provider other than T-Mobile UK then you'll need to change this to reflect the correct APN for your provider (see 'GPRS in the UK' link below).

    * Username and password don't seem to matter, but I set them to web/web.

So what we're doing in the Init String is setting up the correct APN to use and storing it in slot 1 on the card. Then we're dialling the connection just stored in slot 1. You might not need to set up the APN every time but it's better safe than sorry - it seemed to get erased somehow half way through testing, so probably simplest to set it up every time.

If you now press 'Connect' to fire up the KPPP link and watch the log window, you should see 'CONNECT 1800000' however this doesn't necessarily mean you're in a swanky fast HSDPA coverage area - it still says that even if you've only got GSM coverage! All being well, you should now be able to surf the web over the PPP link. In 3G service areas, you can surf the web with great speed! In GSM-only areas, things are a lot more sluggish (especially on websites with too many bloated images) but it gets there eventually.

You might want to install COMGT and/or UMTSMON (see below) to give further information on the card (e.g. signal strength and name of network in coverage). So far COMGT works well for me, but UMTSMON won't build under Edgy Eft and the pre-built binary won't work.
Further Reading

    * [www.pharscape.org:](www.pharscape.org:) 3G Linux Support Info. Getting different cards working. COMGT and UMTSMON utilities.

    * [www.filesaveas.com/gprs.html](www.filesaveas.com/gprs.html) GPRS in the UK: much of this applies to 3G too.

    * sourceforge.net/projects/comgt/ COMGT: command-line datacard utility for linux.

    * umtsmon.sourceforge.net/ UMTSMON: graphical datacard utility for linux.


===================


HTH

---

