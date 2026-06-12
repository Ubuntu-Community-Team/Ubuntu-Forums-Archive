---
title: "Need a Printer Recommendation"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by t-bone510 on 2007-12-20
Well, I really want Windows off my PC. 

Sadly, my printer (Dell AIO 926) is a paperweight in Ubuntu, and i need windows to print things.

I want a new printer anyway, so I was just wondering what you guys recommend.

I need it to work out of the box. Any ideas?


:D

---

### Post by kool_kat_os on 2007-12-20
I have a cannon mp830 and it automatically installed the drivers for printing and faxing, i haven't tested scanning yet

---

### Post by yabbadabbadont on 2007-12-20
Pretty much any printer that natively supports PostScript should work.  I'm talking about laser printers here.  For inkjets, it seems like HP and Epson are the best supported.  You should check out the linux printing website for suggested printers.

[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)

---

### Post by rfruth on 2007-12-20
just got a plain ole Canon iP1800 (inkjet) had to search the web for a driver but no biggie :)

---

### Post by GSF1200S on 2007-12-20
HP printers work quite well. My moms HP PSC 1300 works perfect, including the printing scanning, and copying. Just needed the HPLIP and HPIJS drivers and it went without a hitch...

---

### Post by discoade on 2007-12-20
definitely not a cannon mp460 a real pain to get it working in ubuntu and its still not great!:(

---

### Post by yabbadabbadont on 2007-12-20
Because of Canon's stance on OSS, there is very little support for most Canon printers.  Unless you pay for the commercial drivers at turboprint.de  ($40 US)

Most of the drivers floating around for some Canon printers came from beta drivers released only in Japan.

---

### Post by rustybronco on 2007-12-20
Got a free hp psc 1610 all-in-one today because it didn't work, "error no mech mode", solution... hold setup button down and plug in power cord to reset, then "carrage jam" it was the idiot's fault at work, you know how that is, solution "un-jam ink cartridge" now a free working printer!
I have 3 hp printers 1750, 1210 and this psc 1610 they all work in 7.04 and 7.10.
With the psc1610 the all the functions worked (scan, copy, print, card reader) but the best thing it was total plug and play!!!!!! (no disc required).

That would make it hp in my book!

---

### Post by Wesseli on 2008-01-05
Hi,

I bought black and white laser printer Samsung ML-2010R and it worked out of the box. Price was 79,90 €. My system is Ubuntu 7.10.

cheers

---

### Post by freddyp on 2008-01-05
I'm using a Brother 2040 laser.  Cheap, reliable and installed by t this newbie with no problems at all in Gutsy 7.10.

---

### Post by SOULRiDER on 2008-01-05
My friend has an Epson (i believe its a C45 or a very similar one) It worked out fo the box, we just plugged it in via USB and it was ready to use, just like a mouse or a keyboard :P

---

### Post by bigken on 2008-01-05
brother mfc660cn downloaded drivers from brother web site easy as double click

---

### Post by adam.tropics on 2008-01-05
Always been with HP, never had a problem. (Had a brief fling with Lexmark in 2000, it wasn't pretty....back with HP)!

---

### Post by sleepingdragon on 2008-01-05
Haven't tried HP printers, but I've heard good things about them. I stick with Epson personally, both the CX and DX range seem to work well, both in printing and scanning. 

I've seen how Lexmarks behave in Ubuntu, it ain't pretty...

Just my $0.02

---

### Post by hannulan on 2008-01-05
Bought a new printer this autumn, a HP Laser-Jet 1018. I'm very satisfied with it. The price was fair (about 100 dollars) and it worked almost out of the box (I had to download the driver, foo2jzs, and compile it first, but that was no problem). The best with the printer is the size. It fit perfectly in my bookshelf.

---

### Post by mrojas73 on 2008-01-06
I have a Canon IP4000 and I have never been to happy with it in Linux.  I would go HP if I were you.

---

### Post by Stunt Double on 2008-01-06
Go with HP just because of HPLIP which is a great GUI which allows you to print a test page, clean cartridges, etc. Keep in mind that with 7.10, HPLIP won't install unless the printer is connected during installation.

---

### Post by christian.convey on 2008-01-07
> **adam.tropics said:**
> Always been with HP, never had a problem. (Had a brief fling with Lexmark in 2000, it wasn't pretty....back with HP)!
I was thinking that too, which is why I looked at HP OfficeJet Pro L7680.  Unfortunately, a large fraction of the reviews suggest frequent mechanical problems.  Very disappointing from HP, and frustrating because they have the best Linux support that I'm aware of.

---

### Post by Niniel on 2008-01-07
Samsung ML1430 laser printer worked right away, an old Epson Color 760 worked after installing the drivers, which was not a problem at all. The list of supported Epson printers was quite long.

---

### Post by LowSky on 2008-01-07
> **hannulan said:**
> Bought a new printer this autumn, a HP Laser-Jet 1018. I'm very satisfied with it. The price was fair (about 100 dollars) and it worked almost out of the box (I had to download the driver, foo2jzs, and compile it first, but that was no problem). The best with the printer is the size. It fit perfectly in my bookshelf.

I have the same printer and trying to get it compilled was pain only because if you turn the printer off then you need to reload the drivers, but the I found out about HPLIP, and is been smooth sailing reloads the divers at ever start up. I even have it set up to for printing through my network for my laptop when I am away from the desktop. I couldnt be happier. Newegg had them on sale for under $90 last time I looked, only prints in Black and white, but how often do you really need color. Besides laser cartriges last forever compared to inkjet.

---

### Post by AbredPeytr on 2008-01-07
HP all the way!

My photosmart 7150 worked without a problem when connected to Ubuntu. Even after getting the Vista driver (beta) it still doesn't work as well as under Ubuntu.

If someone tries to sell you a Kyocera, run, don't walk away!

---

### Post by (((X))) on 2008-01-07
canon ip4300
works with xubuntu and ubuntu

---

### Post by botphly on 2008-01-13
> **kool_kat_os said:**
> I have a cannon mp830 and it automatically installed the drivers for printing and faxing, i haven't tested scanning yet

Quick question:  Which version of Ubuntu?  I'm running Gutsy having Mordor's own time with that same model printing via LPD to the household DLink (Model DI-724GU) router's built-in print server.  I hate to use the "works just fine in XP..." bit, but that's the truth.  

For context:  I've tried exempting CUPS from AppArmor with sudo aa-complain cupsd, but it doesn't make a lick of difference.  No ppd files on the driver CD, so I'm out of brains now.  (Oh, and the old HP 870C Deskjet that's directly attached to the LPT1 port on the Gutsy box won't print either--in CUPs, I just see the message that the printer is busy; will retry in 30 seconds--that sort of thing).  I've read elsewhere that Gutsy may have some overall issues with printing--I seem to be evidence of that...

---

