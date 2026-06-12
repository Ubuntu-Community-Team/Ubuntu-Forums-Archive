---
title: "How stable is ubuntu on PPC?"
date: 2008-02-09
forum: Apple PPC Users
---

### Post by sammydee on 2008-02-09
Hi all

I have a friend who is contemplating buying a mac mini. The older ppc G4 versions are much much cheaper than the new x86 ones, but obviously they are slightly slower and less compatible.

He wants to use the mini as a media centre pc and maybe a network storage drive (with an attached usb drive).

How stable is ubuntu on ppc generally? Would you recommend going for the new mini (3-4 times the price) or the older mini? Does mythtv work on ppc?

Sam

---

### Post by ssam on 2008-02-09
stable as in not crashing. very.

however powerpc support by distros is dropping off. in a few years time it may be hard to find support.

i have never tried mythtv but it should work. you can't use the win32 codecs on powerpc, but there are pretty good opensource codecs and the [fluendo codecs]("https://shop.fluendo.com/") are available for powerpc.

---

### Post by stream303 on 2008-02-09
I agree with Ssam, PPC Linux is very stable.

Once you get past some possible hardware detection issues, as a whole I find that PPC Linux is very stable.

Would a PPC box be my first choice?  No, but I hate to see good hardware go to waste.  They make good general-purpose desktops and servers.  You might be able to get some higher-end Macs pretty cheaply.

I found something that might be a little inspirational for mini owners:

[http://sowerbutts.com/linux-mac-mini/](http://sowerbutts.com/linux-mac-mini/)

---

### Post by Auria on 2008-02-09
Personnaly, on my computer it's crashing quite often - I wouldn't recommend relying on it too much, as ssam said support is being dropped. In the end I think it depends on the price, if it's very cheap I'd go for it but otherwise it's maybe a bit risky

---

### Post by oswaldkelso on 2008-02-09
> **ssam said:**
> stable as in not crashing. very.

however powerpc support by distros is dropping off. in a few years time it may be hard to find support.

I  suspect Debian will still support ppc for a good time to come. I believe  they have only just dropped m68k! I do  see ppc as having a limited life but support will be there in one form or another until the hardware is obsolete  

> **ssam said:**
> 
i have never tried mythtv but it should work. you can't use the win32 codecs on powerpc, but there are pretty good opensource codecs and the [fluendo codecs]("https://shop.fluendo.com/") are available for powerpc.

Myth does run on mac mini ppc with Ubuntu Stuart Langridge of Lug radio fame runs a myth box here's a link to his blogg.

[http://www.kryogenix.org/days/2008/01/26/media-players-and-the-tv#comments](http://www.kryogenix.org/days/2008/01/26/media-players-and-the-tv#comments)

---

### Post by sammydee on 2008-02-10
Ok thanks for the replies guys.

It looks as if mac mini G4's tend to go around half the price of a brand new intel mac mini, so I think the new intel one would be a better choice.

Sam

---

### Post by khelben1979 on 2008-02-10
I can tell everyone who reads this that Debian at least is very, very stable on a powerbook G3 Lombard. This model is from 1999.

Works excellent! Debian is a good distro..

---

### Post by xevix on 2008-02-10
Powerbook G4 here, runs great.  The only qualms are: no 3d acceleration, no hibernation, heats up doing virtually nothing.

---

### Post by Lokesh731 on 2008-02-11
> **xevix said:**
> Powerbook G4 here, runs great.  The only qualms are: no 3d acceleration, no hibernation, heats up doing virtually nothing.

Lucky you!!!!
Frequent crashes of Iceweasel, for reasons I do not understand I cannot run it with a 512 MB RAM without ending in a frozen system (OSX never had this problem). 

Youtube works with swfdec, but the speed is inacceptable.

So far, both with Ubuntu and Debian, I am somewhat disappointed about the numerous troubles I run into. OSX is meanwhile too slow for my tiny iMac, but it runs without any issues.

---

### Post by oswaldkelso on 2008-02-11
> **Lokesh731 said:**
> Lucky you!!!!
Frequent crashes of Iceweasel, for reasons I do not understand I cannot run it with a 512 MB RAM without ending in a frozen system (OSX never had this problem). 

Youtube works with swfdec, but the speed is inacceptable.

So far, both with Ubuntu and Debian, I am somewhat disappointed about the numerous troubles I run into. OSX is meanwhile too slow for my tiny iMac, but it runs without any issues.

I had problems with iceweasel quiting when closing youtube tabs, only youtube?  Either a bug got fixed during my updates or because I  changed my theme?  I changed my theme and straight after its been rock solid.   If it was the theme then  hardly the debian devs fault, but it has made me much more cautious about adding stuff thats not in the offical repos.

I can never get youtube to play but use clive or keepvid to down load them. not perfect but quick and works every time.
I run debian testing and expect a few breaks.  In that last 2 months I've had one. A  bug in icedove that broke it in a nasty way. Hand on heart it has been faster and more stable than osx tiger. 

Lokesh731 you are running linux unstable (sid?)  unstable is called unstable for a reason and it is a little unfair to criticize it for crashing, anymore than you would criticize  water for being wet.

As I understand it a general rule with debian is. (Going from stable but older packages to the latest and greatest but very unstable.)



Etch/stable for servers or corporate and non tech users desktops. Very stable only get security fixes. 

Lenny/testing for average techie user desktops. Stable but some bugs expected. 

Sid/unstable for devs and very techie users who spend their time 50/50 betweent desktop and terminal. Buggy unstable and prone to crashes. you are expected to be able to fix it you self most of the time and file bug reports etc.

Experimental for uber geeks that don't know what a desktop is !!!!


EDIT: A interesting point is that there is now less bugs in Lenny than stable as stable only gets security fixes and any existing bugs are tolerated

---

### Post by Lokesh731 on 2008-02-11
> **oswaldkelso said:**
> I had problems with iceweasel quiting when closing youtube tabs, only youtube?  Either a bug got fixed during my updates or because I  changed my theme?  I changed my theme and straight after its been rock solid.   If it was the theme then  hardly the debian devs fault, but it has made me much more cautious about adding stuff thats not in the offical repos.

I was using the default installation only.

> **oswaldkelso said:**
> Lokesh731 you are running linux unstable (sid?)  unstable is called unstable for a reason and it is a little unfair to criticize it for crashing, anymore than you would criticize  water for being wet.

Debiab stable, minimal installation, then Xorg, CUPS, NFS, then Iceweasel. That was all at the beginning. But Iceweasel frequently shut down after a while. Xorg&CUPS work fine.

> **oswaldkelso said:**
> As I understand it a general rule with debian is. (Going from stable but older packages to the latest and greatest but very unstable.)
YEP. I have no intention to go into sid before my "stable" is what it is supposed to be #-o

---

### Post by oswaldkelso on 2008-02-11
Lokesh731 I was not getting at you its just your footer says you have Linux unstable? If stable is crashing I would reinstall or upgrade to lenny because there seems to be something amiss with your system and as I said lenny has less bugs than stable (they maybe more serious bugs though :)) I had that model (graphite 500) and as far as I know sound was the only sticky point.

---

### Post by Lokesh731 on 2008-02-11
> **oswaldkelso said:**
> Lokesh731 I was not getting at you its just your footer says you have Linux unstable? .

Sorry, my fault. I am using only stable. In the footer I refferred to my experience that Linux (Ubuntu, Debian or Gentoo) crashed during installation with 128+512 MB RAM. I had to take the 512 RAM out, reset the PRAM and then could install it. I am using the 512 RAM since 4 years in OSX without any problems, :confused:, dont know how to deal with it.

> **oswaldkelso said:**
> If stable is crashing I would reinstall or upgrade to lenny because there seems to be something amiss with your system and as I said lenny has less bugs than stable (they maybe more serious bugs though :)) I had that model (graphite 500) and as far as I know sound was the only sticky point.

Thanks for the suggestion. I will give it a try on Wednesday:(

---

### Post by efb on 2008-02-11
For my hand full of MAC OSX 10.4 G3 White  + 1 Silver PPC's, what will I miss most with Ubuntu PPC?

Is security at least as good (Ubuntu -- OS X)?

How well does the new GNOME look speed of rendering wise on G3 PPC .. for Ubuntu?

Just saw some very impressive wares at SCALE6X ..

---

### Post by oswaldkelso on 2008-02-11
> **Lokesh731 said:**
> Sorry, my fault. I am using only stable. In the footer I refferred to my experience that Linux (Ubuntu, Debian or Gentoo) crashed during installation with 128+512 MB RAM. I had to take the 512 RAM out, reset the PRAM and then could install it. I am using the 512 RAM since 4 years in OSX without any problems, :confused:, dont know how to deal with it.
Thanks for the suggestion. I will give it a try on Wednesday:(

Cool. The one thing I would check is your firmware. It needs to be upto date, but I think you need to install it from osx? If your going to do an install wednesday it maybe a good time to check it.

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

ref: [http://lowendmac.com/macdan/04/0907.html](http://lowendmac.com/macdan/04/0907.html)

"One of our iMac 333s has 320 MB total RAM (a 64 MB module in the short slot, 256 MB in the long one) and runs OS X pretty comfortably. The other one won't see more than 128 MB in the long slot even if we plug in a 256 MB module. So that iMac has only 192 MB, and it's noticeably slower running OS X because it has to depend on virtual memory so often."

I know its a tray loader they reffer to but the firmware seem the best starting point.

---

### Post by Lokesh731 on 2008-02-14
> **oswaldkelso said:**
> Cool. The one thing I would check is your firmware. It needs to be upto date, but I think you need to install it from osx? If your going to do an install wednesday it maybe a good time to check it.
I did that a couple of years ago for OSX. No update since (version 2001 is still the actual one)

> **oswaldkelso said:**
> "One of our iMac 333s has 320 MB total RAM (a 64 MB module in the short slot, 256 MB in the long one) and runs OS X pretty comfortably. The other one won't see more than 128 MB in the long slot even if we plug in a 256 MB module. So that iMac has only 192 MB, and it's noticeably slower running OS X because it has to depend on virtual memory so often."
Both RAM modules are recognised, but not to their full extend. The 128MB is seen as 123 and the 512 as 496 MB???.

Anyway, that is getting too specific in this post. I shall bring it up in a new one. 

I switched to Lenny, thanks for the advise! At a first glance it indeed seems to be better working, the 512 MB module though again lead to a big bang during installation. Seems that neither Xorg nor Iceweasel is in the packages, had to use Xfree86 and Firefox. Thought that Xfree86 does not meet the full open source criteria?:confused:

---

### Post by thierryg on 2008-02-14
My take on this one... Being a long time Linux/Mac OS X user.

> **efb said:**
> For my hand full of MAC OSX 10.4 G3 White  + 1 Silver PPC's, what will I miss most with Ubuntu PPC?

Flash support on the web... Well, if you do youtube and dailymotion; at the moment it just means I don't need flashblock anymore with firefox. Yeah!

Photos handling extensions in the finder: handling EXIF/rotation/batch rename out of the finder.

Slow speed of folder displays with the mac os X finder...

Very slow and quite ugly NeoOffice...

Messy fink-only-works-correctly-with-latest-expensive-MacOSX... (and latest Xcode is for latest OSX too).

Messy only-drivers-for-my-pda-and-scanner are the Linux ones anyway and are a pain to install.

Wifi connection handling: NetworkManager in Gutsy ppc simply doesn't work at all.

Quicktime Pro: every media viewer in Linux ppc does full screen!

> Is security at least as good (Ubuntu -- OS X)?

Yes, very similar models and feel. Except that Ubuntu doesn't allow you to install an application without checking on your password.

> How well does the new GNOME look speed of rendering wise on G3 PPC .. for Ubuntu?

Very good (iBook G4 1,2GHz / 512Mo). Gives the feeling the machine has a lot more graphics power than under MacOS X. Compiz looks and feel really nice.

> Just saw some very impressive wares at SCALE6X ..

That is?

---

### Post by farruinn on 2008-02-15
Have you considered a [Koala Mini]("http://system76.com/product_info.php?cPath=27&products_id=83") from System76? I don't know how much G4 mini's are going for, so may not be comparable.

---

### Post by oswaldkelso on 2008-02-16
> **Lokesh731 said:**
> I did that a couple of years ago for OSX. No update since (version 2001 is still the actual one)
Seems that neither Xorg nor Iceweasel is in the packages, had to use Xfree86 and Firefox. Thought that Xfree86 does not meet the full open source criteria?:confused:

I'm running Debian Testing which has the same packages as Lenny  at the moment.   iceweasel and xorg should be on your mirror, I would try adding another mirror in your sources.list . 

[http://www.debian.org/mirror/list](http://www.debian.org/mirror/list)

---

