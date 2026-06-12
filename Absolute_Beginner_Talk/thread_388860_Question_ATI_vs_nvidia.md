---
title: "Question: ATI vs nvidia"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-03-20
It seems that linux has much better support for nvidia gfx cards, compaired to ATI. A friend of mine, an ATI user, had a bit of trouble getting Beryl to run, but managed to get it going after a few hours of hacking away. Whereas I, being a nvidia user, got it up and running in a matter of minutes...

Why is the support for nvidia better than for ATI?

---

### Post by Icemanyurt on 2007-03-20
Nvidia, the company, is more Linux minded...

---

### Post by Stickymaddness on 2007-03-20
Hmmm okay.... So the crummy manufacturer is to blame....

---

### Post by scxtt on 2007-03-20
eh, ATI puts out driver releases for linux on a pretty regular basis - and installing them isn't too hard now-a-days ...

can't speak about beryl really - i've only used it w/ sabayon and that all worked "out of the box" ...

so i'm pretty well versed in getting ATI 3D drivers working, but just bought a new motherboard w/ nvidia onboard video - so we'll see how that goes ;)

---

### Post by Bakerconspiracy on 2007-03-20
Not crummy manufacturing, but ATI doesn't like to be as open source with their drivers. (based upon the past)

---

### Post by Stickymaddness on 2007-03-20
> **Bakerconspiracy said:**
> Not crummy manufacturing, but ATI doesn't like to be as open source with their drivers. (based upon the past)

No, I meant that ATI is crummy because they don't like to be as open source......

---

### Post by Xenogis on 2007-03-20
The only problem I have with my ATI card right now is that frame buffer objects don't work. I don't care much though because that just makes the blur effect in beryl look a teeny bit worse. Doesn't effect me in another way. I like ATI more than nvidia since it is now owned by AMD which I have loved forever

EDIT: Another choice is to use an integrated intel graphics card. They have open source drivers and everything works out of the box most of the time. I had a really good experience installing beryl on my desktop with one of those

---

### Post by Bakerconspiracy on 2007-03-20
They both have their +'s and -'s, but it seems as if the nvidia package would be easier to install just off the bat because its a .deb in the repositories.

---

### Post by konst88 on 2007-03-20
The ati driver also exists in the repositories. xorg-driver-fglrx

---

### Post by cowlip on 2007-03-20
ATI's drivers don't even support AIGLX, so you'd have to use the more confusing XGL, which means it's hard to play videos with Totem when running Beryl or Compiz.  You're much better off with the open source ATI drivers if your card is supported by them because they do support AIGLX

Of course Intel cards are supported the best since they open source and open the video specs, and also employ Keith Packard to write X.org.

Look for the Nouveau drivers and do a renouveau dump if you have time to help in the hunt for open source NVidia drivers: [http://ubuntuforums.org/showthread.php?t=357369](http://ubuntuforums.org/showthread.php?t=357369)

---

### Post by russell.h on 2007-03-20
Just so we're clear, the nvidia driver isn't open source, its just a heck of a lot better than the ATI driver.

However, AMD bought out ATI a little less than a year ago, and AMD has a history of working well with Linux. It seems like I read somewhere that under the direction of AMD ATI now has a team working on better Linux drivers. I hope so anyway (I use nvidia myself, but thats ok).

---

### Post by cowlip on 2007-03-20
AMD will ___NOT___ open source ATI's drivers (sadly).   Read this: [http://liquidat.wordpress.com/2007/03/13/amdati-linux-interview-with-terry-makedon-the-head-of-software-development/](http://liquidat.wordpress.com/2007/03/13/amdati-linux-interview-with-terry-makedon-the-head-of-software-development/)  I hope AMD gets punished for this, apparently their bugs get less priority from kernel developers now so maybe they will learn someday.

Regardless, all that most developers want is open device specs from NVidia and ATi, that's what Intel does..

---

### Post by justleen on 2007-03-20
i've  had  to "similair" cards from ati/nvidia on ubuntu (this was a year ago! on Nvidia ever since), and i must say there wasnt much difference in installing the drivers for either. I did find that the Nvidia drivers perfomed slightly better (WoW on wine, GLXGears), but even that was minimal.

Over all, i think (and thats only my personal experience!) that Nvidia is better.. It drivers gets updated at better intervals (ATI takes there times with there linux drivers) and it has a slight edge performance wise... 

In the real world, it doenst matter really, which card you use..

---

### Post by segalion on 2007-03-20
The worst ATI for me is not support XvMC (mpeg-2 hw), that means not recomend to use ATI in HTPC linux machines...

[http://www.linuxis.us/linux/media/howto/linux-htpc/video.html](http://www.linuxis.us/linux/media/howto/linux-htpc/video.html)

[http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC)

Maybe one day... (if ati sales grown down due this).

---

### Post by rushin_911 on 2007-03-23
ATI support for linux is horrible ! I seriously advice everyone not to purchase ATI cards at all if they plan to use linux.

Perhaps the best evidence for this is the whole AIGLX / composite extension issue. ATI does not support the composite extension of xorg, and therefore you can not run AIGLX, and you are only stuck with XGL, which does not support stuff such as videos as well as AIGLX (annoying pitiful playback). ATI does not seem to be planning to support the extension any time soon.

The ATI drivers also seem more prone to bugs, and generally speaking they don't care about them. ATI drivers also usually lag behind when it comes to supporting anything in Linux in general. They still do not support the 2.6.20 kernel, and so you have to resort to hacks in order to install them.

ATI generally brings me a lot of grief, as I am sure it does for many Linux users. The only reason I'm stuck with it is because I own a laptop, and therefore I really don't have much when it comes to the option of changing this disgusting card. Had I had that option, I wouldn't hesitate to do so in an instant. 

Therefore I suggest you and any prospective buyers to spare yourself the trouble, and just buy either a nvidia or intel card.

---

### Post by Stickymaddness on 2007-03-24
> **rushin_911 said:**
> Therefore I suggest you and any prospective buyers to spare yourself the trouble, and just buy either a nvidia or intel card.

I'd have to agree with you there. While ATI is supported, it's just that must easier and headache-less if you have a nvidia card...

---

### Post by maniacmusician on 2007-03-24
Nvidia isn't more open-source; just wanted to clear this fact up. They're just as closed-source, but they just actually give a crap about their Linux drivers.

And they are more Linux friendly. A simple example of this is that Nvidia excels at rendering OpenGL, which is the linux platform for 3D graphics.

ATI puts all of its focus on DirectX, which is Windows' attempt at OpenGL.

---

### Post by Stickymaddness on 2007-03-24
It's my understanding that  DirectX is the primary reason that game support in Linux isn't what it is in Windows. Therefor nvidia are merely more Linux friendly than ATI. 

> **maniacmusician said:**
> ATI puts all of its focus on DirectX, which is Windows' attempt at OpenGL.

:-? I always thought OpenGL was Linux's attempt at DirectX ?

---

### Post by rajeev1204 on 2007-03-24
why should u care if the drivers are open source?

I use nvidia drivers on my dapper 64 bit  and they are the primary reason my transition from windows to linux was smooth .

nvidia drivers are rock solid and i dont care or want them to be open source.

Nvidia provide the drivers free as we are using their chips in our  cards and hence they are giving us that service. 

ATI has just managed to spoil their name with their poor to set up linux drivers .

Open sourcing their drivers aint going to solve anything cos u cant buy a card and then wait for someone to finish writing the drivers !

I Dont want some freelance hacker writing code for my expensive card only to later fry it.

better to have proprietary drivers for something so critical( this is harware we are talking about


regards

rajeev

PS. maybe we can move this thread to cafe?

---

### Post by rushin_911 on 2007-03-24
> **rajeev1204 said:**
> why should u care if the drivers are open source?

I use nvidia drivers on my dapper 64 bit  and they are the primary reason my transition from windows to linux was smooth .

nvidia drivers are rock solid and i dont care or want them to be open source.

Nvidia provide the drivers free as we are using their chips in our  cards and hence they are giving us that service. 

ATI has just managed to spoil their name with their poor to set up linux drivers .

Open sourcing their drivers aint going to solve anything cos u cant buy a card and then wait for someone to finish writing the drivers !

I Dont want some freelance hacker writing code for my expensive card only to later fry it.

better to have proprietary drivers for something so critical( this is harware we are talking about


regards

rajeev

PS. maybe we can move this thread to cafe?

I'm sorry but what you're saying is simply not true.

If we take things by your logic then the all the drivers in the Linux kernel should be closed source, which pretty much negates much of its use.

The point of a GNU/Linux system is freedom. Anyone can view the source and edit as they like (freedom as in free speech), and while it does not mean or directly imply freedom as in free beer, it usually follows that suit, probably due to the fact compiling a given program isn't difficult, and anyone can simply distribute this free binary to those who don't know how to compile.

The fact is if those graphics companies open source their drivers the same way intel did, it would make integrating with open source systems a lot simpler, easier and better. Historically speaking open source drivers have always fared much better than closed source ones.

If any company makes their drivers open source that doesn't necessarily mean any hacker can paste code in the main project however they'd like. The company can still maintain management of the drivers. What any hacker can do is download the source, modify it, and then release it as another project.

Therefore, be it from an ethical perspective of open source, or from a practical point of view, it is essential that Nvidia and ATI open source their drivers, and it's only fair that they're requested to do so.

---

### Post by cowlip on 2007-03-24
....lest we mention the NVidia root exploit.  Also the fact that you're beholden to a company who would love ot drop support ASAP.  Also the fact that it can't be ported to another computer architecture, which is why Vista 64 sucks so much compared to Linux 64 bit, because all Linux drivers have the source code available and can be easily ported to wherever.  Bug fixes, security fixes, no need for a stable binary drivers interface (which could have design flaws), etc.

The kernel is GPL'd, not LGPL'd, and therefore anything that links to it or derives from it that is not GPL'd would be copyright infringement, and illegal.  They're just not enforcing it right now.

BTW, if they don't want to open source their drivers, the bare minimum would be to open their driver and hardware specifications.  That's all that would be needed.

If you're ok on Linux with 3d binary drivers, would you be ok with binary ethernet drivers (like Nvidia was doing until open source drivers were reverse engineered)?  Would you be ok with binary usb drivers?  At what point does it stop?

Also: [http://lwn.net/Articles/162686/](http://lwn.net/Articles/162686/)

> Linux in a binary world


What if.. what if the linux kernel developers tomorrow accept that
binary modules are OK and are essential for the progress of linux. 

a hypothetical doomsday scenario by Arjan van de Ven

the primary assumption in this scenario is obviously not going to
happen, but all assumptions that follow are based things that are true
in some form or another, but of course the names of the "innocent" have
been omitted.




On December 6th, 2005 the kernel developers en mass decide that binary
modules are legally fine and also essential for the progress of linux,
and are as such a desirable thing. At first, the development process of
the linux kernel doesn't change much other than a bunch more symbols
getting exported, and EXPORT_SYMBOL_GPL removed.
...[read the rest of the link for more]

---

### Post by muep on 2007-03-24
Even though there are working proprietary drivers for most Nvidia and ATi cards, as well as a decent free driver for ATi cards, having to rely on a proprietary driver is not a good thing. You can't adapt a closed driver to fit any changes in Linux or any other operating system components. You can't use the proprieraty driver on any platforms the driver doesn't officially support. The manufacturer may lose interest in you as a customer or even stop existing. What will you do with your expensive hardware when there is no working driver for it, at all?

For example. if Nvidia's drivers were open source, I could be sure that I can use my Nvidia cards as long as the hardware is intact. I have an Nvidia TNT2 card that isn't cutting edge anymore, but it still works. However, Nvidia has practically stopped developing drivers for cards that old, and the current legacy drivers leave a lot to be desired. At the moment I can't use their drivers because they crash X. What can I do? The card is still in perfectly good condition but it's of no use because the only available driver doesn't work and nobody except Nvidia can fix it.

Even if my problem isn't because of the Nvidia driver, the situation is bad. If X.org gets some new improvements that require driver changes, Nvidia has no interest in making them because there is no profit for them in supporting crappy old legacy hardware.

---

### Post by Stickymaddness on 2007-03-26
Why would you not want thousands of hackers working on your graphics drivers? I'm yet to hear of someone who installed linux and it fried their system! Especially Ubuntu! Also as muep has pointed out, once a card reaches its "use by date" work on its drivers stops. Half the power of Linux is that you can haul out all your old machines that can't handle windows, install linux on and they run like a dream. This would be even more the case, if gfx drivers were open and development of old gfx cards was continuing!

---

