---
title: "The Impossible"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-04-29
I'm pretty sure I'm beyond help at this point.
I'm MUCH of a newb when it comes to Linux. I installed Ubuntu successfully on a second partition. The next thing for me to do was to install the graphics card drivers for my ATI Radeon x1650 pro which was hard as hell. I couldn't install it the regular way which was described in the ATI website. I had to download this thing called Envy and install it that way. Even then the display seemed to be fuzzy and kind of big. It didn't seem to be a TRUE 1440x900 display the way it looks on any other OS. This, I think was my main issue among others.

The next thing I wanted to do was install Beryl, but it seemed I had a problem every step of the way. I couldn't even repeat any of the messages I read after having typed something like ./configure. The next step after that was to type 'make' and then enter. When I typed 'make' and then enter it gave me some sort of error message as if 'make' was not working. I DO remember however that when I did see part of the errors that it said something like kbe configure wasn't installed(or whatever) so I went to the system application thing and installed 'kbeconfigure'. I typed ./configure again and the instillation(or whatever) seemed to have gone further then before, but I still wasn't able to successfully complete 'make' I gave up at that point and decided to write this thread.

So my main issues:
Get my display/drivers for ATO Radeon x1650 Pro PCIE to work properly at a crisp display
Instlall Beryl.

Im running the 64 bit version of Ubuntu.
I wanted to give you guys my EXACT system specs too:
[*][ASUS P5B-E LGA 775 Intel P965 Express ATX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131070")
[*][  Intel Core 2 Duo E6600 Conroe 2.4GHz 4M shared L2 Cache LGA 775 Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115003")
[*][Logitech®  Premium Notebook Headset]("http://www.radioshack.com/product/index.jsp?productId=2715435&cp=2032061.2032365.2032388&fbx=0&allCount=113&fbn=Type%2FHeadsets&f=Brand%2F1000179%2F&f=PAD%2FProduct+Type%2FHeadsets&fbc=1&parentPage=family")
[*] (2X)   [PNY Optima 1GB PC2-5300 DDR2 DIMM Memory]("http://www.bestbuy.com/site/olspage.jsp?skuId=7997475&type=product&productCategoryId=cat01169&id=1155071451493")
[*][ SABRENT SBT-SCIDE SATA to IDE Ultra ATA-100/133 Mini Converter]("http://www.newegg.com/Product/Product.asp?Item=N82E16812156010")
[*][The MicroFly]("http://www.sudhian.com/index.php?/articles/show/ultra_microfly_review/")
[*][ I-Inc TW-191D / 19" Wide / 5ms / 700:1 / WXGA+ 1440 x 900 / DVI·VGA / Black / Widescreen LCD Monitor with Speakers]("http://www.tigerdirect.ca/applications/searchtools/item-detailsInactive.asp?EdpNo=2513662")
[*][ SAPPHIRE 100165L Radeon X1650PRO 512MB 128-bit GDDR2 PCI Express x16]("http://www.newegg.com/Product/Product.asp?Item=N82E16814102064")
[*]Memorex MRX-510L dual layer multi-format drive
[*][Logitech® LX7 Cordless Optical Mouse]("http://www.logitech.com/index.cfm/products/details/CA/EN,CRID=2135,CONTENTID=10918")[/LIST]

Hope someone can help me achive all my goals in LAYMANS, step by step terms and not give me links to install guides which i've already tried.

Thanks in advance

Regards,
Dann

---

### Post by HereInOz on 2007-04-29
If make is not working, ensure that you have the build-essential package installed.  If it is not there, make will not happen.

Can't help with the ATI card though.  I have avoided them like the plague and have no experience with them.

---

### Post by bobplano on 2007-04-29
try the fglrx drivers. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Coucouf on 2007-04-29
You should post the error you get when you './configure' it.
Extract the beryl package to some place, do a './configure' and let us see the error message. Then we may be able to help you.

You must be missing some development packages to compile beryl if you have a fresh Ubuntu installation.

Also be aware that it is probably no use to run 'make' if the 'configure' failed.
The configure script does (among other things) check that you have all the packages needed to complete the compilation successfully.

---

### Post by dannymichel on 2007-04-29
Build-essential is checked listed in Synaptic.
I installed Beryl through Synaptic as well, but it doesn't seem to be working.

---

### Post by TheeMahn2003 on 2008-04-17
I have just purchased 2 of your video cards, and will eventually buy 2 more 4 X crossfire board, I currently do not have the cards yet, but have read bad reviews on the card when it comes to linux, I am hoping that I will not have these issues, I have an admin on my forum that is a ATI "god" named drama, I suggest you take some time and read his post on [setting up ATI]("http://forumubuntusoftware.info/viewtopic.php?f=7&t=323"), it will be what I use when the cards arrive.  Please let me know if you have success or not.  I wish you luck.

TheeMahn

---

### Post by northern lights on 2008-04-17
Dude you realize this post is near a year old? ...

;-)

---

### Post by Triggerhapp on 2008-04-17
You're just about a year late.

---

