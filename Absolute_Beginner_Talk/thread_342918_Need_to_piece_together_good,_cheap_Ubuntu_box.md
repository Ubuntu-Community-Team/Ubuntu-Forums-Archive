---
title: "Need to piece together good, cheap Ubuntu box"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Wartooth on 2007-01-20
The little emachine that I've made run with a spare HDD and Ubuntu is going to be given away.  The OTHER emachine that I've struggled with is going to be used for spare parts as it has quite a few issues that have caused me to do this: ](*,)  far too much.

So, I have this available for spare parts:

AMD Athlon 64 3400+ Socket 939
2 x 512MB DDR 400 RAM
40GB Western Digital HDD
TDK CD/DVD R/RW Drive

I'll also be using my KVM switch into my Gateway FPD2485W 24" LCD monitor. 

I am looking at this in which to put everything: [http://www.newegg.com/Product/Product.asp?Item=N82E16856110045](http://www.newegg.com/Product/Product.asp?Item=N82E16856110045)

So, theoretically, I could have an Ubuntu machine for about 100 bucks (yeah, I know, shipping, etc.). BUT, I am a little nervous after having searched for the VIA K8M800 video that comes with the Asus AV8-M board that is in that barebones.  I've seen the K8M800 come up in quite a few video problem related threads.  Am I being paranoid, or pessimisic, or is there real reason for concern?  I know there are no guarantees about any of it, but I would like to know whether it would be best to keep looking, or if I have a good shot at being successful with this.  Also am trying to find out if that video will do widescreen (1920x1200) and play well with my monitor.  I'm going to try to keep searching about that. 

Again, I've been at this whole Ubuntu/Linux thing for only a matter of days really, and although I've learned a LOT, I have a long, long, LONG way to go.  However, despite what I have run into (which is merely due to using existing, freebie hardware), I have enjoyed my experience thus far and would like to continue to have a second machine which runs Ubuntu.

Thanks in advance for any replies.

---

### Post by freebeer on 2007-01-20
I have a VIA chipset on the machine I'm typing this from, and I haven't had any issues.  Ubuntu recognized it just fine.  I have not, however, attempted to increase the resolution beyond 1024x768 as that is all this cheapie monitor that I have can handle.

---

### Post by BarfBag on 2007-01-20
If you can afford it, you should get an nVidia-based video card.  I don't think integrated graphics (correct?) could push out resolutions that high.  You don't have to get a card branded by nVidia (those are way too expensive).  You could just get an nVidia-based one.  Usually 128-256 MB VRAM models run from $40-$80 and in between.

---

### Post by Wartooth on 2007-01-20
I can afford a bit here and there, I just don't want to prove my husband right, as he's convinced I'm going to go overboard and spend tons of cash ;)

I do want to use this monitor as best as I can, so I looked at add-on video cards...I found this one: [http://www.newegg.com/Product/Product.asp?Item=N82E16814127121](http://www.newegg.com/Product/Product.asp?Item=N82E16814127121)
 
MSI MX4000-T128 GeForce MX4000 128MB DDR AGP 4X/8X

One of the positive reviews mentions Ubuntu specifically, and their webpage for this card boasts about Linux support.  It seems to have the resolution requirements I'm looking for. 

Is there anything I'm missing that would mean this card wouldn't be ideal for a budget build?  I don't know anything about potential conflicts between an onboard video and an additional card. I'm pretty functionally illiterate, in a sense, about piecing together hardware like this, but I've put a couple of machines together before without dismal failure :)

Thanks again!

---

### Post by freebeer on 2007-01-20
I've never experienced a problem with on-board video and an extra video card.  I've read where some people have had to disable on-board video in the BIOS (a simple process, or at least it should be).  I've never had to do it though.

---

### Post by Wartooth on 2007-01-23
Well, the card I had l linked up there is no longer available...POOF...gone.  Back to looking...hmph.

---

### Post by punx45 on 2007-01-23
i have a GeForce MX400, and while i was able to get the proprietary nvidia driver going, it was a bit of a headache.   while doing research for a new PVR box that i am building  the GeForce FX 5200 was a commonly mentioned card, and appears to be widely supported.   it can be had for pretty cheap on newegg, and in most iterations of the card it supports VGI, DVI, and S-VIDEO, so you are prepared for pretty much every display situation.

also, [see here for VIA drivers]("http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=109").   they are apparently fairly linux friendly.

---

### Post by Wartooth on 2007-01-23
Interesting. I appreciate your mentioning that as I was looking at those cards just a few minutes ago.  I'm one of those kind that has a hard time rationalizing 100 bucks on a video card when I'd be putting it into a mobo/case/PSU combo that I got for the same amount of money.  :)

---

### Post by houstonbofh on 2007-01-23
Build it with the onboard video.  It will have slow 3D but should work.  If you find it does not do what you need, pick up a used nvidia 5x00  I bought one yesterday for $25.

---

### Post by Wartooth on 2007-01-24
Well, then, additional stupid question time:  Is upgrading later, after a clean install of Ubuntu, likely to be any more of a pain than just setting up a new machine?  If it generally isn't too big of a deal, then I might just order the barebones, put it together, and see what happens.  If it tends to be a pain, then I might just go ahead and get the add-on now.

---

### Post by houstonbofh on 2007-01-24
Very simple.  You just need to chose an nvidia driver (xwindows, repository binary, nvidia binary) and select it in the xorg.conf file.  There are several ways to do this as well.  Worst case (no video on boot) you can boot the live CD, and make your xorg.conf file on the hard drive match the one in the LiveCD virtual file system.

---

### Post by punx45 on 2007-01-24
whether you add it now, or add it later, you will have to undergo the same process to add the "good" nvidia driver.

---

