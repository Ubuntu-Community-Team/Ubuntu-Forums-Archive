---
title: "WiFi Help (DWL-650)"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-08-10
Hello,

I've spent a little time looking around the forum for help installing my DWL-650 PCMIA card for my laptop (IBM R32).  Sounds like some people are able to get it to work while others are not ... I did try one suggestion (of installing the linux-wlan-ng and linux-wlan-ng-firmware packages ... which didn't seem to do anything)

Since I am at day 2 with Linux, I really don't know where to start.  When I plug the card into my system I don't get anything to show up under my "Network Settings" (which lists my ethernet connection and modem connection.

How do I begin ?

Thanks!

---

### Post by stevanbt on 2006-08-10
Hi thornomad,
I have a dwl-650+ installed on my laptop.  I don't remember doing anything to get it installed, it was just there (I couldn't get it to work under Fedora or SUSE).

Not much help I suppose.

---

### Post by thornomad on 2006-08-10
Smile - yea, I guess that doesn't help me just yet.  Smile.  It doesn't show up at all in the network manager and the little lights don't even come on.  

I haven't a clue where to begin!

D

---

### Post by gn2 on 2006-08-10
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[http://support.dlink.com/faq/view.asp?prod_id=357](http://support.dlink.com/faq/view.asp?prod_id=357)


There are quite a few flavours of DWL-650... some of which do not have linux drivers, but ndiswrapper should do the trick.

Mine's a DWL-650+ EU.B4.

Initially I installed Ubuntu then inserted the card, nothing no lights, no internet.

Re-installed with card already plugged in, was detected and configured during the Ubuntu install process.

Good luck!

---

### Post by funkydan2 on 2006-08-10
Is it a DWL-650 or DWL-G650+?  The + is significant because it means that a different chipset is being used and thus a different kernel module is required.

---

### Post by thornomad on 2006-08-11
Hi - it is a DWL-650.  I don't see any reference to a P or an additional number (such as a revision number).  The serial number does start with an "H" ... maybe that signifies that it is a "H Revision" ?  If so: that one isn't supported ... hmm.

What is "ndiswrapper" (and would it matter if I have preperation H (wink) ?  Would I have to reinstall for that to work ?  

And, quickly, can I do a "repair" reinstall or do I have to do a full one?  

(so many questions! so much to learn!)

Thank you!

D

---

### Post by schurtek on 2006-08-11
have you tried using a ndis wrapper? a wrapper allows you to use drivers from another operating system.

[check google. ]("http://www.google.co.za/search?hl=en&q=wifi+ndis+wrapper&btnG=Google+Search&meta=")

[Check Sourceforge.]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu")

By clicking the above links you will be taken directly to my search results...

---

### Post by thornomad on 2006-08-11
No, I haven't tried a NDIS Wrapper yet ... I will look into that ... am on the Windows side now and found that the DWL-650 I have is: Version P (At least, that is what windows says when it recognizes it ... the D-Link images on the website don't match at all).

I will see now the NDIS goes.  Thanks.

D

---

### Post by thornomad on 2006-08-11
Hello again - I first tried to do a new clean install of Ubuntu with the wireless card (DWL-650 Rev.P) inserted (I hadn't done that before) ... however, it still is not being recognized.

I have noticed on other posts that there are some quick terminal commands one may excute to see if the card is being recognized at all -- hopefully diagnosing what went wrong ... is there anything I could try.

I am willing to use the NDIS Wrapper, however, the steps seem a little daunting and I am a bit scared at this time (smile).  Not sure which of the instructions to follow ...

D

PS: I ran lspci from terminal and here is the output (I don't see my card there)

```
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host B ridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bri dge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Au dio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02 )
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE ( LOM) Ethernet Controller (rev 42)
0000:02:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controlle r (rev 02)

```

---

### Post by gn2 on 2006-08-11
Have you considered changing your card?

A DWL-650+ has a Texas Instruments ACX100 chipset and works out of the box.

The model you have will need ndis wrapper.

You could sell your DWL-650 and buy a DWL650+ on eBay.....

---

### Post by gn2 on 2006-08-11
If you're in the UK they're quite cheap......

[http://search.ebay.co.uk/search/search.dll?sofocus=so&sbrftog=1&from=R10&satitle=d-link+dwl-650%2B&sacat=-1%26catref%3DC6&fsop=1%26fsoo%3D1&coaction=compare&copagenum=1&coentrypage=search&floc=1&sargn=-1%26saslc%3D2&sadis=200&fpos=AB39+3TW&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&so=Show+Items](http://search.ebay.co.uk/search/search.dll?sofocus=so&sbrftog=1&from=R10&satitle=d-link+dwl-650%2B&sacat=-1%26catref%3DC6&fsop=1%26fsoo%3D1&coaction=compare&copagenum=1&coentrypage=search&floc=1&sargn=-1%26saslc%3D2&sadis=200&fpos=AB39+3TW&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&so=Show+Items)

Someone wants your card: [http://wantitnow.ebay.co.uk/DWL-650-Air-Wireless-Adapter_W0QQadidZ330012063315](http://wantitnow.ebay.co.uk/DWL-650-Air-Wireless-Adapter_W0QQadidZ330012063315)

---

### Post by thornomad on 2006-08-13
Hey - thanks for this info ... I didn't know about the "want it now" thing ... wow ... I was going to get around to switching to a new card.  I will do an ebay search and try to sell it as well.  Would rather have it work out of the box.

THANKS!

---

### Post by jcano88184 on 2006-08-29
lspci doesn't works with pcmcia cards, you have to use the cardctl command:

$ sudo cardctl ident
Socket 0:
  product info: "D-Link", "DWL-650 Wireless PC Card RevP", "ISL37101P-10", "A3"
  manfid: 0x000b, 0x7110
  function: 6 (network)

Anyway.... i still can't make this card to run.

---

