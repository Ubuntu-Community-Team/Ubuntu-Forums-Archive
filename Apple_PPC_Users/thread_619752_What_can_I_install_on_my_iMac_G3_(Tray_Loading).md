---
title: "What can I install on my iMac G3 (Tray Loading)?"
date: 2007-11-21
forum: Apple PPC Users
---

### Post by ECas123 on 2007-11-21
Hello, I have an iMac G3 that I bought at a garage sale for 5 dollars. I'm not sure what the exact specifications are but I do know this: It's running Mac OS 8.6, It has a tray loading, and it has a 6 gig drive. I've gone through to many discs to give up so I want your opinion. What kind of Ubuntu can I run on this thing!? When I insert an Ubuntu or Xubuntu disc and boot nothing happens, I hold down C but still. It's managed to get a Debian disc in it but I can't install it. What (in any) version of Ubuntu can I put on this thing? Thanks.

---

### Post by PaganHippie on 2007-11-21
I've got Feisty (7.04) running on mine.  It's quite stable.

Get an Alternate Install disc rather than a Live CD (you may not have anough RAM to run the Live CD), and of course make sure you have the PPC version and not x86 or one of the other ports.  Your Mac should boot off the Alternate CD by holding down C after the chime as you normally would to boot off a CD.

If the Alternate disc fails to boot, you may simply not have enough RAM, or your CD-ROM drive might possibly be faulty

You should be able to find out how much RAM is in there by selecting "About This Computer" from the Apple menu; if it's less than 64MB either install more or forget about Ubuntu and try Debian or maybe Slackintosh.  If it's more than 64 but less than 256MB, you could probably shoehorn Xubuntu in there, although I'm running regular Gnome Ubuntu with 160MB.  If it's 256 or over, you should be good to go.  Unless....

Does it read other discs while in Mac OS?  If the CD-ROM drive itself is bad, you can either replace it (possibly tricky) or find another way to launch the installer.  There's nearly always a "plan B."

---

### Post by ECas123 on 2007-11-21
> **PaganHippie said:**
> I've got Feisty (7.04) running on mine.  It's quite stable.

Get an Alternate Install disc rather than a Live CD (you may not have anough RAM to run the Live CD), and of course make sure you have the PPC version and not x86 or one of the other ports.  Your Mac should boot off the Alternate CD by holding down C after the chime as you normally would to boot off a CD.

If the Alternate disc fails to boot, you may simply not have enough RAM, or your CD-ROM drive might possibly be faulty

You should be able to find out how much RAM is in there by selecting "About This Computer" from the Apple menu; if it's less than 64MB either install more or forget about Ubuntu and try Debian or maybe Slackintosh.  If it's more than 64 but less than 256MB, you could probably shoehorn Xubuntu in there, although I'm running regular Gnome Ubuntu with 160MB.  If it's 256 or over, you should be good to go.  Unless....

Does it read other discs while in Mac OS?  If the CD-ROM drive itself is bad, you can either replace it (possibly tricky) or find another way to launch the installer.  There's nearly always a "plan B."

Well I always do get the alternative version. and it never boots even if I do hold down C. When I insert a debian cd it does boot but I'm not sure what to type to get it installed. I type install but it just takes me a white screen.

---

### Post by ECas123 on 2007-11-21
Okay, in the about this computer it reads:
Built-In Memory: 32 MB
Virtual Memory: 64MB used on Macintosh HD
Largest Unused Block: 50.9MB
Good or bad?

---

### Post by PaganHippie on 2007-11-21
32MB is not a lot of memory these days.  Ubuntu is pretty much out of the question without more RAM than that.  You could install more, it's still pretty readily available.

I'm very surprised that Debian hung up on you like that.  Instead of "install" try just pressing (enter) at the Debian boot prompt and see what happens.

 The only other PPC distro that I can think of that might work in only 32MB is Slackintosh.  If you're not married to Linux, you could probably also get NetBSD to work.

---

### Post by bodycoach2 on 2007-11-22
You'll need at least 128 mb ram for even the Alternate Install CD to work. Ram for those iMacs are pretty cheap. If you get Slackintosh to work, let us know. Also, check out [lowendmac.com]("http://lowendmac.com") for more information on your iMac.

---

### Post by PaganHippie on 2007-11-22
I've seen the Alt CD work with as little as 64MB, but in that case it seems to do only a minimal install.

More RAM is never a bad idea.

---

### Post by chromebox on 2007-11-22
> **PaganHippie said:**
> Does it read other discs while in Mac OS?  If the CD-ROM drive itself is bad, you can either replace it (possibly tricky) or find another way to launch the installer.  There's nearly always a "plan B."

This is my case! The tray-loading CD-drive is broken. I've got a [[COLOR="Blue"]bondi blue iMac[/COLOR]]("http://www.everymac.com/systems/apple/imac/stats/imac_ab.html")... With 64MB ram and 4GB hard drive. So, what's plan B?

---

### Post by oswaldkelso on 2007-11-22
> **ECas123 said:**
>  It's managed to get a Debian disc in it but I can't install it. 



How to install Debian on imac, emac powerpc. Very verbose setup instrutions

[http://www.my2bits.org/?p=76]("http://www.my2bits.org/?p=76")

---

### Post by oswaldkelso on 2007-11-22
> **chromebox said:**
> This is my case! The tray-loading CD-drive is broken. I've got a [[COLOR="Blue"]bondi blue iMac[/COLOR]]("http://www.everymac.com/systems/apple/imac/stats/imac_ab.html")... With 64MB ram and 4GB hard drive. So, what's plan B?

Ebay and a new drive? or swop the HD  into another mac, install and swop it back. Those are the easy options.

---

### Post by PaganHippie on 2007-11-22
It might also be possible to launch the installer from an external, USB-connected CD drive using BootX.

---

### Post by ECas123 on 2007-11-23
Alright I guess I'll go with Slackintosh. I'm looking at the download page for CD's but I see
```
[   ] slackintosh-12.0-install-d1.iso 14-Jul-2007 13:37   634M  
[   ] slackintosh-12.0-install-d2.iso 14-Jul-2007 13:38   516M  
[   ] slackintosh-12.0-install-d3.iso 14-Jul-2007 13:39   483M  
[   ] slackintosh-12.0-install-d4.iso 14-Jul-2007 13:41   634M  
```

Do I really need to download and burn all 4 of those isos?

---

### Post by PaganHippie on 2007-11-24
No, you can install with just disc 1.  The others contain extra software that you may or may not want.  You can always grab them later if you need them.

Good luck & let us know how it works out.

---

### Post by ECas123 on 2007-11-24
> **PaganHippie said:**
> No, you can install with just disc 1.  The others contain extra software that you may or may not want.  You can always grab them later if you need them.

Good luck & let us know how it works out.

Alright, I got it burned and booted from it. The first black screen pops up and I hit install and then it takes me to a black screen reading
```

done
copying OF device tree....
Can't allocate initial device-tree chunk
DEFAULT CATCH, code=900 at SRR0: ff81ab68 SRR1: 0000b030
Apple iMac Open Firmware 3.0. f3 biult on 07/16/99 at...
ok
0 >
```
What does this mean and how do I get around it?

---

### Post by oswaldkelso on 2007-11-24
> **ECas123 said:**
> Alright, I got it burned and booted from it. The first black screen pops up and I hit install and then it takes me to a black screen reading
What does this mean and how do I get around it?

You may need to reset your p-ram also check your firmware is up to date


[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

[http://docs.info.apple.com/article.html?artnum=42642](http://docs.info.apple.com/article.html?artnum=42642)

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

[http://docs.info.apple.com/article.html?artnum=60384](http://docs.info.apple.com/article.html?artnum=60384)

---

### Post by ECas123 on 2007-11-24
Alright, I'm confused. I got to the white screen and typed reset-nvram then hit return, hit  reset-all, and the iMac rebooted. I booted into the CD and the same thing happend when I typed install. Also I'm not sure which is the latest firmware for the Mac or how to install it. (I'm a real mac n00b)

---

### Post by Luigi239 on 2007-11-24
Sorry, I haven't read through this entire thread, so I am not sure if this has been solved or not, but this is what I did to fix that exact same issue.

I took a regular q-tip, sprayed it with some regular glasses cleaner, and wiped the lens of the CD drive. I then used the other side of the Q tip to dry the lens. 5 minutes later, the damn thing worked.

Good luck! :)

---

### Post by ECas123 on 2007-11-24
So doing that gave you more ram, reset the PRAM, and installed linux on the iMac G3? You should really read the thread.
[Note: if I have offended you I'm sorry, I'm a little testy and I haven't had mah coffee all day!]

---

### Post by PaganHippie on 2007-11-25
Try just pressing "enter" instead of typing "install" at the boot prompt.  You might be inadvertently launching something that your setup can't handle.  (I haven't tried Slackintosh myself.)

---

### Post by ECas123 on 2007-11-25
All the times I've either typed install, or hit enter and the same things always happend.

---

### Post by PaganHippie on 2007-11-25
At this point, my best advice to you would be to get more RAM, at least 256MB,  and try again with Ubuntu.

---

### Post by ECas123 on 2007-11-25
I don't really want to spend that much on it. How much would 256MB cost?

---

### Post by PaganHippie on 2007-11-25
A quick check on the web shows that they can be had for ~ $20 if you shop carefully.

---

