---
title: "Recent stable distro with infrequent changes for newbie dad?"
date: 2013-01-01
forum: Any Other OS
---

### Post by ApolloSanNovus on 2013-01-01
Hi. This is my first post here. 

I am not really new to Linux as such. Have tried many distros over the years but not settled on any one. I use a Mac currently but can use almost any general purpose OS with a GUI. The command line does overwhelm me however, apart from the infrequent "sudo apt-get install" and such. 

This is regarding my dad. He's not really new to computers as such but is definitely a luddite - nothing can be done about that and I am of the opinion that nothing need be done about that. 

**His needs are very elementary - office suite, presentations, printing, web browser, and infrequent media playback. **

I just got a new Sony VAIO with 3rd generation Core i3 and Intel HD graphics for dad. The problem is that it came with Windows 8 and with it come too many changes to the desktop metaphor which can easily confuse an old timer not very acquainted with technology. 

(PS: In an effort to be innovative, Microsoft also kinda shot itself in the foot there, with many Windows faithful resentful with the changes -- it's worse than what happened with Ubuntu and Unity, or Gnome 3, as far as I believe.)

If it had Windows 7, we would have been good to go. He's used to Windows XP and you can make 7 look/feel close enough to classic Windows to make him feel at ease. Not exactly the same with Windows 8 where so many crucial UI interaction features are not obvious and "hidden" behind gestures and such. (I mean with the kind of user base they have, how did MS expect to get away with overhauling such a crucial destination as Start menu in a single release? Even if they wanted to do that, they should have been gradual about it. Metro isn't bad per se. The way they fused it with Windows however, screams of stupidity.)

Here are the concerns:
[B]- Should support the Sony VAIO with 3rd gen Core i3 and Intel HD 4000 graphics. 
- Should be logical, obvious and easy to use for a long time Windows user (classic, XP like GUI). 
- Should require little to no maintenance. 
- Should have good support. 
- Should be something akin to Ubuntu Long Term Support releases. 
- Should have infrequent upgrade cycles, closer to that of Windows than Ubuntu.  
- Updates/Upgrades shouldn't radically change the way one uses the OS, requiring the unsuspecting user to re-learn stuff from scratch. 
- Shouldn't have too much bling, whizz bang, etcetera. Just to the point and getting the stuff done type. [/B]

Ubuntu loses out because of their upgrade cycle and the way they change stuff every now and then. Also, Unity's bling. I don't hate Unity (quite the contrary, as I use OS X myself) but Windows 8 has made dad wary of all flashy graphical stuff like docks and such. He's more used to a menu driven UI from his Windows experience. 

I think I described Debian with my conditions. But I think Debian will require much work during setup -- drivers and media, partly because of their pledge to adhere to free software principles. Fine ideology, but not one of my concerns.  Also, their latest stable is Squeeze with the friendly Gnome 2 but I don't know what the next version (Wheezy?) which is due any day now might bring. 

Linux Mint is a candidate, but I don't know about their upgrade cycles -- probably close to Ubuntu. I just don't want anything to break. I know that is an impossible goal, so I want something that'll prefer stability over updates. 

Zorin OS looks promising, but I don't know the DE they're using, their support or upgrade cycles to commit to it. 

Basically, I want something close to Windows that is most likely to run fine for years with or without updates/upgrades.

---

### Post by iMac71 on 2013-01-01
you might install Kubuntu 12.04 LTS:
[http://www.kubuntu.org/getkubuntu/download-lts](http://www.kubuntu.org/getkubuntu/download-lts)
and, when the installation process has finished, right-click on the "K" icon at the bottom left corner of the screen and choose "classic menu".

---

### Post by tartalo on 2013-01-01
Kubuntu or Xubuntu LTS would be my choice too. [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Note that Xubuntu 12.04 LTS is supported for 3 years, not for 5 years like Kubuntu and "normal" Ubuntu, and that Lubuntu hasn't released any LTS yet.

But perhaps you need to install a newer Kernel manually, because there seem to be some problems with Intel HD 4000 and Kernel 3.2 (The one used by Debian wheezy and by Ubuntu 12.04 LTS):

[http://debian.2.n7.nabble.com/Bug-689268-Intel-HD-4000-Ivy-Bridge-graphics-freeze-td2782198i20.html](http://debian.2.n7.nabble.com/Bug-689268-Intel-HD-4000-Ivy-Bridge-graphics-freeze-td2782198i20.html)

How to install a newer Kernel in Ubuntu:
[http://www.upubuntu.com/2012/07/install-linux-kernel-35-from-ppa-on.html](http://www.upubuntu.com/2012/07/install-linux-kernel-35-from-ppa-on.html)

Eventually, the "official" Kernel of Ubuntu 12.04 will be upgraded.

---

### Post by mips on 2013-01-01
Debian 7 might be out 'soon'.

---

### Post by TREESofRIGHTEOUSNESS on 2013-01-01
Linux Mint is based off of Ubuntu (except their Debian spin...) and Zorin as well.  Really, you might choose Xubuntu for the nice XFCE4 interface which has a normal Old School menu interface, that can easily be configured to look like WinXP or whatever you'd like (Win7 Win98...).  The pros of using Xubuntu are the solid Ubuntu core, and ease of use, however Arch Linux is the kind of 'ideal' never have to reinstall again setup... but it is definetly not for a newbie.  There are a few versions of Arch that are more suited like [http://www.cinnarch.com/](http://www.cinnarch.com/)  You can always check out [http://distrowatch.com/](http://distrowatch.com/) and search there too.

---

### Post by irv on 2013-01-01
The release of 12.04 LTS when for 5 year support. Came out in April 2012 and will run until April 2017. You are looking at anything like Xubuntu, Lubuntu, Kubuntu, etc, all being 12.04 would have the same time support.
I also like Ubuntu with Unity and find it easy to use once you work with it for a short while. I don't know how old your Dad is, but I am 74 but come from a computer background. To me a smart move would be Ubuntu 12.04 right out of the box. Just make sure you install Ubuntu restricted extras for multimedia.
There is a few issue with flash and the Chrome browser, but there are some work arounds or just use FireFox.
Edit: I forgot to mention I use Cairo Dock so I have a menu.
[ATTACH]229440[/ATTACH]

---

### Post by blackbird34 on 2013-01-01
What about Gnome Classic or maybe Cinnamon (my personal "classic" favorite, but the Buntu version is in a PPA) in Ubuntu 12.04 LTS? I dunno if I'd recommend Linux Mint because their Software Center contains less stuff, I think, if you're ever hunting around to install something extra easily. I never got the hang of it.

Also, in Ubuntu you can configure the updates to only be prompted weekly, monthly and even to be done automatically, could be helpful.

---

### Post by exploder on 2013-01-01
I would go with Linux Mint 14 KDE. KDE uses a classic desktop layout, so that would not create much of a learning curve. Mint 14 KDE is already set up for multimedia playback so your Dad would be good to go there.

On my system, after upgrading KDE to 4.9.4 I do not get very many updates. I did add a ppa repo to fix the scratchy sound in VLC when you advance tracks but all in all I see very few updates coming in and everything works fine. 

KDE is reasonably similar to Windows as far as desktop effects go and if your Dad does not like or need compositing it can be easily turned off.

Just my two cents.

---

### Post by PaulInBHC on 2013-01-01
For Windows 8, install Classic Shell, a freeware that adds the start button and menu. You can then choose to use the XP look for the menu. Show him where the Windows key is. If he has a Hotmail account he can use Skydrive. From the Metro ui, show him where the desktop tile is. Maybe remove all the tiles except the basics.
On the desktop, install Open Office and what ever browser he likes although IE10 is the best IE yet.
 
W8 so far has maintained itself pretty well for me. I have IE set to clear history when it closes. It updates overnight and restarts itself.
 
If he is use to Windows you might try this first.

---

### Post by offgridguy on 2013-01-01
> 
 To me a smart move would be Ubuntu 12.04 right out of the box. Just  make sure you install Ubuntu restricted extras for multimedia.

+1 from me. As a new user i find unity the easiest to use.

---

### Post by xenopeek on 2013-01-01
Linux Mint 14 KDE has already been recommended by exploder. While I second that, I'd also consider Linux Mint 14 Cinnamon. It looks modern while having the classic desktop paradigm as your father is comfortable with from Windows. It's based on GNOME 3. Cinnamon gives easy access to the applications your father needs, without the operating system getting in the way. If your father has any special needs (with sight or other), both Cinnamon and KDE include options for that.

Now you mentioned you wanted an infrequent upgrade cycle, and with Linux Mint 14 being based on (and fully compatible with) Ubuntu 12.10 you'd have to upgrade in April 2014. I'd still recommend you go for this release as it comes with Linux kernel 3.5. If you want good compatibility with Intel HD 4000 Graphics, you'll go for a distro release that has at least Linux kernel 3.5. All the earlier ones, like Ubuntu 12.04 with Linux kernel 3.4 as the supported highest kernel, will give you trouble on Intel HD 4000 Graphics.

---

### Post by trent.josephsen on 2013-01-01
OP expressed a desire to make his father's new environment close to WinXP, so he will have less to (un)learn. Unity is probably not the best solution.

I'd say anything+XFCE. It's a full-featured desktop and very easy to configure. Should take like 5 minutes to set up (although you have to tweak the panel yourself if you want it to look like XP, the panel settings GUI is a piece of cake to use).

I'd probably go for Debian stable for stability (and because I like vanilla XFCE). I haven't used Xubuntu in some time but I'm sure it would be fine too, just more frequent updates. Also with regards to the freezing bug tartalo mentioned, Debian stable (squeeze) is still on a 2.6 kernel, so that shouldn't be a problem as it might be with Xubuntu.

Best of luck

---

### Post by irv on 2013-01-01
> **trent.josephsen said:**
> OP expressed a desire to make his father's new environment close to WinXP, so he will have less to (un)learn. Unity is probably not the best solution.

I disagree with this. You will find anyone coming from Windows to Linux will fine learning Ubuntu with Unity much easier then other desktops. I have Xfce on a laptop running a sound system, and I find it harder to use then Unity.
To be honest with you if you install Cairo dock along with Unity and it makes it even easier to use.

---

### Post by offgridguy on 2013-01-01
> **irv said:**
> I disagree with this. You will find anyone coming from Windows to Linux will fine learning Ubuntu with Unity much easier then other desktops. I have Xfce on a laptop running a sound system, and I find it harder to use then Unity.
To be honest with you if you install Cairo dock along with Unity and it makes it even easier to use.
+1 again

---

### Post by mamamia88 on 2013-01-01
If I wanted rock solid stability with infrequent changes I would go either Debian Stable or CentOS period end of discussion.  Want something that takes almost no time to install and has everything ootb?  Mint no doubt.  Either way set up ssh and once a week ssh into his machine and update it.   It's really not that difficult.  As far as gui goes really any distro will offer the same gui because a distro is just a collection of packages that is "distributed" as a single os. You can easily install xfce,kde,etc on other distros

---

### Post by TREESofRIGHTEOUSNESS on 2013-01-01
> **PaulInBHC said:**
> For Windows 8, install Classic Shell, a freeware that adds the start button and menu. You can then choose to use the XP look for the menu. Show him where the Windows key is. If he has a Hotmail account he can use Skydrive. From the Metro ui, show him where the desktop tile is. Maybe remove all the tiles except the basics.
On the desktop, install Open Office and what ever browser he likes although IE10 is the best IE yet.
 
W8 so far has maintained itself pretty well for me. I have IE set to clear history when it closes. It updates overnight and restarts itself.
 
If he is use to Windows you might try this first.

IE has a huge security flaw in it, I would never recommend using IE to anyone, and especially not on a Linux forum where stability and security are generally required.

[http://thenextweb.com/microsoft/2012/12/12/internet-explorer-flaw-allows-websites-to-track-your-mouse-cursor-even-when-you-arent-browsing/](http://thenextweb.com/microsoft/2012/12/12/internet-explorer-flaw-allows-websites-to-track-your-mouse-cursor-even-when-you-arent-browsing/)

---

### Post by malspa on 2013-01-01
> **ApolloSanNovus said:**
> Here are the concerns:
[B]- Should support the Sony VAIO with 3rd gen Core i3 and Intel HD 4000 graphics. 
- Should be logical, obvious and easy to use for a long time Windows user (classic, XP like GUI). 
- Should require little to no maintenance. 
- Should have good support. 
- Should be something akin to Ubuntu Long Term Support releases. 
- Should have infrequent upgrade cycles, closer to that of Windows than Ubuntu.  
- Updates/Upgrades shouldn't radically change the way one uses the OS, requiring the unsuspecting user to re-learn stuff from scratch. 
- Shouldn't have too much bling, whizz bang, etcetera. Just to the point and getting the stuff done type. [/B]

The distro that comes to mind here is Mepis. Not sure about support for that particular hardware, but I've had good luck with it on various computers over the years.

Mepis is based on Debian Stable, so that takes care of the concerns about release cycles and maintenance. Comes with KDE, but you could turn off most of the effects, if you want to. Or you could do what I've done sometimes, add Xfce to Mepis and use that instead.

Excellent support at their forums (you may want to inquire about your hardware there).

The only thing is, they're working on the next release -- hard to say when it'll be finished (I'm guessing a month or two). But if you install the current release (Mepis 11), it's based on Debian Squeeze and I think the Squeeze repos will be good for at least a year after Wheezy goes to Stable; Mepis 11 will be good to use for quite some time.

With Mepis, you get the benefits of Debian Stable, but with a very quick and easy installation and set-up. Mepis is also my favorite choice for live sessions, when I need one. Whenever some new (to me) hardware falls my way, it's the first distro I try on it, and it usually works. I'm not one for touting one distro over others, but I'd try Mepis first if I was installing Linux for my own parents.

---

### Post by trent.josephsen on 2013-01-01
> **irv said:**
> I disagree with this. You will find anyone coming from Windows to Linux will fine learning Ubuntu with Unity much easier then other desktops. I have Xfce on a laptop running a sound system, and I find it harder to use then Unity.

OP **explicitly asked** for something that would be *close to classic Windows*. How easy it is to learn *in the abstract* is not the issue I was addressing.

---

### Post by PhilGil on 2013-01-01
Someone with more experience may correct me, but I think you're going to need a newer kernel for full Ivy Bridge support regardless of whether you choose a 12.04 LTS based distro or Debian.

CentOS or Scientific Linux might be a good choice, as Gnome 2 is supported until at least 2017. The downside is that you may have a learning curve (since they are Red Hat based rather than Debian based). Also, I don't know how they handle essential upgrades (such as the kernel and web browser).

If you're sticking to the Debian family, some good choices might be:
Debian stable with KDE, Gnome 2 or XFCE (although graphics support may be a problem)
SalineOS (Debian stable with XFCE)
Mepis (Debian Stable with KDE)
Mint LTS XFCE or MATE
Xubuntu 12.04 LTS
Kubuntu 12.04 LTS

That being said, Debian Stable is absolutely rock solid, and well worth the bit of extra work to install. I'd like to recommend Debian Wheezy with XFCE (currently in testing), but it's (likely) two to three months from going stable, so there's still a lot of updating going on, with the breakage potential that entails.

---

### Post by drawkcab on 2013-01-01
For your father's needs I think he would probably be best served by a distro that is based on Ubuntu 12.04 that has the long-term support cycle.  I've been running various versions on three of my machines and it is very solid so far.  Once you update to the latest kernel you should have no problems with hardware compatibility.  

I prefer Ubuntu-based distros because Ubuntu seems to work extremely well with peripherals out of the box.  If not, it's easy to find solutions on the web.  Debian, Cent OS, Scientific and the like are sometimes a hassle when it comes to plugging in your devices.

In terms of cloning windows I would say take another close look at Zorin.  Again, get the version that's based on 12.04.

Linux Mint is also a good choice.  I personally would steer you in the direction of the xfce or mate versions.

Whatever you choose, there will be some adjustment, although with your father's basic needs you can set everything up so that there's minimal gnashing of teeth.

---

### Post by Lars Noodén on 2013-01-01
Another vote here for the Kubuntu LTS or Xubuntu LTS.  Those will give a customizable interface but one that won't change, unless you change it, until 2017.

---

### Post by Cheesemill on 2013-01-01
I recently faced the same decision. Ended up putting Ubuntu 12.04 + Cinnamon on my mums new laptop.

Set up Firefox to auto-start when she logs on with the only 7 or 8 pages she ever visits on the bookmarks toolbar and away she went.

---

### Post by orb9220 on 2013-01-01
[How to make Linux Mint 14/ 13 (Cinnamon) look like Windows 7]("http://forums.linuxmint.com/viewtopic.php?f=42&t=121096")

To get even closer to windows. And I use Mint Cinnamon 14 myself.
But [Kde may even be more to his liking]("http://linuxmint.com/").

Can always download both Cinnamon & KDE and burn to LiveCD and let your dad kick the tires and take them for a spin.
.

---

### Post by BBQdave on 2013-01-01
> **Cheesemill said:**
> I recently faced the same decision. Ended up putting Ubuntu 12.04 + Cinnamon on my mums new laptop.

Set up Firefox to auto-start when she logs on with the only 7 or 8 pages she ever visits on the bookmarks toolbar and away she went.

+1

And I think Ubuntu 12.04.1LTS would be fine. Even though his comfort zone is XP, you will probably find he takes to Unity with little issue.

My Mom's first home computer had XP. She had no trouble using Fedora with Gnome, first distro switch. Then an Ubuntu LTS, with Gnome. And now at age 72, with new hardware, she is cruising along with an iMac and osX :)

---

### Post by mamamia88 on 2013-01-02
> **BBQdave said:**
> +1

And I think Ubuntu 12.04.1LTS would be fine. Even though his comfort zone is XP, you will probably find he takes to Unity with little issue.

My Mom's first home computer had XP. She had no trouble using Fedora with Gnome, first distro switch. Then an Ubuntu LTS, with Gnome. And now at age 72, with new hardware, she is cruising along with an iMac and osX :)

then again if you wanted cinnamon why wouldn't you use mint? especially when it's based on ubuntu and they are the primary developers of cinnamon?

---

### Post by ApolloSanNovus on 2013-01-02
> **tartalo said:**
> Kubuntu or Xubuntu LTS would be my choice too. [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Note that Xubuntu 12.04 LTS is supported for 3 years, not for 5 years like Kubuntu and "normal" Ubuntu, and that Lubuntu hasn't released any LTS yet.

But perhaps you need to install a newer Kernel manually, because there seem to be some problems with Intel HD 4000 and Kernel 3.2 (The one used by Debian wheezy and by Ubuntu 12.04 LTS):

[http://debian.2.n7.nabble.com/Bug-689268-Intel-HD-4000-Ivy-Bridge-graphics-freeze-td2782198i20.html](http://debian.2.n7.nabble.com/Bug-689268-Intel-HD-4000-Ivy-Bridge-graphics-freeze-td2782198i20.html)

How to install a newer Kernel in Ubuntu:
[http://www.upubuntu.com/2012/07/install-linux-kernel-35-from-ppa-on.html](http://www.upubuntu.com/2012/07/install-linux-kernel-35-from-ppa-on.html)

Eventually, the "official" Kernel of Ubuntu 12.04 will be upgraded.

Another problem with this computer (and probably all Windows 8 preinstalled computers) is that they have put in UEFI and Secure Boot. Now, I did disable secure boot but am wondering if UEFI changes what I can/cannot install and the process a bit. 

I had Ubuntu 12.04 32-bit ISO with me which I "burned" to a flash drive to boot off Live and check whether the hardware would work okay or not. Unfortunately, the system halted just as the GUI started loading. I was stuck with the wallpaper and the top Unity panel with an unresponsive mouse pointer. Hard reboot it was. 

Perhaps it's the Intel HD 4000 related issue you're hinting at. Should I try the alternate install CD instead? If the 12.04 kernel doesn't support the graphics in the first place, how am I to install it and upgrade the kernel? Note that I'm not extremely capable of utilizing the command line and will probably need some tutorials. 

Also, the ISO I have with me, I downloaded just as 12.04 released like 8 months ago. Will an ISO I download today have the newer kernel and support for 3rd gen Core i3 with Intel HD 4000?

> **irv said:**
> The release of 12.04 LTS when for 5 year support. Came out in April 2012 and will run until April 2017. You are looking at anything like Xubuntu, Lubuntu, Kubuntu, etc, all being 12.04 would have the same time support.
I also like Ubuntu with Unity and find it easy to use once you work with it for a short while. I don't know how old your Dad is, but I am 74 but come from a computer background. To me a smart move would be Ubuntu 12.04 right out of the box. Just make sure you install Ubuntu restricted extras for multimedia.
There is a few issue with flash and the Chrome browser, but there are some work arounds or just use FireFox.
Edit: I forgot to mention I use Cairo Dock so I have a menu.
[ATTACH]229440[/ATTACH]

I wouldn't say it's exactly about age. He's like 53 now. He has been using computers for about 2 decades but just to get what he wants from it. Not really the exploring kind. Definitely not into the radical usage pattern changes that a default Windows 8 demands. 

He even uses my sister's netbook now and then on which I've installed Ubuntu 12.04 but changed the default desktop to Gnome 3 classic fallback. That was a precaution on my part. Unity seems to make certain things complicated on netbooks, namely performance, horizontal real estate (1024*600 - the dock/panel takes a portion and makes viewing standard format 1024*768 irritating - vertical scrolling is fine and necessary most of the time - horizontal scrolling is just an added headache - i know you can autohide the dock/panel, but that makes things worse by removing the obviousness from the UI). 

But the Ubuntu installation on the netbook has issues every now and then and it requires frequent maintainence on my part. Crashes, error messages that really bug the uninitiated, including me (and they ask to submit error reports, which never get submitted and return with "error reporting for this version has now ended" or something to that tune). 

I am not really happy with the supposed "just works" that Ubuntu promises. Though things rarely ge to the point of making the installation completely dysfunctional (technically, it's still always "working"), they do seem to break far often than say on my Mac with OS X and need far more upkeep on my part than I'd care. Note that I'm not starting a platform war here, I understand the strengths of Linux very well. I'm just voicing out my *own* experience with Ubuntu specifically and various other distros in general, over the years and numerous versions, on various machines. 

My friend, enthusiastic about Linux initially, used Ubuntu for a few months and reverted back to Windows because of the constant upkeep that Linux demands and how you have to look for a fix for some nagging issue every now and then, anecdotally more often than with Windows. I know that looking for fixes yourself comes with the Linux experience and is part of what makes it fun. I also think that Linux has come a long way in the past few years. Heck, it's all given for free despite the huge effort that goes into it. But I also believe that Linux has a long way to go, even play catchup with competitors on certain fronts. 

"Free and open" is the modality. "Perfection" is the goal (and will always be). 

> **exploder said:**
> I would go with Linux Mint 14 KDE. KDE uses a classic desktop layout, so that would not create much of a learning curve. Mint 14 KDE is already set up for multimedia playback so your Dad would be good to go there.

On my system, after upgrading KDE to 4.9.4 I do not get very many updates. I did add a ppa repo to fix the scratchy sound in VLC when you advance tracks but all in all I see very few updates coming in and everything works fine. 

KDE is reasonably similar to Windows as far as desktop effects go and if your Dad does not like or need compositing it can be easily turned off.

Just my two cents.

I never got into KDE as such. It always felt far more complicated and loaded with options than it needed to be. GNOME felt simple and clean (not too clean so as to impact usage, as in Windows 8. Or Openbox maybe? ;) )

I also never personally bought that KDE would be simpler for Windows users. But I haven't tried it recently, speaking of which, I should. 


The latest in my issues is this: 
**Dual booting Ubuntu 12.04 LTS 64-bit on a Windows 8 preinstalled UEFI based Sony VAIO with 3rd gen Core i3 and Intel HD 4000 graphics. **

Is the latest 12.04 ISO hosted by Ubuntu (I tried one I downloaded back in April - GUI would get stuck while booting off LiveUSB) updated with the new kernel that'd support my machine? Or do I have to do it manually? 

Also, in case it will support my machine, how do I go about installing it while preserving the default Windows 8 installation? Life was so much simpler when we had the legacy BIOS and you could just boot off a Live USB, partition for Linux, install and be done with it. 

*PS: I've rambled quite a bit in this post, probably because I haven't been into Linux forums recently and felt like talking. I hope it doesn't become fodder/flame-bait for anybody. These are the genuine issues I've experienced that I feel need to be addressed.*

---

### Post by irv on 2013-01-02
I googled win8 and ubuntu dual boot with uefi and here is one I came up with that might help.
[Ubuntu install and dual Boot with Windows 8 UEFI]("http://askubuntu.com/questions/193103/ubuntu-install-and-dual-boot-with-windows-8-uefi")
It was on askubuntu.com. I don't know if it will help with your graphic problem.

---

### Post by qyot27 on 2013-01-02
The desktop environment that comes closest to Windows Classic is LXDE.  The default panel orientation is the same, the menu is broken up into per-purpose categories, and it's very light on resources.

I find that most of those error reporting messages in 12.04 and 12.10 come from Compiz experiencing hiccups.  For LXDE as it ships from the Ubuntu repos (or via Lubuntu) this is a non-issue because it doesn't use Compiz by default, and I wouldn't attempt to hook the two together anyway.  On my 11-year-old computer, with stock Ubuntu 12.10+LXDE, I don't think I've ever experienced those sorts of error messages.  For the long term support concern, you could just go with stock 12.04 LTS+LXDE.

The biggest choice would basically be between Ubuntu proper + LXDE or going fully into Lubuntu.  The difference is mostly in the visual theming and default applications (Lubuntu specifically targets lighter applications, whereas just adding LXDE on top of an existing 12.04/10 install will usually keep the default programs the same).  You can also pin application shortcuts to the desktop for those key needs, if you want to (I managed to do it in a Live session when testing Lubuntu, at any rate - IIRC, just right-click on the menu entry for a program and it should give you the option to do this; if not, it's also possible to copy and paste .desktop entries into the Desktop directory and accomplish the same thing).

---

### Post by Lila7714 on 2013-01-02
Id say Debian.

---

### Post by tartalo on 2013-01-02
> **ApolloSanNovus said:**
> Another problem with this computer (and probably all Windows 8 preinstalled computers) is that they have put in UEFI and Secure Boot. Now, I did disable secure boot but am wondering if UEFI changes what I can/cannot install and the process a bit. 

I had Ubuntu 12.04 32-bit ISO with me which I "burned" to a flash drive to boot off Live and check whether the hardware would work okay or not. Unfortunately, the system halted just as the GUI started loading. I was stuck with the wallpaper and the top Unity panel with an unresponsive mouse pointer. Hard reboot it was. 

Perhaps it's the Intel HD 4000 related issue you're hinting at. Should I try the alternate install CD instead? If the 12.04 kernel doesn't support the graphics in the first place, how am I to install it and upgrade the kernel? Note that I'm not extremely capable of utilizing the command line and will probably need some tutorials. 

Also, the ISO I have with me, I downloaded just as 12.04 released like 8 months ago. Will an ISO I download today have the newer kernel and support for 3rd gen Core i3 with Intel HD 4000?

I have no experience with UEFI, I can't help there.

If the computer is freezing, it might have to do with the bug I linked. If that's the reason, using the alternate install CD should help, you have the option to start a command line at certain point during the installation, you can enter then the commands to install the 3.5 kernel from the article I linked above.

Use an up to date ISO (12.04.1 for LTS) that matches the Ubuntu flavor you plan to install:
[http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/)
[http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/)

If that doesn't work for you, perhaps it pays to go with 12.10, your laptop is quite new and you can expect serious improvements in hardware support still, so in this case moving ahead makes quite sense.

---

### Post by BBQdave on 2013-01-02
> **ApolloSanNovus said:**
> **Dual booting Ubuntu 12.04 LTS 64-bit on a Windows 8 preinstalled UEFI based Sony VAIO with 3rd gen Core i3 and Intel HD 4000 graphics. **

...how do I go about installing it while preserving the default Windows 8 installation?

Dual booting is definitely the challenge with Win 8 and Secure Boot. OpenSUSE and Redhat are developing a work around - still in development. And FSF, and my guess is the Debian camp soon too, are calling for removal of MS's secure boot on hardware.

For now, you can disable secure boot, lose Win 8 and install Linux.

Not trying to stir the pot, but *secure boot* is MS's attempt to block user choice. There is nothing *secure* about *secure boot*.

---

### Post by ld114 on 2013-01-03
I would also suggest trying Ubuntu 12.04 LTS first. If the Unity launcher is set up with all the user's favourite programs then they can often take to it very quickly.

If your Dad still hankers after a menu system then try the Cinnamon or Mate desktops. Cinnamon is very easy to use, and Mate is pretty much the classic gnome 2 desktop that featured in Ubuntu 10.04 LTS.

---

### Post by AlexDudko on 2013-01-03
> **PhilGil said:**
> 
CentOS or Scientific Linux might be a good choice, as Gnome 2 is supported until at least 2017. The downside is that you may have a learning curve (since they are Red Hat based rather than Debian based). Also, I don't know how they handle essential upgrades (such as the kernel and web browser).


2.6.32 kernel will be there till the end of the release support (6.x). It will receive only security updates. Browser (firefox) has an enterprise version (10 at the moment) which is supported for a year. Then it will be changed by the next enterprise version - 18, which will also have a year support cycle.
They've already changed to Libreoffice and the current version is 3.4.x.

---

### Post by irv on 2013-01-03
> **ld114 said:**
> I would also suggest trying Ubuntu 12.04 LTS first. If the Unity launcher is set up with all the user's favourite programs then they can often take to it very quickly.

If your Dad still hankers after a menu system then try the Cinnamon or Mate desktops. Cinnamon is very easy to use, and Mate is pretty much the classic gnome 2 desktop that featured in Ubuntu 10.04 LTS.

As I said earlier anyone who wants a menu in Ubuntu with Unity, all they need to do is install Cairo-Dock.
[ATTACH]229510[/ATTACH]

---

### Post by BBQdave on 2013-01-03
> **irv said:**
> As I said earlier anyone who wants a menu in Ubuntu with Unity, all they need to do is install Cairo-Dock.
[ATTACH]229510[/ATTACH]

+1 and Cool :)

I think if *Dad* tries and explores Unity, he will like it :D

---

### Post by lykwydchykyn on 2013-01-03
I wouldn't be afraid of Debian; IME it's not really that much setup to install the non-free stuff -- just add the non-free repository and the associated packages.  Since you have Intel graphics, there won't be any proprietary video drivers to monkey with.  If you understand APT, you understand Debian.

If you want a desktop environment with no surprises for a Windows user, just go with LXDE.  It's like Windows 2000's desktop only simpler.

Put Wheezy on there, it's almost finished.  I bet Wheezy goes stable by March, and most of the outstanding bugs affect other platforms or non-desktop stuff.

---

### Post by MadmanRB on 2013-01-05
How about openSUSE 12.2, suse has about 3 years of support, decent enough hardware support and has a windows like interface.
KDE4 should not be any issue for an XP user, its very easy to operate and use even for a total newcomer.

---

### Post by AlexDudko on 2013-01-06
> **MadmanRB said:**
> How about openSUSE 12.2, [COLOR="Red"]suse has about 3 years of support[/COLOR], decent enough hardware support and has a windows like interface.
KDE4 should not be any issue for an XP user, its very easy to operate and use even for a total newcomer.

OpenSUSE's life cycle is twice shorter - 18 months.
[http://en.opensuse.org/openSUSE:FAQ#What_is_the_security_update_life_cycle_for_openSUSE.3F](http://en.opensuse.org/openSUSE:FAQ#What_is_the_security_update_life_cycle_for_openSUSE.3F)

---

### Post by MadmanRB on 2013-01-06
> **AlexDudko said:**
> OpenSUSE's life cycle is twice shorter - 18 months.
[http://en.opensuse.org/openSUSE:FAQ#What_is_the_security_update_life_cycle_for_openSUSE.3F](http://en.opensuse.org/openSUSE:FAQ#What_is_the_security_update_life_cycle_for_openSUSE.3F)

Thats release cycle, one can run a opensuse release until its EOL.
12.2 wont see its end until 2014, that is still three years.
Plus there is community support

---

### Post by AlexDudko on 2013-01-06
> **MadmanRB said:**
> Thats release cycle, one can run a opensuse release until its EOL.
12.2 wont see its end until 2014, that is still three years.
Plus there is community support

OpenSUSE 12.2 has been released on 2012.09.05 and is expected to be supported till 2014.01.15 which is a bit over a year. And it's the official information:
[http://en.opensuse.org/Lifetime#Supported_distributions](http://en.opensuse.org/Lifetime#Supported_distributions)

Could you give a link to prove your words?

And community support doesn't provide any security updates it's just a forum help.

---

### Post by montag dp on 2013-01-06
To me it seems like for someone who's not really a computer person but is used to Windows OS and software, and who already has Windows 8, the best course of action might be to just put classic shell on there and be done with it.

---

### Post by arkanabar on 2013-01-09
I'm going to go outside the box here and suggest rolling-release PCLinuxOS.  Kernel, grub-legacy, synaptic for RPM, and Xorg are kept conservative; other apps roll out pretty quickly after upstream.  Once you've got it installed, just teach him to run synaptic, click "Reload," then "Mark all updates" and then "Apply."  The PCLOS Control Center isn't too terribly different from Windows' Control Panel, either.

---

