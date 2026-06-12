---
title: "Belkin wireless notebook card - help to set it up"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by KiNG - TOMO on 2007-03-07
Help please, im gonna reformatt everything tonight the only reason am not using linux is becuase the wireless isnt working. my laptop is using a belkin wireless notebook card. can someone explain everything to get it working please. All internet guides I have read are just not clear enough. cheers in advance

---

### Post by Fitzcarraldo on 2007-03-07
Wireless cards in ubuntu are a minefield, I'm afraid *KiNG-TOMO*.

The first thing I suggest you do is try and find out precisely what model of Belkin wireless notebook card you have, *including the version number*, the country/region where it was bought, etc. and post the details with a request for help in the ubuntu Networking & Wireless forum.

To complicate matters, different versions of the same model of wireless card often have different chipsets and can require different installation procedures and software. I have read that even the same version of one particular model of wireless card can have different chipsets depending on whether it was made in China or Taiwan. That's why it is useful to post in your query as much information as possible about your particular card (look at what's printed on the labels on the front and back of the card, and the box and CD label if you have still have them).

You will also need the Belkin CD that came with the wireless card, just in case ubuntu/Linux software called NdisWrapper is required for the particular chipset in your card. If it is, you will need the original Windows drivers for your version of the card, which NdisWrapper will use.

To give you an idea of the type of steps that *may* be involved with a Belkin card, read the posts in the following thread:

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

particularly Post #13 which explains a bit about all the different versions of the Belkin F5D7010 model of card. Not that I'm assuming your Belkin card is that particular model, but many wireless cards from various manufacturers have different versions of supposedly the same model. For example, I have a Linksys WPC54G wireless notebook card that has "v7.1" printed on it, and the procedure for installing it is completely different to the procedure required to install e.g. v1.2 of the WPC54G card.

The more information you provide about your particular card, the more likely someone in the ubuntu Networking & Wireless forum will be able to advise you.

---

### Post by KiNG - TOMO on 2007-03-07
This is what I pulled from the NDISWRAPPER List On My Card

Card: Belkin F5D7010 Wireless-G Notebook Adapter

    * Chipset: RaLink RT2500
    * pciid: 1814:0201 (rev 01)
    * Driver: ndiswrapper 0.11 and A-Link [ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip)
    * Other: Debian sid/i386, kernel 2.6.7/9, Inspiron 2650. Tried the linux driver (v1.4.3.0) from [54] -- module loaded, interface created, but settings for iwconfig don't get committed. Tried to get NDIS driver off CD but couldn't locate/extract INF file. Finally tried NDIS driver for another card using RT2500 (the A-Link above), and (so far) it has worked wonderfully.

---

