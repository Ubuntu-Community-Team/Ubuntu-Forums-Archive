---
title: "OpenOffice 2 and Canon Pixma iP3000"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by natsmith9 on 2006-03-08
I'm using canon's Pixus drivers explained in other threads.
[http://ubuntuforums.org/showthread.php?t=38995](http://ubuntuforums.org/showthread.php?t=38995)

I want to print from the paper tray (cassette) and I can do this in other programs like Firefox, gedit, and AbiWord, but I cannot get it to print from the cassette in OpenOffice...it always prints from the top auto paper feeder :-k .  I have tried to change the default paper source from APF to the cassette to no avail.  I am printing over a network, but I wouldn't see why this would be a problem.

Thanks!

---

### Post by Pragmatist on 2006-03-08
Have also you tried to print using those other programs (abiword, etc...) over the network?

---

### Post by natsmith9 on 2006-03-09
I have.  Other programs print from the cassette tray.

---

### Post by qwazert on 2006-03-10
OpenOffice and Canon printers don't seem to get along. I have a Pixma IP1500 that is an absolute nightmare to configure with Oo.

Eventually, after installing other apps it works...but I'm never quite sure what I did!
Try installing your printer AFTER Oo.

---

### Post by Pragmatist on 2006-03-10
I'm assuming you have tried printing with openoffice locally to the printer (not over a network).  If not, I would for sure try that, if possible, just to eliminate that aspect of the problem.  If the problem is still there, what happens if you try this:
```
oowriter2 -pt printername filename
``` from a command line?

Also give us your ppd file (you can find it in /etc/cups/ppd)

---

### Post by DavidW2 on 2006-03-10
I'm not sure what apps you tried in the Ooo suite but I was looking in Writer since I have it open right now. 

Under Tools->Options->Print-> there is a box labeled "Paper tray from printer settings".

Have you tried checking that?

---

### Post by dvarsam on 2006-03-10
Yeah, I have a Canon i550.

I have never been able to print colored pics nicely.
They come out as drafts...

Unfortunately, even though Canon Printers are MUCH better than Hewlett Packard's printers (& cheaper in the inks), when it comes to installing them in Linux... you better forget it...
Canon MUST do something about this !!!

---

### Post by qwazert on 2006-03-10
The biggest problem I've had with my Printer and Oo, is that Oo will default to an A5 paper regardless of the Printer settings.
Almost as if it doesn't accept the GLOBAL settings for my printer. 

After much folling and fiddling, I eventually get it where the two are talking to each other and it works fine...but I am never sure exactly _what it was_ that I did to make it work.

---

### Post by natsmith9 on 2006-03-11
> **DavidW2]I'm not sure what apps you tried in the Ooo suite but I was looking in Writer since I have it open right now. 

Under Tools->Options->Print-> there is a box labeled "Paper tray from printer settings".

Have you tried checking that?[/QUOTE]


Yeah, I've set the cassette tray as default and Oo doesn't print from it.

Here is my ppd file:


[QUOTE]
*PPD-Adobe: "4.3"
*%  CUPS add-on PPD file for Canon Bubble Jet Printer.
*%  Copyright CANON INC. 2001-2005
*%  All Rights Reserved.
*%
*%  This program is free software said:**
>  /ImagingBBox null>>setpagedevice"

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality 

*OpenUI *PageSize/Paper Size: PickOne
*DefaultPageSize: letter
*PageSize a5/A5: "<</CNPageSizeName(a5)/PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageSize a4/A4: "<</CNPageSizeName(a4)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize b5/B5: "<</CNPageSizeName(b5)/PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageSize letter/Letter: "<</CNPageSizeName(letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize legal/Legal: "<</CNPageSizeName(legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageSize postcard/Hagaki 100x148mm: "<</CNPageSizeName(postcard)/PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageSize postdbl/Hagaki 2 148x200mm: "<</CNPageSizeName(postdbl)/PageSize[567 420]/ImagingBBox null>>setpagedevice"
*PageSize envj4p/Youkei 4 105.5x235mm: "<</CNPageSizeName(envj4p)/PageSize[298 666]/ImagingBBox null>>setpagedevice"
*PageSize envj6p/Youkei 6 98x190mm: "<</CNPageSizeName(envj6p)/PageSize[278 539]/ImagingBBox null>>setpagedevice"
*PageSize l/L 89x127mm: "<</CNPageSizeName(l)/PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageSize 2l/2L 127x178mm: "<</CNPageSizeName(2l)/PageSize[360 505]/ImagingBBox null>>setpagedevice"
*PageSize panorama/P 89x254mm: "<</CNPageSizeName(panorama)/PageSize[252 720]/ImagingBBox null>>setpagedevice"
*PageSize businesscard/Card 2.16x3.58in 55x91mm: "<</CNPageSizeName(businesscard)/PageSize[156 256]/ImagingBBox null>>setpagedevice"
*PageSize creditcard/Credit Card 2.13x3.39in 54x86mm: "<</CNPageSizeName(creditcard)/PageSize[153 244]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*DefaultPageRegion: letter
*PageRegion a5/A5: "<</CNPageSizeName(a5)/PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageRegion a4/A4: "<</CNPageSizeName(a4)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion b5/B5: "<</CNPageSizeName(b5)/PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageRegion letter/Letter: "<</CNPageSizeName(letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion legal/Legal: "<</CNPageSizeName(legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageRegion postcard/Hagaki 100x148mm: "<</CNPageSizeName(postcard)/PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageRegion postdbl/Hagaki 2 148x200mm: "<</CNPageSizeName(postdbl)/PageSize[567 420]/ImagingBBox null>>setpagedevice"
*PageRegion envj4p/Youkei 4 105.5x235mm: "<</CNPageSizeName(envj4p)/PageSize[298 666]/ImagingBBox null>>setpagedevice"
*PageRegion envj6p/Youkei 6 98x190mm: "<</CNPageSizeName(envj6p)/PageSize[278 539]/ImagingBBox null>>setpagedevice"
*PageRegion l/L 89x127mm: "<</CNPageSizeName(l)/PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageRegion 2l/2L 127x178mm: "<</CNPageSizeName(2l)/PageSize[360 505]/ImagingBBox null>>setpagedevice"
*PageRegion panorama/P 89x254mm: "<</CNPageSizeName(panorama)/PageSize[252 720]/ImagingBBox null>>setpagedevice"
*PageRegion businesscard/Card 2.16x3.58in 55x91mm: "<</CNPageSizeName(businesscard)/PageSize[156 256]/ImagingBBox null>>setpagedevice"
*PageRegion creditcard/Credit Card 2.13x3.39in 54x86mm: "<</CNPageSizeName(creditcard)/PageSize[153 244]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion

*OpenUI *MediaType/Media Type: PickOne
*DefaultMediaType: plain
*MediaType plain/Plain Paper: "<</MediaType(plain)>>setpagedevice"
*MediaType prophoto/Photo Paper Pro: "<</MediaType(prophoto)>>setpagedevice"
*MediaType superphoto/Photo Paper Plus Glossy: "<</MediaType(superphoto)>>setpagedevice"
*MediaType doublesidephoto/Photo Paper Plus Double Sided: "<</MediaType(doublesidephoto)>>setpagedevice"
*MediaType matte/Matte Photo Paper: "<</MediaType(matte)>>setpagedevice"
*MediaType glossypaper/Glossy Photo Paper: "<</MediaType(glossypaper)>>setpagedevice"
*MediaType highres/High Resolution Paper: "<</MediaType(highres)>>setpagedevice"
*MediaType ijpostcard/Inkjet Hagaki: "<</MediaType(ijpostcard)>>setpagedevice"
*MediaType postcard/Hagaki: "<</MediaType(postcard)>>setpagedevice"
*MediaType tshirt/T-Shirt Transfer: "<</MediaType(tshirt)>>setpagedevice"
*MediaType ohp/Transparency: "<</MediaType(ohp)>>setpagedevice"
*MediaType envelope/Envelope: "<</MediaType(envelope)>>setpagedevice"
*CloseUI: *MediaType

*OpenUI *InputSlot/Paper Feed: PickOne
*DefaultInputSlot: cassette
*InputSlot asf/Auto Feeder: ""
*InputSlot cassette/Cassette: ""
*CloseUI: *InputSlot

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

*DefaultImageableArea: letter
*ImageableArea a5: "9.64 14.17 409.89 586.77"
*ImageableArea a4: "9.64 14.17 585.64 833.39"
*ImageableArea b5: "9.64 14.17 506.27 720.00"
*ImageableArea letter: "18.14 14.17 594.14 783.50"
*ImageableArea legal: "18.14 14.17 594.14 999.50"
*ImageableArea postcard: "9.64 14.17 273.83 411.02"
*ImageableArea postdbl: "9.64 14.17 557.29 411.02"
*ImageableArea envj4p: "9.64 75.12 288.00 657.64"
*ImageableArea envj6p: "9.64 75.12 268.16 530.08"
*ImageableArea l: "9.64 14.17 242.65 351.50"
*ImageableArea 2l: "9.64 14.17 350.36 496.06"
*ImageableArea panorama: "9.64 14.17 242.65 711.50"
*ImageableArea businesscard: "9.64 14.17 146.27 249.45"
*ImageableArea creditcard: "9.64 14.17 143.43 235.28"

*DefaultPaperDimension: letter
*PaperDimension a5: "420 595"
*PaperDimension a4: "595 842"
*PaperDimension b5: "516 729"
*PaperDimension letter: "612 792"
*PaperDimension legal: "612 1008"
*PaperDimension postcard: "283 420"
*PaperDimension postdbl: "567 420"
*PaperDimension envj4p: "298 666"
*PaperDimension envj6p: "278 539"
*PaperDimension l: "252 360"
*PaperDimension 2l: "360 505"
*PaperDimension panorama: "252 720"
*PaperDimension businesscard: "156 258"
*PaperDimension creditcard: "153 244"

*%CNPpdToOptKey PageSize       --papersize
*%CNPpdToOptKey MediaType      --media
*%CNPpdToOptKey InputSlot      --paperload
*%CNPpdToOptKey CNCartridge    --cartridge
*%CNPpdToOptKey CNQuality      --quality
*%CNPpdToOptKey CNHalftoning   --halftoning
*%CNPpdToOptKey CNRenderIntent --renderintent
*%CNPpdToOptKey CNGamma        --gamma
*%CNPpdToOptKey CNBalanceC     --balance_c
*%CNPpdToOptKey CNBalanceM     --balance_m
*%CNPpdToOptKey CNBalanceY     --balance_y
*%CNPpdToOptKey CNBalanceK     --balance_k
*%CNPpdToOptKey CNDensity      --density
*%CNPpdToOptKey CNGrayscale    --grayscale
*%CNPpdToOptKey CNLocation     --location
*%CNPpdToOptKey CNPercent      --percent
*%CNPpdToOptKey CNCopies       --copies
*%CNPpdToOptKey CNPaperGap     --papergap




Yeah, Canon has great products, but they have horrible Linux support.  I have a LiDE50 scanner that I can't use w/ Ubuntu.  Kinda sucks.

---

### Post by andyatnimbin on 2006-04-01
[QUOTE=qwazert]The biggest problem I've had with my Printer and Oo, is that Oo will default to an A5 paper regardless of the Printer settings.
Almost as if it doesn't accept the GLOBAL settings for my printer. 

After much folling and fiddling, I eventually get it where the two are talking to each other and it works fine...but I am never sure exactly _what it was_ that I did to make it work.[/QUOTE]

I think I solved my ip3000 and Openoffice A5 problem after a bit of messing around.  I'm using a canon 7000 driver and cups with one of the gimp options (7000  -bjc600).  Doesn't do a great job compared to the canon driver for wndows and the printer seems to loose about half it s capabilities but it works OK.  Try setting the scale to 200%, after I did that a couple of times it seems to work ok on 100% with 300X300 or 600X600 forget 600X1200 altogether (or, I wish you luck)

---

### Post by andyatnimbin on 2006-04-01
[QUOTE=qwazert]The biggest problem I've had with my Printer and Oo, is that Oo will default to an A5 paper regardless of the Printer settings.
Almost as if it doesn't accept the GLOBAL settings for my printer. 

After much folling and fiddling, I eventually get it where the two are talking to each other and it works fine...but I am never sure exactly _what it was_ that I did to make it work.[/QUOTE]

I think I solved my ip3000 and Openoffice A5 problem after a bit of messing around.  I'm using a canon 7000 driver and cups with one of the gimp options (7000  -bjc600).  Doesn't do a great job compared to the canon driver for wndows and the printer seems to loose about half it s capabilities but it works OK.  Try setting the scale to 200%, after I did that a couple of times it seems to work ok on 100% with 300X300 or 600X600 forget 600X1200 altogether (or, I wish you luck) *** andyatnimbin***

---

