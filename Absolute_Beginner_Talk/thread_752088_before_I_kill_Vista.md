---
title: "before I kill Vista"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by zumosol on 2008-04-11
I have some really super beginner questions:
First of all I am sick and tired of Vista, so I desperate look for something better..

1/ If I use Ubuntu is it then possible to use Nvidia dualview? ( or ATI Theater mode) so DVD and movies are shown on monitor #1 in a window and on monitor #2 in full screen in two different resolutions. Dualview is not possible in Vista, and are now not supported in XP drivers either. Measn Nvidia´sdrivers and ATI´s drivers are can´t be used  anymore according to their supports)

2/ will WDM drivers for TV satellite TV cards work? so Diseqc 1.2 commands to control positioners is working, and are there any software availeble with good motor positioner menues? I use a Motech motor controoler for this ( Vista also don´t support Disecq and BDA drivers)

3/ will games like Sims2 work?, and are there any software similar to Cyberlink Power Director/Producer that works using Ubunto?

4/How do Ubunto react to SATA discs? ( how to? I have heard that is a problem.. ??)

5/My new PC have a quad-core 2.4Ghz CPU, is that a known problem?

6/ anything else I should be aware of, before formatting? :) Drivers? and so on?:guitar:

Thanx..for any answwers,  I have searched forums but can´t find any clear answers to these questions. The PC is a Medion MD8833, TV card not the original, but a Technotrend S2-3200 for sat reception, and a Zolid DVB-T210 for  terristical and DVB-T.

---

### Post by Tomatz on 2008-04-11
If you are not confident in installing ubuntu via the normal method (creating partitions etc). You can install ubuntu just like any other windows installation using wubi:

[http://wubi-installer.org/](http://wubi-installer.org/)

After installation you can just select which os (ubuntu or vista) to boot when you switch your computer on.

Also by defauld hardy heron (installed by wubi) supports dual monitors. Your tv card **MAY** be supported but it probably wont be as easy as installing it under windows. Just google its make and model number followed by ubuntu ;)

The sims may work under wine (windows emulator) and there are many free video editors (but if you dont like them you will still have vista) ;)

---

### Post by ByteJuggler on 2008-04-11
> **zumosol said:**
> I have some really super beginner questions:
First of all I am sick and tired of Vista, so I desperate look for something better..

1/ If I use Ubuntu is it then possible to use Nvidia dualview? ( or ATI Theater mode) so DVD and movies are shown on monitor #1 in a window and on monitor #2 in full screen in two different resolutions. Dualview is not possible in Vista, and are now not supported in XP drivers either. Measn Nvidia´sdrivers and ATI´s drivers are can´t be used  anymore according to their supports)

2/ will WDM drivers for TV satellite TV cards work? so Diseqc 1.2 commands to control positioners is working, and are there any software availeble with good motor positioner menues? I use a Motech motor controoler for this ( Vista also don´t support Disecq and BDA drivers)

3/ will games like Sims2 work?, and are there any software similar to Cyberlink Power Director/Producer that works using Ubunto?

4/How do Ubunto react to SATA discs? ( how to? I have heard that is a problem.. ??)

5/My new PC have a quad-core 2.4Ghz CPU, is that a known problem?

6/ anything else I should be aware of, before formatting? :) Drivers? and so on?:guitar:

Thanx..for any answwers,  I have searched forums but can´t find any clear answers to these questions. The PC is a Medion MD8833, TV card not the original, but a Technotrend S2-3200 for sat reception, and a Zolid DVB-T210 for  terristical and DVB-T.

You have fairly specific requirements, so I would be careful, and would firstly test Ubunt**u** before wiping Windows.  Probably, a dual boot setup would be best, (probably a Wubi based install, which installs ubuntu onto your Windows Filesystem into disk image files, and avoids having to repartition.)  Graphics drivers for Ubuntu at this stage sadly still tend to lag behind their Windows counterparts in terms of features so if you don't have a feature in Windows its highly unlikely that you'll have it in Linux.  Which brings me to my next point.  Ubuntu doesn't use Windows drivers. It's not windows, so can't (except for a few special cases for example Wireless drivers where people have written a translation layer for linux to allow it to use Windows drivers.)  Your hardware either has to be supported by the default drivers in the Linux kernel (which is pretty comprehensive to be fair), or your hardware vendor must provide drivers for Linux themselves.

As for games for Windows, some will work via Wine, which is a translation layer for linux to allow you to run Windows API applications, or alternatively Cedega, which is a commercial product focussed on games.  These applications have lists of applications that are certified to work, so you'll have to check whether the Sims work or not.  

Ubuntu generally has no problem with SATA disks, nor with multi-core cpu's.  

Hope that helps.

---

### Post by zumosol on 2008-04-11
hmm...
The main problem I have now ( using Vista) is the TV cards and dualview..
The TV card problems are to live with, but the dualview problem is simply impossible to live with.. The set-up is as follows:
Monitor ( and PC) in one room, and second monitor ( a Sanyo z3 projector) in another room for movies only.
The answers I have got from ATI and Nvidia so far is: dualview is no longer supported, also not using XP. No working drivers even for XP availeble.
squared!...zip..closed..
Of course one could say: drag and drop the window from one screen to another or make a screenswap, but that means keyboard and mouse have to work in both rooms, or I must buy some kind of X-Ray device to see therough walls :lolflag:  a pitty my name is not Superman...
The main explanation from both is: Vista don´t support it and for copyright reasons..
As a comment I can say I have an old PC from 2002, where everything works PERFECT as long as I don´t update to latest graphics-card drivers... and that reallly p.... me off. A brand new multimedia PC can´t use two monitors?, or recieve DVB-S? ... 
Use the old?
YUP.. but it sounds like a F16 fighterplane when started, and repair a 5-6 year old PC?.. 

But of course worth to try Ubuntu, if it solves anything. If to use original drivers for the Nvidia card well then I can´t see why I should try? Especially not if it gives me a lot of other problems...
:(
Stand alone products could be a slolution, ut not why I spend a fortune on a new "super" multimedia PC...
The above is only some added explanations,and thoughts,  and not ment as critisism of Ubunto or something like that..

---

### Post by Tomatz on 2008-04-11
> **zumosol said:**
> hmm...
The main problem I have now ( using Vista) is the TV cards and dualview..
The TV card problems are to live with, but the dualview problem is simply impossible to live with.. The set-up is as follows:
Monitor ( and PC) in one room, and second monitor ( a Sanyo z3 projector) in another room for movies only.
The answers I have got from ATI and Nvidia so far is: dualview is no longer supported, also not using XP. No working drivers even for XP availeble.
squared!...zip..closed..
Of course one could say: drag and drop the window from one screen to another or make a screenswap, but that means keyboard and mouse have to work in both rooms, or I must buy some kind of X-Ray device to see therough walls :lolflag:  a pitty my name is not Superman...
The main explanation from both is: Vista don´t support it and for copyright reasons..
As a comment I can say I have an old PC from 2002, where everything works PERFECT as long as I don´t update to latest graphics-card drivers... and that reallly p.... me off. A brand new multimedia PC can´t use two monitors?, or recieve DVB-S? ... 
Use the old?
YUP.. but it sounds like a F16 fighterplane when started, and repair a 5-6 year old PC?.. 

But of course worth to try Ubuntu, if it solves anything. If to use original drivers for the Nvidia card well then I can´t see why I should try? Especially not if it gives me a lot of other problems...
:(
Stand alone products could be a slolution, ut not why I spend a fortune on a new "super" multimedia PC...
The above is only some added explanations,and thoughts,  and not ment as critisism of Ubunto or something like that..


As said hardy heron (latest **ubuntu**) supports dual monitors.

---

### Post by gali98 on 2008-04-11
> **Tomatz said:**
> As said hardy heron (latest **ubuntu**) supports dual monitors.

But are you sure a brand new user should be using a beta? 
Obviously you (zomosol) are not stupid or anything, but it doesn't sound like you've ever used ubuntu or linux before. I'm not doubting your ableness, but using a beta isn't the best thing to start with. I suggest You  either wait.....

[IMG]http://www.ubuntu.com/files/countdown/804/ubuntu/804UbuntuCountdown_13days.jpg[/IMG]

or use gusty. But I suppose that you can do whatever you want. I don't suggest wiping vista before you know what works and doesn't. Use the live cd, or install wubi.
Cheers,
Kory

---

### Post by Tomatz on 2008-04-11
> **gali98 said:**
> But are you sure a brand new user should be using a beta? 
Obviously you (zomosol) are not stupid or anything, but it doesn't sound like you've ever used ubuntu or linux before. I'm not doubting your ableness, but using a beta isn't the best thing to start with. I suggest You  either wait.....

[IMG]http://www.ubuntu.com/files/countdown/804/ubuntu/804UbuntuCountdown_13days.jpg[/IMG]

or use gusty. But I suppose that you can do whatever you want. I don't suggest wiping vista before you know what works and doesn't. Use the live cd, or install wubi.
Cheers,
Kory

Nah jump in at the deep end!

Thats what Linux is all about ;)

Besides wubi uses the beta anyway.

---

### Post by gali98 on 2008-04-11
lol...
Actually wubi is on the gusty cd... I installed it on my brothers laptop....
but as far as wubi itself, then yes it is beta.... actually it'll still be beta when hardy actually releases.

Kory

---

### Post by zumosol on 2008-04-11
> **gali98 said:**
> But are you sure a brand new user should be using a beta? 
Obviously you (zomosol) are not stupid or anything, but it doesn't sound like you've ever used ubuntu or linux before. I'm not doubting your ableness, but using a beta isn't the best thing to start with. I suggest You  either wait.....

[IMG]http://www.ubuntu.com/files/countdown/804/ubuntu/804UbuntuCountdown_13days.jpg[/IMG]

or use gusty. But I suppose that you can do whatever you want. I don't suggest wiping vista before you know what works and doesn't. Use the live cd, or install wubi.
Cheers,
Kory

You are absolutely right.. I have close to no idea what Ubuntu ( or Linux ) is.. Have what I would call a half high degree of knowledge in XP and so on, but that´s not the same ( hopefully not hahaha:)) 
- and the reason I asked, so I don´t end up in tons of problems. 
Think a beta would be ..ehmm well.. let me put it this way: not a smart solution..](*,)

---

### Post by Tomatz on 2008-04-11
> **gali98 said:**
> lol...
Actually wubi is on the gusty cd... I installed it on my brothers laptop....
but as far as wubi itself, then yes it is beta.... actually it'll still be beta when hardy actually releases.

Kory

Really?

I thought wubi allowed you to install hardy? I haven't used it but have only heard good things about it.

---

### Post by Tomatz on 2008-04-11
> **zumosol said:**
> You are absolutely right.. I have close to no idea what Ubuntu ( or Linux ) is.. Have what I would call a half high degree of knowledge in XP and so on, but that´s not the same ( hopefully not hahaha:)) 
- and the reason I asked, so I don´t end up in tons of problems. 
Think a beta would be ..ehmm well.. let me put it this way: not a smart solution..](*,)

Just download this in vista:

[http://wubi-installer.org/](http://wubi-installer.org/)

Install it (in vista)

Then run it ;)

Its as simple as that and if you don't like it just uninstall it in vista via add/remove programs. There is no risk of damaging your system this way.

---

### Post by sammydee on 2008-04-11
I think this is a good a point as any to bring up [this essay.]("http://linux.oneandoneis2.org/LNW.htm")

Points to consider:

- Linux is NOT windows. If you want to switch you have to forget some of the things you assumed you knew about how operating systems work
- Windows programs, generally speaking, will NOT run on linux. In specific cases, windows software may run on a compatibility layer called wine. Most programs will at least run and do something of use when run in wine, however, expect bad desktop integration and LOTS of bugs.
- The above is in most cases not a problem (with the notable exception of games) because there are about 20,000 free software packages available in the ubuntu repositories that can be installed very easily by simply searching for what you want in synaptic. Nine times out of ten, the free versions tend to be as good or better than the versions you would normally use on windows.

I would not recommend dumping vista just yet, try wubi like other people in the thread suggest. If you really don't like it, you can simply remove it, but I encourage you to try it.

Sam

---

### Post by gali98 on 2008-04-11
> **Tomatz said:**
> Really?

I thought wubi allowed you to install hardy? I haven't used it but have only heard good things about it.

Okay now that I can remember right here's how I think it is.
Wubi first started with fiesty. They got it to work relatively well. On gusty it was always in testing, even still I believe. So it wasn't on the gusty or fiesty cd. Scratch what I said earlier. lots of things in my head to keep up with :)
as far as zumosol, I suggest you listen to sammydee

Kory

---

### Post by bradwilliamson on 2008-04-11
Regarding point 1)

Using the NVidia drivers, you can:

Have both monitors display the same thing at the same resolution
Have both monitors display the same thing at different resolution (scrolling around on the lower res screen, or just showing what it can w/o scrolling)
Have the more normal really wide desktop across both
etc. etc.

I have done what you say you need to do with the TV and computer monitor and playing DVD's. It works.

I use MythTV with PVR-150 and HD-3000 cards with this setup and it worked great, I can't help you with the DVB cards though as I'm in the states.

---

### Post by Weidbrewer on 2008-04-11
> **zumosol said:**
> You are absolutely right.. I have close to no idea what Ubuntu ( or Linux ) is.. Have what I would call a half high degree of knowledge in XP and so on, but that´s not the same ( hopefully not hahaha:)) 
- and the reason I asked, so I don´t end up in tons of problems. 
Think a beta would be ..ehmm well.. let me put it this way: not a smart solution..](*,)

My 2 cents:

If anything, wait until the new release is out of beta, and install it on a separate boot partition at very least...on a separate "learning machine" at best.

Everyone told me to just "jump in" when I started on this Linux journey, and that ended up leading to a lot of frustration.   Installing it as a duel boot will help you learn the ropes of the OS (and test it on your hardware) without leaving you high and dry without something familiar (Windows.)   

Having a separate learning machine is another great option.   First of all, Ubuntu seems to work well with out-of-date equipment, so you can use spare parts to put one together.  With this machine, you will have the ability to easily wipe the hard drive and start over completely if you really screw something up (Which can happen.  It's a great way to learn.)


Now, a word on games:  I'd say, keep a windows partition for them.  Sure, you *can* get *some* games to work under WINE...Some.   And most, not well.  As of right now, Linux is not a gaming OS...it's not the focus, so it doesn't have a lot of support.  People have gotten things "good enough" in some areas, because they don't want windows, but want games.

Me?  Not so much.  "Good enough" is generally not "good enough."  I'm not willing to fight with my machine, tweak lots of little things, do without others all to have something that's just playable at best.   I actually keep a dedicated XP machine at home, and a partition on my laptop just for gaming.  

If you have the resources to do so, I'd advise going that route for your games.   You'll be a lot happier in the end.   (Windows has *some* uses.)

---

### Post by Lazy-buntu on 2008-04-11
If you want to dual boot vista and ubuntu this guide worked well for me:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by StRiFe10101 on 2008-04-11
Humm.... I'm wondering where some of your info is coming from.

Just the other day I was messing with Extended desktop/dual monitors and everything was running like a dream.  I did install the drivers from Ati's site.  I had no problem.

When you say "dualview" what do you mean?  Do you mean the Clone fuctionality?  I know good and well that Ati still supports the clone functionality.  Having the samething on both screens at once.  

I too have a projector setup, it does 720p, and i have to say that the the media players for linux are not up to snuff.  (please don't bombard me with statements on that, it's my opinion but i will take suggestions)  The video seem lacey on both my monitor and projector.  

Anyway, I'm with all these guys, use Wubi, and try it out.  You have nothing to lose by using Wubi, only experience to gain.

Oh, you can look into [http://www.mythtv.org/](http://www.mythtv.org/), they say Ati tv cards don't work that great.

---

### Post by Tomatz on 2008-04-11
> **StRiFe10101 said:**
> Humm.... I'm wondering where some of your info is coming from.

Just the other day I was messing with Extended desktop/dual monitors and everything was running like a dream.  I did install the drivers from Ati's site.  I had no problem.

When you say "dualview" what do you mean?  Do you mean the Clone fuctionality?  I know good and well that Ati still supports the clone functionality.  Having the samething on both screens at once.  

I too have a projector setup, it does 720p, and i have to say that the the media players for linux are not up to snuff.  (please don't bombard me with statements on that, it's my opinion but i will take suggestions)  The video seem lacey on both my monitor and projector.  

Anyway, I'm with all these guys, use Wubi, and try it out.  You have nothing to lose by using Wubi, only experience to gain.

Oh, you can look into [http://www.mythtv.org/](http://www.mythtv.org/), they say Ati tv cards don't work that great.


Yeah the free codecs aren't as good as proprietary ones found in proprietary software but you can pay for the fluendo codecs (proprietary linux codecs) if you want higher quality video ;)

---

### Post by stchman on 2008-04-11
> **zumosol said:**
> I have some really super beginner questions:
First of all I am sick and tired of Vista, so I desperate look for something better..

1/ If I use Ubuntu is it then possible to use Nvidia dualview? ( or ATI Theater mode) so DVD and movies are shown on monitor #1 in a window and on monitor #2 in full screen in two different resolutions. Dualview is not possible in Vista, and are now not supported in XP drivers either. Measn Nvidia´sdrivers and ATI´s drivers are can´t be used  anymore according to their supports)

2/ will WDM drivers for TV satellite TV cards work? so Diseqc 1.2 commands to control positioners is working, and are there any software availeble with good motor positioner menues? I use a Motech motor controoler for this ( Vista also don´t support Disecq and BDA drivers)

3/ will games like Sims2 work?, and are there any software similar to Cyberlink Power Director/Producer that works using Ubunto?

4/How do Ubunto react to SATA discs? ( how to? I have heard that is a problem.. ??)

5/My new PC have a quad-core 2.4Ghz CPU, is that a known problem?

6/ anything else I should be aware of, before formatting? :) Drivers? and so on?:guitar:

Thanx..for any answwers,  I have searched forums but can´t find any clear answers to these questions. The PC is a Medion MD8833, TV card not the original, but a Technotrend S2-3200 for sat reception, and a Zolid DVB-T210 for  terristical and DVB-T.

Not sure of #1, but the Nvidia proprietary drivers support Twin View.

I am not sure about #2 either.  Ubuntu has drivers for a great array of hardware OOB.

Playing Windows games on Ubuntu is really hit or miss.  If you are a gamer, I recommend you dual boot and keep Windows for games.

I have SATA hdd and SATA DVD burners and they work well.

My PC has a Core 2 Quad and it works perfectly.  Linux has had SMP for a long time.

Check the Ubuntu Hardware Compatibility List.  As I said before Linux kernel has great support.  My Intel P35 board worked OOB.

---

### Post by zumosol on 2008-04-11
> **Tomatz said:**
> If you are not confident in installing ubuntu via the normal method (creating partitions etc). You can install ubuntu just like any other windows installation using wubi:

[http://wubi-installer.org/](http://wubi-installer.org/)

After installation you can just select which os (ubuntu or vista) to boot when you switch your computer on.

Also by defauld hardy heron (installed by wubi) supports dual monitors. Your tv card **MAY** be supported but it probably wont be as easy as installing it under windows. Just google its make and model number followed by ubuntu ;)

The sims may work under wine (windows emulator) and there are many free video editors (but if you dont like them you will still have vista) ;)

Well I installed using wubi-intaller and first time it started but ever since it freezes after aprox. 30 seconds, that orange moving "thing " moving forht and back stops moving, and that´s it..

Sometimes if I then press "enter" I get a lot of information, aout hat has been loaded so far, but that´s all.

allready in deep troubles, even before I got started? :confused:
Ubuntu is installed on it´s own harddrive, and I can choose between Vista and Ubuntu,  just for information

---

### Post by R6V2 on 2008-04-11
Pretty much off topic but...

My friend had a laptop gaven to him with Windows VISTA installed. He hated this laptop so much. He decided he wanted to crash it. Permantly. He tries making programs and stuff to remove vista but he had no luck. So, he took a bb-gun, and shot the laptop until it was into 500 pieces.

LOL!

---

### Post by zumosol on 2008-04-11
> **StRiFe10101 said:**
> Humm.... I'm wondering where some of your info is coming from.

Just the other day I was messing with Extended desktop/dual monitors and everything was running like a dream.  I did install the drivers from Ati's site.  I had no problem.

When you say "dualview" what do you mean?  Do you mean the Clone fuctionality?  I know good and well that Ati still supports the clone functionality.  Having the samething on both screens at once.  

I too have a projector setup, it does 720p, and i have to say that the the media players for linux are not up to snuff.  (please don't bombard me with statements on that, it's my opinion but i will take suggestions)  The video seem lacey on both my monitor and projector.  

Anyway, I'm with all these guys, use Wubi, and try it out.  You have nothing to lose by using Wubi, only experience to gain.

Oh, you can look into [http://www.mythtv.org/](http://www.mythtv.org/), they say Ati tv cards don't work that great.

I use ..well I have used several actually, Mytheatre  forexample,  works great on the old PC using WDM drivers, means no HDTV...but those drivers are not supported by Vista, and MyTheatre don´t suppord BDA drivers... and DvbViewer that is the only one I have tried that can controll satellite motors almost error free, using BDA drivers...

The dualview is disabled on Nvidia cards, this is from their support dept..:

Full Screen Video Mirror is no longer supported in NVIDIA drivers for Vista and XP due to the following.

1) Newer GPU&#8217;s support dual hardware overlays making software (FSVM) overlays redundant and difficult to maintain.

2) Copy protection issues and potential liability from content copyright holders.

3) Windows XP is being deprecated in favor of Window Vista.

Best regards,
NVIDIA

Then I asked ATI ( I have ATI card on the old PC) they answered:

[I]737-25747: Windows Vista Theater Mode Settings Not Working

The information in this article applies to the following configuration(s): 
Catalyst Display Driver 7.1 
Radeon® X1900 series 
Radeon® X1800 series 
Radeon® X1600 series 
Radeon® X1300 series 
Radeon® X850 series 
Radeon® X800 series 
Radeon® X700 series 
Radeon® X600 series 
Radeon® X550 series 
Radeon® X300 series 
Radeon® 9800 series 
Radeon® 9700 series 
Radeon® 9650/9600 series 
Radeon® 9550/9500 series 
Windows Vista 32bit 
Windows Vista 64bit 
Symptoms:
When outputting to a secondary display such as a TV, HDTV or monitor, the theater mode settings for clone mode do not function.

Cause:
In Windows Vista, Windows Media Player 11 and Windows Media Center do not use Overlay.  Overlay is required for the Overlay Theater Mode to work.[/I]Of course I can use two monitors, but when starting a DVD it is shown on monitor #1
and of course it can be swapped to monitor #2 (t he projector ) and then zoomed to full screen, and so on, but not the same way Dualviw does it ( or Theatre mode with ATI cards) here the DVD is automatically shown on monitor #2 in full screen. ( and different resolution of course)
In the Nvidia control panal - the version you can download from their site- the Dual view menu is simply not present anymore.

---

### Post by crjackson on 2008-04-11
> **R6V2 said:**
> Pretty much off topic but...

My friend had a laptop gaven to him with Windows VISTA installed. He hated this laptop so much. He decided he wanted to crash it. Permantly. He tries making programs and stuff to remove vista but he had no luck. So, he took a bb-gun, and shot the laptop until it was into 500 pieces.

LOL!

Your friend isn't the sharpest knife in drawer is he?

---

### Post by zumosol on 2008-04-11
> **R6V2 said:**
> Pretty much off topic but...

My friend had a laptop gaven to him with Windows VISTA installed. He hated this laptop so much. He decided he wanted to crash it. Permantly. He tries making programs and stuff to remove vista but he had no luck. So, he took a bb-gun, and shot the laptop until it was into 500 pieces.

LOL!

HA :lolflag: I have been VERY close to do exactly the same with this PC.. trust me!!

---

### Post by zumosol on 2008-04-11
> **sammydee said:**
> I think this is a good a point as any to bring up [this essay.]("http://linux.oneandoneis2.org/LNW.htm")

Points to consider:

- Linux is NOT windows. If you want to switch you have to forget some of the things you assumed you knew about how operating systems work
- Windows programs, generally speaking, will NOT run on linux. In specific cases, windows software may run on a compatibility layer called wine. Most programs will at least run and do something of use when run in wine, however, expect bad desktop integration and LOTS of bugs.
- The above is in most cases not a problem (with the notable exception of games) because there are about 20,000 free software packages available in the ubuntu repositories that can be installed very easily by simply searching for what you want in synaptic. Nine times out of ten, the free versions tend to be as good or better than the versions you would normally use on windows.

I would not recommend dumping vista just yet, try wubi like other people in the thread suggest. If you really don't like it, you can simply remove it, but I encourage you to try it.

Sam

some good points in that essay!! But I must say I wish there was a version maybe a little more collected than a box of Lego.. I mean so I don´t have to start from scratz and learn how to build the car 100%.. hope you understand what I mean here..

Another thing is: I think there should be a real alternative to MS products for normal users that actually just need their PC´s to work when they turn it on.  But of course easy for me to say:) I can´t build such a OS... ehmm or a car ...

---

### Post by Weidbrewer on 2008-04-11
> **crjackson said:**
> Your friend isn't the sharpest knife in drawer is he?

Yeah...did I miss something?   Did Window, some where along the way, become totally immune to a format?

---

### Post by sammydee on 2008-04-11
zumosol:

That essay is slightly out of date. The entire objective of ubuntu is to make linux easier to use for people who DON'T know how to put all the lego bricks together to make an operating system :-). I know I certainly don't. But Ubuntu also certainly ain't windows.

Give it a try! You might even find it easier to use than Vista.

Sam

---

### Post by R6V2 on 2008-04-11
Ahh! I'm mad at Linux right now. Read my topic! Wahh!

I hate Ubuntu!!!

---

### Post by zumosol on 2008-04-18
> **sammydee said:**
> zumosol:

That essay is slightly out of date. The entire objective of ubuntu is to make linux easier to use for people who DON'T know how to put all the lego bricks together to make an operating system :-). I know I certainly don't. But Ubuntu also certainly ain't windows.

Give it a try! You might even find it easier to use than Vista.

Sam

Hi again..
I have tried, but the installation stops after about 30 seconds and nothing further happens..
A pretty good start...:-?

any ideas?

---

### Post by bradwilliamson on 2008-04-18
What is the last thing that it prints and/or does?

---

### Post by Tomatz on 2008-04-18
Download the alternate .iso. Its a text based installer :)

---

### Post by zumosol on 2008-04-18
oups I can´t remember, have to try one more time..

---

### Post by zumosol on 2008-04-23
> **bradwilliamson said:**
> What is the last thing that it prints and/or does?

well.. and orange "thing" is moving from left to right...[-(

then it stops, after - I think - 3-4 min. aprox. 1.2cm in from left on a 22" monitor, and nothing more happens.. 

I bet this information is really valueble..:roll:

After that I had to delete Ubuntu to get SP1 for Vista installed, I mean I have to do something to get at least some value for the money I spend on this brand new PC, and SP1 leads to a blank ( black) screen after one hour, and only way to start the PC again is : re-install totally from scratz.. :-({|=
I miss Commodore 64.. :lolflag:

---

### Post by bradwilliamson on 2008-04-24
The next time Vista craters and you have to reboot, boot with the Ubuntu disk and press F6 at the boot menu, backspace over the "quiet splash --" and hit enter.

It will then boot up with the full text list of what's going on while booting and it should show you what's wrong by the list of what's going on.

---

### Post by zumosol on 2008-04-24
> **bradwilliamson said:**
> The next time Vista craters and you have to reboot, boot with the Ubuntu disk and press F6 at the boot menu, backspace over the "quiet splash --" and hit enter.

It will then boot up with the full text list of what's going on while booting and it should show you what's wrong by the list of what's going on.

Ok I will try that, will get back later..

---

