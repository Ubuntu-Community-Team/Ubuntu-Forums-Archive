---
title: "For those of us stuck in the stone age of DIAL-UP, any Help?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by dspilman on 2008-02-06
I have recently installed Ubuntu and am gaining familiarity with it.  my biggest problem, is that at my home, in a section of Maryland in the country, there is no broadband service (save for satelitte which is more $$ then I can afford, and unreliable).  therefore I must resort to the stone age of Dial up service.  I need to know how to set this up in Ubuntu.  I can either use MSN dialup  or Net zero as my ISP, either one is fine, maybe one is easier to get working on Ubuntu then the other.  

I tried to do some research on this topic before posting.  I found that I needed to use ScanModem to detect which modem I have.  I did this, but now i need to know where to get the drivers from?  I am having no luck finding the drivers.  here is what the ScanModem result was:
                   Conexant HSF 56k Data/Fax Modem

After drivers are installed?  where do I go from there?  I have no idea what to do?  as to my knowledge, there is no program for Ubunutu for dialing the ISP (MSN, NetZero), as such there is in Windows.  Any help on this subject is greatly appreciated!  I would love to have internet access on my Ubuntu machine! Thank you

---

### Post by lamalex on 2008-02-06
Have you looked in System > administration > Restricted drivers manager
for an option for your internal modem? I don't know a lot about dial up, but there is some configuration you can if you click on the network-manager applet and select "manual configuration"

---

### Post by dspilman on 2008-02-06
yes i did try that.  the only one listed is the one for my nvidia gfx card

---

### Post by spiderbatdad on 2008-02-06
try using gnome-pppfixedforgutsy.deb  Setting up a dial-up is about as hard as it gets, as far as internet connection goes, in Ubuntu. Good luck.


[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by Joe Dinmore on 2008-02-06
Dell have this driver on their site. Kudos to them, because Conexant want to charge you for it.

[http://direct2dell.com/one2one/archive/2007/07/17/21325.aspx](http://direct2dell.com/one2one/archive/2007/07/17/21325.aspx)

I use dial-up in outback Oz, and it's way better than nothing. I found that using GnomePPP to set everything up saved a lot of headaches.

---

### Post by doorknob60 on 2008-02-06
Netzero actually DOES have a dialer program for Liinux, but it says it's only compatible with Linspire, but Linspire is based off Ubuntu so it might work. I have no way of testing it though because in order to download it you need to be paying for Netzero :(

---

### Post by Bartender on 2008-02-07
Are any of these numbers local for you?  
[http://shop2.outpost.com/isp/phone_prefixesMD.html](http://shop2.outpost.com/isp/phone_prefixesMD.html)
Fry's ISP works great with Linux.  Sometimes I get a faster connection than in vista.
I use a USR external serial modem.  Internal winmodems just too much work.  My laptop doesn't have a serial port so I use one of these:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008)
Ubuntu recognizes the adapter and runs it no sweat.  Have been unable to find a vista driver!
netzero horrible isp for linux.  I wouldn't use MSN if they paid me.

---

### Post by dspilman on 2008-02-07
thank you all so much for you help, greatly appreciated, i got things working now.  Ubuntu rocks, and the community is great.  So glad I decided to broaden my horizons past windows haha.

---

