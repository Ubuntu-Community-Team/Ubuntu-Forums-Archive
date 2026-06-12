---
title: "Very Simple Laptop Question"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Max Roswell on 2006-07-07
Hey, all...

I've been using Ubuntu on my desktop for about 4 months now, and I'm a true believer.  I finally saved enough scratch to go buy myself a laptop.  I've been combing threads here, and the Wiki, and various Google searches, trying to find out what machines might be a good choice.

It's a little dizzying, you know? 

So straight-up - if I buy this laptop:
[http://www.newegg.com/Product/Product.asp?Item=N82E16834115231](http://www.newegg.com/Product/Product.asp?Item=N82E16834115231)

Will I have any major issues?  I'm mostly concerned with wireless (ndiswrapper is OK) and the 64-bit thing.  I don't want to spend too much time tinkering under the hood, so I'll probably just use a 32-bit kernel unless that's asking for trouble.  I intend to use Ubuntu 90% of the time, but will probably dual-boot XP because I'm paying for it, so I might as well keep it.

Thanks in advance!

---

### Post by ovimunt on 2006-07-07
Hi,

I have an Acer laptop too and I didn't have any major issues.

Yet, for Acer laptops, there are a couple of things you'll need to tweak before you'll get it up and running. I don't think it will work "out of the box" so you'll need to fiddle "under the bonnet" a bit.

---

### Post by T700 on 2006-07-07
System 76 has a good reputation.  Preloaded with Ubuntu.

[SIZE=-1][COLOR=#008000]_[www.**system76**.com/]("http://www.ubuntuforums.org/www.system76.com/")_

[COLOR=Black]Paul[/COLOR]
[/COLOR][/SIZE]

---

### Post by lordlollo on 2006-07-07
> **ovimunt said:**
> Hi,

Yet, for Acer laptops, there are a couple of things you'll need to tweak before you'll get it up and running. I don't think it will work "out of the box" ...

I have an old travelmate 1310 and it did work out of the box...
Yeah, the 56k modem was just another thing...

IMO, Dell rules.

---

### Post by Max Roswell on 2006-07-07
I like the System 76 machines, but they're definitely on the pricey side.  I'm looking to maximize the bang for my buck, here.  I'm willing to do *some* work to get Ubuntu up and running - but I don't want to have to spend a ton of frustrated nights trying to get my new toy to work, you know?  Theoretically, I'm buying a laptop to get MORE work done, not less.

---

### Post by lordlollo on 2006-07-07
> **Max Roswell said:**
> I'm looking to maximize the bang for my buck, here.

ACER laptops are very good value for money.

---

### Post by barrack on 2006-07-07
> **lordlollo said:**
> ACER laptops are very good value for money.

Does anyone have any experience with Everex? It's the cheapest laptop I can find that has decent specs.

---

### Post by BPG on 2006-07-07
> **ovimunt said:**
> Hi,

I have an Acer laptop too and I didn't have any major issues.

Yet, for Acer laptops, there are a couple of things you'll need to tweak before you'll get it up and running. I don't think it will work "out of the box" so you'll need to fiddle "under the bonnet" a bit.

I have an Acer 1682 WLMI and had heaps of trouble trying to get hoary & Breezy to run, but Dapper runs out of the box.

I nearly fell off my chair when I heard sound at the login screen when I booted up Dapper.:o Recognised the wide screen display and set a readable resolution etc.

Only required minor tuning of network settings and ATI gfx driver. Very, very cool!!!:D

---

### Post by ovimunt on 2006-07-07
Right, the glitches you'll get on an Acer Aspire 5024WLMi are the following:

1. No graphics immediately after instalation - Ubuntu tries to output the image to the standard monitor connector instead of the laptop screen - SOLUTION: edit the /etc/X11/xorg.conf file in text mode to tell it to look for additional display devices - very simple

2. Wireless card is a Broadcom 43xx so it won't work "out of the box" - yet, you DON'T need ndiswrapper! Dapper has the drivers for it but no firmware. SOLUTION: install firmware - very simple, there is a guide on Wiki about how to do that or I could assist if required

3. Wireless will still not work even with the firmware. This is because this Acer laptop has a button to enable/disable the wireless and this doesn't work in linux. SOLUTION: install a bit of software that will enable/disable the function without using the button.

4. Graphics card is an ATI Mobility Radeon X700 - usually simple to install proprietary drivers but might have some difficulties.

As far as I'm aware EVERYTHING ELSE will work "out of the box"

---

### Post by Max Roswell on 2006-07-07
> **ovimunt said:**
> Right, the glitches you'll get on an Acer Aspire 5024WLMi are the following:

(snip)

As far as I'm aware EVERYTHING ELSE will work "out of the box"

Well, that doesn't seem like so much.  About what I expected.  I assume the software for #3 above is easy to come by?

---

### Post by ovimunt on 2006-07-07
The first time round it took me 2 weeks of Ubuntu pain to sort it all out. Now it only takes me about 2 hours to install everything.

In any case I am aiming to provide a FULL Acer Aspire 5024WLMi installation guide very soon.

---

### Post by Frank Golden on 2006-07-07
[http://www.bhphotovideo.com/bnh/controller/home?A=details&kw=ACAS5672WLMI&is=REG&Q=&O=productlist&sku=439361](http://www.bhphotovideo.com/bnh/controller/home?A=details&kw=ACAS5672WLMI&is=REG&Q=&O=productlist&sku=439361)
Check out the above link for Acer Aspire as5672WLMi.
It is  a great buy and will work out of box with Ubuntu 6.06 LTS
(Dapper). You will still need to update to ATi propritary drivers
after install to use all the 3-D features of the X1400 video card
as well as the native 1280x800 native resolution.[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
You should use Synaptic after install to update to the 686 smp kernel to make full use of the Core Duo processors features.
The machine comes with a Panasonic DVD dual layer burner.
To play commercial DVD movies in Ubuntu you need to choose a DVD
region in Windows on this drive, it comes unset. You will also need to run EasyUbuntu [http://www.google.com/search?sourceid=navclient&ie=UTF-8&rls=GGLG,GGLG:2006-18,GGLG:en&q=EasyUbuntu](http://www.google.com/search?sourceid=navclient&ie=UTF-8&rls=GGLG,GGLG:2006-18,GGLG:en&q=EasyUbuntu) to add restricted multimedia codecs.
You would need to do this on any laptop to play DVD movies or MP3
files etc.
Wi-Fi works.
Check out this thread for agreat deal of info on this great laptop.
[http://ubuntuforums.org/showthread.php?t=121125](http://ubuntuforums.org/showthread.php?t=121125) 
Look around you may find a better deal.
If you get this machine save your pennies and get another Gig of ram. Mine came with 2GB but cost more. You can get (2)1GB sticks of DDR2-PC5300 for around $220.00 USD. Again look around.
This is a great machine for Ubuntu.
See my sig for system details.
E-mail me if you want more info.
I love my Acer.

---

### Post by Frank Golden on 2006-07-09
[http://www.notebookforums.com/thread162284.html](http://www.notebookforums.com/thread162284.html)
Check out this link.
Compusa online is offering 5672 for much reduced price.

---

