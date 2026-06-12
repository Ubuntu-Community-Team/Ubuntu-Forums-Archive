---
title: "Edgy's ndiswrapper not taking wireless driver"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-11-28
I'm a former Dapper user who just upgraded to Edgy Eft, and all of a sudden ndiswrapper won't accept my wireless card driver (which Dapper had no problem with). Whenever I try to ndiswrapper -i, I get:

```
couldn't copy /drivers/NETI2120.INF at /usr/sbin/ndiswrapper-1.8 line 144
```

I went into the .inf file and looked at line 144; it is completely blank, as is line 145. Line 146 onwards reads:

```
;-----------------------------
;IPN2120 NT specific
;
[IPN2120WinNT.reg]
```

And then goes on to list various Windows specifications. I looked up the card on [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/) , and while my version was on there when I installed the driver in Dapper, it doesn't seem to be there any more (not exactly, anyway). The closest match was:

> #
Card: Linksys WMP11 v4 802.11b

    * Chipset: InProComm? ?
    * pciid: 17fe:2120
    * Driver: Linksys [ftp://ftp.linksys.com/pub/network/wmp11_v4_dr.zip](ftp://ftp.linksys.com/pub/network/wmp11_v4_dr.zip)
    * Other: Debian Unstable/Sid with NdisWrapper 0.11. You must install all three inf files from the driver zip file (I had to force NDIS to load all three drivers for the one card with the -d option on each inf). Card works great, but WEP is untested. Works great on Slackware 10.1 with a 2.6.10 kernel, and Ubuntu Breezy using the latest version of NdisWrapper.
    * Fedora Core 5, Kernel 2.6.15-1.2054_FC5, works fine with ndiswrapper 1.13, I only needed the LSIPNDS.INF file. I added the line &#8220;&#8216;alias wlan0 ndiswrapper&#8216;&#8221; to the /etc/modprobe.conf file so that the network configuration gui would pick it up. Once I applied DNS, IP, Gate, Mask, ESSID, I was running wide open. These are good inexpensive cards at any WalMart in USA.

lspci returns my card as:
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card
```

 I can't for the life of me figure out why this worked fine for Dapper and not Edgy. It's my only available wireless card, and until I get it working, my laptop has no capability for internet.

Help?

---

### Post by Halfling Rogue on 2007-11-28
Bump.

---

### Post by Halfling Rogue on 2007-11-28
Bump

---

### Post by Halfling Rogue on 2007-11-28
So no one knows how to fix this?

---

### Post by NullHead on 2007-11-28
You might try using a web search sight  and search for the filename of you're .inf file that seems to be corrupt. 

Try waiting a wile before betting all upset about no one posting about this ;)

---

### Post by Halfling Rogue on 2007-11-28
Heh, I would, but I need this laptop up and online as soon as possible. I'll put [this]("http://www.americanexplorer.com.br/suporte/Wireless/Kodama/Drivers%20KOD-752/INPROCOMM/IPN2120driver/9xInf/neti2120.inf") in and see if it works, but if not, I'm stumped. I can't figure out why it would work with Dapper and not Edgy.

---

### Post by NullHead on 2007-11-28
Well I won't be of very much help to you becuase I don't have the card you're talking about. 

The new .inf might be of use to you. 

Did you change to 64-bit by any chance when you updated? It would be apparent to you if you did. I also suggest you go all of the way to Gutsy ... there is allot of new features in the new version ;)

---

### Post by Halfling Rogue on 2007-11-28
Just tried the new .inf and got the exact same error message. *sigh*

Nope, same computer, same card, just a different OS. I'd use Gutsy if I had any blank CDs on hand, which I don't. Plus my laptop only lets alt. Ubuntu CDs install for some reason.

---

### Post by NullHead on 2007-11-28
Heck if thats you're problem just ask for one from hear they're free!!:popcorn:

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

EDIT: OH I forgot to mention that the .debs for edgy don't work. If you want to stat with edgy though download the source file from [hear]("http://ndiswrapper.sourceforge.net/") and follow the instructions.

You should install essential build tools first.```
sudo apt-get install build-essential openc++
```

---

### Post by Halfling Rogue on 2007-11-28
I did, but I'm waiting on it. ^^; In the meantime, I need my laptop working now. I can't wait a month for the CD to show up.

---

### Post by NullHead on 2007-11-28
I updated my old post ... but you posted before I could get it all in there ;) so give it a look over.

---

