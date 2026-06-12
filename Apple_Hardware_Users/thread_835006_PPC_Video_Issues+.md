---
title: "PPC Video Issues+"
date: 2008-06-20
forum: Apple Hardware Users
---

### Post by neizvestno on 2008-06-20
So,

I've tried the community supported PPC 8.04 on my G4 mirrored drive door mac and had significant video issues. All colors distorted/text unreadable/etc.

So I went back to 6.10 Ubuntu and while the drivers work I am not able to go higher than 800x600 resolution.

Additionally I always have to zap PRAM and hold CMD+OPT+SHIFT+DEL to boot from the drive I have Ubuntu installed to.

These problems were probably solved years ago but my endless Googling and headthrashing have not fixed my own problems.

Can anyone lend guidance? Many thanks.

---

### Post by stream303 on 2008-06-20
> **neizvestno said:**
> I've tried the community supported PPC 8.04 on my G4 mirrored drive door mac and had significant video issues. All colors distorted/text unreadable/etc.

Ok, there are three versions of mirror-door powermacs, one with an nvidia card, one with a radeon 9000, and one with a radeon 9000 pro.  This might be part of the problem.  Which one do you have?

[http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html](http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html)

Also, what size / brand / model of monitor are you using?

> So I went back to 6.10 Ubuntu and while the drivers work I am not able to go higher than 800x600 resolution.

In this case, you might be able to get it to reconfigure with the older

```
sudo dpkg-reconfigure -phigh xserver-xorg
or
sudo dpkg-reconfigure xserver-xorg
```

Note that in Hardy, your video card is no longer a part of this old standby for reconfiguring the xserver, so we can get some very valuable info from 6.10 here should we run into problems later with Hardy.

Even though it is not performing perfectly, make a copy or write down your 6.10 /etc/X11/xorg.conf, and /etc/yaboot.conf.  These may contain some very valuable data that we can put into Hardy's config.

> Additionally I always have to zap PRAM and hold CMD+OPT+SHIFT+DEL to boot from the drive I have Ubuntu installed to.

This is odd - sounds like you may want to make sure that either of these two commands are performed:

```
sudo ybin -v -C /etc/yaboot.conf
```

in addition you could try

```
mkofboot -v -C /etc/yaboot.conf
```

I've had to run mkofboot on some install-resistant drives before for some reason - the more knowledgeable yaboot gurus can probably point out why...

Be sure to see the powerpc faq especially in regards to making sure that your video drive is either "nv" or "radeon" depending on which mirror-door model you have:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

We'll be glad to help - in fact, if you could post your 6.10 /etc/X11/xorg.conf and possibly your /etc/yaboot.conf here, that would make a great starting point.

---

