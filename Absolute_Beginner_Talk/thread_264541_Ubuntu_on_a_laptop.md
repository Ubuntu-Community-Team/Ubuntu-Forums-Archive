---
title: "Ubuntu on a laptop"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-09-24
Looking to buying a laptop for work, and want to put Linux on it.

I found some laptops that would ship with Dapper pre-installed, but as a meer Database Administrator, they're kindof out of my price range. 

But, are there any laptops that Ubuntu -won't- instal smoothly on? And are there any troubles with the built-in 802.11 Wireless?

Thank you for the input!

---

### Post by halitech on 2006-09-24
I've got an olderish HP pavillion ZE5700 with builtin wireless and it seems to have installed the card fine, I just don't have a wireless router so no idea how it works (should take a drive downtown and hit the wireless spot sometime I guess)

Everything else works fine.

---

### Post by topheth on 2006-09-24
I've installed Ubuntu on an HP Pavilion dv5020us without too much of a hitch.  Wireless card was identified but it took some effort to get it hooked up to my wireless.  Otherwise, thoroughly enjoying it.

---

### Post by xyz on 2006-09-24
I have been using a Toshiba Satellite A 40 for 2 years now - no problems -
Also check:

[Laptop Forum]("http://www.ubuntuforums.org/forumdisplay.php?f=137")

---

### Post by oss_monkey on 2006-09-24
I've been using a Satellite 1800 (talk about old!) for about two months or so. Dapper installed ok, though I'm having trouble with the video (Trident Cyberblade Ai) rendering of 3d. Seems unsupported everywhere I look.

I plugged in a Linksys Wireless-G card, and with ndiswrapper, it installed fine. :)

---

### Post by PriceChild on 2006-09-24
Ralink Chipsets are very good on ubuntu... i hear they're reccomended by the FSF.

I've got a rt2500 PCI or something working perfectly :) Even usb works fine.

---

### Post by tylerjames on 2006-09-24
I've got a dell inspiron 6400 with 1.83ghz Centrino Duo, 120gb hd, 1gig ram, ati radeo x1400.... everything pretty much worked when I installed dapper (including wireless) the only thing i had to do was install the ATI drivers. And it was only about $1000 CDN

---

### Post by crokett on 2006-09-24
Lenovo (formerly IBM) Thinkpads work pretty well.  A good number of the Ubuntu staff use these machines so support is pretty good

The live CD booted nicely on my Thinkpad and detected everything including my combo wireless NIC/modem.

---

### Post by kaens on 2006-09-24
I second croketts claim of Thinkpads being nice.

---

### Post by lonce on 2006-09-24
I installed xubuntu on a dell inspiron 8500.  It was a P3 433 processor with 256 of ram, and it ran pretty good.  It took firefox about 15 seconds to open.  But it was still very very usable.  In fact I gave it to my son for school and he uses it daily.

---

### Post by 758 on 2006-09-24
I have a HP Pavilion ze4900 with dapper. It runs great althought I did have a little trouble with the wireless card at first, but it is a very simple thing to solve. Just had to blacklist the dapper drive and ndiswrapper my own driver ;). Just so you know for future reference, there are no Linux drivers (at least in my cases) for broadcom wireless cards. So you'll have to use ndiswrapper. But other than that dapper recognized all of the external bells and whistles of my laptop (mute button, volume, internet/media/help buttons).

---

### Post by jimrz on 2006-09-24
another vote for thinkpad ... T42 works very well with ubuntu with very little tweaking required.

depending what you need, just research the model #, wifi chipset and vid card (nvidia seems to have acpi probs on laptops and radeon may prove difficult or impossible to get hardware accelleration working)  before you buy.

---

### Post by blx_286 on 2006-09-24
> **Taigrr said:**
> Looking to buying a laptop for work, and want to put Linux on it.

I found some laptops that would ship with Dapper pre-installed, but as a meer Database Administrator, they're kindof out of my price range. 

But, are there any laptops that Ubuntu -won't- instal smoothly on? And are there any troubles with the built-in 802.11 Wireless?

Thank you for the input!

I am running it on an older Dell Inspiron 4150 (P4) and I have the Airlink MIMO XR wireless pc card. It was a little tricky to setup the wifi until I found the right instructions. It has the RaLink Chipset and uses the RT61 drivers.

---

### Post by DarkN00b on 2006-09-24
I'm running Dapper on an HP Ze2000 with a 1.2G Celeron and 256 Megs of mem.  Everything worked perfectly on first install except for the Intel 82852/855 graphics chipset (no drivers). I also had to install firmware for my ZyXel B-220 wireless dongle.  Other than that it runs flawlessly.

---

### Post by d3v1ant_0n3 on 2006-09-24
If you're shopping for a laptop in person (rather than looking online), why not take along a live cd with you and ask the sales people nicely if you can boot the laptop up with it (explain that it's not installing anything etc)...The functionality of the live cd should give you a good idea of how things are going to run.

---

### Post by LookTJ on 2006-09-25
I'm running Dell INSPIRON 600m with absolutely no issues :D

---

### Post by Taigrr on 2006-09-29
Okay, so far I have decided on this. Here's all the stats and such -
[http://www.bestbuy.com/site/olspage.jsp?skuId=7959006&type=product&id=1153336509992](http://www.bestbuy.com/site/olspage.jsp?skuId=7959006&type=product&id=1153336509992)

Looking at the specs and such, it seems like everything is pretty common. But, i'm posting it here just to be safe. Because it's a cheap laptop, that isn't a compaq, and eMachines seems to be up-and-comming as of late. 

I thank you all for your input =D Hopefuly someone will have an opinion on this laptop as well.

---

### Post by sbergman27 on 2006-09-29
> **Taigrr said:**
> Looking to buying a laptop for work, and want to put Linux on it.

Have a look at:

[http://tuxmobil.org/mylaptops.html](http://tuxmobil.org/mylaptops.html)

I recently bought a Compaq Presario V2552US at CompUSA for $549.

Everything works, including the broadcom wireless. (Requires ndiswrapper).  The modem I've never tried.  I suspect it doesn't work but don't care.  pcmcia modems are inexpensive if I need one.

---

### Post by gn2 on 2006-09-29
> **Taigrr said:**
> Okay, so far I have decided on this. Here's all the stats and such -
[http://www.bestbuy.com/site/olspage.jsp?skuId=7959006&type=product&id=1153336509992](http://www.bestbuy.com/site/olspage.jsp?skuId=7959006&type=product&id=1153336509992)

Looking at the specs and such, it seems like everything is pretty common. But, i'm posting it here just to be safe. Because it's a cheap laptop, that isn't a compaq, and eMachines seems to be up-and-comming as of late. 

I thank you all for your input =D Hopefuly someone will have an opinion on this laptop as well.

e-machines are fairly well established and are a budget brand in the UK.
This seems to be thecase with this laptop, 4200rpm hdd, cd-rw not dvd-rw.
It will have been made by an OEM manufacturer and just has e-machines branding.
Search the forums for info on the graphics chipset, and do some googling to see if you can find out what the wireless chip is, then another forum search for that.

If money is really tight there'a always eBay?

---

### Post by dppowell on 2006-09-29
Another vote here for the Dell Inspiron 600m.  Smoothest Linux setup I've ever had in my life.  Absolutely everything (volume buttons, internal Intel wireless, DVDRW combo drive) worked on first boot.

---

### Post by joshua5421 on 2007-07-02
which steps did you take to get the wireless card to work? I have the same laptop with 7.04 32 bit edition and I can't get the card to work. any suggestions?

---

### Post by ettienne on 2007-07-02
I ran Ubuntu on a Toshiba Satellite 2410-S203 for about a week, I'm back on WinXP due to too many problems.
I tried to run Google Earth, which needs 3D, which needs something else, which requires installing drivers for the NVIDIA graphics card and from there everything fell apart.

---

