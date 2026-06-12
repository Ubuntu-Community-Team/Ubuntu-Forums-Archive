---
title: "Problem with graphic card"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by ghih on 2006-11-30
Hi,

I just installed ubuntu an hour ago.
everything went fine.
Exept one thing, my graphic card doens't got recognised by the system.
My screen is ok and so does the colors.
The big problem is when e.g. i'm browsing the internet and I scroll down, it goes down in pieces and not smooth like it must be.

It's an internal graphical card:

vendor: S3 graphics (VIA chrome9 HC IGP)

integrated in the motherboard (MSI K9VGM-V)

anyone knows how to solve this problem?

thanks in advantage


maybe handy to know:
pc specifications:

- AMD Sempron 3000+
- 512MB DDR2 RAM
- 40Gig for winXP
- 40Gig for linux ubuntu

---

### Post by K.Mandla on 2006-11-30
Try setting the color depth to 16. Edit the xorg.conf file like this:

```
sudo nano /etc/X11/xorg.conf
```
Find the line that says 

```
DefaultDepth 24
```
and change the 24 to 16. Press CTRL+O to save the file, CTRL+X to close it. Then restart.

If this doesn't fix it, you can change it back to 24 the same way.

---

### Post by ghih on 2006-12-01
First, thanks for the quick reply.

I tried your tip but it still goes in shocks when I scroll down.
if I look to the hardware I see that the VIA graphic card is not installed
It says unknown in the devices list.

how does this come and how can I fix it.


thanks in advantage

---

### Post by Delkster on 2006-12-01
> **ghih said:**
> if I look to the hardware I see that the VIA graphic card is not installed
It says unknown in the devices list.

how does this come and how can I fix it.

Can you take a look at /etc/X11/xorg.conf again and find in the file the section similar to the following:
```

Section "Device"
        Identifier  "..."
        Driver      "..."
        ...
EndSection

```
In particular, could you find out what is specified on the "Driver" line there in the "Device" section?

---

### Post by ghih on 2006-12-01
I got the following:

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

---

### Post by ghih on 2006-12-02
IS this not good configurated or something?

---

### Post by ghih on 2006-12-02
Can someone pls help me with this problem.

thanks in advantage

---

### Post by Delkster on 2006-12-05
> **ghih said:**
> I got the following:

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"

EndSection


IS this not good configurated or something?


No, it's not very good. VESA is a generic driver compatible with practically every PC (x86) graphics board manufactured since the early 90's so it generally works even if you don't have a specific driver available for your graphics chip. The downside is that it's pretty slow. That would probably explain the problems you experience with scrolling.

Unfortunately, I don't know about Linux support for your graphics chip. What little I've been able to find has suggested that it may be that there's no open source driver for the card, only a proprietary one from S3 (and thus probably not included in Ubuntu). I'll try to see if I can find something a bit later, but if someone else knows, by all means let us know.

Meanwhile, you could try replacing "vesa" in the configuration with "s3" and rebooting, but note that this is only guesswork and if the S3 driver of X.org doesn't happen to support your chip directly, the X server (graphical user interface) will fail to start, so please **only do this if you know how to use the command line enough to change it back to vesa if it doesn't work!** In fact I'd guess that the driver doesn't support your chip -- if it did, the X server would probably have been configured for it automatically already.

---

### Post by CatKiller on 2006-12-05
The **via** driver says that it supports "VIA/S3... UniChrome cards," but I have no idea at all whether that is the same thing at all.

Ah. Apparently VIA have closed off their drivers for reasons they haven't made clear. Or something. Maybe they'll give you the driver themselves, though? I have no idea how you'd go about installing something from them.

---

### Post by klittzzer on 2006-12-05
You can check this out, if you haven't already.

[http://forums.viaarena.com/categories.aspx?catid=28&STARTPAGE=3&FTVAR_FORUMVIEWTMP=Linear](http://forums.viaarena.com/categories.aspx?catid=28&STARTPAGE=3&FTVAR_FORUMVIEWTMP=Linear)

 I am looking to find a driver for my Via/SG3 Unichrome Pro IGP because I have the same scrolling problem. Moving a frame around the screen leaves trails and is annoying. The worst bit, however, (and I don't know if this is due to the graaphics driver???) happens when I type. Every few words, if I hit, for eg, the letter a once, about fifty fly across the screen. I would try reinstalling Ubuntu 6.10 Edgy but I have only just managed to configure a modem and get on the web (taken 3 weeks of frustration). I would like to be able to try 6.06 LTS but am fed up losing discs due to 'write errors'( I have used 4 diff burners at x1 x4 x8 and never faster. 
Seems a bit buggy but if it means I can evict Bill Gates from my life.
It is worth it

KZ

---

