---
title: "Trouble with PowerMac G3"
date: 2008-01-20
forum: Apple PPC Users
---

### Post by sddmbr on 2008-01-20
I just bought a power mac G3 at a Goodwill for 10 bucks.It has no OS on it.Downloaded ubuntu 7.1 feisty fawn and no luck installing it. I've tried everything. I have 320 mg ram on it, which i think is enough. When I boot the computer up, I press the c button so that the computer can boot up from the disk, everything seems ok. Then this pops up 

/[I]pci@8000000/pci-bridge@dmac-io@5/ata-3@20000/disk@0:2,yaboot.conf. unknown or corrupt file system
cant open configuration file
welcome to yaboot version 1.3.13

Boot:[/I](cursor blinking right here)

What does this mean? I have tried everything i know. to no avail. Desperately need some help.

---

### Post by Midwest-Linux on 2008-01-21
> **sddmbr said:**
> I just bought a power mac G3 at a Goodwill for 10 bucks.It has no OS on it.Downloaded ubuntu 7.1 feisty fawn and no luck installing it. I've tried everything. I have 320 mg ram on it, which i think is enough. When I boot the computer up, I press the c button so that the computer can boot up from the disk, everything seems ok. Then this pops up 

/[I]pci@8000000/pci-bridge@dmac-io@5/ata-3@20000/disk@0:2,yaboot.conf. unknown or corrupt file system
cant open configuration file
welcome to yaboot version 1.3.13

Boot:[/I](cursor blinking right here)

What does this mean? I have tried everything i know. to no avail. Desperately need some help.

 Just remember to burn it into a ISO at the slowest speed that you can. Ubuntu 7.1 is Gusty while 7.04 is Feisty...which one did you try to install? I'd stick with 7.04 and make sure you use the alternate text installer version for PPC for a trouble free installation.

---

### Post by stream303 on 2008-01-21
Almost sounds like someone tried to install linux to it already and didn't get far.  With a second-hand machine, who knows what is really in there.

With unknown machines, I always zap the pram, nvram, and pmu before trying any install just to start from a clean slate for the open firmware and then try to install.

Just a shot in the dark since I don't have any experience with G3's...

---

### Post by sddmbr on 2008-01-21
Thanks guys, ok to burn my my iso I used k3b on mepis linux. It does a great job and has not failed me yet. I tried to install both feisty and gutsy to no avail. I dont know how to zap the pram, nvram, and pmu , this sounds like a great idea, can some one show me how? I think I need to start from a clean slate for the open firmware and then try to install. Thanks guys.

---

### Post by stream303 on 2008-01-21
Here ya' go for zapping pram, nvram, and pmu

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

---

### Post by sddmbr on 2008-01-21
Thanks. I'll try this and let you know

---

### Post by rakker16mm on 2008-01-24
> **sddmbr said:**
>  I have tried everything i know. to no avail. Desperately need some help.

I'm completely new to the world of Linux and my friend was recommending Ubuntu. I also have a B&W G3 and was looking for the correct version to download, and I think the G3 is just not supported in the latest versions.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

> Note to PowerPC (PPC) users: The PowerPC platform of computers is not supported by the newest versions of Ubuntu. However Ubuntu 6.06 is still supported and available for your machine. Please use the link above to view the complete list of download locations to choose a location near you.

So I'm going to try Ubuntu 6.06 and see how that goes. If I can find the Power PC version that is ;p

If any one has that link please let me know.... Thanx

---

### Post by pizzach on 2008-02-01
I had all sorts of problems getting my PPC to boot Gentoo Linux.  But luckly, that was not one of the problems.  Anyway, sddmbr,**[COLOR="Red"]to answer your question[/COLOR]** by quoting from [_[COLOR="Blue"]the Gentoo PPC faq[/COLOR]_]("http://www.gentoo.org/doc/en/gentoo-ppc-faq.xml"):

> I have an early NewWorld Mac such as the Blue and White G3. It should be compatible with the InstallCD, but on boot it returns an "Unknown or corrupt filesystem" error.

As a workaround, boot into Open Firmware by holding down the Apple + Option + O + F keys on startup. When the prompt appears, type:

boot cd:,\\yaboot

The CD should boot as expected now, thanks to John Plesmid for this workaround.

People here who are trying to install Linux on their PPC Mac might want to go for a distribution that officially supports it like [_[COLOR="Blue"]Yellow Dog Linux[/COLOR]_]("http://www.terrasoftsolutios.com/products/ydl/").  I just find it overly ominous how Canotical hides the PPC version on the Ubuntu website even if it is only a community version.  But that is just my opinion.  (I'm currently using Gentoo on my PPC, but I do not recommend Gentoo to newbies and people who don't enjoy large amounts of tinkering and research...but their support for PPC is official too.)

---

### Post by Midwest-Linux on 2008-02-02
> **pizzach said:**
> I had all sorts of problems getting my PPC to boot Gentoo Linux.  But luckly, that was not one of the problems.  Anyway, sddmbr,**[COLOR="Red"]to answer your question[/COLOR]** by quoting from [_[COLOR="Blue"]the Gentoo PPC faq[/COLOR]_]("http://www.gentoo.org/doc/en/gentoo-ppc-faq.xml"):



People here who are trying to install Linux on their PPC Mac might want to go for a distribution that officially supports it like [_[COLOR="Blue"]Yellow Dog Linux[/COLOR]_]("http://www.terrasoftsolutios.com/products/ydl/").  I just find it overly ominous how Canotical hides the PPC version on the Ubuntu website even if it is only a community version.  But that is just my opinion.  (I'm currently using Gentoo on my PPC, but I do not recommend Gentoo to newbies and people who don't enjoy large amounts of tinkering and research...but their support for PPC is official too.)

 Yellow Dog makes Windows ME look good. 

Yellow Dog, well I downloaded all Five ISOs, burned all five discs, took hours..then tried to install...took well over a hour and a half...upon installation...rebooted and then nothing ... I go to the Yellow Dog Forum for help....I have to register...it says my email address is invalid...so I give them my other email address...that was invalid too.... After wasting nearly a good part of the morning ... Yellow Dog...is on the top of my worst distro of all time....

---

### Post by pizzach on 2008-02-02
:mad:  Sounds like my debian install problems with 7 CDs...speaking of which, I think debian still officially supports PPC too ;-).  I haven't tried yellowdog in a while, but it looks interesting since they come with E17 out of the box instead of gnome.  I do think you have to register to post to most forum type places though.

Ubuntu was my first distro that actually booted to a graphical environment and is the reason I have a fairly good feel for linux.  Because of that, I have a bit of a soft spot for it.  Nowadays I know enought to tweak a xorg.conf file or connect to the net without a gui and look up help when needed.  I believe I had tried Debian the YellowDog to no avail before that which both failed to boot x after install.  I do not know how they are nowadays, but I like to think that they at least made some strides...especially with how much X11 now autodetects many components.

The last Ubuntu install I tried was on a iMac which didn't even boot the installer because of errors.  So the problems are not restricted to Debian or Yellow Dog.  It really ominous that there is no official PPC version of Ubuntu and the unofficial one is hidden away.  When support for the last officially released PPC version of Ubuntu ends (what is it a year left?), the PPC section of the Ubuntu forums will likely disappear too.  But as of right now, it might still be the best choice for many people regardless.  

For now, I'm just going to play with my gentoo install on my B&W G3 :guitar:

---

### Post by stream303 on 2008-02-02
> **pizzach said:**
> The last Ubuntu install I tried was on a iMac which didn't even boot the installer because of errors.  So the problems are not restricted to Debian or Yellow Dog.  It really ominous that there is no official PPC version of Ubuntu and the unofficial one is hidden away.  When support for the last officially released PPC version of Ubuntu ends (what is it a year left?), the PPC section of the Ubuntu forums will likely disappear too.

I've got a feeling that Hardy Heron will show up for PPC.  I wouldn't be too scared of "official" vs "unofficial".  In reality, I believe that the official support is coming upstream from Debian anyway. :)

It's up to US to provide support.  Kind of what Ubuntu is all about.  You and I can do it, in fact we're doing it right now.  Take pride in fixing things and providing support in an unofficial way.  What could be cooler than getting Hardy Heron up and running on a low-spec G3 for example.  Sometimes you have to wonder how many lurkers are benefitted by this forum who own macs running Ubuntu.  You never know....

---

### Post by pizzach on 2008-02-02
Yeah.  I suppose I'm being a bit overly pessimistic, stream303.  I wonder if a user petition could be used to get the user supported PPC version on the [ubuntu download page]("http://www.ubuntu.com/getubuntu/download")?

As is, a lot of people wouldn't think a PPC version exists period.  I still remember telling my dad to download the PPC version and that it was easy...but that was when they had just switched the page.  It confused the heck out of me until I checked it out for myself.

...I can't help but think this must have been discussed somewhere else on the forums. :p

---

### Post by stream303 on 2008-02-02
I think that would be a great idea to put the notes for PPC users right up front, rather than as a sidenote down at the bottom of the page for sure.  Some may not even be aware that Feisty and Gutsy are available.

I think it's almost a rite of passage - you've got to really *want* to dig into your PPC for the most benefit and if so, you'll end up in the forums.

Don't despair.  When you think about it, not putting considerable "official" resources into a platform that is no longer mainstream from a consumer-standpoint like PPC makes sense.

I look at it this way:
1) The number of people using Linux is small comparatively to the rest of the world, but growing all the time.

2) The users running PPC linux are even smaller

3) Many might find that running PPC Linux on a low-spec machine like a G3 not worth the trouble even if it can be done.  I find it a worthy cause, but your expectations about the box, and intended use may change.

In the end, I am still blown away by the fact that we are not locked in to just using Apple's OS.  And instead of just killing it outright, they leave it to us as a community to fine-tune it.

At first I was despondant over the lack of official support, but it makes sense to me now.
Now support is a cool challenge!  I'm not going to let "the man" beat me. :)

---

### Post by pizzach on 2008-02-02
> **stream303 said:**
> I think it's almost a rite of passage - you've got to really *want* to dig into your PPC for the most benefit and if so, you'll end up in the forums.
I don't know.  It sounds like a good way to scare people away to other distros even if they are Linux lovers.  There is no reason for people to think of looking in the forums for the 7.xx release ISOs.  In fact, I didn't know until just now.

> Many might find that running PPC Linux on a low-spec machine like a G3 not worth the trouble even if it can be done.  I find it a worthy cause, but your expectations about the box, and intended use may change.
There are still the Power Mac G5s.  Also, Power Macs are not the only computers still running PPC.  IBM sells desktop style servers even if they do generally cater to people outside of ubuntu's demographic.  There is also the PS3 which Yellow Dog does happen run on.

Now that I am done playing devil's advocate, interestingly enough, Sparc seems to be getting more love than PPC in general nowadays.  Adobe is working on porting the Flash plugin to Sparc over PPC on linux.  Also, the Ubuntu download page has an option for sparc if I remember.

My love went down for Ubuntu when they stopped linking anything PPC for new releases.  Gentoo runs by community support, so that in itself isn't a reason to dislike Ubuntu PPC.  But gentoo doesn't hide it's PPC section.  A year down the road I do look forward to seeing how the PPC forum is doing here.  I'm pessimistic, but I will be happy if I'm surprised ;-)  I'll be interesting if a "ubuntuppc-forums.org" url spins off.

---

### Post by BudaTx on 2008-02-02
There's a Fedora8 PPC distro, have you given that a go?  I have a b&W G3 and did get ubuntu installed, but didn't like the way it ran, very slow (384mb ram)  Actually I purchased a copy of Os-9 and an upgrade to X and installed that, but I'm not really jazzed about it for some reason either, though I do like leopard on my IMac aluminum core-duo.  My notebook, Dell Lat. D600 is running ub-7.1 and it rocks! - it's my favorite machine and the better half even likes to use it (I run VM XP on it in case I need to dig in the dirt)  So I recently saw Fedora8 for PPC, live cd.  I have it downloaded but haven't burned it to try yet but all the F-8 reveiws look good.  The G3 BW was supposed to go to my 14yr old but he got DreamLinux working on his AMD Duron and likes it so I'm now thinking about making the G3 a fileserver, but can't find much along those lines and have too many unused towers that need to go away.  Anyway let us know how you fare.

---

### Post by pizzach on 2008-02-03
In ubuntu land, Xubuntu is probably the most approriate version of B&W g3s.  My B&W is acutally fairly heavily upgraded so it isn't too bad with gnome.  (400mhz G4, 1Gb RAM...32mb vram Radeon etc)

---

