---
title: "Which version should I install?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by ridl on 2007-03-27
Hi all.

I'm pretty itchy to get my old P3 Dell Inspiron (1.2 Ghz, only 256 RAM right now, though I will double that soon, small (>20 gig) HD, running XP SP2) out of the clutches of the Gates cartel but I can't tell which version of (k)ubuntu would work best for me and my system. I gather from /., Lifehacker etc. that the beta is pretty stable and has some great features, but I'm unclear what the advantages/disadvantages would be. I lean towards GNOME rather than KDE (maybe just because it's a cooler acronym), so perhaps I shouldn't even open that can of worms.

Also, since it's an older computer right at the edge of the specs, should I consider an older release?

I'm no code-savvy command-line supergeek, but I'm not phobic and I'm willing to invest the time to do this right. I can post more of my box's specs if that will help.

Tangentially, can I easily import all my Firefox extensions, or will I need to install them one by one again? And why is the Firefox icon different in Linux anyway? It's so much more boring.

Thanks in advance,
Ridl in Cascadia

---

### Post by aysiu on 2007-03-27
256 MB of RAM? I'd go for Xubuntu.

By the way, I generally don't advise new users to install beta releases, but I have an old Dell Inspiron, too (500m... also with 256 MB of RAM). Dapper (6.06) and Edgy (6.10) were okay on my Inspiron 500m, but resume from suspend was broken. Once I upgraded to Feisty (7.04), which is officially to be released next month, resume from suspend worked like magic.

Just something to consider. I know a lot of people will say I'm giving bad advice, but on a laptop, suspend is an essential function.

You can mount your Windows partition and copy your entire Firefox profile straight out of C:\Documents and Settings\ridl\Application Data\Mozilla Firefox to /home/ridl/.mozilla

---

### Post by zorkerz on 2007-03-27
Im a gnome user so im biased I find it less cluttered and more connected. I would recommend gnome as your first jump over.  As for which version i would use edgy for now. Im running feisty and it tends to be pretty stable but every update runs the risk of breaking something. You can always upgrade when its released or anytime you want without loosing anything (assuming it works and it has for me 3 times now). An older release will not be easier on your system. If anything the revers as it has less fine tuning. 

You will need to reinstall the firefox extensions im afraid but you will find the normal loved firefox icon.

If this is your first jump it will take some getting used to but you will catch on fast.  The forums, the documentation and the wiki are you best friends!  Welcome and Good luck.

I have never run on 256 mb of ram though Xubuntu may be you best bet depending on when you plan to get more

---

### Post by aysiu on 2007-03-27
> **zorkerz said:**
> 
You will need to reinstall the firefox extensions im afraid but you will find the normal loved firefox extension. Only if ridl erases the Windows partition and doesn't keep a copy of the Firefox profile from that old installation.

---

### Post by ridl on 2007-03-27
Would Xubuntu still be a better choice after upgrading to 512m RAM? Will GIMP and Inkscape run decently on it?

---

### Post by aysiu on 2007-03-27
> **ridl said:**
> Would Xubuntu still be a better choice after upgrading to 512m RAM? Will GIMP and Inkscape run decently on it?
No, probably not. If you upgraded to 512 MB of RAM, either Kubuntu or Ubuntu would be fine choices. You can read about the differences here:
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

GIMP and Inkscape will run decently even without the RAM upgrade, but with 256 MB of RAM, I wouldn't run Firefox, GIMP, and Inkscape all at the same time!

By the way, what model Inspiron do you have? To get an idea of what problems you may or may not encounter, you may want to check out this page:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

---

### Post by dfreer on 2007-03-27
> Tangentially, can I easily import all my Firefox extensions, or will I need to install them one by one again?

Ubuntu 7.04 "Feisty" (the release coming out) has a new feature that *supposedly* lets you import old user settings (from windows/ubuntu) during a fresh install. I say supposedly because I haven't tried it myself and dunno if it works.

> And why is the Firefox icon different in Linux anyway? It's so much more boring.

Hmmm, I assume you mean the plain blue globe? Yeah, that was pretty boring, I can't remember which release had that, Dapper I think. I'm running Feisty and it's gone now. See [*_this guide_*]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_replace_Firefox_Icons") if you install Dapper and want it changed.

> Also, since it's an older computer right at the edge of the specs, should I consider an older release?
Nope. I don't think there is any reason to consider using a older release, you don't *have* to have beryl/compiz installed :D 
1.2 Ghz should run decently, although I use 250-300 MBs of memory on average, so to avoid swapping all the time the RAM upgrade will be worth it.

All in all? Try Edgy out I'd say. If you find that X hardware isn't supported try upgrading to Feisty. If you find Edgy too unstable try reinstalling with Dapper.

GNOME vs KDE? Do not be so quick to mutter such a thing, lest you call the wrath of the flamewar gods upon us all!! Try them both out (*sudo apt-get install ubuntu-desktop* OR *sudo apt-get install kubuntu-desktop*), and keep whichever you like best.


EDIT: OMFG I'm slow to post

---

### Post by ridl on 2007-03-27
> **aysiu said:**
> 

By the way, what model Inspiron do you have?


Woops... it's actually a Latitude. C600. Heh. Too... many... trademarks... in... my... brain.... 

From the page you gave me, it looks like I'll have some issues, including video problem with X refusing to start, using default ati driver. I have a feeling this forum will be hearing from me again... 

Now that I'm thinking about hardware, I have to use pcmcia cards for both wireless and ethernet/phone modem. I have a Belkin 54g wireless card and plan to get a Xircom PCMCIA RBEM56G-100 RealPort Ethernet Modem. Modem functionality is actually pretty key, as I may be living in a rural setting with only dialup available. Should I expect problems here?

---

### Post by kinson on 2007-03-27
Since your system seems to be of lower spec, I'd suggest going for Xubuntu, which feels a lot like GNOME anyways.

Having said that, if you have the luxury of downloading(and burning) several image files, there's no harm in downloading Ubuntu and giving it a spin, especially since you said you'd prefer GNOME. I installed it(Ubuntu) on a lower spec laptop with 128RAM, it wasn't the smoothest, but it worked.

As to your question regarding the firefox logo, you might wanna give this a read:
[http://en.wikipedia.org/wiki/Mozilla_Firefox#Trademark_and_logo_issues]("http://en.wikipedia.org/wiki/Mozilla_Firefox#Trademark_and_logo_issues")

Cheers,
Kinson :)

---

### Post by riven0 on 2007-03-27
> **ridl said:**
> Now that I'm thinking about hardware, I have to use pcmcia cards for both wireless and ethernet/phone modem. I have a Belkin 54g wireless card and plan to get a Xircom PCMCIA RBEM56G-100 RealPort Ethernet Modem. Modem functionality is actually pretty key, as I may be living in a rural setting with only dialup available. Should I expect problems here?

Modems are tricky. Ubuntu works better with broadband, but the only way you'll find out is to pop in the liveCD, (try all of them if you can - Dapper, Edgy & Feisty), and test if it works on there. If your modem isn't detected you'll may have to search the forums for a workaround.

---

### Post by immrlizard on 2007-03-30
I have a couple dell laptops running different flavors of ubuntu.   At 512 (when you double it) you won't have many problems running any of them.    Feisty (when it is released) would be my first choice though.    I have been using it since herd3 and some of the things that they have fixed are worthy of a try.   If it is too slow for you once it is loaded, try xubuntu.    I had it running on a computer with a 366 Mhz processor and 256 MB ram and it was slow but usable for basic stuff, so I tried puppy linux and have been happier with that on there.   Another test laptop that I tried was the exact same as yours and it ran fine.   I doubled the memory and it runs even better now.   My advice, no matter which one you choose, try the alternate install cd (because of your video card) for anything ubuntu and burn it at a slow speed to avoid any problems.

Once you get it installed and start working with it you will love it.

---

### Post by halitech on 2007-03-30
by the sounds of it, you have close to the same base system as I do (Duron 1.3, 256meg ram) and personally I find Ubuntu with Gnome works just fine. Only time I have a problem is if I get too rambuncious and have 10-15 windows open doing things and drive my CPU processes way up. For most normal every day usage, Gnome will be fine. I have Xubuntu running on a PII with 256 and it runs great there but GNome is too slow to work.

to however posted the link about changing FF icons, thank you, looks ALOT better now :)

---

### Post by Feenix3k on 2007-04-01
My laptop which is a Dell Inspiron 5150, I used 6.06 Ubuntu. With it I was able to get printer, built in wireless card and syn my pda.

In 6.10 the printer will not work, have not tryed beta yet. Pda works with all versions using jpilot. 

My desk system which is an AMD 64 duel , 6.06 would not load , 6.10 and the beta does load and work .

I am afraid to update the laptop due to fear that I will lose the wireless. Once I got it working I did a full Ubuntu install.

So your desion depends on your hardware and if it will work with the version you want to use.

---

### Post by SorenK on 2007-04-02
I'd go with Xubuntu as well.  I've installed Vector Linux with Xfce on a bunch of P100s through P2-233s.  Xfce makes a big difference when it comes to older hardware.

That said, I think your laptop is on the border.  You could run Ubuntu and have it be okay.  Also, if there are apps that Xubuntu ships with that you'd rather run the more resource needy options, you can approach it on a case by case basis.  

For example, you could go with Open Office for compatibility with .doc and .xls files instead of using the GTK2 options that come with Xubuntu (Abiword for example).  Some people recommend having OpenOffice not use Java (you can turn it off under Tools-->Options under the Java item on the left) for older computers.

It might just be a matter of how snappy Xubuntu vs. Ubuntu feels to you.  You may have to try both to know.  May as well give both live CDs a go.

---

### Post by Executioner on 2007-04-02
Can someone help me on this:
I was going to download one of the ISO's, but noticed they have "Supported to 2008" as one example. Can someone tell me what does that mean? Will you have to upgrade after that date?
Also, which version should be installed? I have these options:
Ubuntu 6.10 - Supported to 2008
Ubuntu 6.06 LTS - Supported to 2009

I'm going to be installing it on an old spare pc I have. I believe it's a p3 900MHz with 512 megs of ram.

---

### Post by SorenK on 2007-04-03
The "support" is just how long they'll fix bugs and host documentation and/or packages for it.  One thing to remember about Ubuntu is that Dapper (6.06LTS) to Edgy (6.10) is not the same as say, Windows XP to Vista.  Each version is simply the continual natural progression of bug fixing and whatnot that is released every six months.

I went for 6.10 and plan on going with 7.04 as soon as it's officially released later this month.  Don't worry about 6.10's support expiring in 2008 because you'll likely not be running 6.10 in 2008.

6.60 is the "**L**ong **T**erm **S**upport" edition.  This simply means that the Ubuntu team has committed itself to providing documentation, updates and packages for a longer period of time.  This can appeal to certain individuals and institutions with particular update/upgrade policies and plans.  They can just install it, knowing that the version installed will be supported through documentation and packages for a few years to come.

So if you want stability, you can go with 6.06LTS.  If you want the latest features (and in my opion, great stability anyway), go with 6.10 or even 7.04.  Linux is really stable so even the "beta" Feisty Fawn can be rock solid once it's setup.  I for one, went with 6.10 and plan on going with Feisty once the official release is out and I've had the chance to kick some tires.  To be perfectly honest, I find the community documentation and forum support for both 6.10 and 7.04 to be great.  Every bit as good as the official documentation that's around for 6.06LTS.

6.06LTS is the rock solid, stable one that has gotten more testing:
[http://www.ubuntu.com/products/whatIsubuntu/releases](http://www.ubuntu.com/products/whatIsubuntu/releases)

---

### Post by Executioner on 2007-04-03
OK thanks SorenK for the info. I'm not actually thinking about installing Ubuntu on my old laptop. It's a P3 233MHz with 256 megs of ram. I'm currently installing Win xp "stripped to the bone" edition to see how that works, but I might end up installing Ubuntu with Open Office. The HD is small at 5 gigs.

---

### Post by dfreer on 2007-04-04
> It's a P3 233MHz with 256 megs of ram. I'm currently installing Win xp "stripped to the bone" edition to see how that works, but I might end up installing Ubuntu with Open Office. The HD is small at 5 gigs.

...I assume you have to have a typo in there. There should be no reason why a P3 is running at 233Mhz... my P1 ran at 233 Mhz. Whichever it is, linux is surely going to run faster on it that Win XP, especially if it is really running at 233 Mhz.

---

### Post by ridl on 2007-04-24
I just want to thank you all for the great replies. After deciding that a RAM upgrade wouldn't give me the performance I wanted I actually gave up on that old Dell and just got a good deal on a faster CTL laptop (company out of Portland) from Freegeek Olympia. I just installed Feisty with no Gates partition(!). I'm oh so excited...

Thank you thank you! What a cool community, it's an honor to join. 

Full disclosure: I plan to install xp as a virtual machine... if I have to.

Sincerely, 
Ridl in Cascadia
[6 Years of Pirate Radio! Free Radio Olympia[]("http://frolympia.org")URL="http://frolympia.org"]

---

