---
title: "Which videocard to buy"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Kevf on 2007-05-04
I'm getting pretty fed up with my ati radeon xpress chipset and ubuntu or any other distro. So I've decided to buy a new videocard in the near future.

Which one to pick. I don't want anything fancy, but it would be nice if I could get some eyecandy with feisty/compiz I'm currently installing. 

I don't play games on my pc (got a 360 for that :P), and I want it to be as cheap as possible,

Which one do you recommend in combination with feisty?

---

### Post by Kobalt on 2007-05-04
If you find a cheap nVidia card I believe it would satisfy you... something like a GeForce4 MX440 is the cheapest I can think of and beryl/compiz capable.

---

### Post by Surkow on 2007-05-04
> **Kevf said:**
> I'm getting pretty fed up with my ati radeon xpress chipset and ubuntu or any other distro. So I've decided to buy a new videocard in the near future.

Which one to pick. I don't want anything fancy, but it would be nice if I could get some eyecandy with feisty/compiz I'm currently installing. 

I don't play games on my pc (got a 360 for that :P), and I want it to be as cheap as possible,

Which one do you recommend in combination with feisty?

Please list your current system specs. Otherwise choosing a graphics card can be very difficult. Nvidia has a range of well supported graphics cards where you can choose from.

---

### Post by hardyn on 2007-05-04
I just bought a geforce 6200 for less than 50$ cdn... and it allows you to use the nvidia-glx-new drivers.
it runs compiz okey, if you have the funds, i would step up to a 6600.

you do not want to get into a situation where you have to used depreciated drivers.

---

### Post by houstonbofh on 2007-05-04
Nvidia 7xxx cards are at $100 now.  And I have never heard anyone say, "Darn.  My card is just too powerful!"

---

### Post by igknighted on 2007-05-04
The cheapest cards still supported by NVIDIA are the FX series (5200-5900).  I might go with the 6000 series just to ensure future support as well.  There are still legacy drivers available for older hardware of course, but they may not support the next generation of 3d desktops or anything like that as technology changes.

---

### Post by Kevf on 2007-05-04
Tnx for the replies so far. Sorry for not posting my specs:

Asus Pundit Barebone
Intel pentium 2,6 GHz
512 mb Ram
250 gig hd

---

### Post by ruimoura on 2007-05-04
I wouldn't go for something lower than a 7xxx series, because they are pretty recent and cheap. Oh, and you have PCI xpress ou still AGP ? If you are stuck with AGP, you don have much of a choice, but you can get a 6600 that are pretty nice (7xxx AGP are more expensive). If you have PCI xpress you can get a nice 7300 gs for something like &#8364;70 (here in Portugal), that's about 60 us dollars, and if you can push it a little you can get a 7600 gs for about 90 us dollars.

---

### Post by Kevf on 2007-05-04
I think I have pci-express (that's the type of the slot right?). 

Anyway of checking that?

---

### Post by walesmd on 2007-05-04
May I ask why you are upset with this card and Ubuntu? I have an ATI Radeon 9600 and have never had an issue...

---

### Post by ruimoura on 2007-05-04
> **walesmd said:**
> May I ask why you are upset with this card and Ubuntu? I have an ATI Radeon 9600 and have never had an issue...

Dude, i know what he is talking about. ATI drivers for linux are a total crap, and don't even support AIGLX (if you want to use beryl or compiz you need XGL). 

@Kevf: the only way i know to see that is to open the box and see if you board has pci express (little  slots) or AGP (huge slots) for the graphics card.

---

### Post by Kevf on 2007-05-04
> **walesmd said:**
> May I ask why you are upset with this card and Ubuntu? I have an ATI Radeon 9600 and have never had an issue...

Just surf the internet for a bit and you'll find tons of problems. Opening the box it will be! 

Give you an answer asap.

---

### Post by justleen on 2007-05-04
i bought a Nvidia 6200, for 45 euro..  works like a charm with all the eyecandy!

---

### Post by walesmd on 2007-05-04
hmm... maybe it's cause I don't intend to use Compiz/Beryl. Everything works fine for the few games I play though.

---

### Post by Kevf on 2007-05-10
Opened the computer yesterday. Seems that I only have 'normal'  pci? 

Isn't that a bit out of date?

Anyway, which card to buy?

---

### Post by lamalex on 2007-05-10
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814170114](http://www.newegg.com/Product/Product.aspx?Item=N82E16814170114)

buy that one.

---

### Post by Kevf on 2007-05-10
Nice comments on the right side :confused:

---

### Post by reckless2k2 on 2007-05-10
Don't buy an ATI. Get anything NVIDIA. It is much more heavily supported in Linux. Depending on if you have AGP, PCI, or PCI-E, the 5200 line is reasonable in price.

---

### Post by orb9220 on 2007-05-10
> Opened the computer yesterday. Seems that I only have 'normal' pci?


No If you have a usually long blue slot sitting all by itself that is a agp slot.
Just type your mobo in google or look in manual and get the specs on your motherboard to see 
Exactly what you have.

Do not Guess! Know what your system has.

---

### Post by Kevf on 2007-05-11
I'll never buy an ati. I have a ati chipset at the moment and its terrible with ubuntu

maybe someone here can find which slot I have?

complete specs

1 x SAMSUNG 250Gb SATA II 8Mb SP2504C () = €73.77
1 x Twinmos / M-tec DDRII 533mhz 512MB (3958) = €35.47
1 x ASUS INTEL S775 PUNDIT1 P1-PH1 ID1 (9440248) = €144.98
1 x Intel Cel D326 2.5G 533/256 64 775 B () = €46.89

Including prices :lolflag:

---

### Post by arkangel on 2007-05-11
> **orb9220 said:**
> No If you have a usually long blue slot sitting all by itself that is a agp slot.
Just type your mobo in google or look in manual and get the specs on your motherboard to see 
Exactly what you have.

Do not Guess! Know what your system has.

DITO   , if your ati  is there, even when doesnt work well, try to see the type you have using lspci

there must a line like  00.00.00 PCIE Ati something or PCI ..

---

### Post by Kevf on 2007-05-11
```
kevin@kevin-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
kevin@kevin-desktop:~$ 

```

That did the trick! 
Tnx. Ok so I have a normal pci :( 

What is the best/cheapest (nvidia)solution?

---

### Post by houstonbofh on 2007-05-11
> **Kevf said:**
> 
Tnx. Ok so I have a normal pci :( 

What is the best/cheapest (nvidia)solution?
I seriously doubt it.  Not with a socket 775 CPU from Asus.  You need to find a link to your motherboard.  Post it, and we can tell you.  I am betting PCI-E, but without telling us the motherboard, we are guessing.  And a google of "ASUS INTEL S775 PUNDIT1 P1-PH1 ID1" was unhelpful.

---

### Post by Kevf on 2007-05-15
This is the link to my barebone:

[http://www.asus.com.tw/products.aspx?l1=1&l2=3&l3=408&l4=0&model=999&modelmenu=2](http://www.asus.com.tw/products.aspx?l1=1&l2=3&l3=408&l4=0&model=999&modelmenu=2)

Looks like a normal pci to me

---

### Post by houstonbofh on 2007-05-15
No wonder I could not find it in "motherboards!" :)  And you are correct.  No advanced graphics slot.  Sorry...  As to solutions, you are in a bind.  I have seen 5500s on PCI, but the buss is so slow, they will be slower than other 5500s.  Try [http://search.ebay.com/ws/search/SaleSearch?sofocus=bs&satitle=nvidia+pci&sacat=-1%26catref%3DC5&fbd=1&sorefinesearch=1&from=R14&nojspr=y&pfid=0&fswc=1&few=express+pci-e&saprclo=&saprchi=&fss=0&saslop=1&sasl=&fls=4%26floc%3D1&sargn=-1%26saslc%3D0&salic=1&saatc=1&sadis=200&fpos=77550&fsct=&sacur=0&sacqyop=ge&sacqy=&ftrt=1&ftrv=1&sabdlo=&sabdhi=&saaff=afdefault&afcj=&afmp=&fsop=1%26fsoo%3D1&fcl=3&frpp=50](http://search.ebay.com/ws/search/SaleSearch?sofocus=bs&satitle=nvidia+pci&sacat=-1%26catref%3DC5&fbd=1&sorefinesearch=1&from=R14&nojspr=y&pfid=0&fswc=1&few=express+pci-e&saprclo=&saprchi=&fss=0&saslop=1&sasl=&fls=4%26floc%3D1&sargn=-1%26saslc%3D0&salic=1&saatc=1&sadis=200&fpos=77550&fsct=&sacur=0&sacqyop=ge&sacqy=&ftrt=1&ftrv=1&sabdlo=&sabdhi=&saaff=afdefault&afcj=&afmp=&fsop=1%26fsoo%3D1&fcl=3&frpp=50)

---

### Post by Josey on 2007-05-15
This is the card you want....

[http://www.amazon.com/XFX-GeForce-6200-DDR2-Video/dp/B000CQ73PW/ref=pd_bbs_sr_1/102-9251312-3484909?ie=UTF8&s=electronics&qid=1179246286&sr=8-1](http://www.amazon.com/XFX-GeForce-6200-DDR2-Video/dp/B000CQ73PW/ref=pd_bbs_sr_1/102-9251312-3484909?ie=UTF8&s=electronics&qid=1179246286&sr=8-1)

The link you have for your motherboard doesn't say whether or not it even has a graphics expansion slot.  My link is for an agp.

After looking around briefly I'm not even sure your machine has a slot for a graphics card.... correct me if I'm wrong.

All I've found is that graphics are integrated and they never say anything more about it.

---

### Post by houstonbofh on 2007-05-15
> **Josey said:**
> This is the card you want....

[http://www.amazon.com/XFX-GeForce-6200-DDR2-Video/dp/B000CQ73PW/ref=pd_bbs_sr_1/102-9251312-3484909?ie=UTF8&s=electronics&qid=1179246286&sr=8-1](http://www.amazon.com/XFX-GeForce-6200-DDR2-Video/dp/B000CQ73PW/ref=pd_bbs_sr_1/102-9251312-3484909?ie=UTF8&s=electronics&qid=1179246286&sr=8-1)

The link you have for your motherboard doesn't say whether or not it even has a graphics expansion slot.  My link is for an agp.

His motherboard has 2 PCI slots only, and the link says this.  You choice will not work.

---

### Post by Kevf on 2007-05-24
other suggestions?

---

### Post by Kevf on 2007-05-25
none?

---

### Post by Outrunner on 2007-05-25
This seems to have good reviews [http://www.newegg.com/Product/Product.aspx?Item=N82E16814122205](http://www.newegg.com/Product/Product.aspx?Item=N82E16814122205)

I have a GeForce 6200 as well(from ASUS) and it's not exactly great for gaming but it works well for more general tasks.

---

### Post by Mizled on 2007-05-25
> **Outrunner said:**
> This seems to have good reviews [http://www.newegg.com/Product/Product.aspx?Item=N82E16814122205](http://www.newegg.com/Product/Product.aspx?Item=N82E16814122205)

I have a GeForce 6200 as well(from ASUS) and it's not exactly great for gaming but it works well for more general tasks.

That's a PCI-E. He cant use those. 

Any of these here will work for your computer and are GeForce cards.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642+106790727&name=GeForce+FX+series](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642+106790727&name=GeForce+FX+series)

With only PCI slots you're not going to find a great graphics card. You will be limited to your selection. Most of them on the link I posted should run the eye candy for Beryl, etc. If you want something better you will need to upgrade your Motherboard to have an AGP slot or even better a PCI-E slot. Hope this helps.

---

### Post by Kevf on 2007-05-25
Tnx a lot!!! You really helped me out :D

---

