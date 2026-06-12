---
title: "FreezyLinux"
date: 2011-11-03
forum: Any Other OS
---

### Post by lucazade on 2011-11-03
I'm glad to announce my distro: Freezy Linux
It is a lightweight derivative of Ubuntu Oneiric Ocelot 12.04, based on GNOME 3.4.1

As main shell it provides a single panel placed at the bottom of the screen, with a hierarchical main menu, a taskbar and tray indicators.
For this reason Freezy doesn't come with Unity (2D/3D) or with GNOME Shell. I prefer a classic setup on a pure GNOME environment!


Applications shipped are more or less the same stock of Ubuntu, main differences are the following:
Firefox &#8594; Chromium
Software Center &#8594; Synaptic
UbuntuOne &#8594; Dropbox
Tomboy &#8594; Zim Note

It comes with an homemade Gtk3/Gtk2 theme and with Faenza icons, memory consumption is really low.. circa 150mb at cold boot!
To create this derivative I've used the great UbuntuMiniRemix iso image, Uck tool and a simple script to build and customize the entire image.


_Some screenshots:_
[URL="http://dl.dropbox.com/u/1338581/freezy/images/menu.png"][IMG]http://dl.dropbox.com/u/1338581/freezy/images/menu-s.png[/IMG]
[/URL]
[URL="http://dl.dropbox.com/u/1338581/freezy/images/control.png"][IMG]http://dl.dropbox.com/u/1338581/freezy/images/control-s.png[/IMG]
[/URL]  


**FreezyLinux [homepage and download links]("http://freezylinux.altervista.org/") **

Any feedback is welcome! :)

---

### Post by dino99 on 2011-11-03
Good project, thanks to have made it :)
Will fight with Lubuntu, same target.

---

### Post by IWantFroyo on 2011-11-03
That looks good! I look forward to a stable release!

> Will fight with Lubuntu, same target.

This is true. I think this looks better than Lubuntu, however.

---

### Post by ventrical on 2011-11-03
I'll consider giving it a try , but , with Linux Mint 11 LDXE running from a  cold boot at 66MBs of sdram ... I mean .. it will be hard to tear me away from that.

---

### Post by lucazade on 2011-11-03
Thanks guys!

@ventrical
honestly it seems a bit low considering that a plain session (only virtual terminals and no Xserver) is around 50mb.
Here you have the full power of GNOME3, a more complete DE.

anyway for miracles I'm not ready yet :P

---

### Post by ventrical on 2011-11-03
> **lucazade said:**
> Thanks guys!

@ventrical
honestly it seems a bit low considering that a plain session (only virtual terminals and no Xserver) is around 50mb.
Here you have the full power of GNOME3, a more complete DE.

anyway for miracles I'm not ready yet :P


 I have an old PIII 650MHz with 512 sdram that I am going to build, I'll test your OS and do some work with Precise. I want to see how far back I can get the newer Ubuntu Kernels - to run on that older software - why with a few mods here and there , jump a couple of pins  etc.. I might surprise myself ! :)

---

### Post by ventrical on 2011-11-03
So far it is a rather elegant desktop. I'm really busy .. but I'll get back at it. :)

Nice work ! :)

[http://www.youtube.com/watch?v=u9W1Ek0eEWU](http://www.youtube.com/watch?v=u9W1Ek0eEWU)

---

### Post by cbowman57 on 2011-11-03
I think Freezy will find an audience. :)

Looks like you did a real nice job on it.

---

### Post by salemboot on 2011-11-03
Slick.

Faenza Icons are good.  I use the Cupertino brand.
[http://gnome-look.org/content/show.php/Faenza-Cupertino?content=129008](http://gnome-look.org/content/show.php/Faenza-Cupertino?content=129008)


I also recommend including Minitube.  I have an older PC that runs flash terribly from the browser but Minitube makes it appeasing even at 480p.

---

### Post by lucazade on 2011-11-04
> **salemboot said:**
> Slick.

Faenza Icons are good.  I use the Cupertino brand.
[http://gnome-look.org/content/show.php/Faenza-Cupertino?content=129008](http://gnome-look.org/content/show.php/Faenza-Cupertino?content=129008)


I also recommend including Minitube.  I have an older PC that runs flash terribly from the browser but Minitube makes it appeasing even at 480p.

nice suggestions.. i'll think about inclusion for a next release.

I'd like to thank everyone  for the support, really appreciated :)

---

### Post by PilotPaul on 2011-11-05
Hi Luca,

Have you included GMA500 support?  I'll be happy to give it a try on my 751h...

Cheers

Paul

---

### Post by lucazade on 2011-11-05
Hi PilotPaul

Unfortunately not yet.. At the moment EMGD drivers should be installed manually. 
Anyway it seems a good idea to include them in a special iso, I'll look what can I do :)

---

### Post by sffvba[e0rt on 2011-11-05
Looks good :)


404

---

### Post by PilotPaul on 2011-11-05
> **lucazade said:**
> Hi PilotPaul

Unfortunately not yet.. At the moment EMGD drivers should be installed manually. 
Anyway it seems a good idea to include them in a special iso, I'll look what can I do :)

Thanks Luca - I have a USB stick ready and waiting! :P

---

### Post by sffvba[e0rt on 2011-11-05
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by wolfen69 on 2011-11-05
Looks good, but reminds me of Lubuntu. You're using gnome 3?

---

### Post by lucazade on 2011-11-05
Yes, it is based on gnome3.. it is the fallback session (gnome-panel + metacity) and the rest of the DE. So no unity or gnome-shell is present in the iso, but installable alongside.

In the first beta (the one available for download) I've used the xfce4-panel because it allowed to use the indicators instead of the old notification area.
Now that indicators are available also for gnome-panel I've replaced the xfce panel to get a full gtk3 gnome3 session. 
In the meanwhile I've fixed also the plymouth issue and the installer refuse present in first build, so in a couple of days I'll release a new build.

---

### Post by wolfen69 on 2011-11-05
> **lucazade said:**
> Yes, it is based on gnome3.. it is the fallback session (gnome-panel + metacity) and the rest of the DE. So no unity or gnome-shell is present in the iso, but installable alongside.

In the first beta (the one available for download) I've used the xfce4-panel because it allowed to use the indicators instead of the old notification area.
Now that indicators are available also for gnome-panel I've replaced the xfce panel to get a full gtk3 gnome3 session. 
In the meanwhile I've fixed also the plymouth issue and the installer refuse present in first build, so in a couple of days I'll release a new build.

Cool, I'll have to check it out soon.

---

### Post by lucazade on 2011-11-06
new build is out with the changes mentioned above..
[http://www.multiupload.com/KAID6XJYSH](http://www.multiupload.com/KAID6XJYSH)

---

### Post by MarjaE on 2011-11-06
Can the desktop environment run with Ubuntu 11.04? I tried a fresh install of Xubuntu 11.10 and it was a disaster, with most of the things that could go wrong going wrong, some of the things that couldn't go wrong going wrong too, and basic functions like _turning the malfuctioning touchpad off_ unavailable.

---

### Post by lucazade on 2011-11-07
> **MarjaE said:**
> Can the desktop environment run with Ubuntu 11.04? I tried a fresh install of Xubuntu 11.10 and it was a disaster, with most of the things that could go wrong going wrong, some of the things that couldn't go wrong going wrong too, and basic functions like _turning the malfuctioning touchpad off_ unavailable.

Did you have the touchpad issue also with the latest build?
About 11.04 i'm afraid it could require too much work and adaptation.. if anyone want to help I'll share sources and steps to create the iso.

---

### Post by lucazade on 2011-11-08
New build.
* added metapackages (freezy-desktop)
* improved panel appearance
* reduced iso image size

This image seems quite stable.. if no other issues are present it can be considered final.
[http://www.multiupload.com/AXZUNGMSV9](http://www.multiupload.com/AXZUNGMSV9)

---

### Post by chrisbarnes1992 on 2011-11-08
Looks good,

I am going to try it in virtual-box. Hopefully it should run with out any issues on Guest additions as i have ad problems running Ubuntu 11.10 with guest additions.

If goes well i might try it on my net-book. Let you know how it goes.

---

### Post by wolfen69 on 2011-11-08
> **ventrical said:**
> I have an old PIII 650MHz with 512 sdram that I am going to build, I'll test your OS and do some work with Precise. I want to see how far back I can get the newer Ubuntu Kernels - to run on that older software - why with a few mods here and there , jump a couple of pins  etc.. I might surprise myself ! :)

Keep us abreast of your findings. I also like to test distros on various equipment. (to say the least)

I'll be trying Freezy soon, look forward to it.

---

### Post by lucazade on 2011-11-09
Added new build, link is in the first post.
* reduced image size, now is 744mb
* replaced banshee and mono-libs with rhythmbox

let me know how it works.. almost every modification is packaged in ppa so it will be easy to spread updates among installations.

cheers

---

### Post by chrisbarnes1992 on 2011-11-09
I have installed your latest version of Freezy in virtual box and is working perfectly. I have also managed to get the Guest additions installed and working properly. :)

As i am planning on putting it on my net-book as it collecting dust at the moment so i shall be able to tell you if it works well.

The net-book is Asus eeepc 900 and it runs Ubuntu 11.04 with out any issue so Freezy should be no problem at all.

Ill let you know how it goes.

---

### Post by Evandar on 2011-11-11
This is absolutely gorgeous. It is so gorgeous that I am considering removing LMDE from my old hardware. I'm  currently running it in virtualbox, and loving it. I would love it to be more customisable though. For one, I prefer my panel on top. Is there a way to use the GNOME 3 fallback with something other than Metacity maybe?

---

### Post by LinuxFan999 on 2011-11-11
I installed this in Virtualbox, and although it is still sluggish, it runs better than Ubuntu 11.10 with Unity 3D.

2 Things I would like to see in a future release:
1. Smaller ISO size.(Under 700MB)
2. Less Ubuntu branding.

Keep up the good work!

---

### Post by lucazade on 2011-11-12
> **chrisbarnes1992 said:**
> I have installed your latest version of Freezy in virtual box and is working perfectly. I have also managed to get the Guest additions installed and working properly. :)

As i am planning on putting it on my net-book as it collecting dust at the moment so i shall be able to tell you if it works well.

The net-book is Asus eeepc 900 and it runs Ubuntu 11.04 with out any issue so Freezy should be no problem at all.

Ill let you know how it goes.

Glad you liked it.. let me know hot it works on your netbook :)


> **Evandar said:**
> This is absolutely gorgeous. It is so gorgeous that I am considering removing LMDE from my old hardware. I'm  currently running it in virtualbox, and loving it. I would love it to be more customisable though. For one, I prefer my panel on top. Is there a way to use the GNOME 3 fallback with something other than Metacity maybe?

If you want to customize panel you need to ALT+Right click .. you can move and add new panels or manage applets.

You can install compiz as metacity alternative and select from login window the correct session, otherwise for a lighter window manager also xfwm4 works great.


> **LinuxFan999 said:**
> I installed this in Virtualbox, and although it is still sluggish, it runs better than Ubuntu 11.10 with Unity 3D.

2 Things I would like to see in a future release:
1. Smaller ISO size.(Under 700MB)
2. Less Ubuntu branding.

Keep up the good work!

I'll keep in mind both suggestions!

---

### Post by Evandar on 2011-11-12
yeah, I discovered how to customise the session after some google searching and have kept playing around with it.

This is showing promise for me. I'm still trying to decide what to use on my main laptop, and freezy is looking more and more appealing since I've wanted to minimise resource hunger for a while now. Major props for bringing out the fallback mode to the forefront like this, I would probably have never even tried GNOME 3 if it wasn't for your spinoff. Screenshots/Videos of it were enough to make me puke in my central nervous system. I wish you all the best, you've earned a supporter in me. This is one to follow.

---

### Post by cwklinuxguy on 2011-11-12
Hmm. Looks quite interesting. I too am working on an Ubuntu derivative at the moment, which I will have an Alpha of soon.

---

### Post by Dlambert on 2011-11-12
Looks good! Any hopes of a 64 bit version? :KS:KS:KS:KS:KS

---

### Post by Megaptera on 2011-11-13
> **Dlambert said:**
> Looks good! Any hopes of a 64 bit version? :KS:KS:KS:KS:KS

+ 1 (if poss)  :D

---

### Post by lucazade on 2011-11-13
ok for the 64bit version.. just give me some days to build and upload :)

---

### Post by Megaptera on 2011-11-13
:D thanks!

---

### Post by Dlambert on 2011-11-13
Wooooooooo!

---

### Post by lucazade on 2011-11-13
It looks like I need to install ubuntu64 in order to create a 64bit version of freezy.. otherwise chroot-ing the mini image fails miserably.. ugh :/

Anyone can confirm this? Can I chroot a 64bit image from a 32bit install?

---

### Post by cbowman57 on 2011-11-13
> **lucazade said:**
> It looks like I need to install ubuntu64 in order to create a 64bit version of freezy.. otherwise chroot-ing the mini image fails miserably.. ugh :/

Anyone can confirm this? Can I chroot a 64bit image from a 32bit install?

I know with UCK it takes a 64-bit OS to build a 64-bit iso, so I'd say it's pretty much confirmed. :)

---

### Post by lucazade on 2011-11-13
> **cbowman57 said:**
> I know with UCK it takes a 64-bit OS to build a 64-bit iso, so I'd say it's pretty much confirmed. :)

oh thanks.. the whole process requires more love than I thought.
let's start partitioning and downloading standard ubu64 to create the derivative.. it is anyway an oppurtunity for me to test again 64bit here and evaluate about a switch for my next lts installation :)

---

### Post by chrisbarnes1992 on 2011-11-13
I hvae now got Freezy going on my net-book and it is going really well.  its working very fast and is much more responsive than Ubuntu's 11.04  as that is was last on there.

There is a lot of Ubuntu branding around however you have to start  somewhere. LOL. I know that very well as i am re-starting my little os  project. I used Debian as a base. 

Have you got anymore plans for Freezy?

I have seen 64bit mentioned which would be good.

---

### Post by lucazade on 2011-11-13
> **chrisbarnes1992 said:**
> I hvae now got Freezy going on my net-book and it is going really well.  its working very fast and is much more responsive than Ubuntu's 11.04  as that is was last on there.

There is a lot of Ubuntu branding around however you have to start  somewhere. LOL. I know that very well as i am re-starting my little os  project. I used Debian as a base. 

Have you got anymore plans for Freezy?

I have seen 64bit mentioned which would be good.

I'm glad to hear it works well, personally I've installed on 6 machines thanks to my friends and their disposability and they are happy as well!

Yep, I've to purge the remaining ubuntu branding (plymouth and grub in livecd, ubuntu username during live session and ubiquity installer brands).. I've already the bits ready but no time to test them properly yet.

About plans.. surely a 64bit version and if possible shrink iso size below 700mb in order to fit common cd size.
If there will be no particular news in Precise Pangolin I suppose Freezy will be very similiar to Oneiric release, just updated software.

Anyway I will be glad to hear from all of you about suggestions for the future...

---

### Post by gordintoronto on 2011-11-13
In Freezy, the CPU in my AMD-based laptop keeps running at top speed (2.1 GHz), where it spends most of its time at 800 MHz in Oneiric. As a result, it runs about 15 degrees hotter!

Also, I have used only 64-bit OSes for more than two years.

---

### Post by BrokenKingpin on 2011-11-14
I really don't like the name, but other than that it looks okay. I like the default application selection... zim Notes is awesome.

I am not sure about the inclusion of Dropbox though. Dropbox is not open source, so there may be legal issues redistributing it. I also don't see the need for it to be included  by default. If people want it they can take two seconds and get it from the website or whatever.

The theme has the same feel as clearlooks to me, which makes it seem dated. That is personal preference though. I always leaned towards dark panels and window decorators, with light controls (i.e. Shiki Brave).

I do like the single panel approach, gives it a simplistic and clean look. I really don't see the point of using the Gnome 3 fallback though... you might as well just use something like Xfce.

---

### Post by lucazade on 2011-11-14
> **BrokenKingpin said:**
> I really don't like the name, but other than that it looks okay. I like the default application selection... zim Notes is awesome.

Free + Easy = Freezy
and tux works well with freezy climate :)

> I am not sure about the inclusion of Dropbox though. Dropbox is not open source, so there may be legal issues redistributing it. I also don't see the need for it to be included  by default. If people want it they can take two seconds and get it from the website or whatever.

'nautilus-dropbox' included in the distro is just the web installer.. until you execute it for the first time you don't have any closed source bit installed in your system.
Just like jockey (video drivers installer) or flash-plugin installer present in firefox.

UbuntuOne unfortunately is not at the same level of dropbox.

> The theme has the same feel as clearlooks to me, which makes it seem dated. That is personal preference though. I always leaned towards dark panels and window decorators, with light controls (i.e. Shiki Brave).
tastes.. I can say only I like simple and easy on the eyes themes for everyday use.

> I do like the single panel approach, gives it a simplistic and clean look. I really don't see the point of using the Gnome 3 fallback though... you might as well just use something like Xfce.

I prefer gnome over xfce, that's why I employed it.

---

### Post by Hylas de Niall on 2011-11-15
You need a logo for the backdrop and the site, and a banner for users to fly. This thing seems good enough to wear a badge.
:guitar:

---

### Post by KBD47 on 2011-11-20
Looks good, I will burn it onto a stick and check it out.
KBD47

---

### Post by chrisbarnes1992 on 2011-11-20
Freezy is still running well on the netbook, not ran into 1 problem yet. 

Have you done anything else to Freezy recently?

---

### Post by KBD47 on 2011-11-20
Just booted up on my netbook. So far very impressed. I do miss the weather app on the panel. Also curious about the long term plans, future of Freezy, do you plan on carrying this into the 12.04 LTS release next Spring? 
KBD47

---

### Post by lucazade on 2011-11-20
Hi!

No changes recently.. I was really busy at work and no spare time to invest in freezy dev.
Asap i'll try to build the 64bit version, sorry for the delay.

About the future the only thing I can assure at the moment is the tradition panel layout, no docks, globalmenu or other new paradigms for the shell. So next LTS will look probably the same.
If Slickpanel will mature enough, and gnome-panel won't receive any good development, I could think about a switch.
(Slickpanel is a new panel written in vala, mainly a fork of elementary wingpanel)

---

### Post by KBD47 on 2011-11-20
Thanks! I will be watching with interest.

---

### Post by KBD47 on 2011-11-21
After playing around with this on a usb stick I liked it so much that I decided to add it to a partition on my hard drive. I have come across two issues: the Jupiter power saver applet won't work with Freezy, at least I couldn't get it to work. I can't get Thunderbird to work either. Here is the what the window says after I put in my info:
Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.
  I hit OK then it says:
[Exception... "Component returned failure code: 0x804b0033 (NS_ERROR_UNKNOWN_SOCKET_TYPE) [nsISocketTransportService.createTransport]"  nsresult: "0x804b0033 (NS_ERROR_UNKNOWN_SOCKET_TYPE)"  location: "JS frame :: chrome://messenger/content/accountcreation/guessConfig.js :: SocketUtil :: line 1085"  data: no]

  Never seen that before on any of the installs that I've used Thunderbird on. I'm not out of space as this is on a 60 gig partition. Any help would be appreciated.
Thanks!
KBD47

---

### Post by sammiev on 2011-11-21
> **lucazade said:**
> Hi!

No changes recently.. I was really busy at work and no spare time to invest in freezy dev.
Asap i'll try to build the 64bit version, sorry for the delay.

About the future the only thing I can assure at the moment is the tradition panel layout, no docks, globalmenu or other new paradigms for the shell. So next LTS will look probably the same.
If Slickpanel will mature enough, and gnome-panel won't receive any good development, I could think about a switch.
(Slickpanel is a new panel written in vala, mainly a fork of elementary wingpanel)

Sounds great. I will wait for the 64 bit version. :)

---

### Post by wolfen69 on 2011-11-21
Two of my **test** hard drives just died, but I plan on checking it out soon. I just got a new drive. :D I'm still not sold on opensuse and mint.

---

### Post by KBD47 on 2011-11-21
> **wolfen69 said:**
> Two of my **test** hard drives just died, but I plan on checking it out soon. I just got a new drive. :D I'm still not sold on opensuse and mint.

I think Gnome Fallback can be tweaked in Mint to work very well. I also think Freezy is a good choice for those wanting to keep a familiar classic desktop.

---

### Post by lucazade on 2011-11-22
> **KBD47 said:**
> After playing around with this on a usb stick I liked it so much that I decided to add it to a partition on my hard drive. I have come across two issues: the Jupiter power saver applet won't work with Freezy, at least I couldn't get it to work. I can't get Thunderbird to work either. Here is the what the window says after I put in my info:
Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.
  I hit OK then it says:
[Exception... "Component returned failure code: 0x804b0033 (NS_ERROR_UNKNOWN_SOCKET_TYPE) [nsISocketTransportService.createTransport]"  nsresult: "0x804b0033 (NS_ERROR_UNKNOWN_SOCKET_TYPE)"  location: "JS frame :: chrome://messenger/content/accountcreation/guessConfig.js :: SocketUtil :: line 1085"  data: no]

  Never seen that before on any of the installs that I've used Thunderbird on. I'm not out of space as this is on a 60 gig partition. Any help would be appreciated.
Thanks!
KBD47

Thunderbird works well here with freezy, no issues with it..
about jupiter I don't know, I don't use it. I'll try to install to see if there is any conflict.

---

### Post by KBD47 on 2011-11-22
Really not sure what happened with Thunderbird. I've probably used it on at least a half-dozen distros with no problem getting it to connect and download my mail. I spent an hour trying different things and it just wouldn't connect, even though everything else connected fine. It would be nice if I could get Jupiter to work, but neither of those things are deal breakers. I'm totally impressed with Freezy. It is more polished and better looking than Xubuntu or Lubuntu. The icons and desktop look incredible, almost 3D. I like the default programs you've chosen. I think if more people knew about this, particularly those who dislike Unity and Gnome Shell, many people would be using this. Fallback is the only thing about Gnome right now that is worth anything.
  I do have one concern, what happens if Gnome drops Fallback? From what I've read that looks like where they are headed, they apparently are going to get Shell set up to work on older hardware so they won't need Fallback. I'd like to see Fallback at least make it to LTS so we would have it with 5 years support. Will you be able to keep Freezy with Fallback working if Gnome drops Fallback?
Thanks again for your good work, it is much appreciated!
KBD47

---

### Post by jimrew111 on 2011-11-22
very cute name :D
nice job removing shell :) :KS
but is needs a better desktop background.

---

### Post by gordintoronto on 2011-11-22
You want great backgrounds, go to the National Geographic site.

---

### Post by jimrew111 on 2011-11-22
where's the tweak tool? I want it to show trash and computer and home.

---

### Post by KBD47 on 2011-11-22
> **jimrew111 said:**
> where's the tweak tool? I want it to show trash and computer and home.

Look for advanced settings under: menu-other

---

### Post by cbowman57 on 2011-11-22
Pretty sure you can toggle that stuff on with dconf-editor too.

---

### Post by jimrew111 on 2011-11-23
I did try that and nothing.

---

### Post by el_bandido on 2011-11-29
Luca - how did you force gnome 3.2 back to panel mode? I know there is an option in shell for fallback mode, but I don't want to have to install the whole shell to make it run like that.

---

### Post by cbowman57 on 2011-12-04
@lucazade, did you by chance install broadcom support by default?

I've got a project I need wireless from the start & installation.

If it doesn't that's not a problem, I can crack it open with UCK & add it myself.

---

### Post by lucazade on 2011-12-04
> **el_bandido said:**
> Luca - how did you force gnome 3.2 back to panel mode? I know there is an option in shell for fallback mode, but I don't want to have to install the whole shell to make it run like that.

i've simply installed gnome-session-fallback, gnome-panel and the support for indicators

---

### Post by lucazade on 2011-12-04
> **cbowman57 said:**
> @lucazade, did you by chance install broadcom support by default?

I've got a project I need wireless from the start & installation.

If it doesn't that's not a problem, I can crack it open with UCK & add it myself.

I don't think I'll add it, I prefer to not play with drivers in the stock image to avoid any issues.
Feel free to crack it :)

---

### Post by cbowman57 on 2011-12-04
> **lucazade said:**
> I don't think I'll add it, I prefer to not play with drivers in the stock image to avoid any issues.
Feel free to crack it :)

Thanks, I reached that same conclusion on my old spin.

I bet 99.999% of the Ubuntu users have never taken a peek at UCK.  :)
It's a very handy tool for doing things like installing wireless support, or other apps & drivers into a live iso.

---

### Post by lucazade on 2011-12-04
> **cbowman57 said:**
> Thanks, I reached that same conclusion on my old spin.

I bet 99.999% of the Ubuntu users have never taken a peek at UCK.  :)
It's a very handy tool for doing things like installing wireless support, or other apps & drivers into a live iso.

Exactly :)

If anyone want to contribute or create Freezy from scratch this is
the build script I use on top of Ubuntu [mini image]("https://help.ubuntu.com/community/Installation/MinimalCD") or 
[mini remix image]("http://www.ubuntu-mini-remix.org/") (livecd):

```
wget dl.dropbox.com/u/1338581/freezy/freezy

```
and execute it after minimal installation or with uck/chroot/miniremix with:
sudo sh freezy

OT note: lately i'm playing with gnomeshell and it looks like is really improved.. if you see any strange update in ppa it's me :)

---

### Post by cbowman57 on 2011-12-04
@lucazade, do you still want a 64-bit version?

If so I'll try to look at your script & grab mini remix this week, if it's something I can figure out I'll generate one for you.

Does the script handle all your app substitutions & locate the artwork?

If it's something you want to see get done, and nobody else steps up, I'll give t a go.

I've been head over heels for Gnome shell within hours of trying it out, which coincided with the availability of extensions & themes.  I couldn't go back to anything else now. :)

---

### Post by lucazade on 2011-12-04
I'd be great if you can make the 64bit version.. i'm really busy in this period :|

The script works for both 32bit and 64bit, it provides ppa, packages, artwork and tweaks.
So all the necessary stuff...

To create a livecd with miniremix and uck you need to use commandline backend of uck (gui version of uck can't handle miniremix).

there are other 2 script that automatize uck command line:

```
# unpackage mini iso image
wget dl.dropbox.com/u/1338581/freezy/uck1
sudo sh uck1

# chroot session
wget dl.dropbox.com/u/1338581/freezy/freezy
sh freezy
exit

# finalize iso image
wget dl.dropbox.com/u/1338581/freezy/uck2
sudo sh uck2
```

and you'll find the new iso in /home/xx/uck/newimages

let me know if it's clear :)

---

### Post by cbowman57 on 2011-12-04
I'll try to get that done within the next couple days.  

If I have any problems or questions I'll ask you.  If you don't hear anything from me by Wednesday ask me what's the hold up. :)

---

### Post by cbowman57 on 2011-12-04
I've run into a snag, not sure that I'm following instruction to the letter.
Open it with UCK from command line (I'm not finding that)

Then once the iso is opened up wget those files & run the scripts in sequence?

I feel like a dunce this morning. :)

---

### Post by cbowman57 on 2011-12-04
Well this has frustrated me to no end.
It seems to construct ok, boots up & gets me to the lightdm, asking for username & pwd.  Just to check it out I tried to see what options are available for login & all it shows is fvwm. ???

Is there a username & pwd that I overlooked?

---

### Post by lucazade on 2011-12-04
> **cbowman57 said:**
> Well this has frustrated me to no end.
It seems to construct ok, boots up & gets me to the lightdm, asking for username & pwd.  Just to check it out I tried to see what options are available for login & all it shows is fvwm. ???

Is there a username & pwd that I overlooked?

mmh.. no, there are no special username or pwd.
is gnome-session-fallback installed? it provides 'gnome-fallback' session in lightdm.

---

### Post by cbowman57 on 2011-12-04
> **lucazade said:**
> mmh.. no, there are no special username or pwd.
is gnome-session-fallback installed? it provides 'gnome-fallback' session in lightdm.

I'm beginning to wonder about that as well, I was up all night, had to get some rest I was unproductive.  One thought I had is that the 64-bit might require some multi-lib files & I don't think your script takes that into account, if indeed they are required. 

Going to take a break from it, do some thinking and revisit the process later.

---

### Post by cbowman57 on 2011-12-06
Ok, in a bit of a fix.  Is there anyone interested in this project that is willing to try & tackle creating a 64-bit iso using  the recipe & scripts provided by lucazade?

I don't know what's keeping from creating one successfully but I wouldn't mind some feedback from anyone else that tries it.

---

### Post by el_bandido on 2011-12-06
Using this on an eeepc 1001px in stock form, works very well. Might try it on my T91mt, what's the GMA500 support like? Any chance you could package it with the latest kernel and driver modules? :D

---

### Post by TeamRocket1233c on 2011-12-06
Sweet.
What hardware specs will it run on?

---

### Post by el_bandido on 2011-12-07
Lucazade - The installer fails after the initial option menu on the T91mt, not sure why.

---

### Post by lucazade on 2011-12-07
> **el_bandido said:**
> Lucazade - The installer fails after the initial option menu on the T91mt, not sure why.

start 'ubiquity' installer from terminal and look where it dies.. also report a bug with: 'ubuntu-bug ubiquity'

anyway didn't see here, so can't help at the moment.

---

### Post by lucazade on 2011-12-07
Made the 64bit iso image, testing right now.. everything seems ok.
In the next hours i'll upload to some server and report back the links.

Recipes and scripts were ok also for 64bit, so cbowman57 I don't get where you found problems building.. 

I made also some changes to gnome panel, default theme and wallpaper and to the login manager. So i'll push both i386 and amd64 iso images in the next hours. 

See you

---

### Post by cbowman57 on 2011-12-07
> **lucazade said:**
> Made the 64bit iso image, testing right now.. everything seems ok.
In the next hours i'll upload to some server and report back the links.

Recipes and scripts were ok also for 64bit, so cbowman57 I don't get where you found problems building.. 

I made also some changes to gnome panel, default theme and wallpaper and to the login manager. So i'll push both i386 and amd64 iso images in the next hours. 

See you

Could be I was over-thinking the process, or maybe your familiarity with the scripts worked to your advantage.

Whatever the reason, glad you got it done, I'm sure there are some people waiting to try it out. ;)

---

### Post by Megaptera on 2011-12-07
Looking forward to giving it a spin, thanks!

---

### Post by lucazade on 2011-12-07
thanks guys for the support.. 
i386 is uploaded, now it is the turn of amd64.. I believe tomorrow will be both available :)

---

### Post by Dlambert on 2011-12-07
> **lucazade said:**
> thanks guys for the support.. 
I386 is uploaded, now it is the turn of amd64.. I believe tomorrow will be both available :)

Good news!!!!! :)

---

### Post by Dlambert on 2011-12-07
I know this is nearly impossible.....but rolling release??? Rather than installing the latest version of ubuntu, just have all they key updates/tweaked ones automatically install? That would make this my #1 Distro. Currently #3 After Debian Testing and Ubuntu.

---

### Post by lucazade on 2011-12-08
[B]New 32 and 64 bit releases are available on freezy homepage..
[/B][http://freezylinux.altervista.org/](http://freezylinux.altervista.org/)

let me know how it works..


#####


@Dlambert

It would be nice... also because next Ubuntu release won't ship full gnome 3.4 but only some pieces.
I'll think about it, maybe it could be enough to ships ppa for every app.. mmh.. what do you think?! :)

---

### Post by Basher101 on 2011-12-08
*Tear of Joy* 
*sniff*

oh the beauty of FOSS....making your own distro..
oh the possibilities...

Have a nice day trying to make your own OS from Windows without hacking it :D


this really looks great! high regards from me. Keep it up.

---

### Post by chrisbarnes1992 on 2011-12-08
Nice ill see if i can get some time before going away from xmas to play with the 64bit version. 

Im still using Freezy on my eepc 900 which i might be updating soon.

---

### Post by Megaptera on 2011-12-08
D/l 64 bit now ... thanks!

---

### Post by cbowman57 on 2011-12-08
good job lucazade, sorry I couldn't get it built to save you the hassle, but it looks like a lot of people were looking forward to it.

---

### Post by Dlambert on 2011-12-08
Myself included :)

---

### Post by cbowman57 on 2011-12-08
> **Dlambert said:**
> Myself included :)

I stay in the shell but I have to give props where they are due, this is one fast light gnome-fallback distro.

+1

---

### Post by Dlambert on 2011-12-08
What's going to happen with the upgrade to 12.04?

---

### Post by mivilleb on 2011-12-09
I was hoping FreezyLinux would work out of the box with GMA500 but I just tried the live version from USB and it failed and only gives me the command line. Since my WiFi does not work until a driver is installed, I can not manually install the drivers (no Lan input). Since you already done it in your Ubuntu version of 10.04 (the one I am using right now) any chance you will add support to GMA500 in future update of FreezyLinux?

---

### Post by lucazade on 2011-12-09
@mivilleb
I can't add EMGD drivers for gma500 directly in Freezy because I have to downgrade all Xorg server and add a lot a tweaks that don't work well with other graphic cards (i.e. ati or nvidia). 
I use this also on other machines so I'd like to have a clean iso to use and add drivers after installation.
(If you need an Oneiric iso with emgd on board I've posted one in gma500 megathread some time ago).

In the next release of Ubuntu 12.04 (and freezy of course) there will be support out of the box for the gma500 thanks to the kernel 3.2 ;)

---

### Post by mivilleb on 2011-12-09
Your 11.10 iso with GMA500 support:

[http://ubuntuforums.org/showpost.php?p=11356431&postcount=4605](http://ubuntuforums.org/showpost.php?p=11356431&postcount=4605)

Grazie

---

### Post by Dlambert on 2011-12-10
So, after doing some testing on the 64 bit version, I've come across a couple bugs. When first booting up, at the "try" or "install" Ubuntu screen, there is a giant pink bar taking up 1/4th of the screen with some sys tray icons. in the middle right. 
 
 
A few suggestions; 
 
1) Make your own boot screen, I could not for the life of me determine if this was freezy or Ubuntu. 
 
2) Make a logo and rebrand everything, I don't want to see the Ubuntu logo *or at least the default one* Maybe a "frozen" iced over kind of Ubuntu logo, that sounds cool to me.
 
3) MAYBE, and I mean MAYBE if it's legal, include the ATI/Nvidia proprietary drivers.
 
4)I think a nice winter (freezy) wallpaper would look slick.
 
 
Anyways, I love this distro and will continue to test it and let you know what I think. Thank you!

---

### Post by cbowman57 on 2011-12-10
> **Dlambert said:**
> So, after doing some testing on the 64 bit version, I've come across a couple bugs. When first booting up, at the "try" or "install" Ubuntu screen, there is a giant pink bar taking up 1/4th of the screen with some sys tray icons. in the middle right. 
 
 
A few suggestions; 
 
1) Make your own boot screen, I could not for the life of me determine if this was freezy or Ubuntu. 
 
2) Make a logo and rebrand everything, I don't want to see the Ubuntu logo *or at least the default one* Maybe a "frozen" iced over kind of Ubuntu logo, that sounds cool to me.
 
3) MAYBE, and I mean MAYBE if it's legal, include the ATI/Nvidia proprietary drivers.
 
4)I think a nice winter (freezy) wallpaper would look slick.
 
 
Anyways, I love this distro and will continue to test it and let you know what I think. Thank you!

Good suggestions.  How are you with gimp?

---

### Post by lucazade on 2011-12-10
> **Dlambert said:**
> So, after doing some testing on the 64 bit version, I've come across a couple bugs. When first booting up, at the "try" or "install" Ubuntu screen, there is a giant pink bar taking up 1/4th of the screen with some sys tray icons. in the middle right. 

never seen here this bug in tons of trials.. sound really strange.

 > **Dlambert said:**
> 
1) Make your own boot screen, I could not for the life of me determine if this was freezy or Ubuntu. 
definitely on my list but my gimp capabilities are low, really. 
so any contribution is welcome.
 > **Dlambert said:**
> 
2) Make a logo and rebrand everything, I don't want to see the Ubuntu logo *or at least the default one* Maybe a "frozen" iced over kind of Ubuntu logo, that sounds cool to me.
same as before.

 > **Dlambert said:**
> 
3) MAYBE, and I mean MAYBE if it's legal, include the ATI/Nvidia proprietary drivers.
I can't because it is not legal and because different drivers installed cannot coexist in the same system. (nvidia drivers for example create a xorg.conf that breaks ati cards from loading up)
 > **Dlambert said:**
> 
4)I think a nice winter (freezy) wallpaper would look slick.
if we gather something cool I'll update the wallpaper package.
 > **Dlambert said:**
> 
Anyways, I love this distro and will continue to test it and let you know what I think. Thank you!

thanks mate for support and feedbacks

---

### Post by Dlambert on 2011-12-12
I'll see what i can do this weekend in GIMP. I'll work on it! This is going to replace Ubuntu on my rig!

---

### Post by Dlambert on 2011-12-12
Working right now! Uploads maybe later tonight!

---

### Post by Dlambert on 2011-12-12
WELL! I made a logo ( Your decision though) And I started with this:

---

### Post by Dlambert on 2011-12-12
Then I split it and added an alpha channel: (The last one's White so it's hard to see) I wanted a "snowflake" like look, and this is what I came up with.

---

### Post by Dlambert on 2011-12-12
Then I had the idea of using this as the "start orb" ? :

---

### Post by lucazade on 2011-12-12
Dlambert.. they both look good. It seems a good start.
The first one, even if not really original, or better too much close to the ubuntu logo, is anyway appropriated  to the 'freezy' meaning.. it looks like a snow flake, nice :)
The second logo also looks good but I don't find anything that recall freezy in it. Dunno..

anyway play with them and let me know your new or improved stuff ;)
ciao

---

### Post by Dlambert on 2011-12-12
Then I started to make wallpapers, (I don't think I can upload them)

---

### Post by Dlambert on 2011-12-12
Thanks! The ubuntu logo is just a template

---

### Post by Dlambert on 2011-12-12
AND, the logo can be rotated or changed as you see fit. Just let me know if you're interested. And I thought of an arctic wolf as a good logo (kinda like ur avatar)

---

### Post by cbowman57 on 2011-12-12
That's really looking nice & unique. :)

---

### Post by sammiev on 2011-12-12
Now if you can make it look a little like each. 1/2 of one and then the other I would think that would be great. Nice to have a little of ubuntu and you in there. :)

---

### Post by KBD47 on 2011-12-12
How about a white wolf's head inside a snowflake shape? Or inside an Ubuntu type shape?

---

### Post by Warren Watts on 2011-12-12
Are the ISOs available as torrents?  I don't have the patience to wait an entire hour for a file sharing service, and besides, I can seed it when I am done.

---

### Post by Dlambert on 2011-12-13
> **Warren Watts said:**
> Are the ISOs available as torrents?  I don't have the patience to wait an entire hour for a file sharing service, and besides, I can seed it when I am done.

Yeah I thought about this too, but then, there isn't a huge user base (yet) so really no need for torrents ATM.



I'll see what I can do about the Logo idea, but again it's the OP's decision.

---

### Post by Dlambert on 2011-12-13
I made the "snowflakes" with white spots etc to give it a flaky look, rather than one solid color, this can be reversed if needed.

---

### Post by Hylas de Niall on 2011-12-14
I'm liking those logos and wallpapers very much. Great work!

---

### Post by Dlambert on 2011-12-14
Thank you! But they aren't the Official Freezy logo. (yet at least)

---

### Post by lucazade on 2011-12-17
Dlambert I appreciate your contributions and to make them default for freezy I need some variations and different sizes.

To fully rebrand freezy we need a plymouth splash background.. I'd say to keep the bg black with a logo in the middle. Black because bootup will look smooth without too much flickering.

The wallpaper attached seems good as default one and could be used also for login manager. I need it at 1920x1080 in png, maybe the logo should be polished a little.

For login manager Lightdm it would be nice to have also a "Freezy Linux" label in the bottom left, like the current ubuntu label. This could be a simple overlay trasparent png.

We need also an icon for the bottom panel, the start orb.
It should be 22x22 png and follow the faenza-dark style to fully fit with the rest.

what do you think?

---

### Post by Dlambert on 2011-12-17
> **lucazade said:**
> Dlambert I appreciate your contributions and to make them default for freezy I need some variations and different sizes.

To fully rebrand freezy we need a plymouth splash background.. I'd say to keep the bg black with a logo in the middle. Black because bootup will look smooth without too much flickering.

The wallpaper attached seems good as default one and could be used also for login manager. I need it at 1920x1080 in png, maybe the logo should be polished a little.

For login manager Lightdm it would be nice to have also a "Freezy Linux" label in the bottom left, like the current ubuntu label. This could be a simple overlay trasparent png.

We need also an icon for the bottom panel, the start orb.
It should be 22x22 png and follow the faenza-dark style to fully fit with the rest.

what do you think?

I will start working! They were all just rough sketches/ideas.

---

### Post by Dlambert on 2011-12-17
Which one do you like better? The white, light blue, or darker blue logo?

---

### Post by Dlambert on 2011-12-17
I was just messing around and this happen:

---

### Post by Basher101 on 2011-12-17
> **Dlambert said:**
> I was just messing around and this happen:

somehow doesn't look right lol

---

### Post by Dlambert on 2011-12-17
I know! Another prototype:

---

### Post by Dlambert on 2011-12-17
And:

---

### Post by Dlambert on 2011-12-17
> **Dlambert said:**
> And:

Which turns into this:

---

### Post by lucazade on 2011-12-17
the last 2 logo are ok.. at least as shape.
color is mainly ok.. but if you want to iterate it a little more you're free.

---

### Post by Dlambert on 2011-12-17
> **lucazade said:**
> the last 2 logo are ok.. at least as shape.
color is mainly ok.. but if you want to iterate it a little more you're free.

What would you like? Color wise, etc?


Also I kinda like this, but I don't know how to smooth the curves in gimp.

---

### Post by Dlambert on 2011-12-17
Or something like:

---

### Post by cmcanulty on 2011-12-26
Is a 2nd panel an option? I like all my app shortcuts on top panel and all minimized running apps in bottom panel. Looks great .

---

### Post by Dlambert on 2011-12-29
Anything new to report?

---

### Post by lucazade on 2011-12-30
Dlambert, I'd say to use cyan or white as logo color because it will adapt better to different contexts (i.e .the dark panel and dark plymouth)  
It would be nice also a variation with the label "FreezyLinux" to put alongside the logo. what do you think?

---

### Post by Dlambert on 2011-12-30
> **lucazade said:**
> Dlambert, I'd say to use cyan or white as logo color because it will adapt better to different contexts (i.e .the dark panel and dark plymouth)  
It would be nice also a variation with the label "FreezyLinux" to put alongside the logo. what do you think?

I can do that, hows development going?

---

### Post by lucazade on 2011-12-30
> **Dlambert said:**
> I can do that, hows development going?

Lately I've refined some freezy packages, especially desktop metapackage and gtk theme.. Everything is stable at the moment so no major work is expected in this period (except artwork/branding).

What I'm not so happy is the state of gnome-panel3.. is still buggy and no more developed (gnome-shell will provide a 2d experience in future so gnomepanel doens't get any attention).
If I had some spare time I'd develop a new panel in python and gtk3 because there are no good alternatives. A simple panel that provides a main menu for apps, taskbar and notification/indicator area. If anyone want to contribute for this I'd be happy :)

---

### Post by Dlambert on 2011-12-30
> **lucazade said:**
> Lately I've refined some freezy packages, especially desktop metapackage and gtk theme.. Everything is stable at the moment so no major work is expected in this period (except artwork/branding).

What I'm not so happy is the state of gnome-panel3.. is still buggy and no more developed (gnome-shell will provide a 2d experience in future so gnomepanel doens't get any attention).
If I had some spare time I'd develop a new panel in python and gtk3 because there are no good alternatives. A simple panel that provides a main menu for apps, taskbar and notification/indicator area. If anyone want to contribute for this I'd be happy :)

Good news. I'll look into it.

---

### Post by vanlong441 on 2011-12-30
> **lucazade said:**
> 
If I had some spare time I'd develop a new panel in python and gtk3 because there are no good alternatives. A simple panel that provides a main menu for apps, taskbar and notification/indicator area. If anyone want to contribute for this I'd be happy :)

[http://www.ubuntugeek.com/slickpanel-modern-panel-that-provides-tools-such-as-a-list-of-open-windows-and-an-indicator-bar.html](http://www.ubuntugeek.com/slickpanel-modern-panel-that-provides-tools-such-as-a-list-of-open-windows-and-an-indicator-bar.html)

---

### Post by VanR on 2011-12-30
Downloaded and ran it from Live CD and really liked what I saw. Nice minimal desktop without a lot of clutter.  But it really needs some branding. Freezy Linux splash screen, Freezy Linux menu icon. I know you are working on these and I may come back to it when those things are implemented. Good job.

---

### Post by cbowman57 on 2011-12-31
I installed Freezy on an old notebook for some friends last week, it came with XP but barely had the power to run it.  I got a message the other day & they can't believe how fast their computer is now. (Even better than when it was new) :)

---

### Post by lucazade on 2011-12-31
> **vanlong441 said:**
> [http://www.ubuntugeek.com/slickpanel-modern-panel-that-provides-tools-such-as-a-list-of-open-windows-and-an-indicator-bar.html](http://www.ubuntugeek.com/slickpanel-modern-panel-that-provides-tools-such-as-a-list-of-open-windows-and-an-indicator-bar.html)

I know slickpanel... it is a nice project but unfortunately is not actively developed.
Otherwise it would be a great alternative.

[https://code.launchpad.net/~and471/slickpanel/trunk](https://code.launchpad.net/~and471/slickpanel/trunk)

---

### Post by vanlong441 on 2011-12-31
I see the opposite
[https://code.launchpad.net/~and471/+archive/slickpanel-daily](https://code.launchpad.net/~and471/+archive/slickpanel-daily)

---

### Post by lucazade on 2011-12-31
> **vanlong441 said:**
> I see the opposite
[https://code.launchpad.net/~and471/+archive/slickpanel-daily](https://code.launchpad.net/~and471/+archive/slickpanel-daily)

Trust me, there are some commit some time but the panel is not usable at the moment and with this development speed it will be not usable for a long time.

I'm in touch with the slick panel author and if you look at bug reports I've already provided some help were I can.

---

### Post by BrokenKingpin on 2012-01-03
> **lucazade said:**
> 
What I'm not so happy is the state of gnome-panel3.. is still buggy and no more developed (gnome-shell will provide a 2d experience in future so gnomepanel doens't get any attention).
If I had some spare time I'd develop a new panel in python and gtk3 because there are no good alternatives. A simple panel that provides a main menu for apps, taskbar and notification/indicator area. If anyone want to contribute for this I'd be happy :)
Reasons like this are why I use Xfce... a nice simple design with a standard panel that just works.

---

### Post by lucazade on 2012-01-04
> **BrokenKingpin said:**
> Reasons like this are why I use Xfce... a nice simple design with a standard panel that just works.

I agree with you, xfce has a simple design with a standard panel but i've always prefered gnome over it even with its limits.
I prefer also to use gtk3 applications, xfce needs a rewrite because its apps are no more developed.. so xfce5 could be a great surprise.

---

### Post by KBD47 on 2012-01-08
Been playing around with Freezy Linux again tonight. Installed it to a usb using unetbootin and set for 2 gig persistence. It is working great. This must be a newer iso than I used the last time, I notice the wallpaper is different and I was able to get the weather app working this time. The only issue I've had is after installing dropbox and restarting it launches the dropbox setup window instead of just syncing in the panel. When I close that window then dropbox completely disappears from my panel. It is the the same dropbox setup window you get if you go to the menu and click on internet and then dropbox under apps. I'm guessing something is set up wrong in the startup applications setting for dropbox. When the computer restarts it should just sync and check for updates instead of launching that dropbox setup window.
  Otherwise it is great!
  KBD47

---

### Post by lucazade on 2012-01-08
@KBD47
strange issue about dropbox...
never experienced here, I'll give it a look to see if I made some mistakes somewhere :)
thanks for the feedback.

---

### Post by KBD47 on 2012-01-08
Maybe it has to do with my using it via live usb with persistence.
  I really like your choice of programs, saves me time: Chromium, Rhythmbox, Dropbox, Gparted,LibreOffice Writer. I think the only thing I needed to install was Thunderbird and Firefox as a back up browser :-)
  I'm guessing you are going to have this as an LTS release this Spring? Looking forward to seeing that. Thanks for your hard work on this.
KBD47

---

### Post by lucazade on 2012-01-08
> **KBD47 said:**
> Maybe it has to do with my using it via live usb with persistence.
  I really like your choice of programs, saves me time: Chromium, Rhythmbox, Dropbox, Gparted,LibreOffice Writer. I think the only thing I needed to install was Thunderbird and Firefox as a back up browser :-)
  I'm guessing you are going to have this as an LTS release this Spring? Looking forward to seeing that. Thanks for your hard work on this.
KBD47

Absolutely yes.. I'll continue to provide Freezy images also because I personally use it on my PCs and I'm no more able to use the 'plain' Ubuntu.. too much stuff to adapt to my tastes :)

---

### Post by KBD47 on 2012-01-08
The main Ubuntu lost me as well. My wife and I spent about 2 months trying to adapt to Unity and we just never liked it any better, too much hassle. I do like Xubuntu and Lubuntu, and of course Freezy.
  I did run into one other issue besides dropbox. Freezy is hanging up on shutdown. The first time I thought it was a fluke, but it does it every time. This is the line it hangs on:

modem-manager[2444]: <info> Caught signal 15, shutting down [OK]

but it's stuck and I have to do a force shutdown.
   It's 3:30 am here so I better get myself to bed, Linux has a bad habit of keeping me up late :-)
KBD47

---

### Post by lucazade on 2012-01-08
> **KBD47 said:**
> The main Ubuntu lost me as well. My wife and I spent about 2 months trying to adapt to Unity and we just never liked it any better, too much hassle. I do like Xubuntu and Lubuntu, and of course Freezy.
  I did run into one other issue besides dropbox. Freezy is hanging up on shutdown. The first time I thought it was a fluke, but it does it every time. This is the line it hangs on:

modem-manager[2444]: <info> Caught signal 15, shutting down [OK]

but it's stuck and I have to do a force shutdown.
   It's 3:30 am here so I better get myself to bed, Linux has a bad habit of keeping me up late :-)
KBD47

mmh.. interesting and weird at the same time.
There is an upstream bug in network manager I've reported during the Oneiric development cycle and also a workaround for it. The network service usually hangs for some seconds during shutting down but sincerly never required a force shutdown here.

I hope this will be fixed in Precise (there is some work in the bug report) .. you can try to revert my workaround to see if fix your problem:

remove or comment this line:
stop on runlevel [06]

in /etc/init/network-manager.conf

let me know if ok.

---

### Post by KBD47 on 2012-01-08
How exactly do I get to that? Do I use leafpad or some other editor? Should I put a # in front of that line?
Thanks!
KBD47

---

### Post by KBD47 on 2012-01-08
I just confirmed that the dropbox problem is related to using unetbootin live usb. I'm getting the same dropbox results from netrunner 4 using a live usb. So I just have the problem with shutting freezy down.
KBD47

---

### Post by gzaro on 2012-01-10
Great alternative for a simple gnome environment. Thank you.

I use awn instead of gnome-panel and it looks nice...

---

### Post by Hylas de Niall on 2012-01-10
> **KBD47 said:**
> I just confirmed that the dropbox problem is related to using unetbootin live usb. I'm getting the same dropbox results from netrunner 4 using a live usb. So I just have the problem with shutting freezy down.
KBD47

Have you tried making the usb with ubuntu's startup disk creator?

---

### Post by KBD47 on 2012-01-10
The last time I tried the Ubuntu startup disk creator it was not persistently saving my settings like it should. I think I used Ubuntu 11.10 disk creator to create a Lubuntu 11.10 usb. But the newest Unetbootin does a good job of saving persistent settings.
  I do suspect though that Unetbootin is creating my problems. I had recently some difficulty shutting down pclinuxos after I made a live usb with Unetbootin, so that could be the problem. I think the old startup disk creators worked better than the newer ones. I know that Mint 9 startup disk creator usually worked flawlessly. I might try to make a freezy usb using it.
KBD47

---

### Post by Hylas de Niall on 2012-01-10
I just downloaded and live tested the latest Freezy (from the Megaupload link, using Oneiric's Startup disk creator), though without persistence (it was with a 1gig Sony M2) and it ran like a dream.

I wonder how often the iso is updated, as there is no indication on the homepage (or here, unless my failing eyesight is missing it)? 

I understand that Canonical are looking for someone(s) to develop a Gnome alternative to the default Unity setup ...would Freezy fit this criteria? I was tempted to suggest it earlier, but thought they might mean a pure Gnome Shell release.

---

### Post by KBD47 on 2012-01-10
My Freezy problems were all caused by Unetbootin. I picked up a 16 gig usb stick today and did a full install and Freezy is running flawlessly.
  Next to Linux Mint, Freezy is the best out of the box OS in my opinion. It has basically everything I want on it. The only suggestion I would make, if you can do it legally, is follow Mint's lead and install all the codecs and restricted extras out of the box. 
  This distro needs much more advertising. If the Unity haters and Classic Gnome lovers realized this distro was around they would be flocking to it IMO.
KBD47

---

### Post by cbowman57 on 2012-01-10
I know what you mean KBD47, I tried leaving trails of bread crumbs to Freezy when it launched.  Was surprised it didn't get a bigger reaction.

---

### Post by KBD47 on 2012-01-10
> **Hylas de Niall said:**
> I just downloaded and live tested the latest Freezy (from the Megaupload link, using Oneiric's Startup disk creator), though without persistence (it was with a 1gig Sony M2) and it ran like a dream.

I wonder how often the iso is updated, as there is no indication on the homepage (or here, unless my failing eyesight is missing it)? 

I understand that Canonical are looking for someone(s) to develop a Gnome alternative to the default Unity setup ...would Freezy fit this criteria? I was tempted to suggest it earlier, but thought they might mean a pure Gnome Shell release.

Ubuntu could save themselves by providing a default alternative to Unity. Cinnamon is the best Gnome Shell alternative I've seen. Freezy is the best Gnome Panel? alternative I've seen. They really should use Freezy or something very like it as a new fallback and for older hardware and for those who just don't like Unity. Freezy runs great even on my 7 year old Compaq Desktop computer. And seems pretty much made to run on my newer netbook.
KBD47

---

### Post by KBD47 on 2012-01-10
> **cbowman57 said:**
> I know what you mean KBD47, I tried leaving trails of bread crumbs to Freezy when it launched.  Was surprised it didn't get a bigger reaction.

Maybe get it listed, announced at Distrowatch? A Wikipedia page for it? I'm thinking Freezy is one of the best kept secrets ever.

---

### Post by KBD47 on 2012-01-10
Just curious, is there a way to adjust the fonts on Freezy? Anti-aliasing, hinting?
Thanks!
KBD47

---

### Post by lucazade on 2012-01-11
@gzaro
thanks for the compliments.. i'm glad my work is appreciated :)

@Hylas de Niall
I made some deep changes lately to ppa and packages so I'll probably push some new iso (32/64bit) soon. 

This oneiric release is just a proof of concept to experiment some stuff and to make a rocksolid Precise release. If any dev will help me I'll think about a roadmap.

@KBD47
Good to know those issue were caused by unetbootin.. I'll think about codecs shipped by default and to make some more advertising.. It is really needed.

about font config you can use dconf-editor or gnome-tweak-tool.. unfortunately at the moment there is no out-of-the-box config tool for this.

---

### Post by KBD47 on 2012-01-11
Thanks!

---

### Post by lucazade on 2012-01-11
new build:
[http://www.multiupload.com/0LMEAAWMB3](http://www.multiupload.com/0LMEAAWMB3)

only i386 atm, i'll make the amd64 asap :)

---

### Post by Hylas de Niall on 2012-01-11
> **lucazade said:**
> new build:
[http://www.multiupload.com/0LMEAAWMB3](http://www.multiupload.com/0LMEAAWMB3)

only i386 atm, i'll make the amd64 asap :)

Cool! TY!
I'll have a slice of that!
:D

---

### Post by cbowman57 on 2012-01-11
@lucazade

What changes did you make to this build?

---

### Post by lucazade on 2012-01-11
changed the freezy ppa (now separated from my personal repo), renamed metapackages and customization files, refined selection of apps trying to lower iso size and switched the lightdm theme from unity-greeter to gtk-greeter (in order to not load indicator at all).
now quite i'm satisfied!

ah.. removed also some ubuntu branding during livecd :)

---

### Post by cbowman57 on 2012-01-11
> **lucazade said:**
> changed the freezy ppa (now separated from my personal repo), renamed metapackages and customization files, refined selection of apps trying to lower iso size and switched the lightdm theme from unity-greeter to gtk-greeter (in order to not load indicator at all).
now quite i'm satisfied!

ah.. removed also some ubuntu branding during livecd :)

Cool, thanks for the update. :)

---

### Post by Hylas de Niall on 2012-01-11
Tux is a nice touch too! :)
Very nice work indeed, how is the logo coming along?
:D

---

### Post by lucazade on 2012-01-11
> **Hylas de Niall said:**
> Tux is a nice touch too! :)
Very nice work indeed, how is the logo coming along?
:D

Dunno if dlambert is still working on the logo and other brand stuff.. at the moment I'll put our beloved tux as placeholder :)

---

### Post by lucazade on 2012-01-12
... and the amd64 build:
[http://www.multiupload.com/WHN31RFAU1](http://www.multiupload.com/WHN31RFAU1)

---

### Post by cmcanulty on 2012-01-12
I downloaded the 64bit edition and when I try it in virtual box it says wrong edition. My laptop is for sure running 64 bit Ubuntu 11.10

---

### Post by lucazade on 2012-01-13
> **cmcanulty said:**
> I downloaded the 64bit edition and when I try it in virtual box it says wrong edition. My laptop is for sure running 64 bit Ubuntu 11.10

Can you post a screenshot of the error, I'm not able to reproduce it here. thanks!

---

### Post by cmcanulty on 2012-01-13
Here are 3 screenshots

---

### Post by cbowman57 on 2012-01-13
> **cmcanulty said:**
> Here are 3 screenshots

I've seen people have such weirdness before, the fix was usually a bios upgrade.

Sure sounds like a problem with hardware detection.

---

### Post by taiyosun on 2012-01-24
Hello, to let you know,

Due to the recent problem with megaupload and other file hosts, your download links are nearly all dead.

I tried the 32bit version of Freezy and it's very pleasant to use in a live session.  Good luck.

---

### Post by Ludalex on 2012-01-25
Still no GMA500 support?

---

### Post by sffvba[e0rt on 2012-01-27
> **Ludalex said:**
> Still no GMA500 support?

Not to hi-jack or divert attention away from this awesome spin, but for GMA500 support you can check out - [http://blog.bodhizazen.net/linux/ubuntu-gma500-live-cd/](http://blog.bodhizazen.net/linux/ubuntu-gma500-live-cd/)


404

---

### Post by Dlambert on 2012-01-27
I...um have had some family issues. I will get back to work this weekend. Thanks for the patience.

---

### Post by L0rd C0rx on 2012-02-02
Hi!

I have to say I love this distro, it works phenomenally well on my little Asus Eeepc. However, I have installed it on a Dell Latitude D830 and it hangs on boot at this stage: 
**see attachments**
I am using the 64bit version (I haven't tried the 32bit version, I would really like the 64bit one to work) and its a stock install on a fresh format.

If anyone can shed some light on the issue I would very much appreciate it.

Thanks again for all your hard work!

LC

---

### Post by L0rd C0rx on 2012-02-02
I have also had a few ideas for logos....

following on from the work in previous posts and some suggestions I have made a few icons using similar ideas.... feedback would be appreciated!

This is Part I

---

### Post by L0rd C0rx on 2012-02-02
And Part II :-)

---

### Post by KBD47 on 2012-02-02
> **L0rd C0rx said:**
> I have also had a few ideas for logos....

following on from the work in previous posts and some suggestions I have made a few icons using similar ideas.... feedback would be appreciated!

This is Part I

I like the last one on the right. Just a thought, but I wonder what it would look like if you had the circles touching so that the logo looked more like a snowflake? I like the Freezylinux font, maybe if it was bigger and the snowflake-like symbol was smaller and somehow incorporated into the name? Just thinking out loud :-)
KBD47

---

### Post by lucazade on 2012-02-03
@L0rd C0rx

thanks for compliments and for logo ideas.. I would go for something like a snowflake and slightly different from ubuntu logo.
It is needed in different sizes, so a .svg would be perfect for this because it could be used in plymouth, lightdm, panel...

let me know :)

---

### Post by cbowman57 on 2012-02-03
What if it was just a snowflake & incorporated the ubuntu logo on the points, I can't create anything with gimp so I can't do a mockup.

Out of this last batch I really liked the colors of the 2 on the right in part II.

---

### Post by L0rd C0rx on 2012-02-03
I will do some more mockups when I can later today/weekend.
I also had a problem with booting up on a dell that I would like to get some help with :-) (see first post before logo ideas!) if someone was able to help me I'd really appreciate it. Love to get freezy working on my dell too!

LC

---

### Post by lucazade on 2012-02-03
> **L0rd C0rx said:**
> I will do some more mockups when I can later today/weekend.
I also had a problem with booting up on a dell that I would like to get some help with :-) (see first post before logo ideas!) if someone was able to help me I'd really appreciate it. Love to get freezy working on my dell too!

LC

great.. thanks for efforts.

about that issue you get on dell it seems related to video drivers.. strange this doesn't happen also with regular ubuntu because for these things freezy relies on stock stuff. 
try to start live cd with nomodeset.. when you see tux at start hit F6, select nomodeset and press enter to continue boot.

---

### Post by L0rd C0rx on 2012-02-05
I can boot live into Freezy, just when I installed it did it not want to boot. I know that laptop has restricted drivers for the gpu - just not sure how I will be able to do that from the cli... but if that's the issue, I have some ideas on how to fix it.

Thanks LC

---

### Post by L0rd C0rx on 2012-02-05
Ok, so I got in:

I resintall xorg using this :
> 
**Try to completely remove your nvidia drivers from your system:**[INDENT]   sudo apt-get purge nvidia*
[/INDENT]**Remove your xorg.conf**[INDENT]   sudo rm /etc/X11/xorg.conf
[/INDENT]**Reinstall xorg completely**[INDENT]   sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
[/INDENT]**Re-configure Xorg**[INDENT]   sudo dpkg-reconfigure xserver-xorg
[/INDENT]**Reboot**[INDENT]   sudo reboot
[/INDENT]You should be greeted with lightdm, this will default everything x the same way a fresh install would.
  After this you can try installing the drivers again using the  'Additional Drivers' tool in Ubuntu but if those drivers don't work you  can test the latest drivers from the [x-swat ppa]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
[INDENT]   sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
[/INDENT] **Note - if the above doesn't work - try also using the PAE kernel**[INDENT]   sudo apt-get install linux-headers-generic-pae 
[/INDENT]which I got from [COLOR=Blue]_[here]("http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled")._[/COLOR][URL="http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled"]
[/URL] 
In case anyone else had similar issues!

---

### Post by L0rd C0rx on 2012-02-09
ok, so I have done some work on some SVGs, I have one long one (text based) and that looks cool. I will upload them tonight perhaps - I have some more ideas I want to work on, I just need to learn how to use some new software that will give me the right outputs!! (i am unfortunately doing it on a PC as I am able to use PC software better than the linux equivalent!) so hopefully this weekend will be a productive one for me.

---

### Post by lucazade on 2012-02-09
> **L0rd C0rx said:**
> ok, so I have done some work on some SVGs, I have one long one (text based) and that looks cool. I will upload them tonight perhaps - I have some more ideas I want to work on, I just need to learn how to use some new software that will give me the right outputs!! (i am unfortunately doing it on a PC as I am able to use PC software better than the linux equivalent!) so hopefully this weekend will be a productive one for me.

thumbs up!
looking forward to your work :)

---

### Post by L0rd C0rx on 2012-02-09
This is an svg of the text with a nice little snowflake as the i's dot!

I want to make a more square icon type logo, but I am not sure what would look good?

any ideas are welcome!

---

### Post by KBD47 on 2012-02-09
> **L0rd C0rx said:**
> This is an svg of the text with a nice little snowflake as the i's dot!

I want to make a more square icon type logo, but I am not sure what would look good?

any ideas are welcome!

I like it. I wonder if you used the snowflake to dot the i and made the checkerboard squares larger so it was easier to read 'freezy linux' how that might look.
KBD47

---

### Post by L0rd C0rx on 2012-02-10
how do you mean? like more dots, or what? thats a font I used so - i could find a better font perhaps? its very easy to read I think....

---

### Post by L0rd C0rx on 2012-02-10
ok, so having looked at the svg on a pc without the fonts installed it didnt render properly, I will look into making it work on any machine... I have a few ideas

---

### Post by Dlambert on 2012-02-10
I like your work! Keep it up!

---

### Post by trelex on 2012-02-11
I would like to give FreezyLinux a spin but it seems that multiupload is down. Is there an alternative download available?

---

### Post by lucazade on 2012-02-11
> **trelex said:**
> I would like to give FreezyLinux a spin but it seems that multiupload is down. Is there an alternative download available?

this is an updated iso i'm working on... there is some ongoing work on the panel to have it also for the next precise release.
[http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso](http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso)

---

### Post by lucazade on 2012-02-11
> **L0rd C0rx said:**
> ok, so having looked at the svg on a pc without the fonts installed it didnt render properly, I will look into making it work on any machine... I have a few ideas

what font did you use?

---

### Post by trelex on 2012-02-11
> **lucazade said:**
> this is an updated iso i'm working on... there is some ongoing work on the panel to have it also for the next precise release.
[http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso](http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso)

Wow, that was quick thanks!

---

### Post by L0rd C0rx on 2012-02-13
> **lucazade said:**
> what font did you use?

its called 6x7oct

I know its not a standard font, as when I viewed the svg on my FreezyLinux laptop it was rendered with the system font, I will make the font into a vector shape and thus it won't rely on the fonts installed.

---

### Post by L0rd C0rx on 2012-02-13
Try this one - this should work regardless of the fonts installed

---

### Post by KBD47 on 2012-02-13
> **L0rd C0rx said:**
> Try this one - this should work regardless of the fonts installed

I like it. I think it needs better contrast so you can see the logo better, otherwise, very cool :-)

---

### Post by elgandoz on 2012-02-14
Another great contribution for the Linux community... thanks a lot!
Does it works with the infamous AO751h (yesss, gma500!!!)?

---

### Post by L0rd C0rx on 2012-02-14
> **KBD47 said:**
> I like it. I think it needs better contrast so you can see the logo better, otherwise, very cool :-)

I'll try something and post some different colours and maybe some different fonts.

Does anyone have any ideas for a more square-like logo? something that doesn't need text, just a logo...?

I'll happily take on board any ideas :D

LC

---

### Post by KBD47 on 2012-02-14
> **L0rd C0rx said:**
> I'll try something and post some different colours and maybe some different fonts.

Does anyone have any ideas for a more square-like logo? something that doesn't need text, just a logo...?

I'll happily take on board any ideas :D

LC

Just tossing out an idea:
How about simply the letters: FRZ* with the snowflake following. The nice blue color on a dark background, or a darker blue on a white snowflake shaped background?

---

### Post by L0rd C0rx on 2012-02-15
Ok, so I have done some more work, and changed a few things around :-)

I hope you like what I have come up with, and as always am open to all criticisms and feedback!

---

### Post by Dlambert on 2012-02-15
> **L0rd C0rx said:**
> Ok, so I have done some more work, and changed a few things around :-)
 
I hope you like what I have come up with, and as always am open to all criticisms and feedback!
 
Keep up the good work, sorry I havent been able to contribute! School sucks (high school) that is.

---

### Post by L0rd C0rx on 2012-02-15
thanks - i know how it is, being at University gives me a bit more free time!

---

### Post by KBD47 on 2012-02-15
I like the second one, but it seems a bit large, the third one is my favorite :-) Interested in what everyone else thinks.
KBD

---

### Post by L0rd C0rx on 2012-02-15
> **KBD47 said:**
> I like the second one, but it seems a bit large, the third one is my favorite :-) Interested in what everyone else thinks.
KBD

well the size doesnt matter, just the relationships inside the image, being a svg file it is a **s**calable **v**ector **g**raphic

---

### Post by cwklinuxguy on 2012-02-15
Oh, I keep meaning to try this one! I definitely will as soon as I have the free time...but who knows when that will be.

---

### Post by taiyosun on 2012-02-21
> **lucazade said:**
> this is an updated iso i'm working on... there is some ongoing work on the panel to have it also for the next precise release.
[http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso](http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso)

Thank you, the new iso works well, and it is very convenient to be able to add software during a live session.  I took VLC 2.0 for a spin last night in Freezy.

---

### Post by L0rd C0rx on 2012-02-22
Ok, so I have done some more work on logos,

had this idea last week but I needed to work on it quite a bit, its quite plain and that, I would like all feedback good and bad, and any ideas people have I am happy to work on them!!!

Please note the actual sizes are very rough, as in the inverse one the canvas size is way bigger than it needs to be, but this is easily changed, this is just to show my ideas!

---

### Post by KBD47 on 2012-02-23
I think the 3rd one looks best :-)

---

### Post by PhantomTurtle on 2012-02-29
I was trying to download Freezy Linux last night but multiupload (the download on the website) was down. I was wondering if there was different mirror I can download from. (btw I wanted the 32-bit version).

---

### Post by Dlambert on 2012-03-01
> **PhantomTurtle said:**
> I was trying to download Freezy Linux last night but multiupload (the download on the website) was down. I was wondering if there was different mirror I can download from. (btw I wanted the 32-bit version).
 Oh yeah, i forgot Megaupload* got shut down. -_-

---

### Post by PhantomTurtle on 2012-03-01
> **Dlambert said:**
> Oh yeah, i forgot MU got shut down. -_-

Are you talking about Megaupload or Multiupload because those are different. Megaupload was the one that got shut down. Anyway's does anybody have a different site to download it?

---

### Post by lucazade on 2012-03-01
here is it:
[http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso](http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso)

---

### Post by PhantomTurtle on 2012-03-03
> **lucazade said:**
> here is it:
[http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso](http://i.minus.com/1329046960/kzyF4KlFlIsBNng9IgHrkQ/dBGTT2V51AHed.iso)

Thanks:D

---

### Post by shizz on 2012-03-04
Hey really like the look of this derivative and I'm planning on giving it a go later on, but I was wondering if you could link me to the wallpaper that's in the screen shots? Love it.

---

### Post by lucazade on 2012-03-04
> **shizz said:**
> Hey really like the look of this derivative and I'm planning on giving it a go later on, but I was wondering if you could link me to the wallpaper that's in the screen shots? Love it.

it is one of the stock wallpapers of kde 4.x .. don't have any link right now

---

### Post by shizz on 2012-03-04
I presume it comes stock with Freezy?

---

### Post by lucazade on 2012-03-04
you presume well.. if you install freezy you can find the wallpaper pre installed in it.
unfortunately I don't have a spare link just to that wallpaper.

---

### Post by shizz on 2012-03-04
Haha, it's not a problem. I'll get it when I'm trying it out. Thanks again.

---

### Post by KBD47 on 2012-04-14
Just curious, are we going to see a Freezy LTS release this month?
KBD47

---

### Post by lucazade on 2012-04-15
> **KBD47 said:**
> Just curious, are we going to see a Freezy LTS release this month?
KBD47

Probably yes, I'll publish a LTS release this month.
I'm waiting for the Ubuntu Mini Remix ISO to build Freezy on top of this.

BTW.. I'm still looking for a good logo for this distro. Any proposal?

---

### Post by KBD47 on 2012-04-15
Thanks!

---

### Post by swizZ8 on 2012-04-26
Download links not working? :/

---

### Post by lucazade on 2012-04-26
In the next weeks I'll publish updated links for FreezyLinux 12.04 LTS.
I'll probably make 32bit PAE, 32bit NON-PAE and 64bit iso images.. 

By default Freezy will come with Gnome-Classic session and with Cinnamon (Gnome-shell fork shipped in Mint).

At the moment everything is ready but Ubuntu Mini Remix images for Precise are not available yet to build Freezy upon it.

---

### Post by swizZ8 on 2012-04-26
Link is working, file hoster is little bit confusing.

EDIT: Downloading 793mb version from minusdotcom.

---

### Post by reset042 on 2012-04-26
Freezy looks very interesting. As this uses Gnome, does it have Zeitgeist integrated? And if so, is it easily un-integrated?

---

### Post by KBD47 on 2012-04-26
Cool :-)

---

### Post by lucazade on 2012-05-07
Hi all!

I've uploaded FreezyLinux 12.04 images..
at the moment only the 64bit iso is available, the 32bit image and the non-pae are currently uploading (in the next hours will be available).

If you want to try it out this is the link for the 64bit image:
[http://www.multiupload.nl/PKVFUUZG1S](http://www.multiupload.nl/PKVFUUZG1S)

let me know how it works
:)

---

### Post by taiyosun on 2012-05-08
> **lucazade said:**
> Hi all!

I've uploaded FreezyLinux 12.04 images..
at the moment only the 64bit iso is available, the 32bit image and the non-pae are currently uploading (in the next hours will be available).

If you want to try it out this is the link for the 64bit image:
[http://www.multiupload.nl/PKVFUUZG1S](http://www.multiupload.nl/PKVFUUZG1S)

let me know how it works
:)

Hello, I believe multiupload is no longer in operation.  Clicking your 64bit link only loads a blank page.  I would like to try the 32bit non-PAE version whenever it's available.  Thank you.

---

### Post by lucazade on 2012-05-08
> **taiyosun said:**
> Hello, I believe multiupload is no longer in operation.  Clicking your 64bit link only loads a blank page.  I would like to try the 32bit non-PAE version whenever it's available.  Thank you.

multiupload is working normally.. just click the link and you'll find 3 different sources.

this is the 32bit image PAE:
[http://www.multiupload.nl/BYLNRDK7RJ](http://www.multiupload.nl/BYLNRDK7RJ)

the 32bit non PAE is coming soon :)

---

### Post by NickZe on 2012-05-08
Hey there, I'm Nick owner of Zeusoft. I'm going to upload the both versions of the distro to the Dropbox. Luca, when you feel ready to open the site to the public, feel free to tell me.

---

### Post by cmcanulty on 2012-05-08
still blank page

---

### Post by PhantomTurtle on 2012-05-08
> **cmcanulty said:**
> still blank page

Seems to be working fine, at least for me it is... (see attached screenshot).

---

### Post by taiyosun on 2012-05-08
> **PhantomTurtle said:**
> Seems to be working fine, at least for me it is... (see attached screenshot).

Maybe it's that USA users are being banned from multiupload, then.

---

### Post by nleibert on 2012-05-09
> **taiyosun said:**
> Maybe it's that USA users are being banned from multiupload, then.

I'm also having trouble downloading this from multiupload...showing a blank page.

---

### Post by lucazade on 2012-05-09
ok guys... i'll upload them to another host.
If possible i'll also seed a bittorrent for them.

These current images are btw just release candidate without the installer on board.. with some positive feedback i'll push the final one.

@NickZe
thanks for the support.. I'll contact you in the next days ;)

---

### Post by nleibert on 2012-05-09
> **lucazade said:**
> ok guys... i'll upload them to another host.
If possible i'll also seed a bittorrent for them.

These current images are btw just release candidate without the installer on board.. with some positive feedback i'll push the final one.

@NickZe
thanks for the support.. I'll contact you in the next days ;)

Thanks, can't wait to try it out! I have an old laptop that I'm trying to find the right distro for and the setup you have with Freezy Linux looks great.

---

### Post by Veazer on 2012-05-10
I can't get it to install. (Freezy 12.04 x64)

During the boot process, I see the little Ubuntu installer boot logo (similar to [THIS]("http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png")) and then it boots to the live desktop. If I instead press a key during that portion of the boot, i get a text menu asking if i want to "Try Freezy without installing", "Install Freezy", etc. However, even if I choose Install it still just boots to the live desktop, and unlike standard ubuntu there is no installer icon on the desktop.

---

### Post by lucazade on 2012-05-10
> **Veazer said:**
> I can't get it to install. (Freezy 12.04 x64)

During the boot process, I see the little Ubuntu installer boot logo (similar to [THIS]("http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png")) and then it boots to the live desktop. If I instead press a key during that portion of the boot, i get a text menu asking if i want to "Try Freezy without installing", "Install Freezy", etc. However, even if I choose Install it still just boots to the live desktop, and unlike standard ubuntu there is no installer icon on the desktop.

These current images are just release candidate without the installer on board..
I'll post the final iso soon.

---

### Post by NickZe on 2012-05-10
OK, should I wait with the upload or upload the RC?
PS: Forum is in the work: [http://freezy.zeusoft.net/forum/](http://freezy.zeusoft.net/forum/)

---

### Post by lucazade on 2012-05-10
> **NickZe said:**
> OK, should I wait with the upload or upload the RC?
PS: Forum is in the work: [http://freezy.zeusoft.net/forum/](http://freezy.zeusoft.net/forum/)

great Nick!
I hope to have some spare time during the weekend to make and upload new iso. I'd say to wait for these.

---

### Post by Veazer on 2012-05-10
> **lucazade said:**
> These current images are just release candidate without the installer on board..
I'll post the final iso soon.

Thanks for the info. Freezy is looking great but after a 10-20 minutes of use it freezes up on me, no pun intended. This running in VirtualBox and in live mode, so maybe things will change on the final. Let me know if there's anything I can do to test here.

---

### Post by sstep on 2012-05-10
Freezy looks great on my netbook (dell mini 10n with GMA500), it's much lighter than stock ubuntu 12.04. Thank you!
However, the touchpad doesn't work at all. To use a mouse I have to boot with a USB mouse already connected, otherwise it isn't detected.
My touchpad works fine in stock ubuntu.

---

### Post by lucazade on 2012-05-11
@Veazer
cannot reproduce your issue here... it works flawlessly in virtualbox and on physical machines. Could you provide any log like 'dmesg' ?

@sstep
strange issue.. don't have problem with touchpad on some different notebook I use.
What is the output of 'lsusb'?

---

### Post by lucazade on 2012-05-11
**Final images of Freezy 12.04:**

[http://min.us/mEoC69Hgc](http://min.us/mEoC69Hgc)    (i386)
[http://min.us/mzMQQ7Vle](http://min.us/mzMQQ7Vle)   (amd64)

@Nick can you post them in the site?

---

### Post by NickZe on 2012-05-11
Aye, Captain.
Edit: Done. You can find links on [http://freezy.zeusoft.net/download/](http://freezy.zeusoft.net/download/) or by visiting our [Forum]("http://freezy.zeusoft.net/forum/").

---

### Post by taiyosun on 2012-05-12
Thanks for the 32bit version of 12.04. (and the extra trouble to upload it).  My PS/2 mouse either wasn't detected or simply won't work - the mouse pointer is frozen in the center of the screen.

---

### Post by KBD47 on 2012-05-12
Too bad there is not a torrent download, said 6-8 hours to download both yesterday and today.

---

### Post by NickZe on 2012-05-13
We really need alternative download. We should just switch to mediafire.

---

### Post by sstep on 2012-05-13
> **lucazade said:**
> @sstep
strange issue.. don't have problem with touchpad on some different notebook I use.
What is the output of 'lsusb'?
Booting without connecting an external usb mouse> 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 003: ID 174f:1403 Syntek Integrated Webcam
Bus 001 Device 004: ID 0bda:0158 Relatek Semiconductor Crop USB 2.0 multicard reader

Then when I connect the external usb mouse thhis line gets added> 
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
but both the mouse and the touchpad don't work. I need to switch to the text terminal with ctrl alt f1 to run lsusb.

Booting with a connected usb mouse, which works while the touchpad doesn't> 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 003: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 004: ID 174f:1403 Syntek Integrated Webcam
Bus 001 Device 005: ID 0bda:0158 Relatek Semiconductor Crop USB 2.0 multicard reader
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel

> 
ubuntu@ubuntu: $ dmesg | grep -i pad
ubuntu@ubuntu: $ dmesg | grep -i mouse
[    10.439748] mousedev: PS/2 mouse device common for all mice


---

### Post by sstep on 2012-05-13
Touchpad and mouse are correctly detected in a full 12.04 release but not in freezy (refer to my previous post). It turns out that not only does freezy miss detecting the touchpad, but also webcam, video bus, HDA (HDMI, mic & headphones) - all of which the full 12.04 detects. If you're willing to take a look, I'm attaching demsg, Xorg.log and proc/bus/input/devices of full 12.04 and freezy 12.04 final for a Dell mini 10n netbook. Thanks.

---

### Post by lucazade on 2012-05-13
@sstep
i'm going to see your logs..
btw i've installed the i386 and amd64 images on circa ten different machines (both desktop and laptop) and I haven't had any single issue with hw and software..
no issues with mouse and touchpad, nothing.

wondering if you have a corrupted iso image..

---

### Post by KBD47 on 2012-05-13
People need to click on the "download all as zip" then extract the iso. It was hopeless trying to download the regular iso file.

---

### Post by lucazade on 2012-05-13
> **KBD47 said:**
> People need to click on the "download all as zip" then extract the iso. It was hopeless trying to download the regular iso file.

clicking on the large green icon you can download the iso file.. probably is a bit slow but it downloads ok here..

btw i'm uploading the iso on sourceforge.. then i'll make a couple of torrents.

---

### Post by KBD47 on 2012-05-13
Freezy isn't working for me either. I put it on a usb stick, it booted, but the cursor froze on the screen, touchpad unresponsive :( May not be Freezy's fault, 12.04 Ubuntu has been nothing but a pain for me. 11.04 and 11.10 worked great on my machines, but 12.04 has proven very buggy.

---

### Post by sstep on 2012-05-14
@tayosun & @KBD47 Does your mouse or touchpad work with the full ubuntu 12.04 vs. freezy? Look at my post #254 - I'm having issues too.

@Lucazade thanks for looking at my logs.

---

### Post by KBD47 on 2012-05-14
Yes, my touchpad worked on Ubuntu 12.04, and Kubuntu, and Xubuntu. But the screen freezing up is a bug I've hit across all the 12.04s. The earlier Ubuntus, and the earlier Freezy for that matter, worked well for me on my computers.

---

### Post by taiyosun on 2012-05-14
> **sstep said:**
> @tayosun & @KBD47 Does your mouse or touchpad work with the full ubuntu 12.04 vs. freezy? Look at my post #254 - I'm having issues too.

@Lucazade thanks for looking at my logs.

Just trying it now live - ubuntu 12.04 - and the mouse is working ok.  I've burned the freezy iso three times with both brasero and k3b with the same result.  

k3b generates a checksum of 49f06eccdcb8a8c883621cf680c22353  on the image I downloaded.

---

### Post by Veazer on 2012-05-14
> **lucazade said:**
> @Veazer
cannot reproduce your issue here... it works flawlessly in virtualbox and on physical machines. Could you provide any log like 'dmesg' ?

I'll try again with a full install and see if it was a problem unique to the live cd. IIRC correctly everytime it happened i was installing some packages in synaptic.

Looking forward to testing freezy on a few machines here. If only cardapio-gnomepanel was working on precise... it would be the ideal menu for freezy.

---

### Post by lucazade on 2012-05-14
@taiyosun
md5 is correct..
is it a logitech mouse? because there is an opened bug report for the usb receiver of logitech mices that is not recognized at boot time. It is necessary to unplug and plug again the mouse usb receiver. This is an upstream bug of ubuntu... so you should have on ubuntu as well..
I need just some more time to debug the issue of touchpad and mouse because i'm not able to reproduce here.

---

### Post by lucazade on 2012-05-14
New mirrors are available for download:
[https://sourceforge.net/projects/freezylinux/files/](https://sourceforge.net/projects/freezylinux/files/)

torrent coming soon...

---

### Post by taiyosun on 2012-05-14
> **lucazade said:**
> @taiyosun
md5 is correct..
is it a logitech mouse? because there is an opened bug report for the usb receiver of logitech mices that is not recognized at boot time. It is necessary to unplug and plug again the mouse usb receiver. This is an upstream bug of ubuntu... so you should have on ubuntu as well..
I need just some more time to debug the issue of touchpad and mouse because i'm not able to reproduce here.
No, my mouse is PS/2 with a round connector, not USB.  It is a new issue, because I didn't have this problem with earlier versions of freezy.  I can always use the previous version and continue testing new ones.

---

### Post by Veazer on 2012-05-15
I can't install Freezy 12.04 x64 on VirtualBox, the installer crashes:

[CENTER][IMG]https://dl.dropbox.com/s/u0n4myabbj6dr29/freezy1204%20installer%20crash.png[/IMG][/CENTER]

I've tried installing during the boot process and using the icon on the desktop. Let me know what i can do to help troubleshoot.

Also, please provide md5 sums on the first post and download pages. Currently we have no way of knowing if our iso files are corrupt.

Here are my results:
freezy-12.04-desktop-amd64.iso:
e9a170ec2eaa30c8015d53d8cd523a92

freezy-12.04-desktop-i386.iso
49f06eccdcb8a8c883621cf680c22353

EDIT: BTW the bug reporting tool did not popup after this error message.

---

### Post by Veazer on 2012-05-15
More VirtualBox testing of your distro:

32 bit isn't working well for me either. 32-bit *installs* on VirtualBox, but...

[LIST]
[*]There is no mouse cursor. I need to navigate with the keyboard. 
[*]After installation, there is no network access. It's hard for me to investigate the problem without a working cursor. There _is_ network access from the live mode.
[*]I can't mount the VirtualBox Guest additions. I get an error: Error mounting mount: unknown filesystem type 'iso9660'
[*]I can't install activate the VirtualBox drivers included with Ubuntu using jockey-gtk: "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"  There's errors about '/sys/module/vboxguest/drivers does not exist' 
[/LIST]

---

### Post by Hylas de Niall on 2012-05-21
Hmmm... curious:

3.2.0-23 generic kernel: everything is working fine
3.2.0-23 generic pae kernel: no network, no usb mouse, no touchpad, basic graphics.

3.2.0-23 generic pae kernel (in vanilla Ubu 12.04): everything is working fine.

This all on my netbook.^^^

On my desktop machine, using the latest image in live mode (non pae, i assume) no usb mouse control.

no idea why that is, but i'm happy enough using the non-pae kernel, and really glad you're continuing with this great little spin. :)

---

### Post by sstep on 2012-05-23
> **Hylas de Niall said:**
> Hmmm... curious:

3.2.0-23 generic kernel: everything is working fine
3.2.0-23 generic pae kernel: no network, no usb mouse, no touchpad, basic graphics.

3.2.0-23 generic pae kernel (in vanilla Ubu 12.04): everything is working fine.

This all on my netbook.^^^

On my desktop machine, using the latest image in live mode (non pae, i assume) no usb mouse control.my understanding is that the latest freezy img is pae.

**@lucazade** can you please provide a non-pae freezy so those who reported mouse/touchpad issues can test?  thanks

---

### Post by Hylas de Niall on 2012-05-23
> **sstep said:**
> my understanding is that the latest freezy img is pae.

**@lucazade** can you please provide a non-pae freezy so those who reported mouse/touchpad issues can test?  thanks

I grabbed the image a couple of days ago from the link in post #265 (above).
Updates seem to have brought in the pae kernel?

---

### Post by prince_of_darkness on 2012-06-20
Any updates on Freezy? I have i had the touch pad not working and have never been able to fix it

---

### Post by Hylas de Niall on 2012-08-27
Congratulations are in order, i believe. :)

[http://distrowatch.com/weekly.php?issue=20120827#waiting](http://distrowatch.com/weekly.php?issue=20120827#waiting)

:guitar:

(now how do we get it onto the leaderboard?)

---

### Post by KBD47 on 2012-08-27
Just curious, have the bugs been worked out? Some of us were having touchpad and other issues with Freezy. Are new iso's available for download somewhere? Will Freezy have a separate repo for updating the Freezy desktop?
Thanks

---

### Post by vasa1 on 2012-08-27
> **Hylas de Niall said:**
> ...
(now how do we get it onto the leaderboard?)

*Cough*

---

### Post by slixz85 on 2012-09-22
what's up on a new 12.04 or somethin? I haven't downloaded this but read alot of post and very apt to get it once 12.04 is out. didn't read all 28 pages though lol. Lubuntu was good so if it is in the realm like that. BOY! can't wait to try it. Bodhi is great and I always use small iso images as they download quicker of course and plus they actually tell ya if the system is light or not pretty much. if you got some beta's/rc's etc I am ready to test it. I need a zorin replacement!

---

### Post by NormanFLinux on 2012-09-23
I tried it on my netbook and my mouse cursor was frozen solid. It could be a kernel problem. Lucadze should update the kernel.

I remember constant freezing and lockups on Natty Narwhal and when I upgraded the kernel, everything worked flawlessly!

Just a thought.

---

### Post by Megaptera on 2013-02-07
What's the current state of Freezy? Still up and running or ... ? Thinking of giving it a try - any info appreciated :D

---

### Post by cbowman57 on 2013-02-07
I think it's dead.

---

### Post by slixz85 on 2013-02-07
if it did die. 28 pages for it wasn't bad

---

### Post by Megaptera on 2013-02-08
Thanks for your replies - I'll keep an eye on this thread in case reports of its death are exaggerated (mis-quoting Mark Twain!).

---

### Post by Megaptera on 2013-02-15
I think I agree ... this one is no more ... it is an ex-spin.

---

### Post by JiuJitsu500 on 2013-02-16
Wow... this is actually quite impressive!

I missed a few other pages, you did this yourse;f with remastersys or did you build everything differently?

Either way I guess doesn't matter - I tried doing my own distro a long time ago and realized how much there was to it and gave up. You, on the other hand, my man... created something pretty damn nice (though looks a lot like LXDE - but also not...)

I freaking like it. I have an old laptop I may put it on. ou plan on rolling out releases and updates as ubuntu does?

---

### Post by Hylas de Niall on 2013-08-13
> **Megaptera said:**
> I think I agree ... this one is no more ... it is an ex-spin.

Damn shame, that. I liked Freezy :(

---

### Post by NormanFLinux on 2013-08-13
Old threads never die! :P

---

