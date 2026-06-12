---
title: "Arch Linux Talk"
date: 2006-06-11
forum: Arch and derivatives
---

### Post by xXx 0wn3d xXx on 2006-06-11
Yesterday, I decided to install Archlinux. Ranked number 20 at distrowatch, Arch is optimized for i686 (Pentium 2+) processors and uses the pacman package manager. It is like Gentoo, because it compiles all packages from source. So here is how I thought Arch Linux was.

**Installation:**
Installing Arch Linux is very difficult. There is no graphical or even ncurses install at all. Everything is text based. I partitioned my HDD to make room, and then I proceded to install the base system. While X packages and such are on the cd you must install the base system first and then install x and gnome later. I found a great guide [ here that was very useful. ](http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html)

**Booting up:**
When you boot Arch, there is no splash screen, making you think: "Great I messed it up." There is no splash in Arch because it aims to be simple, cutting-edge, and fast. Boot was very fast too. My computer started in about 25-30 seconds (from just after grub to a fully usable desktop) because Arch compiles everything from source, optimizing it for your system. It was great having something so fast.

**Installing software:**
Installing something from source is as easy as running "pacman -S program." Arch uses the pacman package manager and it was great. It was fast, simple, and it gets the job done. In seconds the program I wanted was installed and ready to use. 

> Setting up the system
Arch is very nice but it is very difficult to setup. I couldn't get my wireless working with ndiswrapper, due to a problem in the Arch kernel. On top of that, Arch did not detect my USB devices such as my PSP and Ipod.

**Overall:**
Arch is great but it is still getting there. It's really great but a little complex and difficult to use. My rating of Archlinux is 8/10. Now, I am getting ready to try Gentoo.

---

### Post by kabus on 2006-06-11
> It is like Gentoo, because it compiles all packages from source. 

It isn't. It is a binary distro like Ubuntu.

---

### Post by Sheinar on 2006-06-11
Like kabus said, Arch is a binary distribution, though you can build your own packages from source using ABS.

---

### Post by pelle.k on 2006-06-11
Arch primary choice of installing new software is through pacman, and that is installing BINARY, not source. You can very easily install source packages through ABS (arch build system) though...
Arch recognized all my usb perhapsials though... Are you sure you have udev, and hal deamons added (and in the right order) in deamons array?

---

### Post by nalmeth on 2006-06-11
hmm, sounds kind of cool
I like the idea of installing programs with 'pacman'

Arch was/is one of those distros I really never gave a fair chance. I like the sound of fast and clean.

One day anyway

---

### Post by RAV TUX on 2006-06-11
[quote=xXx 0wn3d xXx]Yesterday, I decided to install Archlinux. Ranked number 20 at distrowatch, Arch is optimized for i686 (Pentium 2+) processors and uses the pacman package manager. It is like Gentoo, because it compiles all packages from source. So here is how I thought Arch Linux was.
 
**Installation:**
Installing Arch Linux is very difficult. There is no graphical or even ncurses install at all. Everything is text based. I partitioned my HDD to make room, and then I proceded to install the base system. While X packages and such are on the cd you must install the base system first and then install x and gnome later. I found a great guide [here that was very useful. ]("http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html")
 
**Booting up:**
When you boot Arch, there is no splash screen, making you think: "Great I messed it up." There is no splash in Arch because it aims to be simple, cutting-edge, and fast. Boot was very fast too. My computer started in about 25-30 seconds (from just after grub to a fully usable desktop) because Arch compiles everything from source, optimizing it for your system. It was great having something so fast.
 
**Installing software:**
Installing something from source is as easy as running "pacman -S program." Arch uses the pacman package manager and it was great. It was fast, simple, and it gets the job done. In seconds the program I wanted was installed and ready to use. 
 
 
Arch is very nice but it is very difficult to setup. I couldn't get my wireless working with ndiswrapper, due to a problem in the Arch kernel. On top of that, Arch did not detect my USB devices such as my PSP and Ipod.
 
**Overall:**
Arch is great but it is still getting there. It's really great but a little complex and difficult to use. My rating of Archlinux is 8/10. Now, I am getting ready to try Gentoo.[/quote]
 
 
My advice is to just use Gentoo,...I tried the live CD on my EM64T and it was smooth and flawless, detected all hardware, razer mouse, surround sound speakers, etc.
 
Gentoo is a beautiful distro.
 
Thanks for posting your problems with Arch, I have been wondering about it. I think I will skip on it and stick with Ubuntu and Gentoo.

---

### Post by xXx 0wn3d xXx on 2006-06-11
[QUOTE=yozef]My advice is to just use Gentoo,...I tried the live CD on my EM64T and it was smooth and flawless, detected all hardware, razer mouse, surround sound speakers, etc.
 
Gentoo is a beautiful distro.
 
Thanks for posting your problems with Arch, I have wondering about it. I think I will skip on it and stick with Ubuntu and Gentoo.[/QUOTE]
I'm getting ready to try the Gentoo live cd and possibly install it. How difficult is it to learn and use ?

---

### Post by RAV TUX on 2006-06-11
[quote=xXx 0wn3d xXx]I'm getting ready to try the Gentoo live cd and possibly install it. How difficult is it to learn and use ?[/quote]
 
Gentoo is not difficult at all to learn to use. No worries you'll be fine and the Gentoo Forums are very responsive and helpful(a lot like the Ubuntu forums here). Have fun.
 
I am sure you will be pleased.

---

### Post by xXx 0wn3d xXx on 2006-06-11
[QUOTE=yozef]Gentoo is not difficult at all to learn to use. No worries you'll be fine and the Gentoo Forums are very responsive and helpful(a lot like the Ubuntu forums here). Have fun.
 
I am sure you will be pleased.[/QUOTE]
Thanks for the reassurance. The live cd was very nice so I have decided to install it.

---

### Post by RAV TUX on 2006-06-11
[quote=xXx 0wn3d xXx]Thanks for the reassurance. The live cd was very nice so I have decided to install it.[/quote]
 
cool,...please follow up in this thread and let us know how things are progressing for you. I have only run the live CD but I will probably do the install soon.
 
I plan to dual-boot:
XPsp2/Gentoo on my EM64T
 
I run Ubuntu exclusively on my second older computer.

---

### Post by egon spengler on 2006-06-11
[QUOTE=xXx 0wn3d xXx]It is like Gentoo, because it compiles all packages from source.[/QUOTE]

Others have addressed this

[QUOTE=xXx 0wn3d xXx]
**Installation:**
Installing Arch Linux is very difficult. There is no graphical or even ncurses install at all. Everything is text based.[/QUOTE]

Ncurses IS text based, in fact the arch installation is ncurses based

[QUOTE=xXx 0wn3d xXx]
**Booting up:**
When you boot Arch, there is no splash screen, making you think: "Great I messed it up." There is no splash in Arch because it aims to be simple, cutting-edge, and fast. [/QUOTE]

What splash screen do you mean? A boot splash? There's no boot splash because Arch has the philosphy of giving you the minimum and you add what you want as opposed to, say, ubuntu which gives you a tonne of stuff and you need to strip out what you don't want. I guess you must be fairly new to Linux if this is the first time you've seen a system boot with no boot splash. Anyway, check the Arch wiki for gensplash/fbsplash and you can get a great boot splash easily

---

### Post by John.Michael.Kane on 2006-06-11
[QUOTE=egon spengler]Others have addressed this



Ncurses IS text based, in fact the arch installation is ncurses based



What splash screen do you mean? A boot splash? There's no boot splash because Arch has the philosphy of giving you the minimum and you add what you want as opposed to, say, ubuntu which gives you a tonne of stuff and you need to strip out what you don't want. I guess you must be fairly new to Linux if this is the first time you've seen a system boot with no boot splash. Anyway, check the Arch wiki for gensplash/fbsplash and you can get a great boot splash easily[/QUOTE]


Why must someone be new to linux just cause they say there's not splash screen. **FYI Ubuntu at one point did not boot with a splash screen**. so to make a statement that one must be new to linux based souly on not seeing a splash screen is uncalled for, and untrue.

---

### Post by egon spengler on 2006-06-11
[QUOTE=SD-Plissken]**FYI Ubuntu at one point did not boot with a splash screen**. so to make a statement that one must be new to linux based souly on not seeing a splash screen is uncalled for, and untrue.[/QUOTE]

That's exactly my point son, until Oct last year ubuntu didn't have a splash screen (officially at least) ergo would you not conclude from that tidbit of info that someone on an ubuntu forum surprised to not see a boot splash has most likely not been using Linux that long?

And as far as it being "uncalled for" it's not really an insult to say someone is new to Linux is it? I'm new to using Arch, I'm new to using Subversion at work and I'm new at trying to fathom what it is that you think is untrue. I don't consider any of that something to be ashamed of

---

### Post by xXx 0wn3d xXx on 2006-06-11
Ok, I'm installing Gentoo now. I can't believe how many options there were. I like how many options and questions it gives. The live cd comes with gnome, kde, xfce, and many other desktop enviroments and window managers. And to the person who stated that I must be new to Linux, that is not true. I have used Linux for 7 months.

---

### Post by RAV TUX on 2006-06-11
[quote=xXx 0wn3d xXx]Ok, I'm installing Gentoo now. I can't believe how many options there were. I like how many options and questions it gives. The live cd comes with gnome, kde, xfce, and many other desktop enviroments and window managers. And to the person who stated that I must be new to Linux, that is not true. I have used Linux for 7 months.[/quote]
 
It's good to hear the install is going good for you.
 
I'm going to do my install when I get home from work.
 
Gentoo is simply awesome!

---

### Post by John.Michael.Kane on 2006-06-11
[QUOTE=egon spengler]That's exactly my point son, until Oct last year ubuntu didn't have a splash screen (officially at least) ergo would you not conclude from that tidbit of info that someone on an ubuntu forum surprised to not see a boot splash has most likely not been using Linux that long?

And as far as it being "uncalled for" it's not really an insult to say someone is new to Linux is it? I'm new to using Arch, I'm new to using Subversion at work and I'm new at trying to fathom what it is that you think is untrue. I don't consider any of that something to be ashamed of[/QUOTE]


Frist off i'm not your son. second the OP could  have been using some other form or linux that did have a bootsplash which there are many. so to make the assumption is wrong. however it's your opinionas well as your assumption, and it's between you, and the OP. I spoke my peace on it.

---

### Post by egon spengler on 2006-06-11
Even I know that bootslashes are a somewhat recent addition to Linux, anyone who has been using Linux for some time would not be shocked to see no boot splash. That's not assumption or opinion, it's simple deductive reasoning.

From you bringing up Hoary lacking a splash as somehow countering my point that splashes are a more recent development I can see that perhaps reason is something that you might be new to. But hey, as I already said, there si nothing wrong with being new to something. In fact you might note that the OP didn't seem to get his feelings hurt by the comment

---

### Post by John.Michael.Kane on 2006-06-11
egon spengler feel what you want this topic is done. take up your thought with OP. as your feelings seems to be the only right one.

---

### Post by egon spengler on 2006-06-11
I don't have anything to "take up" with the thread starter. I made a comment which can I sincerely assure was not intended as pejorative and I honestly was very surprised to see you leap to his defence from my heinous non accusation. 

Now you seem to feel commited to informing me how little you care and don't intend to respond. I think we both know that there is close to zero chance of you not responding again so of course, feel free to remind me once more that you won't respond

---

### Post by matthew on 2006-06-11
Let's not take the thread off topic with silly bickering...back to discussing the OP's experience with Arch Linux and his related new experience with Gentoo and we can all stop defending one another and ourselves for now, okay? In simpler words...let go and move on.

---

### Post by RAV TUX on 2006-06-11
[quote=yozef]It's good to hear the install is going good for you.
 
I'm going to do my install when I get home from work.
 
Gentoo is simply awesome![/quote] 
HOLD EVERYTHING !

so I got home from work, hugged my beautiful wife, we made dinner togther and lets just say life is good;)

Now while my wife is in the shower I sat down to install Gentoo.

but I noticed some ISO icon on my XPsp2 desktop...there is one I hadn't burned to CD yet.

So since I sort of collect and test Linux Distros...I figured I should burn it.

Then after the burn I was labeling it and noticed that it is a live CD so I figured what the heck...I'll give it a spin...


well............this Distro is knock-your-socks-off-and-make-your-toes-curl Awesome!

[COLOR=Red]**dyne:bolic 2.0 (code named: "DHORUBA")**[/COLOR][SIZE=+1][B]
[http://www.dynebolic.org/index.php?show=available](http://www.dynebolic.org/index.php?show=available)

[/B][/SIZE]**dyne:bolic** is shaped on the needs of [media activists]("http://italy.indymedia.org/"), [artists]("http://dyne.org/perform.php") and creatives as a practical tool for **multimedia production**: you can manipulate and broadcast both **sound and video** with tools to **record**, **edit**, **encode** and **stream**, having automatically recognized most device and peripherals: audio, video, TV, network cards, firewire, usb and more; all using only free software!

I'm using it now as I write this message.

I may have to triple-boot: XPsp2/Gentoo/dyne : bolic

anyway I'm going to continue checking this out...

---

### Post by xXx 0wn3d xXx on 2006-06-11
I agree Gentoo is awesome. My Broadcom wifi card even worked in the Live cd and it is working now. I am still learning the basics though and upgrading everything. The gentoo wiki can really solve all of your problems. Compiling everything from source is a great idea and I really like it.

---

### Post by briancurtin on 2006-06-11
[QUOTE=xXx 0wn3d xXx]Yesterday, I decided to install Archlinux. Ranked number 20 at distrowatch, Arch is optimized for i686 (Pentium 2+) processors and uses the pacman package manager. It is like Gentoo, because it compiles all packages from source. So here is how I thought Arch Linux was.

**Installation:**
Installing Arch Linux is very difficult. There is no graphical or even ncurses install at all. Everything is text based. I partitioned my HDD to make room, and then I proceded to install the base system. While X packages and such are on the cd you must install the base system first and then install x and gnome later. I found a great guide [ here that was very useful. ](http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html)

**Booting up:**
When you boot Arch, there is no splash screen, making you think: "Great I messed it up." There is no splash in Arch because it aims to be simple, cutting-edge, and fast. Boot was very fast too. My computer started in about 25-30 seconds (from just after grub to a fully usable desktop) because Arch compiles everything from source, optimizing it for your system. It was great having something so fast.

**Installing software:**
Installing something from source is as easy as running "pacman -S program." Arch uses the pacman package manager and it was great. It was fast, simple, and it gets the job done. In seconds the program I wanted was installed and ready to use. 


Arch is very nice but it is very difficult to setup. I couldn't get my wireless working with ndiswrapper, due to a problem in the Arch kernel. On top of that, Arch did not detect my USB devices such as my PSP and Ipod.

**Overall:**
Arch is great but it is still getting there. It's really great but a little complex and difficult to use. My rating of Archlinux is 8/10. Now, I am getting ready to try Gentoo.[/QUOTE]
its not really complex or difficult, because that is how its made. when things are made to be simple and they arent simple, that would be difficult.

by the way, theres no graphical installer, nor will there ever be.

---

### Post by RAV TUX on 2006-06-11
[quote=xXx 0wn3d xXx]I agree Gentoo is awesome. My Broadcom wifi card even worked in the Live cd and it is working now. I am still learning the basics though and upgrading everything. The gentoo wiki can really solve all of your problems. Compiling everything from source is a great idea and I really like it.[/quote]

if you'r impressed with Gentoo, prepare to be blown away with 

dyne:bolic 2.0
[http://www.dynebolic.org/index.php?show=available](http://www.dynebolic.org/index.php?show=available)

---

### Post by K.Mandla on 2006-06-12
My flirtation with Arch linux seems to have come full circle. I loved the speed and simplicity of it, but for whatever reason I couldn't get certain nitpicking little things to work just right. 

For example, I have an ancient Linksys WPC11 wireless card that uses the Prism2 chipset -- it installs under Ubuntu just fine, but under Arch it just sat and blinked at me. After a day or two of wrangling, I decided I could get (more or less) the same effect by installing an Ubuntu server (which configured my wirless for me ... sigh) and building up an XFCE desktop around it.

I know there are some things Ubuntu handles for me, and I appreciate that. I'm still a n00b, so there are just some things that I need help with. One day I'll go back to Arch, and maybe find more to love about it. But for now, I'm an unashamed Ubuntunut.

:rolleyes:

---

### Post by RAV TUX on 2006-06-13
I'm downloading **StartCom MultiMedia Edition 5-ML-5.0.5 (Kessem)**, it seems like a pretty sweet distro.
[B]
[http://www.startcom.org/?lang=en&app=15]("http://www.startcom.org/?lang=en&app=15")[/B]

June 12, 2006: Probably one of the largest and most complete Linux distribution ever released to the public, the new StartCom MultiMedia Edition release ML-5.0.5 offers out of the box capabilities, unheard yet of an operating system.

Designed as a multi media workstation with music studio and advanced video editing applications, it certainly also provides the desktop user with the most applications for the day to day use. More than that, multiple choices are offered, being it the integrated desktops and its tools, the various office applications and sound-video tools.

Read the full [press release]("http://www.startcom.org/?app=14&rel=18") or download it from [here]("http://www.startcom.org/?app=15#ML-5.0.5")...

Bugs should be reported to [StartCom Bugzilla]("http://bugzilla.startcom.org/"), for question you might find answers at the [StartCom Forum]("http://forum.startcom.org/viewforum.php?f=4"). Screenshots are [here]("http://shots.osdir.com/slideshows/slideshow.php?release=623&slide=21&title=startcom+multimedia+edition+ml-5.0.5+screenshots").

Have Fun!

---

### Post by raublekick on 2006-06-13
i think i might give arch a try again sometime soon. my last experience left a good bit to be desired since i couldn't get my eth0 working correctly. but when it didn't work in dapper, i got a new one. i think arch had a newer kernel, which was what caused the problem in dapper. 

anyways, arch seems really cool, and i want to give it an honest shot now that i'm just using openbox anyways.

---

### Post by maagimies on 2006-06-14
Arch Linux is a great distro, I'm currently running it alongside with Kubuntu, and I like what I see.
I don't agree with the OP though with the hardness of installing though, if you have read the docs on the website, and **know what you're doing,** you shouldn't have too hard time.

---

### Post by raublekick on 2006-06-14
[QUOTE=maagimies]Arch Linux is a great distro, I'm currently running it alongside with Kubuntu, and I like what I see.
I don't agree with the OP though with the hardness of installing though, if you have read the docs on the website, and **know what you're doing,** you shouldn't have too hard time.[/QUOTE]


Before I installed it I read so many guides and stuff, thinking it was gonna be super cryptic and that I would basically be guessing my way through. Turns out, with a guide it really isn't hard at all.

---

### Post by Kindred on 2006-06-14
Arch is great.. and yeah it's not that hard to install/use really.  I'd been using Ubuntu for about a month before I switched to Arch and didn't have any problems.

---

### Post by zba78 on 2006-06-14
I used ARCH as my primary distro for a long time. It's a lovely distro that gives you the feeling of total control over your system.

It's not, however, targeted at new-comers to linux.

---

### Post by benplaut on 2006-06-18
>>>>>>>><<<<<<<

Intro
A few weeks ago, dapper was released.  Being on the beta cycle since flight 2, it was a bit of a suprise to not be getting 200 updates per day.  In fact, some of dapper's software is already a sub-version or two out of date.  Summer break was finally here, and I wanted something more.  Something more fun.

Background
Arch Linux was created by Judd Vinet as a personal distro specifically for the author's needs.  Taking many ideas from Crux, it aimed to be fast, efficient, and for goodness sake -- KISS!!  Simple does not always mean GUI everything.  This simple refers to well annotated and logical config files, a simple BSD-style init, and a nice simple package management system.  There are two ways to look at Arch from the perspective of a seasoned distro-junkie; it's either a bleeding-edge slackware with a great package manager, or gentoo... from binary.

Install
Arch's installer is simple and efficient.  Coming from a bcakground involving gentoo, I took the time to print out the 30 page install manual -- not as impressive as gentoo's 90 page opus, but at least I didn't have to buy a $30 printer catridge afterwards.  When the boot the install CD, it goes into a minimal Busybox system.  To start the install, merely execute the ncurses script.  The installer itself is very powerful, quite similar to Debian's.  First, you partition your drive using cfdisk/fdisk and create your fstab through an Ncurses menu; i had already partitioned using the gparted livecd, but the fstab setup worked perfectly. Next, you select your install source, either network or CD.  The next step, of course, is selecting and installing your packages.  It was hard to tell if they were on network or CD, but it seemed that the CD included a very minimal X, and alot of command line userspace tools.  Yes, VIM is included by default :) ...emacs is not.  The next step, somewhat optional, is to configure the system's rc.conf, recheck your fstab, and several other configuration files.  You usually don't need to change anything, but it's worth checking.  The configs are very well annotated, and documented even better in the manual.  The final step was to install a bootloader.  I was planning to add it to my dedicated /boot partition (great for distro hopping, btw), but noticed in he manual that it let you edit your menu.lst, if you use grub, before installing.  I decided to go that far in, then copied down the entry, to be sure that it would work when adding to my own menu.lst.  With all my tasks done, I rebooted to begin post-install.  As a quick note to anyone, it's very useful to either write down everything you do during an install in a notebook, or log it in a spare computer.

Post Install
When I rebooted, I went into ubuntu since I had not installed a bootloader.  Copying the installer-configured entry went perfectly (Side note: I went ahead and added vga=792 to the boot line, since the default res is very hard to do anything serious with), and I then rebooted into my new arch.  As the install guide suggested, I logged into the root account, with no password, and made a new user account after setting the su password.  I was hooked up to an ethernet line, so I decided to learn a it about the package manager  (more on that later) while getting my WiFi up.  Another important tip to distro-hoppers: The first thing you should install on minimalist distros is a command line IRC client, such as irssi, weechat, and bitchx.  Information is invaluable, and being able to share your issues with others via IRC is a wonderful thing.  The second thing you should install, and learn to use very well, is screen.  Think of screen as a window manager for the CLI.  It lets you have many programs open in the same terminal, via tabs or a split screen, and lets you scroll of in a command line.  It is an invaluable tool for any CLI work.  Configuring WiFi was my next task.  Drivers for my card, an Atheros using MadWiFi drivers, was available in the unstable repository, and worked pretty well after ading ath0 to rc.conf; actually, they didn't work at first, but it was user error.  Once i did it the correct way, everything was fine.  Installing X was a relatively simple task, as I copied over my xorg.conf from Dapper.

Package Management
Arch's package manager is a blessing apon distro-kind.  It is simple, efficient, fast, and handles source packages with ease, and the distro has a wonderful thing called AUR.  The arch user repository consists of hundreds (if not thousands) of user contributed PKGBUILDS; simple config files that give the Arch Build System's makepkg instructions for pulling down the source, ./configuring, and making a pkg.tar.gz out of it.  Given that AUR pkgbuilds are not tested much, they don't all work.  I've had prety good luck with most packages, so far.  Scripts and python programs have been made to automatically pull down PKGBUILDs from the AUR, but it's generally easy enough to do it by hand.  Pacman handles the packages themselves.  It's a wonderful tool -- pacman -Ss to search for a package, pacman -S to install it, pacman -A to install a local package, pacman -Sy to pull down the latest repository cache, and pacman -Suy to update the cache, then do a complete update to the latest.

Userspace/Post post install
Installing my usual work environment was a very simple task, all the software I use was either in the repositories, or in AUR.  I reused most of my configuration from ubuntu, as well.  Part of my reason to use Arch was to slim down, so I decided to get rid of many of the gnome programs I had been using.  Gedit was replaced by the wonderful medit, which can do everything as Gedit, plus much more.  As an extra, it's faster and more configurable.  My usual terminal in ubuntu was yakuake, but having all those additional kde and qt libs for a mere terminal seemed a bit extreme, so I made a little shell script to have a pop-down terminal, using screen and urxvt.  Nautilus was replaced by Thunar, which I really prefer to the former.  One extra dependency over my other apps, and it's less than a meg.  Wonderful.

Community
As a whole, the Arch community is more knowledgable than ubuntu's.  Yes, there are plenty of gurus in ubuntuforums and #ubuntu, but Arch is really a more advanced distro, and thus more of the users are knowledgable.  In general, the people seem to be friendly, albeit with a lower tolerance for stupidity than ubuntu.  That's a good thing!  The one question I asked on the forum did not get answered, but I put in it that there was another possibility I wanted to try -- 12 hours later, I did and it worked.  There's another very nice thing about the arch community -- ALOT of people, probably more than half, are using lightweight WMs; finally!

Final Thoughts
I suppose an ubuntu server install or debian sid would give me a similar result, but I really like Arch.  The community is great, the package manager is excellent, and it's really fast.  I'm staying with Arch for now.  It took a bit longer to configure than other distros, but now that that's done, it's very little work to keep it up.  Arch is on a rolling release cycle, meaning that you can just continue to pacman -Suy and always have the latest, kinda like gentoo.  I'm not leaving the ubuntu community, but I'm not using the distro for a while, at least until Edgy is far into dev.

Recommendation
This is a logical next step for those who have tweaked their debian-base beyond all recognition, especially those who use lightweight environments.  Hell, it's worth switching just for AUR.

Have fun!

<Edit>
holy sh*it that's alot of text

---

### Post by loell on 2006-06-18
its more like a comparison than a review ;)

---

### Post by benplaut on 2006-06-18
comparing, but to about 5 other distros :D

---

### Post by Adrian_b on 2006-07-26
Heh, wanting to do an Arch install but it's already a bit hard for me :)
Need to set the keyboard layout to latin-be1 and need to get my WiFi working without a connection already..

However, i have plenty of time and i like screwing around since i have a safe Ubuntu install :)

I have a REALLY weird experience atm.
I set up my gateway and DNS in /etc/resolv.conf and i rebooted in Ubuntu to chroot into my Arch installation and go from there.
However, my WiFi Atheros card already works so it seems, WITHOUT me supplying the WEP and ESSID. :s

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***Arch Linux Tech Talk***

Threads merged:

[http://www.ubuntuforums.org/showthread.php?t=198982](http://www.ubuntuforums.org/showthread.php?t=198982)
[http://www.ubuntuforums.org/showthread.php?t=231311](http://www.ubuntuforums.org/showthread.php?t=231311)
[http://www.ubuntuforums.org/showthread.php?t=194470](http://www.ubuntuforums.org/showthread.php?t=194470)

---

### Post by Rumor on 2006-09-13
I'm just curious to know if any of the other Arch users here have tried the packages for Gnome 2.16 yet. 

The release is discussed in this thread: [http://bbs.archlinux.org/viewtopic.php?t=24958](http://bbs.archlinux.org/viewtopic.php?t=24958)

I've added this to my pacman.conf file, but have not yet taken the plunge.

```

#32 Bit
[karsten] 
Server = http://arch.os-zen.net/pkg/karsten/i686

```

Wondering if anyone else has jumped in yet and what success you've had.

---

### Post by Virogenesis on 2006-09-17
I tried, had to upgrade dbus and basically it didn't agree I wouldn't install  gnome 2.16 if i were you and damn you for the link. 
You borked my machine :)

---

### Post by Kindred on 2006-09-18
I tried a few days ago but it was not too stable and so I quickly reverted back to Openbox.  Probably best to wait till it is done by the devs anyway..

---

### Post by mahy on 2006-10-18
Hi there,

anybody uses Arch Linux? I think i might give it a try, but i'd like to read some testimonials first. Please share your experience a bit, tell me what it's like. TIA

---

### Post by 5-HT on 2006-10-18
[http://ubuntuforums.org/showthread.php?t=118971](http://ubuntuforums.org/showthread.php?t=118971)
[http://ubuntuforums.org/showthread.php?t=231311](http://ubuntuforums.org/showthread.php?t=231311)

---

### Post by Kindred on 2006-10-18
Arch is my distro of choice.. I switched to Arch after a month of Ubuntu (and  Linux), so it's really not all that hard in general - though you'll want to be a little comfortable with the command line.  The installer is okay and simple enough, most people start with a base system, update with pacman and then go from there. 

Arch is perhaps the fastest distro i've used so far, simple & stripped down in nature  you'll need to edit rc.conf to add your services and such yourself.  This file is also used to configure a few things that are typically spread out over several configuration files in other distributions, just another attempt at keeping things simple.   

Pacman is a great package manager & the repos are kept well up to date for the most part, they are of course smaller than debian but have most everything i've wanted and there is also the AUR which makes it easy to build and install packages that aren't in the repositories.  

Anyway I could go on but suggest just trying it out, I dual booted with Ubuntu for a few days till I was on top of everything.

---

### Post by Rumor on 2006-10-18
I dual boot Ubuntu and Arch. As it has been noted in most every post about it, Arch is very fast. I like the Pacman package manager better than Apt, and the idea of a rolling release beats (IMO) performing distribution upgrades. The forums are no where near as active as these, but you'll find them very helpful. Its development is slower than Ubuntu's, but it is a still rock solid OS for me.

---

### Post by mahy on 2006-10-18
THX. Uhm, i was kinda scared off by the requirement to manually edit important system files during installation... I dunno if it's worth trying, coz i'm using Zenwalk right now. I have it downloaded and burnt, so i might try it some day.

---

### Post by K.Mandla on 2006-10-18
> **mahy said:**
> Uhm, i was kinda scared off by the requirement to manually edit important system files during installation. ...
Don't be spooked by that; I think I had to only edit two configuration files -- the host file and the rc.conf (? ... it's been a while) file. It's really not that tricky. 

Give it a try, and if it doesn't work, put the CD on a shelf somewhere and let it roll around in your subconscious for a month or so. Then try again. You might dig it. ;)

---

### Post by xXx 0wn3d xXx on 2006-10-18
I used Arch for about 2 months and it was great. The only problem was that my networking broke and after that I have tried numerous installs but I can't get network-manager to work. I am currently only using Debian Etch right now so I am thinking of installing Archlinux again...

---

### Post by ruhar on 2006-10-19
If you do an install, just remember to additionally edit your grub configuration (when you install the bootloader) and change our initrd line to:
```
image=/boot/vmlinuz26
label=ArchLinux
append="root=/dev/hdXY"
**initrd=/boot/kernel26.img**
read-only
```

If you don't reference kernel26.img, you won't be able to boot.  This is the result of Arch switching over to mkinitcpio with the 2.6.18 kernel upgrade recently.

---

### Post by xXx 0wn3d xXx on 2006-10-19
> **ruhar said:**
> If you do an install, just remember to additionally edit your grub configuration (when you install the bootloader) and change our initrd line to:
```
image=/boot/vmlinuz26
label=ArchLinux
append="root=/dev/hdXY"
**initrd=/boot/kernel26.img**
read-only
```

If you don't reference kernel26.img, you won't be able to boot.  This is the result of Arch switching over to mkinitcpio with the 2.6.18 kernel upgrade recently.

Yes, I have realized this. Thanks to this thread I am back on Arch and loving it ! Debian + Arch is awesome. Network-manager is working great too.

---

### Post by K.Mandla on 2006-10-20
> **ruhar said:**
> If you don't reference kernel26.img, you won't be able to boot.  This is the result of Arch switching over to mkinitcpio with the 2.6.18 kernel upgrade recently.
Hmm. That might explain a few things. ... :-k

---

### Post by RAV TUX on 2006-10-21
[B]"Where's a thread about Arch?" Thread:

merged here.
[/B]

---

### Post by bodhi.zazen on 2006-10-23
Just found this thread.

Arch Linux has been my primary OS for 6 months now.

The most difficult part was installation. Actually it is not so difficult, it just takes time.

Print and read this:[[color=navy]Arch Linux Install Guide[/color]](http://www.archlinux.org/static/docs/arch-install-guide.html)

The best thing to do IMO is to just install the base system from CD, then add to it via pacman.

Advantages of Arch:[list=number][*]Speed.[*]Takes less time then Gentoo.[*]pacman is awesome.[*]Once you install Arch, sys admin is a snap. This is what takes so much time at installation, reading and understanding the text files for sys admin.[*]You will learn the CLI very quickly.[/list]

If you install Arch, try running a light weight WM like Fluxbox, Openbox, or IceWM.

If I can be of assistance to you re: Arch Linux, feel free to PM.

---

### Post by bionnaki on 2006-10-23
I love arch, but I cannot get my wireless card working. I have a wmp54g using rt2500 driver + wpa. any ideas?

---

### Post by bodhi.zazen on 2006-10-23
> **bionnaki said:**
> I love arch, but I cannot get my wireless card working. I have a wmp54g using rt2500 driver + wpa. any ideas?

Have you tried this [Arch Linux Wireless Setup](http://wiki.archlinux.org/index.php/Wireless_Setup) ?

Does the wireless card work on Ubuntu?

---

### Post by bionnaki on 2006-10-23
yup, ive gone over the wiki & posted on the forums.

my card works great in ubuntu by modifying /etc/network/interfaces and then adding my dns info to /etc/resolv.conf

here's a copy of my interfaces:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map ra0

auto ra0

iface ra0 inet static
        address 192.168.1.33
        netmask 255.255.255.0
        gateway 192.168.1.1
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "abc"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="1234"
        pre-up ifconfig ra0 up


hmmm. in arch, I can install the rt2500 driver just fine - just not connect. I can see the networks, so the card/driver does work. I guess I dont understand where to input the above info...tried everything.

---

### Post by bodhi.zazen on 2006-10-26
Sorry, I do know how to fix this.

I would referr you to IRC:

irc.freenode.net
#archlinux

Very helpful folks.

---

### Post by kalle314 on 2006-10-27
I am planning on setting up Arch-Ubuntu dual boot. 
What would be the best way to handle partitioning and boot loader?
Is it easy to partition the HD in the Arch installer, with cfdisc, or would it be better to use another partitioning tool? What partitions would I need? 
The installation Guide talks about boot partition, but it seems that is not necessary. Is it easy to let Arch use the same swap partition as ubuntu?

The Arch Installation Guide is very helpful, but it would be even better if it said exactly what questions you will get and what the options will be during installation. For example, this paragraph sounds a bit scary:
>  If you plan on setting up a multiboot system, it might be a better option to install the bootloader in your root or /boot partition, and refer to that boot sector from whatever other boot loader you want to reside in the master boot record.
Does anyone know exactly what options to chose here?
I thought the installer might say something like "Type in the path to the location where you want to install GRUB:", and that I would have to cancel my installation since I would not know what to write then.

---

### Post by bodhi.zazen on 2006-10-27
> **kalle314 said:**
> Does anyone know exactly what options to chose here?
I thought the installer might say something like "Type in the path to the location where you want to install GRUB:", and that I would have to cancel my installation since I would not know what to write then.


You have several options.

[list=number][*]Make a boot partition. This should be ext2 and 500 mb should be more then enough. Mount it in Arch as /boot. Add (copy-paste) the Ubuntu entry from Ubuntu_root/boot/menu.lst to boot_partition/grub/menu.1st.[*]Use your Ubuntu partition as is. Install Arch, install grub into the Arch Partition. Edit Ubutntu_root/boot/grub/menu.lst to inlcude an entry for Arch as below.[*]You can do the same using Arch as primary. In this event install grub into the Arch partition and the MBR. Add an entry for Ubutu in Arch_root/boot/grub/menu.lst[/list]

I prefer method 1 as it is easier to maintain.

Arch Linux:> # (0) Arch Linux
title Arch Linux
root (hd0,z)
kernel /boot/vmlinuz26 root=/dev/hdxy ro
initrd /boot/kernel26.img

where hd0,z is your arch partition in grub speak and /dev/hdxy is your arch partition in Linux speak. You can find this information in Arch_root/boot/grub/menu.1st.

cfdisk it a fine partitioning tool. Your alternate would be to boot to Ubuntu and use GParted.

You can share /swap between Arch and Ubuntu.

Let me know if I can be of further assistance.

---

### Post by bodhi.zazen on 2006-10-27
Arch Lnux Install Guides:

Start here. [Quick guide](http://bbs.archlinux.org/viewtopic.php?t=25508)
This guide uses KDE but you can easily change to fluxbox or what have you.

Difinitive Guide: [Arch Linux Install Primer](http://www.archlinux.org/static/docs/arch-install-guide.html)

---

### Post by kalle314 on 2006-10-27
Thanks, I think I'll give it a try during the weekend.
I think I will create a ext3 partition for arch using qparted on systemRescueCD before I start the installation.

---

### Post by Rumor on 2006-10-27
> **kalle314 said:**
> I am planning on setting up Arch-Ubuntu dual boot. 
What would be the best way to handle partitioning and boot loader?


You can always choose not to install the bootloader at all. After you install the kernel, read the information screen that is presented to you. As you scroll down, you will see an entry that you can use in your existing Ubuntu /boot/grub/menu.lst

I usually copy that information down and manually edit my Grub list.

If hard drive space is not an issue for you, then creating a small /boot partition and installing grub there rather than in your mbr is probably the way to go.

Good luck on your installation!

---

### Post by bodhi.zazen on 2006-10-27
> **Rumor said:**
> You can always choose not to install the bootloader at all. After you install the kernel, read the information screen that is presented to you. As you scroll down, you will see an entry that you can use in your existing Ubuntu /boot/grub/menu.lst

I usually copy that information down and manually edit my Grub list.

I am not sure about Arch, but with some (if not most) Linux installs if you do not install grub to the root partition you may not get a /boot directory and will not be able to boot. I usually choose to install GRUB to the root partition.

This is different then installing to the MRB.

---

### Post by pelle.k on 2006-10-27
hey! gnome 2.16 moved from testing :) yay!

---

### Post by kalle314 on 2006-10-28
Doing the basic install and getting Arch to dual boot with ubuntu was very easy and even faster than installing ubuntu!

Now I only need to get it to connect to internet, start X and gnome, and 100 other small things!

---

### Post by bodhi.zazen on 2006-10-28
> **kalle314 said:**
> Doing the basic install and getting Arch to dual boot with ubuntu was very easy and even faster than installing ubuntu!

Now I only need to get it to connect to internet, start X and gnome, and 100 other small things!

Welcome to arch. It will not take long. pacman is very fast.

Enable your reositories and start with pacman -Syu.

The "100 things" will not take long.

/etc/rc.conf is the MAIN CONFIGURATION file. This is where you enable your internet card and daemons.

I'm sure you will be up and running very fast. Also try the [arch wiki](http://wiki.archlinux.org/index.php/Main_Page)

See the section on the Left "getting started".

---

### Post by pelle.k on 2006-10-28
Theres a little 'snag' currently. I've been left without a working grub after updating the system from a 0.7.2 install. You'll probably experience the same thing with a fresh install (we're all waiting for the 0.8 release :) )
Just boot the arch install cd, and follow the instructions to boot into your system, and from there, run 'grub-install /dev/hdX' or sdX if it's installed on a sata drive...
[edit]also remember to switch to mkinitpcio right after upgrading to kernel 2.6.18. How? Just edit /boot/grub/menu.lst and change initrd26.img to kernel26.img[/edit]

---

### Post by bodhi.zazen on 2006-10-30
> **pelle.k said:**
> Theres a little 'snag' currently. I've been left without a working grub after updating the system from a 0.7.2 install. You'll probably experience the same thing with a fresh install (we're all waiting for the 0.8 release :) )
Just boot the arch install cd, and follow the instructions to boot into your system, and from there, run 'grub-install /dev/hdX' or sdX if it's installed on a sata drive...
[edit]also remember to switch to mkinitpcio right after upgrading to kernel 2.6.18. How? Just edit /boot/grub/menu.lst and change initrd26.img to kernel26.img[/edit]

LOL :lol:

Arch kernel 2.6.18 got rid of initrd in favor of initcpio. All you need to to do is change initrd26.img to kernel26.img in menu.lst:

Edit /boot/grub/menu.lst:

Change:> title Arch Linux
root (hd0,x)
kernel /boot/vmlinuz26 root=/dev/hdxy ro
initrd /boot/**initrd26.img**


To:> title Arch Linux
root (hd0,x)
kernel /boot/vmlinuz26 root=/dev/hdxy ro
initrd /boot/**kernel26.img**

Arch should now be bootable form HD.

---

### Post by stoffepojken on 2006-11-01
I love ArchLinux. But it lacks in UTF-8 compabalty. Nano is a mess with swedish characters.

---

### Post by pelle.k on 2006-11-02
@bodhi.zazen;
> Arch kernel 2.6.18 got rid of initrd in favor of initcpio. All you need to to do is change initrd26.img to kernel26.img in menu.lst
Yes, and i wrote that in my previous post. This isn't the issue, even though it may look like it.
I've had my boot sector "invalid or not found". I use gag on mbr, and gag boots my root partition, where grub _was_ before i updated. This has happened to me on all occasions i've updated from 0.7.2 cd to "now". It might not happen to all of you running grub from MBR though...

@stoffepojken;
As you may have seen, i'm also swedish by nationality. I have had _no_ errors at all with uft8 compability nor swedish charachters in nano...
This is what i use in my /etc/rc.conf```
LOCALE="en_US.utf8"
HARDWARECLOCK="localtime"
TIMEZONE="Europe/Stockholm"
KEYMAP="sv-latin1"
```

This is the line i uncommented in /etc/locale.gen```
en_US.UTF-8	UTF-8
``` (you're supposed to run locale-gen after uncommenting a line from this file...)

---

### Post by K.Mandla on 2006-11-08
> **ruhar said:**
> If you do an install, just remember to additionally edit your grub configuration (when you install the bootloader) and change our initrd line to:
```
image=/boot/vmlinuz26
label=ArchLinux
append="root=/dev/hdXY"
**initrd=/boot/kernel26.img**
read-only
```

If you don't reference kernel26.img, you won't be able to boot.  This is the result of Arch switching over to mkinitcpio with the 2.6.18 kernel upgrade recently.
Thanks again for this. I retried an Arch install from 0.7.2 base and sure enough, it crapped out after an update. Changing the line of code worked perfectly. Cheers! :D

---

### Post by manmower on 2007-01-13
Just thought I'd share this [short write-up by Cactus](http://e.cactuswax.net/blog/articles/2007/01/archlinux-mini-review.html) that covers some of the interesting aspects of Arch Linux. It's a little different from your typical review as it was written by a long time Arch Linux user, but I think it does a good job describing the essential features that set Arch apart from other distros, and as such it might have some useful information for all you distro hoppers out there. ;)

---

### Post by jas0 on 2007-01-13
I liked the review. I'm damiliar with Slackware but I've never tried archlinux. Now I'm intrigued and I just printed out the installation guide. :)

---

### Post by xabbott on 2007-01-14
I highly recommend Archlinux to a Linux power user. You should be comfortable with command line and conf files. I find the configuation much better than most "modern" distros. It's slim, does what you want, does what you tell it to. If you are unsure here are my tips...

Use the [Alpha installer]("http://archlinux.org/news/279/"). 
Read the [wiki]("http://wiki.archlinux.org")!

---

### Post by xabbott on 2007-01-14
btw here is a screenshot of my arch desktop
[[IMG]http://ubuntuforums.org/gallery/data/500/thumbs/Screenshot225.png[/IMG]]("http://ubuntuforums.org/gallery/showphoto.php/photo/4720/ppuser/196736")

---

### Post by kazuya on 2007-01-16
I think, this may be my next goal after Zenwalk or Sabayon{Gentoo} if not sooner. Is it possible to create or to have packages required as is the case with a slack system where I can simply download the .tgz files from linuxpackages.net or elsewhere for installation?

Does this distro provide all the development tools I need to eventually learn enterprise environments like Fedora and SUSE? That is skills needed for embedded linux, xml, oracle, ASP, javascript, perl, etc?

---

### Post by celsofaf on 2007-01-16
> **kazuya said:**
> I think, this may be my next goal after Zenwalk or Sabayon{Gentoo} if not sooner. Is it possible to create or to have packages required as is the case with a slack system where I can simply download the .tgz files from linuxpackages.net or elsewhere for installation?

Did you read the mini-review? At least part of the answer lies there.

> **kazuya said:**
> Does this distro provide all the development tools I need to eventually learn enterprise environments like Fedora and SUSE? That is skills needed for embedded linux, xml, oracle, ASP, javascript, perl, etc?

If anything is not available in pacman, you can always compile from source. Likewise for any distro.

---

### Post by K.Mandla on 2007-01-26
Anyone have any tips on inserting modules into the kernel during the Arch boot process? 

I'm trying to avoid using autodetection, but invariably whatever order I use in rc.conf leaves me without a working component (not necessarily one in particular, but maybe the mouse doesn't work, or the PCMCIA doesn't work, or something).

I have a full list generated with *hwdetect*, and I've filtered out the ones I don't want, and I know what I can drop altogether because I can blacklist them *with* autodetection and still get a working system. But rearranging the ones I want in the MODULES=() list never seems to work.

I guess what I'm trying to figure out is what order the modules need to be inserted. Any ideas?

---

### Post by K.Mandla on 2007-01-26
Never mind. I figured it out. I took the list of modules I wanted and searched the modules.dep file for each one, then listed them in the order they appeared in that file. System is working fine ... and I shaved four seconds off my boot time by not autoloading! Woo-hoo! :biggrin:

---

### Post by Rumor on 2007-01-26
> **K.Mandla said:**
> Never mind. I figured it out. I took the list of modules I wanted and searched the modules.dep file for each one, then listed them in the order they appeared in that file. System is working fine ... and I shaved four seconds off my boot time by not autoloading! Woo-hoo! :biggrin:

Huh, I have never thought to try that. I'll bet that would have made a couple of non-working systems become working ones. I've always just added them to the end of the list making sure that cups and gdm were the last two. Thanks for the tip!

---

### Post by pelle.k on 2007-01-26
He was acctually talking about the ```
# Modules to load at boot-up (in this order)
#   - prefix a module with a ! to blacklist it
#
MODULES=()
```
array, from which you can manually load modules, instead of letting udev do the job automaticly. :)
Not the ```
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=()
```
array. ;)

---

### Post by K.Mandla on 2007-01-26
Yup, modules, not daemons. :D

By the way, I heartily recommend doing that for anyone who wants to trim the lag they get from udev.

P.S.: Background the network process too; that makes a huge difference as well.

---

### Post by pelle.k on 2007-01-26
Why do i get the impression that you like to tweak stuff k.mandla? ;)
Yeah, starting the network can speed up your boot, but can also cause samba mountpoints in fstab to fail, if network is not up by the time netfs daemon is run.

---

### Post by Rumor on 2007-01-26
> **K.Mandla said:**
> Yup, modules, not daemons. :D

Bah, it's going to be time for bifocals soon . . .

---

### Post by K.Mandla on 2007-01-26
> **pelle.k said:**
> Yeah, starting the network can speed up your boot, but can also cause samba mountpoints in fstab to fail, if network is not up by the time netfs daemon is run.
True, but I don't use samba, and backgrounding the network startup works without error for me.  When I break something, I take a step backward and try again. ... :D

---

### Post by manmower on 2007-02-24
[Arch Linux 0.8 Voodoo Beta 2 .ISOs released](http://archlinux.org/news/296/). As usual with the rolling release system this is just a snapshot of the current packages with a new installer. 0.8 ISOs should be coming real soon now.

---

### Post by celsofaf on 2007-02-24
Some days ago I installed the beta1 for 0.8. No problems whatsover, and I'm even considering using Arch in place of Kubuntu as my main distro. :D They are doing an awesome job on Arch.

---

### Post by K.Mandla on 2007-02-25
> **manmower said:**
> [Arch Linux 0.8 Voodoo Beta 2 .ISOs released](http://archlinux.org/news/296/). As usual with the rolling release system this is just a snapshot of the current packages with a new installer. 0.8 ISOs should be coming real soon now.
Right on. I like the 0.8 installer thus far. 0.7.2 was always a little clunky for me.

> **celsofaf said:**
> Some days ago I installed the beta1 for 0.8. No problems whatsover, and I'm even considering using Arch in place of Kubuntu as my main distro. :D They are doing an awesome job on Arch.
+1! It's a close No. 2 to Ubuntu for me. 

Have you seen [KDEmod]("http://www.kdemod.ath.cx/") for Arch? I hear good things about it. If you dig KDE, you might want to take a look at it. [xabbott]("http://xabbott.wordpress.com/2007/02/12/kdemod/") seemed to like it too.

---

### Post by celsofaf on 2007-02-25
> **K.Mandla said:**
> Have you seen [KDEmod]("http://www.kdemod.ath.cx/") for Arch? I hear good things about it. If you dig KDE, you might want to take a look at it. [xabbott]("http://xabbott.wordpress.com/2007/02/12/kdemod/") seemed to like it too.

Yes I have taken a look at it _after_ I did a *pacman -S kde* on my system, which installed all of KDE. I'll give it a try later, it should be awesome to put in place of "standard" KDE. Being a KDE fan all the way, I must see it working. :)

Another thing I love about Arch, besides of course pacman, is the AUR, whose use can even be made easier by installing the [yaourt](http://aur.archlinux.org/packages.php?do_Details=1&ID=5863&O=0&L=0&C=0&K=yaourt&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd) package (also provided in the AUR), which allowes you to search/install/uninstall/query/etc packages from the AUR the same way you'd do for the repositories packages. And yes, it also searches the standard repositories. Sweet!

---

### Post by K.Mandla on 2007-02-26
Agreed. pacman is cool, but yaourt is like a dream come true. I love the entire ABS and AUR systems too. If I can get around the kernel panics I get when I insert my wireless card into my laptop, I'll go Arch on all my machines, across the board. :biggrin:

Self-aggrandizing screenshot: [http://www.ubuntuforums.org/showpost.php?p=2211586&postcount=466](http://www.ubuntuforums.org/showpost.php?p=2211586&postcount=466)

---

### Post by pelle.k on 2007-02-26
pacman and makepkg is almost the sole reason i use arch linux.
Unfortunately i've grown very tired of the rolling release system. I don't care about how stable arch might be, even though it's has a constantly changing nature. There's always something new breaking when other stuff gets fixed. It might not be that "critical" or hard to fix, but i rather fix my system every 3-6 months or so than once a week.

If there was a freeze every 3 months, arch would totally be the no 1 distro in my opinion. People tell me; "dont update then!". Well, it's a nice idea, but you can't really roll back if something goes wrong. One example is; suspend2ram hasn't been working for me since kernel 2.6.19-1 and because quite a few packages are compiled against 2.6.20.2-1, i can't roll back unless i manually replace the dependant packages as well. (if they even still exist in repo).

I've since then been looking at a few alternatives. Sidux looks promising. Up to date. Clean kde (lite install), to build a system from. The only downside is, it's technically a rolling release too, since it's based on debian sid :(

And no, i won't install ubuntu core, and add kde from there. It's a shame a distro is released with a dysfunctional ndiswrapper, even though it's supposed to be stable. OK i _might_ consider feisty when it's released. edgy broke suspend2ram for me so i have been pretty much ubuntu free for 6 months now.

On the bright side, frugalware 0.6 is going to be released very soon. It's uses pacman and makepkg as package manager, though its based on slackware (sort of anyway. not my favourite linux distro...)
I have had it installed before, and it's a nice distro. Too bad the forums pretty much suck, and the irc channel isn't too crowded. The devs can be pretty harsh (especially one of them...), but they are very competent. Just don't mention the AUR to those folks. It's like people sharing PKGBUILDS, are incompetent lamers without any clue of what they are doing, from their point of view.

---

### Post by K.Mandla on 2007-02-26
> **pelle.k said:**
> One example is; suspend2ram hasn't been working for me since kernel 2.6.19-1 and because quite a few packages are compiled against 2.6.20.2-1, i can't roll back unless i manually replace the dependant packages as well. (if they even still exist in repo).
I've noticed that can be a problem. I occasionally run into things that break on update, and can't really be fixed. I had font issues the other night after an xorg update.

Perhaps some of the eagerness to move to the 2.6.20 kernel comes with the 0.8 installer coming out. But you're right, there is a subtle benefit to staging releases, rather than rolling releases.

I'm going to give a look at frugalware, now that you mention it. :D

---

### Post by manmower on 2007-02-26
I think the rolling release system is one of the killer features of Arch... maybe I just got lucky with my hardware or maybe I don't have the same needs as other people, but pacman -Syu has usually been painless for me. If not there is almost always a fix or workaround.

---

### Post by antenna on 2007-02-26
I tend to find that things are broken more often than I would like in Arch, though I ran it for all last year and put up with it because the base and philosophy is so clean.  Nothing major, just small breakages in packages that mean I have to find alternatives for things fairly often which takes time and often means having to install more dependencies than I would like to get an app of equal functionality working.  For instance, Gnomebaker wont work at all for me after an upgrade, automounting in Gnome means having to run GDM for some reason, and there are too many drives being dislayed in Nautilus.  I typically run Xfce but that seems to have issues with mounting right now also.  It's just little things like that.  I'm just sticking with Debian (testing) for now, I miss the latest software but that's the nature of something stable I guess.

---

### Post by bodhi.zazen on 2007-02-28
Hmm ...

I must admit I like the rolling release style of Arch. I have not had any major problem although I have occasionally had more minor ones ...

At any rate, downgrading an arch package is possible :

[http://wiki.archlinux.org/index.php/Downgrade_packages](http://wiki.archlinux.org/index.php/Downgrade_packages)

---

### Post by celsofaf on 2007-03-04
After playing with KDE, I just started trying XFCE in Arch after a 'pacman -S xfce4'. Hey, it ROCKS! Amazingly fast anc clean! Way too much better than Xubuntu.

After all my tweaking learning Arch, I think I ended up with a much better system than any of the *buntus I tried. That is, at least for my taste. The best part of it all is: I got to learn a lot about Linux those few weeks I'm playing with Arch. Learned to properly use the shell (yes, got to learn a lot more yet), and learned the shell is NICE! Tweaking xorg.conf at hand for my needs proved more than necessary to properly use my keyboard when running X, and it's a good learning experience. Not to mention, of course, all the stuff about daemons and the init system.

Someone might say that it's too difficult to do things at hand like we need with Arch. I say it's not: their Wiki and Forums have more than enough information to guide anyone, step-by-step even. Once you learn how to do it, you do it without thinking. :) Now, surprisingly enough or not, I found the *Gentoo* forums also a very, very good source of help for the troubles I had. Didn't even had to ask for anything: search power!

I'm feeling comfortable enough to consider Arch as my main work distro already.

Yes, Feisty Fawn already has a partition on my hard drive awaiting for it!

---

### Post by unbuntu on 2007-03-06
I've been using Arch on and off on my secondary PC.  Last weekend I finally got the impulsion to get it on my primary PC.  I like the tweaking and install just what you need, and the performance is top-notch.

However, I do think they need some improvement especially on the documentation side.  Some work has been done to clean up their wiki but it's far from enough.  As a distro that targets the crowd that are willing to learn stuff, the wiki lacks the level of broadness and detail that's found in Gentoo wiki.  Also, some wiki articles are out of date; some are poorly written.  I think if Arch wants to attract more competent Linux users, official handbooks like the Gentoo ones are very much in need.

Also, different distros use different init systems, and Arch happens to use the not-so-popular BSD-like init script.  Don't get me wrong, I like the straight-forwardness of this init system but it's very different from the more widely used Debian one.  But of course, once you know the concept, it'd be fairly easy to migrate.

Nevertheless I like the system I've built now and more likely I'll use it as my primary Linux distro.

---

### Post by chaosgeisterchen on 2007-03-08
The reason I now rarely visit the ubuntu forums is my switch from ubuntu to Arch Linux. The main reason was the bleeding edge software and the rolling release system as well as the **rc.conf** centralized configuration. I love the way, things are working in Arch and it's very fast. Not to mention the fabolous [KDEmod](www.kdemod.ath.cx) desktop environment with very engaged maintainers (10 patched versions of 3.5.6 so far!).

---

### Post by K.Mandla on 2007-03-10
I need to try that KDEMod. Everybody raves about it. Of course, if it converts me to KDE, it will be a miracle of Biblical proportions. ;)

---

### Post by pelle.k on 2007-03-10
It's alright... I stay with the vanilla kde though...
If you lika a modded qt and kde, then by all means, go for it. I acctually prefer the arch vanilla kde _because_ of the untouched nature of it.

---

### Post by manmower on 2007-03-26
The long awaited "libified" pacman 3 is in testing. [Here](http://archlinux.org/news/303/)'s the announcement, which links to a detailed list of the many changes.

I've probably got a few hours to go before it hits the Belnet mirror but will be testing this as soon as possible.

---

### Post by celsofaf on 2007-03-26
After a few days in testing it should be moved to current. Great!!

---

### Post by manmower on 2007-04-06
[More news from the Arch front](http://www.archlinux.org/news/308/).

Forthcoming releases will be numbered by year and month and, more importantly, from now on there will be new ISOs with each kernel upgrade!

---

### Post by celsofaf on 2007-04-06
> **manmower said:**
> [More news from the Arch front](http://www.archlinux.org/news/308/).

Forthcoming releases will be numbered by year and month and, more importantly, from now on there will be new ISOs with each kernel upgrade!

I keep wondering why they took so long to do it. Since bringing new "features" never is in Arch's plans, and since every release is only in fact a current snapshot of -current- (with perhaps improvements in the installer), this is the most obvious thing to do. Great news!!

:guitar:

---

### Post by darweth on 2007-04-07
So after 3 1/3 months of Ubuntu goodness (my first Linux experience), I decided to once again go a little overboard and completely wipe my Ubuntu partition to install Arch!  COLD TURKEY, baby!  This is what I did from Windows to Ubuntu as well.

Now... first off let me say that I think Arch is great.  It was pretty easy to get into once I learned a few pointers.  My GNOME Arch is now basically identical to the Ubuntu GNOME and I am mad comfortable.  Got all my xchat/amarok scripts, file-roller context menus, software, configurations, etc.  I appreciate the snappyness of it, but I think this is a bit exaggerated.  It is faster than Ubuntu, for sure, but it is hardly a deal broker.  I really like that I installed the base and built upwards so my menus look slim and are filled with only the goodies I want.  Nice!  

Anyway, it was a great learning experience.  I now got a perfect GNOME box for what I do.  I even tried kdemod for a bit and it was not bad, but I definitely am not experienced with that DE.  

I am a little underwhelmed though.  I guess I am just too basic of a user to really appreciate the advantages of Arch.  Rolling is a nice benefit, but I guess I strongly overrated this option.  Constantly needing the latest is far from a necessity.  For your average Joe who just surfs the web, types papers, listens to music and chats... I will continue to HEAVILY recommend Ubuntu.  It is fine and dandy.  It just works!!  The speed of other distros like Arch is greatly overstated (though it is a bit faster).

Maybe my thoughts will change as I use Ubuntu for more than a day.  hehe.  Don't get me wrong... I am loving it, but I just don't see the point for most users.  Only an advanced power user needs the power offered here in this kind of environment.  But now that it is configured, I will probably keep Arch on this box for all time as long as packages are maintained and the distro continues receiving great support.  I might just stick with Ubuntu on any future boxes though.

---

### Post by pelle.k on 2007-04-08
> It is faster than Ubuntu, for sure, but it is hardly a deal broker.
I don't think that has ever been the one selling of arch linux. If you've tried arch linux, and the speed is the only thing that impressed you, i say you've missed what really make arch linux so great.
ABS, makepkg/makeworld, the initscripts/system, pacman, more than one kernel flavour in repos, very nice and competent forum, the AUR, the KISS attitude etc. etc. is.

Then again, if you're not an advanced user, you might not appreciate these things at all.

I like the fact that it's a bit faster than most distros out there though. :)

---

### Post by celsofaf on 2007-04-08
> **pelle.k said:**
> Then again, if you're not an advanced user, you might not appreciate these things at all.

Well, I don't think myself as an advanced user, yet I do appreciate every feature you described about Arch. Besides, I'm coming to a conclusion: if you *want* to become an "advanced user", Arch (but not *only* Arch, of course) suits your needs.

Did I have a hard time configuring/using Arch? No. Why? Everything you need is available on the forum (not only Arch's forum, of course), the wiki, google, mailing lists... Just search, and ask!, and you're fine.

---

### Post by darweth on 2007-04-08
> **pelle.k said:**
> I don't think that has ever been the one selling of arch linux. If you've tried arch linux, and the speed is the only thing that impressed you, i say you've missed what really make arch linux so great.
ABS, makepkg/makeworld, the initscripts/system, pacman, more than one kernel flavour in repos, very nice and competent forum, the AUR, the KISS attitude etc. etc. is.

Then again, if you're not an advanced user, you might not appreciate these things at all.

I like the fact that it's a bit faster than most distros out there though. :)

Ah.  Sorry if I sounded a little harsh. :)  I guess the differences and advantages aren't immediately obvious to someone who has almost-exclusively used Ubuntu or to someone who just wants convenience and immediate function.  

I did use the AUR for the first time this morning and it was a pleasure.  Also been reading about yaourt which looks to make things even easier.  Haven't tried it yet!

But I will continue to use ARCH and hopefully grow with the distro.  Then I will look back on my original post in this thread with shock and befuddlement!

---

### Post by pelle.k on 2007-04-08
> Then I will look back on my original post in this thread with shock and befuddlement!
:D

Since some time back, i've been running arch most of the time. This does not mean i think ubuntu is a bad distro! If you ride with the defaults most of the time, and don't do any big changes under the hood, ubuntu is great. However, when you want to customize your system from the ground up, you'll do yourself a favour if you choose arch.

There are countless examples, but like back when the ndiswrapper version i got with dapper didn't work with my usb dongle, i could easily build another set (as a package) in arch. I just had to make _one_ change in a PKGBUILD. Hell, i could even rebuild my whole kde without too much effort.

Another nice side effect is you learn what is started in your DAEMONS array in rc.conf, because you _have_ to know what it is you're putting there...
Before i started using arch i didn't know that alsa initscipt was responsible for saving/restoring volume levels at bootup/shutdown. little things like that.

---

### Post by K.Mandla on 2007-04-12
Has anyone run into weird errors with yaourt 0.6.5 and pacman 3? yaourt seems to spit out an error message anytime I try to install something from AUR. I think it's using a flag (a -w flag?) that pacman 3 doesn't handle. I looked on the Arch forums but didn't see anything related.

It doesn't slow me down really, since I just tell yaourt to move everything into /var/abs/local and build it with makepkg. I was just thinking I might be doing something funky that I could fix on my end.

Cheers!

---

### Post by Rumor on 2007-04-12
Huh, what do you know? I had not tried yaourt since upgrading to pacman 3.0. I read your message here and thought I'd give it a try. I tried to install Mozilla's Sunbird from the AUR and got:
```
==> sunbird dependencies:
 - libstdc++5 (already installed)
 - nss (already installed)
 - libxt (already installed)
 - libgnomeui (already installed)

==>  Edit the PKGBUILD ? [y/N] ("A" to abort)
==>  ----------------------------------------------
==> 
==> Building and installing package
/usr/bin/makepkg: illegal option -- w
makepkg version 3.0.0

```
Not terribly helpful to you, but at least you now know it is not just you. Yaourt version 0.6.5

---

### Post by Rumor on 2007-04-12
I just upgraded yaourt to version 0.7.5 from this thread: [http://bbs.archlinux.org/viewtopic.php?id=25718&p=3](http://bbs.archlinux.org/viewtopic.php?id=25718&p=3) and Sunbird installed and runs.

```
==>  Continue installing 'sunbird'? [Y/n] 
==>   ----------------------------------------------
==>
loading package data... done.
checking dependencies... done.
cleaning up... done.
(1/1) installing sunbird           [###################################] 100%
If you like this package, please install aurvote
and vote for its inclusion/keeping in [community]

```

All I did to install the new yaourt was to replace the yaourt and pacdiffviewer files from the archive into /usr/bin (after renaming the ones that were being replaced)

Maybe it will work for you too?

---

### Post by tscook on 2007-04-13
Now that my Arch install is working (mostly) the way I want it too I have found The Distro. All the functionality with a fraction of the packages. Saving tomorrow for configuring suspend to ram, a bootsplash, and finding out why urxvt w/ pseudo-transparency redraws improperly all the time. After that pacman -Syu for life.

---

### Post by K.Mandla on 2007-04-15
> **Rumor said:**
> Maybe it will work for you too?
Yup, that was it. I was looking for a new yaourt because I knew pacman 3 was out; I should've looked a little harder. At least it was easy to pin down the culprit on this one. Cheers! :D

---

### Post by ThinkBuntu on 2007-04-24
So I'm giving Arch a try again. It seems that updates had been causing kernel panics when I tried out 0.7.2, but so far 0.8's going very smoothly for me. GIMP loads in about one second, and everything's lighting quick: quicker even than Zenwalk!

---

### Post by pelle.k on 2007-04-24
> It seems that updates had been causing kernel panics when I tried out 0.7.2
I assume you mean install cd version 0.7.2, since arch linux has no versions or releases...

The switch to mkinipcio (initramfs...) would cause a kernel panic, and that change happened some time after the 0.7.2 cd was released. The solution is to edit menu.lst to point to the new kernel image (since with mkinitpcio it was renamed). Either way, 0.8, obviously solves that "problem" (even though it was announced at the main page), and they are going to release install cd:s even tighter in the future to prevent  new installs to go through such drastic changes.

You'll have to watch out for similar changes at the main page. Even if your system is running perfectly, these changes can render it useless, _if_ you don't read the news.

As an example, atm they are moving gnome to /usr from /opt, and this can bring some slight side effects. Since this is announced at [www.archlinux.org](www.archlinux.org) , you'll know this and keep the forums clean of threads that could easily been avoided.

---

### Post by K.Mandla on 2007-04-26
> **pelle.k said:**
> The switch to mkinipcio (initramfs...) would cause a kernel panic, and that change happened some time after the 0.7.2 cd was released. The solution is to edit menu.lst to point to the new kernel image (since with mkinitpcio it was renamed). 
I remember that. That confused me for a long time. I think the step-by-step for how to fix it is still somewhere in this thread.

---

### Post by moon_dog on 2007-05-05
i've installed arch on a partition (hd0,2), but can't boot.  it always returns an error message: 

no filesystem could mount root, tried:
kernel panic - vfs not syncing

anyone know what's going on?

---

### Post by moon_dog on 2007-05-05
here is my menu.lst on my root partition

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f2b2d330-1af7-49e1-9f19-73a184424c8a ro
# kopt_2_6=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

title		Arch Linux
root 		(hd0,2)
kernel		/boot/vmlinuz26 root=/dev/sda3 ro
intird		/boot/kernel26.img
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

and this is the one on the arch partition

```
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/sda3 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/sda3 ro
initrd /boot/kernel26-fallback.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

```

i've tried changing "sda" to "hda", but it doesn't seem to make a difference.  i always get the error:

Kernel panic - Not syncing: VFS: Unable to mount root fs on unknown-block(0,0) on boot

---

### Post by pelle.k on 2007-05-05
I think you are confused over how grub works...
Why do you have _two_ menu.lst set up? grub, installed as a bootloader to MBR (master boot record, there is only one such one a HD) are set to look for menu.lst at _one_ place only. That is the OS from which grub-install /dev/sda is run. How exactly did you install grub, when you installed arch? If you use grub on MBR, you're supposed to have stanzas for every OS, at one place in you computer (that would be either ubuntu menu.lst _or_ arch menu.lst).

If you wan't to have grub boot-loader installed to root partition instead, you can have a separate menu.lst for every OS you install. This way you can have GAG in MBR which points to grub boot-loader in the root partition of every OS.
See, there's a diffrence between /boot/grub, and grub-boot loader. I'm not very good at explaining these things. I suggest you read up on this.

The best advice i can give you is, always install grub to "boot partition" instead of "MBR", and let GAG ( [http://gag.sourceforge.net/](http://gag.sourceforge.net/) ) take care of booting the correct partition for you. This will save you a lot of troubles setting up many/diffrent OS:es on one hd.

---

### Post by moon_dog on 2007-05-05
i used the cd installation.  grub to arch partition (hd0,2).  root partition is ubuntu (hdo,0).  i just modified the menu.lst on the ubuntu partition to include an entry for arch.  anything else you need to know?

---

### Post by pelle.k on 2007-05-05
What install cd version did you use?
Can you mount /dev/sda3 from ubuntu and ls "/", "/boot" and "/boot/grub" and paste output here?
Do you have multiple hd:s?

---

### Post by moon_dog on 2007-05-06
ok got the whole thing resolved... it was just a typo on the menu.lst file.... now though i can't seem to get my wireless working.  

iwconfig gives this output:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

this is my rc.conf

```
#
# /etc/rc.conf - Main Configuration for Arch Linux
#

#
# -----------------------------------------------------------------------
# LOCALIZATION
# -----------------------------------------------------------------------
#
# LOCALE: available languages can be listed with the 'locale -a' command
# HARDWARECLOCK: set to "UTC" or "localtime"
# TIMEZONE: timezones are found in /usr/share/zoneinfo
# KEYMAP: keymaps are found in /usr/share/kbd/keymaps
# CONSOLEFONT: found in /usr/share/kbd/consolefonts (only needed for non-US)
# CONSOLEMAP: found in /usr/share/kbd/consoletrans
# USECOLOR: use ANSI color sequences in startup messages
#
LOCALE="en_US.utf8"
HARDWARECLOCK="localtime"
TIMEZONE="Canada/Pacific"
KEYMAP="us"
CONSOLEFONT=
CONSOLEMAP=
USECOLOR="yes"

#
# -----------------------------------------------------------------------
# HARDWARE
# -----------------------------------------------------------------------
#
# Scan hardware and load required modules at bootup
MOD_AUTOLOAD="yes"
# Module Blacklist - modules in this list will never be loaded by udev
MOD_BLACKLIST=()
#
# Modules to load at boot-up (in this order)
#   - prefix a module with a ! to blacklist it
#
MODULES=(b44 mii ipw2200) 
# Scan for LVM volume groups at startup, required if you use LVM
USELVM="no"

#
# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
HOSTNAME="myhost"
#
# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available
# interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
#
# Note: to use DHCP, set your interface to be "dhcp" (eth0="dhcp")
#
lo="lo 127.0.0.1"
#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
eth0="dhcp"
eth1="dhcp"
INTERFACES=(lo eth0 eth1)
#
# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
#gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
#
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network-profiles
#
#NET_PROFILES=(main)

#
# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng network netfs crond)


# End of file

```

and my conf.d
```

#
# Settings for wireless cards
#
# For each wireless interface declared in INTERFACES (in rc.conf), declare
# a wlan_${IF} variable that contains the arguments to be passed to
# iwconfig(8).  Then list the original interface name in the
# WLAN_INTERFACES array.
#

wlan_eth1="eth1 mode managed essid default"
WLAN_INTERFACES=(eth1)

```

---

### Post by moon_dog on 2007-05-06
reinstalled the wireless card driver and i can now see my wireless connection and use iwconfig to set up a connection.  however i still can't/don't know how to request and receive an IP address.  i tried using the "commit" flag in iwconfig: 

```

iwconfig eth1 essid "linksys" mode managed channel 6 key off commit
```

but an error message came up saying i couldn't commit.  on ubuntu i would just use
```

iwconfig eth1 essid "linksys" mode managed channel 6 key off
sudo dhclient
```

on boot i still get this error

```
::starting network                       [failed]
```

---

### Post by ahaslam on 2007-05-10
I've just installed 64bit Voodoo & it seems quite fast. To measure the performance I wanted to run a few benchmarks, one of those being super_pi. Unfortunatly I can't run it, in Zenwalk I'd issue 'pi 20' and in Ubuntu 'sh super_pi 20'. Here's what I get:
```

[root@myhost super_pi]# ls
Readme.txt  pi  super_pi
[root@myhost super_pi]# chmod +x *pi
[root@myhost super_pi]# pi 20
bash: pi: command not found
[root@myhost super_pi]# sh super_pi 20
super_pi: line 1: ./pi: No such file or directory
[root@myhost super_pi]#
```

super_pi:
> ./pi $1


Any guidance would be appreciated ;)

---

### Post by pelle.k on 2007-05-10
you can't run
```
pi 20
```
because "pi" isn't in your $PATH.

why don't you just run
```
./pi 20
```

It's a bit strange however, since "./pi $1" is in super_pi. It might be some to me unknown enviroment variable acting up though. Havent seen this script before...
I'm not really sure this qualifies as a "real" benchmark though, as it doesn't measure much more than mathematics performance...

---

### Post by ahaslam on 2007-05-10
Thanks for your response though I'd tried that:
> [root@voodoo super_pi]# ./pi
bash: ./pi: No such file or directory
It's a good bench for me as I'm a keen overclocker & improvements are clearly shown here.

---

### Post by pelle.k on 2007-05-10
that's freakin impossible! Can you "stat" the file, or the whole dir if necessary?

---

### Post by ahaslam on 2007-05-10
> **pelle.k said:**
> that's freakin impossible! Can you "stat" the file, or the whole dir if necessary?

[root@voodoo ~]# stat zen/ahaslam/Desktop/Crap/super_pi/pi
  File: `zen/ahaslam/Desktop/Crap/super_pi/pi'
  Size: 255408          Blocks: 512        IO Block: 4096   regular file
Device: 803h/2051d      Inode: 360482      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/ ahaslam)   Gid: (  100/   users)
Access: 2007-05-10 16:05:34.000000000 -0700
Modify: 2003-09-26 08:28:47.000000000 -0700
Change: 2007-03-19 12:29:09.000000000 -0700
[root@voodoo ~]#

---

### Post by ahaslam on 2007-05-12
The problem persists:

---

### Post by pelle.k on 2007-05-12
weird. this is what i got;
```
[pelle@pelle1 super_pi.tar.gz_FILES]$ ls
PI.DAT  Readme.txt  pi  super_pi
[pelle@pelle1 super_pi.tar.gz_FILES]$ stat ./pi 
  File: `./pi'
  Size: 255408          Blocks: 512        IO Block: 4096   regular file
Device: 807h/2055d      Inode: 2272974     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/   pelle)   Gid: (  100/   users)
Access: 2007-05-12 23:12:25.000000000 +0200
Modify: 2003-09-26 17:28:47.000000000 +0200
Change: 2007-05-12 23:10:46.000000000 +0200
[pelle@pelle1 super_pi.tar.gz_FILES]$ ./pi 20
 Version 2.0 of the super_pi for Linux OS
 Fortran source program was translated into C program with version 19981204 of
 f2c, then generated C source program was optimized manually.
 pgcc 3.2-3 with compile option of "-fast -tp px -Mbuiltin -Minline=size:1000 -Mnoframe -Mnobounds -Mcache_align -Mdalign -Mnoreentrant" was used for the
 compilation.
 ------ Started super_pi run : Sat May 12 23:13:13 CEST 2007
 Start of PI calculation up to 1048576 decimal digits
 End of initialization. Time=       0.372 Sec.
 I= 1 L=       0        Time=       1.000 Sec.
 I= 2 L=       0        Time=       1.152 Sec.
 I= 3 L=       1        Time=       1.160 Sec.
 I= 4 L=       2        Time=       1.300 Sec.
 I= 5 L=       5        Time=       1.296 Sec.
 I= 6 L=      10        Time=       1.296 Sec.
 I= 7 L=      21        Time=       1.256 Sec.
 I= 8 L=      43        Time=       1.308 Sec.
 I= 9 L=      87        Time=       1.380 Sec.
 I=10 L=     174        Time=       1.388 Sec.
 I=11 L=     349        Time=       1.380 Sec.
 I=12 L=     698        Time=       1.380 Sec.
 I=13 L=    1396        Time=       1.384 Sec.
 I=14 L=    2794        Time=       1.372 Sec.
 I=15 L=    5588        Time=       1.176 Sec.
 I=16 L=   11176        Time=       1.156 Sec.
 I=17 L=   22353        Time=       1.116 Sec.
 I=18 L=   44707        Time=       1.172 Sec.
 I=19 L=   89415        Time=       1.096 Sec.
 End of main loop
 End of calculation.    Time=      25.030 Sec.
 End of data output.    Time=       0.132 Sec.
 Total calculation(I/O) time=      25.162(       0.892) Sec.
 ------ Ended super_pi run : Sat May 12 23:13:39 CEST 2007
[pelle@pelle1 super_pi.tar.gz_FILES]$
```

I got the package from [ftp://pi.super-computing.org/Linux/super_pi.tar.gz](ftp://pi.super-computing.org/Linux/super_pi.tar.gz)
What is your folder permissions?

---

### Post by ahaslam on 2007-05-12
A fresh download from your link gives the following permissions:
```
[ahaslam@voodoo Desktop]$ ls -l super_pi
total 260
-rwxr-xr-x 1 ahaslam users    323 Sep  3  2003 Readme.txt
-rwxr-xr-x 1 ahaslam users 255408 Sep 26  2003 pi
-rwxr-xr-x 1 ahaslam users      8 Sep 25  2003 super_pi
[ahaslam@voodoo Desktop]$ 
```

& following your example:
```
[ahaslam@voodoo super_pi]$ ls
Readme.txt  pi  super_pi
[ahaslam@voodoo super_pi]$ stat ./pi
  File: `./pi'
  Size: 255408          Blocks: 504        IO Block: 4096   regular file
Device: 804h/2052d      Inode: 203573363   Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/ ahaslam)   Gid: (  100/   users)
Access: 2007-05-12 23:28:56.024883321 -0700
Modify: 2003-09-26 08:28:47.000000000 -0700
Change: 2007-05-12 23:28:13.626467175 -0700
[ahaslam@voodoo super_pi]$ ./pi 20
bash: ./pi: No such file or directory
[ahaslam@voodoo super_pi]$ 
```

I found [this]("http://www.ocforums.com/archive/index.php/t-405925.html") via google (see the last post), could it be a x86_64 problem :-k


_*- EDIT -*_

**I feel stupid now, of course that's the problem & there doesn't seem to be a 64 bit Linux version** ](*,)

**Thanks for your time**

*_- EDIT 2 -_*

**pacman -S lib32** *(community)* does the trick ;)

---

### Post by moon_dog on 2007-05-13
i've been experiencing this strange problem on my xfce desktop.  it takes about 10 minutes for any changes to the settings of the desktop to take effect.  for example, if i change the background, or the font of the windows, it will take 10 minutes for the changes to take effect.  i've re-installed xfce and the problem persists.  i'm not quite sure if this is some problem with arch or if it's a specific problem with xfce.  the thing is, if i try to run thunar from a terminal in xfce, it also takes about 10 minutes for thunar to come up.

---

### Post by pelle.k on 2007-05-13
moon_dog:
I'm pretty sure this is because you either are not running dbus and hal, or you do not run the "lo" network connection (essential to many interprocess communication protocols...).
 I already assume you've done the regular stuff (added your hostname to /etc/hosts, ran fam daemon)

---

### Post by ceelo on 2007-05-13
Just installed Arch a few days ago and have got most of it up and running how I like it. Man, they aren't joking about the speed, this thing is *fast*. I'm even seeing a noticeable increase in Beryl's performance. Some issues such as auto-mounting CDs/DVDs and other minor things, but I am really enjoying it so far.

---

### Post by rsambuca on 2007-05-13
> **ceelo said:**
> Just installed Arch a few days ago and have got most of it up and running how I like it. Man, they aren't joking about the speed, this thing is *fast*. I'm even seeing a noticeable increase in Beryl's performance. Some issues such as auto-mounting CDs/DVDs and other minor things, but I am really enjoying it so far.

I haven't tried Arch (yet), but I keep hearing about how "fast" it is.  Can someone please let me know what you are talking about when you say fast?  ie. boot-up, programs opening, or actual tasks?

I have used ubuntu, both 32 and 64 bit, Sabayon, 32 and 64, and dreamlinux.

---

### Post by ThinkBuntu on 2007-05-13
> **ceelo said:**
> Just installed Arch a few days ago and have got most of it up and running how I like it. Man, they aren't joking about the speed, this thing is *fast*. I'm even seeing a noticeable increase in Beryl's performance. Some issues such as auto-mounting CDs/DVDs and other minor things, but I am really enjoying it so far.

What's your hardware? I noticed a speed increase over Ubuntu and others, but got pretty much equal speed with Debian, Zenwalk, and PCLOS with my 1.6GHz 1.5GB RAM laptop. Just curious.

---

### Post by ceelo on 2007-05-13
> **rsambuca said:**
> I haven't tried Arch (yet), but I keep hearing about how "fast" it is.  Can someone please let me know what you are talking about when you say fast?  ie. boot-up, programs opening, or actual tasks?

I have used ubuntu, both 32 and 64 bit, Sabayon, 32 and 64, and dreamlinux.

The system boots faster, programs load and run faster. That 2-3 second delay while switching tabs in Firefox that I've noticed in pretty much every other Linux I've tried is absent in Arch. On newer hardware you probably won't notice a significant difference, but I'm running on a Celeron with 512MB RAM and integrated graphics. OpenOffice seems to load quicker too. The most noticeable was definitely Beryl. It's still a bit sluggish for me but smoother than I'd noticed before. I wouldn't say one should make the switch from say, Debian to Arch based on the speed alone, but other distros like Fedora and SuSE, definitely. Then again, my view might be a bit skewed since my system is quite dated.

---

### Post by ceelo on 2007-05-13
> **ThinkBuntu said:**
> What's your hardware? I noticed a speed increase over Ubuntu and others, but got pretty much equal speed with Debian, Zenwalk, and PCLOS with my 1.6GHz 1.5GB RAM laptop. Just curious.

Specs listed above. :KS

---

### Post by Rumor on 2007-05-13
I find a significant speed benefit in boot time, program loading and the response to most every function in Arch.
System Specs (CPU and RAM):
```
cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
model name      : AMD Athlon(TM) XP 3000+
cpu MHz         : 1735.552
cache size      : 512 KB

```
```
free
             total       used       free     shared    buffers     cached
Mem:        775640     284444     491196          0        240     141716
-/+ buffers/cache:     142488     633152
Swap:      1028152          0    1028152

```
And finally, the daemons I load on boot from my /etc/rc.conf file:
```
DAEMONS=(syslog-ng network netfs crond autofs alsa samba cups gdm)

```
I boot in under 30 seconds from grub to the gnome desktop using automatic login.
Abiword opens in under 2 seconds.
Kazehakase (web browser) opens in less than 5 seconds.
Swiftfox opens in around 3 seconds.
Pan newsreader opens in less than 2 seconds.
It is much faster than my Ubuntu Feisty install on the same machine.
**EDIT**
By way of comparison, same machine, now booted into Ubuntu Feisty, not running Samba:
```
 free
             total       used       free     shared    buffers     cached
Mem:        775736     370156     405580          0      10032     210404
-/+ buffers/cache:     149720     626016
Swap:      1510068          0    1510068

```

---

### Post by DJiNN on 2007-05-13
I've finally got Arch running and although i've got a few problems, i agree with the other posters here..... it's fast. Firefox loads in seconds..... way faster than anything else i've tried. :)

Having said that, this is a Dual Core (4200+) AMD machine with 2gb of ram, so i'm going to try it on my other machine that's already running Xubuntu, which is a bog standard old P4 2.4ghz (400fsb) with 1gb Ram. If it's speedy on there as well, then i think i "May" start using it as my main OS..... although i'm not 100% sure yet, because there's still a lot that i don't know about Arch.....

But from what i have seen so far, i can highly recommend it!! :)

DJiNN

---

### Post by celsofaf on 2007-05-14
> **DJiNN said:**
> i'm going to try it on my other machine that's already running Xubuntu, which is a bog standard old P4 2.4ghz (400fsb) with 1gb Ram.

My PC is slower than yours and I wouldn't call it old in any way. Still, in my experience, Arch with KDE runs faster than Xubuntu on it. Go for it! Once you get used to Arch (no, it's not a nightmare), you won't think to use another distro.

---

### Post by rsambuca on 2007-05-14
> **ceelo said:**
> The system boots faster, programs load and run faster. That 2-3 second delay while switching tabs in Firefox that I've noticed in pretty much every other Linux I've tried is absent in Arch. On newer hardware you probably won't notice a significant difference, but I'm running on a Celeron with 512MB RAM and integrated graphics. OpenOffice seems to load quicker too. The most noticeable was definitely Beryl. It's still a bit sluggish for me but smoother than I'd noticed before. I wouldn't say one should make the switch from say, Debian to Arch based on the speed alone, but other distros like Fedora and SuSE, definitely. Then again, my view might be a bit skewed since my system is quite dated.

hmmm...  I'm not sure that I will see much difference then.  I don't have the fastest rig in the world by any means:  AMD Athlon 64 +3500, 1GB Ram, but for me FF opens in less than 3 seconds, and tab switching is instantaneous.  OO is by far the slowest to load at 5 seconds.  Boot up with ubuntu is slow (54 seconds), but is a non issue for me as I never turn my PC off.

---

### Post by moon_dog on 2007-05-14
pelle thanks for the reply.  it was the "lo" network interface

---

### Post by ahaslam on 2007-05-14
> **rsambuca said:**
> I haven't tried Arch (yet), but I keep hearing about how "fast" it is.  Can someone please let me know what you are talking about when you say fast?  ie. boot-up, programs opening, or actual tasks?

I have used ubuntu, both 32 and 64 bit, Sabayon, 32 and 64, and dreamlinux.

In every day situations (booting, app launch, etc)  Arch64 *feels* about the same as Zenwalk which *feels* only slightly faster than Feisty. The performance gain comes when under heavy loads. For example in 3d games Zenwalk produces an average frame rate 15% higher than Feisty. Arch adds a further 4% to Zenwalks figures, offering almost 20% more performance. 

For an overclocking enthusiast like myself, that's the difference of a volt mod'd vga or water cooled cpu.

---

### Post by R3linquish3r on 2007-05-15
Got base Arch installed. Spent 3 hours messing with ndiswrapper before i realised the modules didn't match my kernel. God I hate broadcoms, Installing GDM and Gnome now. So far it's been an interesting experience on my old Latitude C600. I'm hoping Arch will be fairer with it then Ubuntu was.

---

### Post by ThinkBuntu on 2007-05-15
> **Anthony Haslam said:**
> In every day situations (booting, app launch, etc)  Arch64 *feels* about the same as Zenwalk which *feels* only slightly faster than Feisty. The performance gain comes when under heavy loads. For example in 3d games Zenwalk produces an average frame rate 15% higher than Feisty. Arch adds a further 4% to Zenwalks figures, offering almost 20% more performance. 

For an overclocking enthusiast like myself, that's the difference of a volt mod'd vga or water cooled cpu.
I use my machine for design, development, word processing, and some simple games, so the only really CPU-intensive processes I put it through are when I launch multiple programs, or give it some huge task from the terminal (like $ du -h /, which takes a bit).

---

### Post by rokixz on 2007-05-16
Arch is my favorite distro, but when I gave my PC to engineer, my video Card is not support Monitor, only defaults. After that Arch linux with KDE is not opens. On my monitor Writes Not Available mode :(

Can I get help

---

### Post by pelle.k on 2007-05-16
rokixz;
Yes, you i will help you.
You know, a funny thing with linux is that once people learn a thing, they keep doing it and never question if it could be done another way. Maybe there's an easier way?

Check my monitor section out (as long as you run with dpms, you _probably_ dont need vertical and horizontal refresh rate);
```
Section "Monitor"

        Identifier      "crt"
#       HorizSync       30-107
#       VertRefresh     50-160
        Option          "DPMS"

EndSection
```

Now this works just as good as with those lines i commented out in xorg.conf.
Now we just have to wait for xorg 7.3 where there us no real need for an xorg conf file really.

[edit]you might have to turn your resolution down a bit though, if you're _not_ using the same monitor this time...
I didn't really understand what you meant. What components are new ones?[/edit]

---

### Post by moon_dog on 2007-05-16
about ABS, i've found that it's a great way to manage packages.  however, i've also found that there are some packages that aren't found in /var/abs, even though they are installed.  not sure why this is.  how do you manage these packages?

---

### Post by pelle.k on 2007-05-16
If you think about it, pacman and abs isn't the same thing is it?
pacman has it's own .conf and so does abs...

---

### Post by moon_dog on 2007-05-16
so how would you recompile the packages that aren't found in /var/abs?  say i wanted to add --enable-gui to mplayer but it isn't in /var/abs, is there a way to go about it?  i thought abs scanned the computer for all installed packages and placed them in /var/abs.

---

### Post by pelle.k on 2007-05-17
Ok, i'll be a little bit clearer this time. In /etc/pacman/pacman.conf you have these repos to choose among;
```
[current]
# Add your preferred servers here, they will be used first
Server = ftp://ftp.gigabit.nu/current/os/i686
Include = /etc/pacman.d/current

[extra]
# Add your preferred servers here, they will be used first
Server = ftp://ftp.gigabit.nu/extra/os/i686
Include = /etc/pacman.d/extra

#[unstable]
# Add your preferred servers here, they will be used first
#Include = /etc/pacman.d/unstable

[community]
# Add your preferred servers here, they will be used first
Server = ftp://ftp.gigabit.nu/community/os/i686
Include = /etc/pacman.d/community

```
And in /etc/abs/abs.conf you've got those counterparts for loading /var/abs/local with pkgbuilds;
```
SUPFILES=(arch extra !unstable community)

```

So no, it isn't automatic. Since mplayer is in extra, you would have to make sure theres no exclamation (!) mark before "extra" and then run "abs"...

---

### Post by moon_dog on 2007-05-17
thanks for the reply pelle.  so how about if i install a package, like xmms.pkg.tar.gz?  can i edit the PKGBUILD through abs?

---

### Post by moon_dog on 2007-05-17
i mean to say if i install a package that isn't found in the repos.  like a package that i downloaded from AUR.

---

### Post by ThinkBuntu on 2007-05-17
I'm back with Arch! I'm taking the attitude this time of "one thing at a time." I understand it may very well take me two weeks or longer, chipping away at my problems, to get my system "just right" with the features I expect, as opposed to before where I expected that three hours of troubleshooting would get my system perfect. The payoff will be when KDE4, for example, is released, because I know upgrading will go to perfection!

Boot time is spectacular, and I really am learning about my system. And I'm doing it efficiently, not waiting five hours to compile an application like I was with Sabayon.

---

### Post by pelle.k on 2007-05-17
> thanks for the reply pelle. so how about if i install a package, like xmms.pkg.tar.gz? can i edit the PKGBUILD through abs?
Well, abs is nothing more than an "source" interface/mirror for those existing packages in the binary repos. "abs" would be the equivalent of "pacman -Sy", and "makepkg -b" would be like "pacman -S".
**abs just synchs the PKGBUILDS, nothing more.** makepkg, can make use of both the PKGBUILDS from abs _and_  binary packages from the pacman repos though.

If you build a PKGBUILD, and it requires something to be installed as a dependency, this can be done _if_ the dependency is available through "abs"/source or "pacman"/binary repos...
makepkg -s = install dependencies with pacman
makepkg -b = build dependencies from /var/abs
If it's not availiable anywhere, you'll have to make a pkgbuild of it and install it first yourself.

Yes, you can edit you PKGBUILD to your liking.

---

### Post by moon_dog on 2007-05-17
ok i mean if i download a package file from the net, not from the repos (****.pkg.tar.gz), how i edit the PKGBUILD?  it won't show up in abs because it isn't in the repos, and the downloaded file is already packaged.  how would one go about editing this?

---

### Post by ahaslam on 2007-05-17
Simply loving Arch. The upgrades have gone really smoothly so far, a rolling release cycle that actually works ;)

PS. moon-dog, why don't you get the source & build your own package for your needs?

---

### Post by pelle.k on 2007-05-17
> ok i mean if i download a package file from the net, not from the repos (****.pkg.tar.gz), how i edit the PKGBUILD? it won't show up in abs because it isn't in the repos, and the downloaded file is already packaged. how would one go about editing this?
A binary (compiled...)  package doesn't include a PKGBUILD. Neither does a .deb include it's debian counterpart. It seems you got that already. You could ask the same question about a .deb file you found.

In arch you have an advantage though...
I've never seen a package in it's binary form without it's PKGBUILD in close reach. Since all packages have a PKGBUILD in the first place, people commonly distribute the PKGBUILD instead. Like in the AUR. ( aur.archlinux.org )

So, the problem you describe is almost non existant.

---

### Post by Nikron on 2007-05-17
Everything is beautiful, only problem maybe that install and setup took a couple of days (not continuous).  But now everything is just to my liking.  Not too big of a speed increase from what I can see, but its sorta noticeable.

---

### Post by ThinkBuntu on 2007-05-17
I know this much: when KDE4 releases, I'll be happy to be using Arch. I have faith that not only will the transition go smoothly, I also won1t lose any relevant settings. Installing from the 0.8 release, I had already unwittingly upgraded to the new release seamlessly long before seeing the announcement on DW.

---

### Post by A.I. BOT on 2007-05-17
I used to be on arch for a long time, it was fantastic. But unfortunately, I got fed up with making my own ACPI scripts that dident always work. The laptop support wasent as good as I found on Ubuntu. I wanted to beable to close my lid and have my screen shut off ... and when I open the lid, xscreensaver will ask for my password.

If anyone knows how to do that I'd gladly go back and use Arch again because it is simply an elegant system :).

Thanks.

---

### Post by ThinkBuntu on 2007-05-18
> **A.I. BOT said:**
> I used to be on arch for a long time, it was fantastic. But unfortunately, I got fed up with making my own ACPI scripts that dident always work. The laptop support wasent as good as I found on Ubuntu. I wanted to beable to close my lid and have my screen shut off ... and when I open the lid, xscreensaver will ask for my password.

If anyone knows how to do that I'd gladly go back and use Arch again because it is simply an elegant system :).

Thanks.
Have you worked with KLaptop and KDE settings? I'm pretty sure it can be done...

---

### Post by A.I. BOT on 2007-05-18
Yeah I tried KLaptop, it dident do anything, I set it all up and rebooted, tried my lid and nothing happened.

---

### Post by ThinkBuntu on 2007-05-18
> **A.I. BOT said:**
> Yeah I tried KLaptop, it dident do anything, I set it all up and rebooted, tried my lid and nothing happened.
Am I correct in assuming you enabled all ACPI modes and set the laptop lid button action to suspend?

---

### Post by pelle.k on 2007-05-18
bah! klaptop... How medieval ;)
I run powersave dameon, and kpowersave. Thats how you do it.

Oh, and let me tell you, arch is the _only_ distro that can suspend my core2duo and fujitsuSiemens laptop.
You don't need kpowersave for basic suspend/hibernation features though.. "powersave -u" does the trick.

---

### Post by ThinkBuntu on 2007-05-18
> **pelle.k said:**
> bah! klaptop... How medieval ;)
I run powersave dameon, and kpowersave. Thats how you do it.

Oh, and let me tell you, arch is the _only_ distro that can suspend my core2duo and fujitsuSiemens laptop.
You don't need kpowersave for basic suspend/hibernation features though.. "powersave -u" does the trick.

KPowersave vs. KLaptop...explain? My KDE has KLaptop, but i remember KDE distros in the past using KPowersave. They both seem to have the same options available from the applet.

---

### Post by Rumor on 2007-05-18
I just noticed that the new install ISO's have been released.

[http://www.archlinux.org/](http://www.archlinux.org/)

2007.5 "Duke" - Changelog here: [http://www.archlinux.org/news/325/](http://www.archlinux.org/news/325/)

---

### Post by Nikron on 2007-05-18
Has anyone got beryl to work with powersave -u (or powersave -U)?  Or alternatively, anyone know the config file where I can tell powersave to kill beryl and then restart it?

---

### Post by pelle.k on 2007-05-18
ThinkBuntu;
kpowersave is nothing more than a GUI for powersave(d) infrastructure. It's intended as a replacement for klaptop. If klaptop works for you, why fix it... :)

Nikron:
I dont run beryl, so i can't really say for sure. But if beryl _is_ causing problems i see two options here;
1. Make a daemon script in /etc/rc.d and use this in /etc/powersave/sleep (restart service you know?).
2. Make a custom script in /usr/libexec/powersave/scripts and add it to two of these events;
(from /etc/powersave/events ...)
```
EVENT_GLOBAL_SUSPEND2DISK="prepare_suspend_to_disk screen_saver do_suspend_to_disk"
EVENT_GLOBAL_SUSPEND2RAM="prepare_suspend_to_ram screen_saver do_suspend_to_ram"
EVENT_GLOBAL_STANDBY="prepare_standby screen_saver do_standby"

EVENT_GLOBAL_RESUME_SUSPEND2DISK="restore_after_suspend_to_disk"
EVENT_GLOBAL_RESUME_SUSPEND2RAM="restore_after_suspend_to_ram"
EVENT_GLOBAL_RESUME_STANDBY="restore_after_standby"
```

Of course you would have to know how to write this script in the first place...

---

### Post by ThinkBuntu on 2007-05-18
I couldn't even find KPowersave in the repos. Granted, I have KDEmod installed, so it's possible this is blocking the package out. In any case, I have no reason to use it as long as my medieval KLaptop is working.

---

### Post by Rumor on 2007-05-18
It looks like kpowersave is in the AUR.

```
yaourt -Ss kpowersave
aur/kpowersave 0.6.2-5
    KDE-frontend for the powersave daemon
aur/kpowersave-devel 0.7.2-1
    KDE-frontend for the power management
aur/kpowersave-svn 2951-1
    A KDE-frontend for the power management

```

---

### Post by Nikron on 2007-05-18
> **pelle.k said:**
> ThinkBuntu;
kpowersave is nothing more than a GUI for powersave(d) infrastructure. It's intended as a replacement for klaptop. If klaptop works for you, why fix it... :)

Nikron:
I dont run beryl, so i can't really say for sure. But if beryl _is_ causing problems i see two options here;
1. Make a daemon script in /etc/rc.d and use this in /etc/powersave/sleep (restart service you know?).
2. Make a custom script in /usr/libexec/powersave/scripts and add it to two of these events;
(from /etc/powersave/events ...)
```
EVENT_GLOBAL_SUSPEND2DISK="prepare_suspend_to_disk screen_saver do_suspend_to_disk"
EVENT_GLOBAL_SUSPEND2RAM="prepare_suspend_to_ram screen_saver do_suspend_to_ram"
EVENT_GLOBAL_STANDBY="prepare_standby screen_saver do_standby"

EVENT_GLOBAL_RESUME_SUSPEND2DISK="restore_after_suspend_to_disk"
EVENT_GLOBAL_RESUME_SUSPEND2RAM="restore_after_suspend_to_ram"
EVENT_GLOBAL_RESUME_STANDBY="restore_after_standby"
```

Of course you would have to know how to write this script in the first place...

Thanks a lot, that's exactly what I needed, suspend to ram/disk works with beryl now.

---

### Post by ahaslam on 2007-05-20
There seems to be very frew Arch wallpapers around, anyone know of good source?

I've just gimped one up for myself & because of this I thought I'd share: [http://xs215.xs.to/xs215/07206/arch.png](http://xs215.xs.to/xs215/07206/arch.png)

Here it is in use:
[[img]http://xs215.xs.to/xs215/07206/newwall.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs215&d=07206&f=newwall.png) [[img]http://xs215.xs.to/xs215/07206/beryl.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs215&d=07206&f=beryl.png)
I'm glad that there's *pacman -Rs*, Beryl makes good screenies but it's quite annoying.

Enjoy ;)

---

### Post by mahy on 2007-05-21
Yay! I'm just running a fresh Arch installation. Ran into a coupla problems, but so far fixed everything. It rocks! The only thing left is OTR support for my Pidgin. Any ideas?

---

### Post by Rumor on 2007-05-21
> **Anthony Haslam said:**
> There seems to be very frew Arch wallpapers around, anyone know of good source?


Well, up until last week I'd have told you to look in the Arch Gallery, but it has been taken down. There are a few on the Deviant Art website (one of my favorites: [http://www.deviantart.com/deviation/36160302/?qo=4&q=by%3Abathannen&qh=sort%3Atime+-in%3Ascraps](http://www.deviantart.com/deviation/36160302/?qo=4&q=by%3Abathannen&qh=sort%3Atime+-in%3Ascraps)) and a few on Gnome-Look's website.

---

### Post by mahy on 2007-05-21
> **mahy said:**
> Yay! I'm just running a fresh Arch installation. Ran into a coupla problems, but so far fixed everything. It rocks! The only thing left is OTR support for my Pidgin. Any ideas?

Don't bother. A bit more wiki-reading and the AUR repository fixed it. It's even easier than on Ubuntu!

---

### Post by ahaslam on 2007-05-21
> **Rumor said:**
> Well, up until last week I'd have told you to look in the Arch Gallery, but it has been taken down. There are a few on the Deviant Art website (one of my favorites: [http://www.deviantart.com/deviation/36160302/?qo=4&q=by%3Abathannen&qh=sort%3Atime+-in%3Ascraps](http://www.deviantart.com/deviation/36160302/?qo=4&q=by%3Abathannen&qh=sort%3Atime+-in%3Ascraps)) and a few on Gnome-Look's website.

Thx, shame that they took it down, I'd have enjoyed it.

---

### Post by ahaslam on 2007-06-18
I've started a thread for sharing any custom artwork, themes & whatnot on their forums. I've linked my own stuff, I hope others join in & contribute ;)

Here's the thread if anyone here's interested: [http://bbs.archlinux.org/viewtopic.php?pid=259791#p259791](http://bbs.archlinux.org/viewtopic.php?pid=259791#p259791)

---

### Post by finferflu on 2007-06-21
I've installed Arch yesterday, and so far I am immensely impressed. Despite all textual configuration it's so damn simple. I only had some issues with configuring my ndiswrapper, but I found out I had downloaded packages too recent for my kernel, since I was running an outdated system (from an outdated install CD), so what? I plugged in my LAN cable, ran "pacman -Syu" and apart from the time it took to download all the packages, my system was updated in about 5 minutes. Pacman is amazing, soooo fast!
I still had some issues with the grub entry for Arch after the upgrade, but I found the answer quickly by searching for the error message I got in the Arch Linux forums. I edited the grub's menu.lst and I was up and running again. Ndiswrapper worked as a charm, with much less hassle than I had on Ubuntu (not to mention PcLinuxOS). I quickly installed the X server and Gnome, and was able to get Beryl working with not much effort (I had to realise there were some conflicts with the fglrx drivers I had installed by mistake).
I have to say that everything seems to be straight forward and simple (just follow the wiki!), true to the Arch motto. I find the system to be very lightweight, reliable and stable. And pacman is damn fast, did I mention that?
Also the packages seem to be more up to date than Feisty, and I particularly enjoy the AUR philosophy, for the simple way to manage user contributed packages. 
I think I have found my new home, this is the distro of my dreams. I still keep Ubuntu on my hard disk, but I don't think it will be my primary OS. 

So far so good!

---

### Post by 5-HT on 2007-06-21
> **ahaslam said:**
> I've started a thread for sharing any custom artwork, themes & whatnot on their forums. I've linked my own stuff, I hope others join in & contribute ;)

Here's the thread if anyone here's interested: [http://bbs.archlinux.org/viewtopic.php?pid=259791#p259791](http://bbs.archlinux.org/viewtopic.php?pid=259791#p259791)

Thanks! Is there something wrong with the link?

[quote=finferflu]...[/quote]:D

---

### Post by fiery on 2007-06-23
> **mahy said:**
> It's even easier than on Ubuntu!

Agreed. I was on Ubuntu since 5.04, left half way through Edgy for Zenwalk, then moved to Arch a month and a half ago. Yes, takes a a little bit more to set up (just a little bit), but it is sooo much nicer once going. And I love Pacman, so bloody easy.

---

### Post by Raffo on 2007-06-23
I'll install arch after the exams :D 
July is a terrible month for university :(

---

### Post by ahaslam on 2007-06-23
> **5-HT said:**
> Thanks! Is there something wrong with the link?
The links seem fine to me, the only problem is the lack of contributions :p

> **fiery said:**
> Agreed. I was on Ubuntu since 5.04, left half way through Edgy for Zenwalk, then moved to Arch a month and a half ago. Yes, takes a a little bit more to set up (just a little bit), but it is sooo much nicer once going. And I love Pacman, so bloody easy.
*Exactly* the same story here ;)

---

### Post by finferflu on 2007-06-23
I also was impressed by the simplicity, expecially after hearing a lot about Arch as the power-users distro. I don't consider myself a power user, yet I find it quite simple, even because I only do simple things with it. A flexible distro, isn't it?

---

### Post by raja on 2007-06-29
After thinking long about a second distro and trying out various ones on my virtualbox, i finally plumped for Arch a week back. Installation sure takes a little more time and some reading, thanks to how we have been spoiled by Ubuntu. But I have almost everything set up now save a few hiccups and it is an awesome distro. 
Very lean (I installed base and then only what I needed) and very fast. Much faster then Ubuntu - and I was surprised by that. I also like the philosophy of a few clean configuration files to configure everything. You get newer versions of most application thanks to the rolling updates.
So, it looks like great fun, and who knows, may replace Ubuntu as my primary distro.

---

### Post by Rui Pais on 2007-06-30
Hi,
i tried Arch on 2 computers, a pentium4 (duke 32b) and a C2D (duke 64b) but i got a weird problem... i already search Arch forum but didn't find anything.

The problem is that after run Arch for a while (10~15 mn) it turns ADSL line of my router down. The only way to make it back again is power off router an then power on again :(
It's very annoying, of course. 
It happens on both computers/versions and i have tried either with static IPs an DHCP, having both cases the same symptoms. 
I never had such an issue on any Distro i tried or used and never heard about nothing like that.
Can someone give me some light on what may be happen?

Thanks.

---

### Post by pelle.k on 2007-06-30
"sudo tail /var/log/messages.log" or "dmesg | tail" when it happens?

---

### Post by finferflu on 2007-06-30
> **Rui Pais said:**
> Hi,
i tried Arch on 2 computers, a pentium4 (duke 32b) and a C2D (duke 64b) but i got a weird problem... i already search Arch forum but didn't find anything.

The problem is that after run Arch for a while (10~15 mn) it turns ADSL line of my router down. The only way to make it back again is power off router an then power on again :(
It's very annoying, of course. 
It happens on both computers/versions and i have tried either with static IPs an DHCP, having both cases the same symptoms. 
I never had such an issue on any Distro i tried or used and never heard about nothing like that.
Can someone give me some light on what may be happen?

Thanks.


Did you try to post this on the Arch forums? I think it would be more useful for people who may get problems similar to yours. And if you find a solution on the Ubuntu forums, I really suggest you to write it down on the wiki or something like that. It would be very cool for the Arch community :)

Thanks.

---

### Post by Rui Pais on 2007-07-01
hi, thanks for your replys.
> **pelle.k said:**
> "sudo tail /var/log/messages.log" or "dmesg | tail" when it happens?
Only yesterday at night i could log to my arch and check. I used for 3 or 4 hours and... mysteriously... the issue disappeared. 
Maybe an pacman -Syu had fix it... don't know. I checked messages.log from past sessions for anything unusual but didn't find anything. 
When i get time i will check my old machine (that i didn't update yet) and see if i can reproduce it again.
 
> **finferflu said:**
> Did you try to post this on the Arch forums? I think it would be more useful for people who may get problems similar to yours. And if you find a solution on the Ubuntu forums, I really suggest you to write it down on the wiki or something like that. It would be very cool for the Arch community :)

Thanks.

Yes, of course. I just post about it here to see if it was a common issue or get some general tips (i could be something obvious wrong since i have very few experience with Arch), not to get real support :)

I had a problem with Arch Forum. Its very hard to read. The choice of gray for background make it hard for the eyes, the characters vanishes in the too dark pages... Wiki, in opposite it's nice, clear and well written, very informative and easy to find info (i find ubuntu docs and search very confusing). 

But if I get again the problem (or still have it in my old box) i will create and account and post there. :)

Thanks

---

### Post by Ramses de Norre on 2007-07-01
For what it's worth: I've totally switched to Arch a few months ago and for the moment, I'm staying :) I really like the distro as a whole, the package manager is splendid and the community is really helpful. The rolling release system is a superb feature (if you're not on a production server) and breakage hasn't occurred to much for me.
It feels _a lot_ faster than ubuntu and has perfect integration of lightweight WMs, all configuration is done by config files.

The only minor thing is the installer, I find it quite difficult, but [this](http://wiki2.archlinux.org/index.php/Install_Arch_from_within_another_distro) method works flawlessly and lets you use internet and such on the same pc while installing.

I'd say, try out Arch but realize that the distro isn't made for everyone, you need to know the ins and outs of linux a little to get Arch running decently.

---

### Post by finferflu on 2007-07-01
> **Ramses de Norre said:**
> 
The only minor thing is the installer, I find it quite difficult, but [this](http://wiki2.archlinux.org/index.php/Install_Arch_from_within_another_distro) method works flawlessly and lets you use internet and such on the same pc while installing.

I'd say, try out Arch but realize that the distro isn't made for everyone, you need to know the ins and outs of linux a little to get Arch running decently.
Wow, that's a very cool method, it's the first time I hear about that. 
I don't know if I will ever try it, but I think it's *the* solution for my wireless problems, namely ndiswrapper not being in the install CD. So in this way I could set it up from withing the host distro, reboot, and voilà, Arch + internet connection up and runnning. So cool :)
I just hope I will not need to reinstall Arch, that's why I don't know if I will ever try it.
By the way, if you read the instructions, I think the installer is quite straight forward (I didn't try to partition from withing the installer, though, since I've used Gparted).

---

### Post by fwojciec on 2007-08-06
New developments in the Arch Linux land, so I though I'd bump this old thread to let everyone know...  

ISOs for new Arch Linux 2007.08 (Don't Panic) are released.  Info and download links [***HERE***]("http://archlinux.org/news/337/").

Enjoy!

---

### Post by drum on 2007-08-13
Hi,
I've been running Arch on my core2 duo box for 4 months and everything works great.
I just bought a T61 and found that the hardware on it makes it very difficult to get wireless, sound and nvidia running in Arch "Don't Panic"
I'm a little bit past the noob stage and have tried all the detailed instructions I can find to get these things working but I've had no luck so far. Probably my lack of experience.
It's a bit over my head so I would appreciate any advice from people who've had success on this machine.
It runs well with a wired connection but I love to get sound and wireless and using the built in Nvidia chip.

Maybe I should wait till the drivers get more up to date to work without these advanced methods of installing?
Any thoughts? I don't want to give up on it. Am I on the right track?
Thanks:(

---

### Post by 5-HT on 2007-08-14
> **drum said:**
> 
Any thoughts? 
Are your video, sound, and wireless cards supported? Best to search for the specific hardware IMO instead of the whole notebook as more people should have those cards than computer. You can post 'em here, but would probably have better luck either on the Arch forums or their IRC channel. 

> **drum said:**
>  Maybe I should wait till the drivers get more up to date to work without these advanced methods of installing? If the devices are supported you should have no problem. If they're not, there'd be no way to get 'em working at all (but development rates being as they are, hopefully they'll be supported Soon.  And with a rolling release like Arch, you'll get 'em when they're hot off the press...) 
Cheers,

---

### Post by andrek on 2007-08-14
I really would like to try Arch.. I tried to emulate it with Microsoft Virtual PC - the install script is really difficult.. I had to edit many .conf files by myself, it was tough.. Are there any alternative installation scripts, as easy as Debian's one?

---

### Post by bodhi.zazen on 2007-08-14
> **andrek said:**
> I really would like to try Arch.. I tried to emulate it with Microsoft Virtual PC - the install script is really difficult.. I had to edit many .conf files by myself, it was tough.. Are there any alternative installation scripts, as easy as Debian's one?

This is both the biggest advantage and disadvantage of Arch.

The advantage is that the install process forces you to understand how the system actually works. Once you install you know how to maintain and run the OS.

One option it to try March, it is a live CD Arch Linux + Fluxbox. No option to install however.

[http://marchlinux.wikidot.com/](http://marchlinux.wikidot.com/)

Once you decide to install, give yourself 2 hours and read through the documentation.

---

### Post by kellemes on 2007-08-14
> **andrek said:**
> I really would like to try Arch.. I tried to emulate it with Microsoft Virtual PC - the install script is really difficult.. I had to edit many .conf files by myself, it was tough.. Are there any alternative installation scripts, as easy as Debian's one?

The defaults work for most systems I'm sure..
I have installed it on many systems without serious issues.
I actually find the setup-procedure very simple (think KISS principle), transparent and (again) the defaults work most of the time.

What was the difficulty with setting-up Arch? Maybe a little help will make you an Archer! :popcorn:

---

### Post by K.Mandla on 2007-08-14
> **bodhi.zazen said:**
> This is both the biggest advantage and disadvantage of Arch.

The advantage is that the install process forces you to understand how the system actually works. Once you install you know how to maintain and run the OS. ...
 
Once you decide to install, give yourself 2 hours and read through the documentation.
Big +1. Arch forces you to learn about the guts of your computer, and if you're not interested in that, it will be a frustrating experience.

There is a very detailed [installation walkthrough]("http://www.archlinux.org/static/docs/arch-install-guide.txt"), but again, you have to know about the inside of your system for it to be usable. 

And I'm sorry to say it, but Arch users generally don't suffer newbies. I certainly don't mean they're rude, but if you ask a question on the forums and you haven't done you're homework, you might be rebuffed ... un-gently.

---

### Post by kellemes on 2007-08-14
> **K.Mandla said:**
> (..) and you haven't done you're homework..


This is it the thing.. 
[How to ask questions]("http://catb.org/~esr/faqs/smart-questions.html")

The moderators in the Arch forums are doing a great job in keeping threads clean and keep the trolls out.
Most Archers understand and respect not everyone has the same level of knowledge.
All in all there is much less of a elitist-culture going on as in some other (specific dists) forums where just being a n00b seems to be enough to get flamed.

---

### Post by andrek on 2007-08-14
Ok, so according to your posts I SHOULD try installing Arch :)
First, I'm on Debian right now. I don't want to destroy or over-write my current GRUB configuration. The best way for me would be installing the system without any bootloader and then adding Arch info to current GRUB config?
Second, I haven't used any package-manager than apt-get or aptitude. Are there any guides how to get accustomed to pacman ? :)
And the last thing, I'm in 'love' to GNOME, is there any way to make it slim and fast, like KDEmod for KDE?

Oh, and I certainly know what's inside my pc. I'd like to get the best performance from it. I think Arch would manage that ;)

I know i seem to be noob, and so I am. I have no experience in using wide-variety of distros.. just ubuntu and debian.

Cheers.

---

### Post by kellemes on 2007-08-14
> **andrek said:**
> Ok, so according to your posts I SHOULD try installing Arch :)
First, I'm on Debian right now. I don't want to destroy or over-write my current GRUB configuration. The best way for me would be installing the system without any bootloader and then adding Arch info to current GRUB config?
Second, I haven't used any package-manager than apt-get or aptitude. Are there any guides how to get accustomed to pacman ? :)
And the last thing, I'm in 'love' to GNOME, is there any way to make it slim and fast, like KDEmod for KDE?

Oh, and I certainly know what's inside my pc. I'd like to get the best performance from it. I think Arch would manage that ;)

I know i seem to be noob, and so I am. I have no experience in using wide-variety of distros.. just ubuntu and debian.

Cheers.

I understand you wanna dual boot ArchLinux/Debian? Windows also maybe?
I've actually never dual booted GNU/Linux, I will one of these days..
It doesn't really matter if you leave your current Grub as it is (and add Arch-entries) or let Arch install Grub and add Debian-entries. It all depends on from which distro do you want to manage Grub.. (I know there is a way to be able to manage Grub from both distro's but I don't know how)
By the way..it could very well be the installation of Grub **from Arch** will recognize Debian and add the entries automatically. (I know it does recognize Windows.)
Backup you most important stuff anyway ;)

I don't know of any special modular version of Gnome but I can tell ya, on Arch it's so fast you won't believe it.

Pacman is the best thing, see..
[http://wiki.archlinux.org/index.php/Pacman]("http://wiki.archlinux.org/index.php/Pacman")

**pacman -Syu** you'll use the most (update any package currently installed on my system)

By the way, there is nothing wrong with being a n00b as long as you're willing to learn.. And if it doesn't workout you can always go back to Debian (you can't go wrong with that)


Edit: For the best help become a member at the [Arch Forums.]("http://bbs.archlinux.org/")

---

### Post by Rumor on 2007-08-14
> **andrek said:**
> 
First, I'm on Debian right now. I don't want to destroy or over-write my current GRUB configuration. The best way for me would be installing the system without any bootloader and then adding Arch info to current GRUB config?

You can just skip the bootloader installation step and modify your current GRUB to include the boot info for Arch.
```
title Arch Linux
root (hdX,X) <-modify the X's to the correct disc, partition for root
kernel /vmlinuz26 root=/dev/sdaX ro <-again, edit the path to your kernel
initrd /kernel26.img
```


> **andrek said:**
>  Second, I haven't used any package-manager than apt-get or aptitude. Are there any guides how to get accustomed to pacman ? :)


[http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)
The Arch wiki is your friend.

> **andrek said:**
> And the last thing, I'm in 'love' to GNOME, is there any way to make it slim and fast, like KDEmod for KDE?


I use gnome on all three PCs I have running Arch. You can choose to install just the base gnome package and then add to it as you like. I always install both gnome and gnome-extra for the additional packages.

But, there is no Gnome mod for Arch.

---

### Post by Laplace's Daemon on 2007-08-15
I asked about booting to multiple distros in [this thread](http://ubuntuforums.org/showthread.php?t=508301) a little while ago.  Got some good advice that's working for me.

---

### Post by K.Mandla on 2007-09-05
Hey, what's the deal with GTK1 fonts in Arch? I can't seem to find or install anything that doesn't look like complete garbage.

I've tried xfonts-100dpi and xfonts-75dpi, plus a few others, but either they're xft and don't apply to GTK1 applications, or they just don't show up in xfontsel.

I only ask because dillo-improved out of the archlinux.fr repositories is UH-MAZING fast. And it doesn't render pages to look like rubbish either.

But the darn GTK1 interface is ruining it for me. (I know, I'm so superficial. :roll: )

---

### Post by EndPerform on 2007-09-05
Just thought I'd post.  I just downloaded an Arch ISO and have a base install up and running in Virtualbox on my laptop.  It reminds me a bit of Gentoo, except without the compile times.  I'm liking it so far, and if I continue to grow fond of it, Ubuntu may be in trouble on my desktop (my laptop unfortunately runs Vista due to heat and sound issues in Linux).

---

### Post by Rumor on 2007-09-05
> **K.Mandla said:**
> Hey, what's the deal with GTK1 fonts in Arch? I can't seem to find or install anything that doesn't look like complete garbage.

I've tried xfonts-100dpi and xfonts-75dpi, plus a few others, but either they're xft and don't apply to GTK1 applications, or they just don't show up in xfontsel.

I only ask because dillo-improved out of the archlinux.fr repositories is UH-MAZING fast. And it doesn't render pages to look like rubbish either.

But the darn GTK1 interface is ruining it for me. (I know, I'm so superficial. :roll: )

Have you looked at the following info? [http://wiki.archlinux.org/index.php/XOrg_Font_Configuration](http://wiki.archlinux.org/index.php/XOrg_Font_Configuration) I have not messed much with my fonts, but your question has prompted me to look more closely at some of the alternative offerings.

I'll have to look at the dillo-improved package. I tend to ignore the archlinux.fr repository once I have yaourt installed.

Thanks for the head's up!

---

### Post by fwojciec on 2007-09-05
> **K.Mandla said:**
> Hey, what's the deal with GTK1 fonts in Arch? I can't seem to find or install anything that doesn't look like complete garbage.

I've tried xfonts-100dpi and xfonts-75dpi, plus a few others, but either they're xft and don't apply to GTK1 applications, or they just don't show up in xfontsel.

I only ask because dillo-improved out of the archlinux.fr repositories is UH-MAZING fast. And it doesn't render pages to look like rubbish either.

But the darn GTK1 interface is ruining it for me. (I know, I'm so superficial. :roll: )

Are the font paths in your xorg.conf correct?  Do you see any font related errors  in your Xorg.0.log?  I had to play around with the paths in xorg and mkfontdir command before xfontsel would see all the fonts I have installed in Arch.

---

### Post by K.Mandla on 2007-09-05
> **fwojciec said:**
> Are the font paths in your xorg.conf correct?  
Aha! That's what it was. For some reason those paths were commented out. I got the normal series after I uncommented those lines and restarted X. Thanks! dillo-improved looks much better now! ;)

---

### Post by regomodo on 2007-09-05
hmm. a bit dissapointed by Arch Linux. I managed to get a base install up and running no problem but i ran into inconsistencies between the instructions and what was actually possible.

For example, when changing the locales i was told to run $locale -a . This spurted out errors. When changing the timezone the changes were not added to rc.conf.
A certain file that was supposed to be edited didn't exist. How to add the CD packages into a .conf file was wrong. I followed it to the word ( i printed out the 27 base install guide) and must have done it 4 times.

I also managed to bork my Gutsy install as the initrd img was in a seperate /boot partition which Arch wiped even though i set the mountpoints manually and told nothing to format.

Maybe another day but i'm going to try Gentoo instead

---

### Post by pelle.k on 2007-09-05
> **For example, when changing the locales i was told to run $locale -a **
I quote from the install guide;
> You can get a list of the available locales by running locale -a from the commandline. This setting is not needed for US English users.
"locale -a" only shows what locales you have added (or commented out if you will, in /etc/locale.gen  +  run locale-gen). this last step is acctually done in the installer...
> **When changing the timezone the changes were not added to rc.conf**.
I quote from the guide;
> Command tzselect can find correct timezone for you.
It doesn't add your timezone to rc.conf. It _finds_ you timezone. In my case it said "'Europe/Stockholm" which is correct.
> **A certain file that was supposed to be edited didn't exist.**
What file?
> **How to add the CD packages into a .conf file was wrong. I followed it to the word**
I will agree that this would probably not work though. I guess the changes in pacman V3 probably rendered that advice useless. You're supposed to name the [repository] after the database file in the directory your pointing to. In this case it's named current.db.tar.gz on the install cd, and since that is also true of the original repo, you can just as well put
```
Server = file:///mnt/cd/arch/pkg
```
just below the existing [current] in /etc/pacman.conf (temporarily, since pacman will replace the real repo for the cd until you remove this modification)
This entry will be primary even if you have an "Include = " below it.

> **I also managed to bork my Gutsy install as the initrd img was in a seperate /boot partition which Arch wiped even though i set the mountpoints manually and told nothing to format.**
You failed to understand at least two of the instructions from the install guide  judging from your post, so who knows, maybe you did it again.

Better luck next time though. Don't hesitate to ask if something isn't clear to you.

---

### Post by regomodo on 2007-09-06
> **pelle.k said:**
> I quote from the install guide;

"locale -a" only shows what locales you have added (or commented out if you will, in /etc/locale.gen  +  run locale-gen). this last step is acctually done in the installer...

I quote from the guide;

It doesn't add your timezone to rc.conf. It _finds_ you timezone. In my case it said "'Europe/Stockholm" which is correct.

What file?

I will agree that this would probably not work though. I guess the changes in pacman V3 probably rendered that advice useless. You're supposed to name the [repository] after the database file in the directory your pointing to. In this case it's named current.db.tar.gz on the install cd, and since that is also true of the original repo, you can just as well put
```
Server = file:///mnt/cd/arch/pkg
```
just below the existing [current] in /etc/pacman.conf (temporarily, since pacman will replace the real repo for the cd until you remove this modification)
This entry will be primary even if you have an "Include = " below it.


You failed to understand at least two of the instructions from the install guide  judging from your post, so who knows, maybe you did it again.

Better luck next time though. Don't hesitate to ask if something isn't clear to you.

yeah, maybe i should have worded myself a bit better. When it says it shows available $locales -a all i was an error. When i ran $ locale the certain files returned were just the ones specified by rc.conf which was en_US. When i changed it with en_GB pacman spurted errors about the locale.

Woops, missed that about tzselect.In any case i changed the rc.conf to Europe/London anyway. Its hard working from a plump armchair. I can't concentrate properly in this madhouse, can't wait till i get back to uni to my own house. 

/etc/mkinitcpio.conf was the file missing. Yep, i double checked the spelling and tried to tab-complete but it wasn't there.

About Pacman. Cheers for the tips, i'll remember when i get back to it (i.e. when i fail with Gentoo) but first i've got to wait for my custom kernel to compile. yawn.

---

### Post by kazuya on 2007-09-07
I'm loving archlinux. It is a learning machine, but once setup is so rewarding. I inderstand that there is no gui fron-end for pacman?
I can actually do without it, but that would be an added bonus for me.

I find arch and zenwalk equally fast on my 256MB PC. 

My question, I always get a prompt when using pacman -S gnome
about using -C or something like that. It works fine, but I am just curious on what that means. I shall post the message later. Else, the system runs like a dream.

---

### Post by K.Mandla on 2007-09-07
Has anyone ever installed Arch on an i586 machine? I mean, have you ever recompiled the key packages, like it suggests in the wiki?

[http://wiki.archlinux.org/index.php/Install_Arch_i586](http://wiki.archlinux.org/index.php/Install_Arch_i586)

I have a machine I'd love to use Arch on, but it's a K6-2, and Arch doesn't give it any love. I  was just wondering how big a can of worms I'd be opening, if I decided to recompile for i586 on one machine, just to install on another.

Or would I be better off just trying Gentoo?

---

### Post by pelle.k on 2007-09-07
> about using -C or something like that.
Can i take a guess at that it's complaining about your locale? Maybe you should set one in that case.

> Has anyone ever installed Arch on an i586 machine?
I have, using [lowarch]("http://bbs.archlinux.org/viewtopic.php?id=27580")
In the end  i had to compile too many packages by hand, so i gave up. It's really a shame, because that k6-2 i had was perfect for a ligt weight distro like arch.

---

### Post by Rumor on 2007-09-07
> **kazuya said:**
> I'm loving archlinux. It is a learning machine, but once setup is so rewarding. I inderstand that there is no gui fron-end for pacman?
I can actually do without it, but that would be an added bonus for me.


There is one that has been developed by a user. 

Jacman: [http://www.andy-roberts.net/software/jacman/](http://www.andy-roberts.net/software/jacman/)

There were some others, but I believe Jacman is the only one being actively developed.

---

### Post by miggols99 on 2007-09-07
Jacman doesn't work for me :( Tried using it. Nice GUI. But when I tried to install something, it would crash.

---

### Post by K.Mandla on 2007-09-07
> **pelle.k said:**
> I have, using [lowarch]("http://bbs.archlinux.org/viewtopic.php?id=27580")
In the end  i had to compile too many packages by hand, so i gave up. It's really a shame, because that k6-2 i had was perfect for a ligt weight distro like arch.
That's what I was afraid of. If it ends up being recompile after recompile, I think I'd rather just tinker with Gentoo. Not a thrilling prospect, but we'll see what happens. Thanks.

---

### Post by ynnhoj on 2007-09-07
i'm sure if you read the gentoo handbook/install guide you'll have very little (major) to worry about.  there are always bumps in the road, but if yer prepared it's not an issue.

---

### Post by Warren Watts on 2007-09-08
I had Xubuntu installed on my secondary computer for a day or so, but something about Xubuntu's implementation of Xfce left me cold.  The selection of preinstalled packages is minimal at best, and I didn't really feel like Xubuntu really offered any significant speed increase over Ubuntu on the same hardware, So I went back to Ubuntu.

RavTux had really good things to say about Wolvix, so I set up Wolvix Cub on a second 4.3 GB drive in the computer. 

I have been dual booting Ubuntu and Wolvix Cub for about three weeks now on my secondary computer and I realized the other day that I haven't booted into Ubuntu in at least a week.  

The main reason for this is that I have grown to appreciate Wolvix Cub/Xfce's compact size and speed (both being issues considering the computer only has 256MB of RAM and a 700 MHz Duron processor).  It way outperforms Ubuntu running on the same hardware.  My only complaint so far is with the difficulty I seem to have locating and installing Slackware packages.  

Here lately everyone has been raving about Arch Linux, and since I'm not even using Ubuntu on the secondary machine, I have decided it's time for Ubuntu to go. 

Don't panic, I'm still running Ubuntu on my server and primary computer (My 12 year old daugher LOVES Ubuntu, and I don't think I could bring myself to take it away from her anyway).

I downloaded and burnt an Arch ISO, naively expecting an easy Live CD based install similar to Ubuntu and Wolvix, and whoa!, much to my surprise and dismay upon booting the CD I discovered I have to LEARN to install Arch.

At first this put me off, but after reading the Arch Wiki on installation and all 22 pages of this thread, I have decided to give it a go.  I have been using Linux exclusively for about four months now.  Between what I have learned using Ubuntu and my experience with Wolvix, I think it is something I can handle. :-)

I'll post my progress and experiences here as I go thru the install.

---

### Post by Warren Watts on 2007-09-08
Update: Arch Linux Install** Day 1**

Two hours into the install, I am typing this from Firefox running on Xfce!  It wasn't nearly as difficult as I imagined it was going to be. 

I followed the [Beginner's Guide on the Arch Linux Wiki]("http://wiki.archlinux.org/index.php/Beginners_Guide"), built the base install, then rebooted into the base system and installed Xwindows and Xfce.  

The only difficulty I have had so far was configuring xorg.conf.  The default xorg.conf didn't do a very good job of detecting possible screen resolutions and color depths, so I cheated and copied the "Device" and "Screen" sections from my working Wolvix install.  

Now it's time to ***customize***!

---

### Post by 5-HT on 2007-09-09
> **Warren Watts said:**
> 
so I cheated and copied the "Device" and "Screen" sections from my working Wolvix install.  


same here...:)

---

### Post by fwojciec on 2007-09-09
> **5-HT said:**
> same here...:)
make sure to look at /var/log/Xorg.0.log and check for any errors (EE) and warnings (WW).  Most likely you will have to adjust one or two things - like font paths for example - to make everything work correctly in Arch.

---

### Post by afonic on 2007-09-09
Arch's biggest stength imo is the amazing way it stays up to date. Just install once and keep syncing - the way they generate binary packages as soon as a new upstream version is out and serve them to you via pacman is just awesome. Its releases are just snapshots of the current package tree, the concept of different versions as in most other distros is non existant in Arch. Just keep running "pacman -Syu" and you are always updated!

Besides that, Arch is very fast. It can easily run Gnome in my old P3 700MHz laptop with 128MB RAM. Ubuntu - even Xubuntu - are *too* slow and always lock up and crash under that setup. Arch runs pretty fast, even when running Firefox, downloading a torrent and watching an XviD movie at the same time. :)

The only small drawback is the setup. You have to setup everything yourself, including X, Gnome, Alsa etc. Heck, I even added Arch art work myself. :)
However it is very simple. And by saying simple I don't mean the Ubuntu way but the Arch KISS way. The structure of the OS and the config files is so easy that if you have basic Linux knowledge and use the wiki you can configure everything yourself. In my first Arch install I had Gnome running in under 1 hour (excluding the download time) and when it was finished I had this nice feeling that I had achieved something! :) (and imagine I've even installed Gentoo).

Last but not least here is my brand new Arch laptop using Gnome with Deviant Metacity and GTK themes:


[[img]http://www.divshare.com/img/thumb/1902877-192.png[/img]](http://www.divshare.com/download/1902877-192)

---

### Post by K.Mandla on 2007-09-11
Arch is spoiling my anticipation for Gutsy. 

I'm used to Kazehakase 0.4.8 and Openbox 3.4.4, and the idea of dropping back when Gutsy arrives is not enticing. Yes, I could install those externally, from the OB site or by recompiling, but still ... I appear to be addicted to a rolling release. :|

---

### Post by AriciU on 2007-09-11
After trying almost all major distro's out there (ubuntu, debian, slackware, gentoo, fedora, etc) i've finally switched from Slackware 12 to Arch. 

It has the Slack simplicity + pacman (awesome package manager) + more speed. Love it!

---

### Post by 5-HT on 2007-09-12
> **fwojciec said:**
> make sure to look at /var/log/Xorg.0.log and check for any errors (EE) and warnings (WW).  Most likely you will have to adjust one or two things - like font paths for example - to make everything work correctly in Arch.
Thanks for the tip! There were a few errors and warnings that I wasn't aware of.

---

### Post by fwojciec on 2007-09-12
5-HT: sure thing :)
K.Mandla:  I feel your pain... When I discovered Arch I was testing Feisty and, sure enough, by the time Feisty was officially released Arch was already miles ahead in terms of what versions of software were available.  I agree, rolling release system, especially the way Arch implements it, is like crack cocaine ;)  Once you get hooked it's difficult to go back.  I think that maybe one day, when I have matured sufficiently to be a tad more pragmatic in my attitude towards computers, I'm likely to settle for a more stable distro (Slackware?) that simply does what I want it to do but without the (not all that unpleasant) chore of daily updates and other turbulences that go along with the bleeding edge approach.  I digress... Maybe dual booting is the answer for you?

---

### Post by K.Mandla on 2007-09-12
> **fwojciec said:**
> Maybe dual booting is the answer for you?
Even better ... two computers! One Arch, one Feisty! :mrgreen:

---

### Post by EndPerform on 2007-09-12
> **K.Mandla said:**
> Arch is spoiling my anticipation for Gutsy. 

I'm used to Kazehakase 0.4.8 and Openbox 3.4.4, and the idea of dropping back when Gutsy arrives is not enticing. Yes, I could install those externally, from the OB site or by recompiling, but still ... I appear to be addicted to a rolling release. :|

It spoiled me already.  I switched my desktop from Gutsy dev to arch, and now I don't even plan on looking back.  I'll still have Ubuntu at work, though :)

---

### Post by bodhi.zazen on 2007-09-12
I have been rotating my distro every 6 months just to get a deeper feel for what each has to offer. I am finding that I miss arch though for all there reasons that have been stated ...

FYI ~ A little off topic , but for those that like slackware and pacman, you might want to check out Frugal :

[http://frugalware.org/](http://frugalware.org/)

It has been a while since I ran Frugal, but I enjoyed it the last time I looked.

---

### Post by kellemes on 2007-09-12
> **bodhi.zazen said:**
> .. for those that like slackware and pacman, you might want to check out Frugal :

[http://frugalware.org/](http://frugalware.org/)

It has been a while since I ran Frugal, but I enjoyed it the last time I looked.

Yeah, this will be my next endeavour..

---

### Post by bodhi.zazen on 2007-09-12
Oh, I came across this link , it is an alternate install guide.

Looks very nice :

[YAALIG = Yet Another Arch Linux Install Guide](http://www.my-guides.net/en/content/view/49/26/)

I like the organization :)

# For example :
# On the Daemons page is a hint for how to speed boot times by adding an @ in the front of a deamon with advice on which ones to add this to.

---

### Post by afonic on 2007-09-13
My review for Arch:

[http://www.dvd-guides.com/content/view/212/104/](http://www.dvd-guides.com/content/view/212/104/)

:)

---

### Post by epimer on 2007-09-13
That was a well-written review. afonic.

I just switched to Arch last week, and I'm very much liking having a much lighter, more customised system.

---

### Post by bodhi.zazen on 2007-09-13
An easier way to install Arch :

[http://user-contributions.org/wikis/userwiki/index.php?title=Arch_Linux_Office_Install_CD](http://user-contributions.org/wikis/userwiki/index.php?title=Arch_Linux_Office_Install_CD)

Have any of you tried this or advised it to new arch users ?

---

### Post by eyelessfade on 2007-09-13
Arch: Bin there done that. Used it for 1 1/2 years before moving to (k)ubuntu. And why did I switch?. Because it is horrible unstable. It was even more unstable then debian sid, which I used until glibc broke ^^

Arch has a nice package system. But it doesn't help when they roll out packages which breaks X, or even worse the entire system. I know a lot of people who ran arch, but had to switch because the unstable nature of the distro.

Gentoo was more fun, although I finally got tired of waiting hours for a simple upgrade. Maybe I will try it again someday, if I get a core2quad or something :)

---

### Post by bodhi.zazen on 2007-09-13
I have heard of people running into problems with Arch, but honestly I find it to be very stable, as much so as any of the major distor's.

I can not think of a single distro that has not had problems you describe.

My experience has been that updating with any distro has some risk and if I were updating a production server yo bet I would do be cautious and perform a system backup first.

With Arch I have had problems with isolated packages, but never any major problem I could not resolve with a brief visit to the forums. 

I would have to disagree that Arch is any more or less stable then any other distro with the exception of Slackware ...

---

### Post by afonic on 2007-09-13
> **eyelessfade said:**
> 
Arch has a nice package system. But it doesn't help when they roll out packages which breaks X, or even worse the entire system. I know a lot of people who ran arch, but had to switch because the unstable nature of the distro.


Ubuntu had a problematic update that broke X as well. In Arch if something like that happens you can roll back by installing the older version of the package kept in the pacman cache.

> An easier way to install Arch :

[http://user-contributions.org/wikis/...ice_Install_CD](http://user-contributions.org/wikis/...ice_Install_CD)

Have any of you tried this or advised it to new arch users ?

I won't suggest such an install way. If you want to use Arch you'll have to do it "the Arch way", learning how it works. Installing Arch like that and then trying to mess with rc.conf to setup CUPS has no meaning imo.

---

### Post by Rumor on 2007-09-13
I've been an Arch user for about a year and have had no problems with stability. None of the upgrades have broken X, and maintaining my nVidia drivers has been much easier with Arch than it was with Ubuntu; upgrades for which frequently broke X.

You can make your system as stable / unstable as you wish by enabling the testing and/or unstable repositories. I have not had any issues with the packages in the testing repo. Of course, your mileage may vary :-)

---

### Post by kellemes on 2007-09-13
> **Rumor said:**
> I've been an Arch user for about a year and have had no problems with stability. None of the upgrades have broken X, and maintaining my nVidia drivers has been much easier with Arch than it was with Ubuntu; upgrades for which frequently broke X.

You can make your system as stable / unstable as you wish by enabling the testing and/or unstable repositories. I have not had any issues with the packages in the testing repo. Of course, your mileage may vary :-)

Same here..
Haven't had stability-issues at all.. Arch is very transparent and thereby it's easy to keep an eye on system-essential packages and see to it they don't break, and if they do.. there is no challenge in fixing it.
I respect distro's like Ubuntu, but for most Ubuntu'rs it seems a lot harder to maintain there system as it is for Archers to maintain there's.

---

### Post by afonic on 2007-09-13
Their kernel update system should be better though. They install the new kernel in the place of the old one, not even leaving two of them in parallel. So in case the new kernel does not boot you need to use the install CD to fix it.

---

### Post by pelle.k on 2007-09-13
> **afonic said:**
> Their kernel update system should be better though. They install the new kernel in the place of the old one, not even leaving two of them in parallel. So in case the new kernel does not boot you need to use the install CD to fix it.

That is true, however, booting your installation with the kernel from the cd, is a piece of cake, and from there, it's just a matter of installing the old kernel from the package cache (or the install cd). I think it's rather elegant.
Also, you could easily have another kernel install beside your standard kernel, like the "ck" or "suspend" flavor, kept in "IgnorePkg" (pacman.conf) when you upgrade. You could of course also compile your own "flavor" and have this installed just as a backup.

In either case, i see your point.

---

### Post by K.Mandla on 2007-09-15
I gave Lowarch a shot yesterday on my lowly 450Mhz K6-2. It was like a breath of fresh air. Fully 30 seconds faster to boot than a stripped Ubuntu. I loved it.

But the distro is stalled so badly that I'm working with six- and eight-month old packages. I'm considering recompiling a lot of stuff, but I'm not sure if it's worth the effort. 

Opinions? or should I just do my best with Gentoo?

---

### Post by K.Mandla on 2007-09-15
By the way, I don't know if anyone noticed or not, but xorg is no longer a metapackage. You have to install the subpackages individually.

```
# pacman -Sy xorg-server xorg-xinit xf86-input-{mouse,keyboard} xf86-video-<mycard> xorg-fonts-<mydpi>
# X -configure
# $EDITOR xorg.conf.new
# mv xorg.conf.new /etc/X11/xorg.conf
```
[http://bbs.archlinux.org/viewtopic.php?id=37062](http://bbs.archlinux.org/viewtopic.php?id=37062)
(Warning: Very mean thread there. Sad.)

Personally I like it better that way, but I'm a rabid minimalist.

---

### Post by Pancetilla on 2007-09-15
> **K.Mandla said:**
> [http://bbs.archlinux.org/viewtopic.php?id=37062](http://bbs.archlinux.org/viewtopic.php?id=37062)
(Warning: Very mean thread there. Sad.)

:popcorn:

Anyway

I have installed xorg using pacman -S xorg and recently using the whole thing (pacman _S xorg-server et al.l). It's the same to me (begginer-intermediate user), both ways work flawless. But maybe the xorg group package mantainer should have passed (or tried to pass) the task of mantaining it to another guy before removing it instead of vanishing after one single post in the forums.

---

### Post by afonic on 2007-09-15
> **K.Mandla said:**
> By the way, I don't know if anyone noticed or not, but xorg is no longer a metapackage. You have to install the subpackages individually.

```
# pacman -Sy xorg-server xorg-xinit xf86-input-{mouse,keyboard} xf86-video-<mycard> xorg-fonts-<mydpi>
# X -configure
# $EDITOR xorg.conf.new
# mv xorg.conf.new /etc/X11/xorg.conf
```
[http://bbs.archlinux.org/viewtopic.php?id=37062](http://bbs.archlinux.org/viewtopic.php?id=37062)
(Warning: Very mean thread there. Sad.)

Personally I like it better that way, but I'm a rabid minimalist.

Very sad thread indeed. Especially the user that said "it was relly fast to install arch...now its verrrryyy borring" I don't know if I should laugh or cry. :S

I don't agree with that change though, from what I've seen that xorg group pulled just the basics you need plus the vesa drivers. (just what you'd install anyway), so I don't think it changed something except the user using the keyboard a bit more. :P

---

### Post by ynnhoj on 2007-09-15
> **K.Mandla said:**
> [http://bbs.archlinux.org/viewtopic.php?id=37062](http://bbs.archlinux.org/viewtopic.php?id=37062)
(Warning: Very mean thread there. Sad.)
yeesh, what a mess.  it doesn't seem like such a big deal to me :confused:

---

### Post by finferflu on 2007-09-15
I don't see anything sad about that thread. In every forum there are people who complain arrogantly, but it's nice to see how the people in charge (developers and moderators) dealt with the situation. They had very cool spirits, and every attempt to create flames has been extinguished quickly. I think it's something that indicates the maturity of the people over there.

I don't agree with the decision to remove the Xorg metapackage without thinking ahead to prevent possible problems with dependencies. I think everyone makes mistakes, and disagreement between developers in such cases is quite healthy. 
I actually don't know whether this has been fixed yet, since I don't need to install any Xorg-related stuff at the moment...

---

### Post by regomodo on 2007-09-15
ah, i've just returned to Arch and i've spotted the typo in the "Official Arch Linux Install Guide". Wherever it says /etc/mkinitrd.conf  it should actually say /etc/mkinitcpio.conf

Correct me if i'm wrong

---

### Post by regomodo on 2007-09-15
grrr! Pacman is p**sing me off again

i've added the cdrom packages to my pacman.conf and mounted the cd

when i run find from the cd in terminal i see all the packages but $pacman -Sy just returns loads of errors

---

### Post by regomodo on 2007-09-15
sod it. Without internet access/cd repo working properly this is pure hell going package by package due to dependencies

---

### Post by fwojciec on 2007-09-15
> **regomodo said:**
> ah, i've just returned to Arch and i've spotted the typo in the "Official Arch Linux Install Guide". Wherever it says /etc/mkinitrd.conf  it should actually say /etc/mkinitcpio.conf

Correct me if i'm wrong

Could you give me a link?  if this is true, then the wiki needs to be updated - I'll be happy to have a look.
Nevermind: found it...

Edit: Note that the official install guide is for 0.7.2 (gimmick) version, which is pretty old...  I agree that it should be updated, but it seems like a bigger project, so it might take a while before it gets done.  Meanwhile I'd suggest using the [Beginners Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide#Configure_The_System") instead - it is less comprehensive as far as installation instructions are concerned (but sufficient for most situations, IMO) but it does seem more up to date.

---

### Post by regomodo on 2007-09-15
hmmph. Another wiki error.

When it explains how to edit /etc/pacman.conf to add the cd repo it states

add the lines

[cd] Server = file:///mnt/cd/arch/pkg

well. It should be

[current]
Server = file:///mnt/cdrom/arch/pkg


The cd/cdrom difference is due to my fstab though

lol. It has no idea what the lspci command means

---

### Post by regomodo on 2007-09-15
> **fwojciec said:**
> Could you give me a link?  if this is true, then the wiki needs to be updated - I'll be happy to have a look.
Nevermind: found it...

Edit: Note that the official install guide is for 7.2 (gimmick) version, which is pretty old...  I agree that it should be updated, but it seems like a bigger project, so it might take a while before it gets done.  Meanwhile I'd suggest using the [Beginners Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide#Configure_The_System") instead - it is less comprehensive as far as installation instructions are concerned (but sufficient for most situations, IMO) but it does seem more up to date.

hi ,cheers for the reply. I am currently going between the 2 guides. I was looking at the "Official Arch.." as the beginners guide just glazed over the use of Pacman

---

### Post by fwojciec on 2007-09-15
> **regomodo said:**
> hi ,cheers for the reply. I am currently going between the 2 guides. I was looking at the "Official Arch.." as the beginners guide just glazed over the use of Pacman

Well, it looks like you're managing OK in spite of the wiki inaccuracies.  Good luck with the remainder of the installation!

---

### Post by pelle.k on 2007-09-15
regomodo;

I have, in fact, already told you this in this very thread, answering one of your complaints about arch linux. Let me quote myself;

> I will agree that this would probably not work though. I guess the changes in pacman V3 probably rendered that advice useless. You're supposed to name the [repository] after the database file in the directory your pointing to. In this case it's named current.db.tar.gz on the install cd, and since that is also true of the original repo, you can just as well put
Code:

Server = file:///mnt/cd/arch/pkg

just below the existing [current] in /etc/pacman.conf (temporarily, since pacman will replace the real repo for the cd until you remove this modification)
This entry will be primary even if you have an "Include = " below it.


I have now updated this section of the guide to be in sync with reality. :)
Oh, and since this is a _WIKI_, you may also go ahead and register yourself, and correct these sorts of errors, just as i did.

---

### Post by regomodo on 2007-09-16
> **pelle.k said:**
> regomodo;

I have, in fact, already told you this in this very thread, answering one of your complaints about arch linux. Let me quote myself;



I have now updated this section of the guide to be in sync with reality. :)
Oh, and since this is a _WIKI_, you may also go ahead and register yourself, and correct these sorts of errors, just as i did.

sorry pelle. I have a tendency to skim read or do things when i should be asleep (brain turns to a sponge). About the wiki editing, you have to be a registered member at the arch forums, which i recently became. I found another few typos in the RT61 arch wiki which i found rather hopeless for me and have created my own scripts to setup my wireless with wpa.

Anyways, Archlinux is awesome, especially with KDE-Mod. My 440MHz Thinkpad flies. Just need to sort out my sound issues and then i'm finished. It's a little memory consuming but it's what i expect with KDE

---

### Post by fwojciec on 2007-09-16
> **regomodo said:**
> sorry pelle. I have a tendency to skim read or do things when i should be asleep (brain turns to a sponge). About the wiki editing, you have to be a registered member at the arch forums, which i recently became. I found another few typos in the RT61 arch wiki which i found rather hopeless for me and have created my own scripts to setup my wireless with wpa.

Anyways, Archlinux is awesome, especially with KDE-Mod. My 440MHz Thinkpad flies. Just need to sort out my sound issues and then i'm finished. It's a little memory consuming but it's what i expect with KDE

I think the wiki account is separate from the forums one, but anyone can register, of course...

When the memory issue starts bugging you try Openbox or something like that ;)  When my laptop boots it uses something something like 65MB or ram, I'm under/around 100MBs with Firefox running - and it's not even a particularly optimized or ascetic setup (all visual bells and whistles, desktop search enabled, all necessary daemons in place, etc.).

Enjoy Arch!

---

### Post by afonic on 2007-09-16
I am at 130MB with Gnome, Exaile, Firefox and Apache/PHP/MySQL running.

---

### Post by pelle.k on 2007-09-16
> It's a little memory consuming but it's what i expect with KDE
I've noticed that "system monitor" in gnome show you the real value of free memory, but the equivalent in kde show it with cached memory, and thus you might do an unfair comparison.
Use "free" instead, and note the line;
```
-/+ buffers/cache:
``` which should give you an approximation of the "real" values.

---

### Post by regomodo on 2007-09-16
it's not really the issue of KDE (fresh boot) being memory hogging, it's just some of the apps that KDE uses as default (i think). I'm not too bothered as i have 320MB to play with, just as long as they aren't slow to startup/use.

At a fresh boot and logged in memory usage is ~55MB. I use htop and don't care much for the inbuilt system monitors on DE's

I found out why i had no sound. I had forgotten to add my username to the audio group. Duh.

---

### Post by K.Mandla on 2007-09-18
Did everybody switch to the core repository?

---

### Post by epimer on 2007-09-18
Yep!

</useful post>

---

### Post by Rumor on 2007-09-18
Yep, switched on three computers with no problems. I don't know if it was necessary, but I commented out all the repositories in /etc/pacman.d/core file that I won't be using. Probably it does not make any difference.

---

### Post by afonic on 2007-09-18
> **Rumor said:**
> Yep, switched on three computers with no problems. I don't know if it was necessary, but I commented out all the repositories in /etc/pacman.d/core file that I won't be using. Probably it does not make any difference.

It goes make pacman run faster I think.

---

### Post by Ramses de Norre on 2007-09-19
> **afonic said:**
> It goes make pacman run faster I think.

You mean if you drop most of the "Server" lines? There's a little term-confusing here... Core is the repository and in /etc/pacman.d/core you define the servers to download the packages from that repo from. It wont make a difference whether the file is big or not because pacman will just use the first server and only if that one doesn't work it'll use the second and so on. Deleting those servers wont make pacman faster, it'll just give you less certainty a file will get downloaded even if it's corrupted on your first-choice mirror.

---

### Post by afonic on 2007-09-19
I made quite a weird sentence there. :)

Yes you should use the rankmirror script to select the fastest server and keep just that enabled afaik.

---

### Post by fwojciec on 2007-09-23
For those who can't wait for xorg-server 1.4, it has just appeared in the testing repo.  I will need to make that upgrade at some stage in either case so I decided to try it to see how it works.  It is potentially a quirky upgrade so it's best to read a bit before upgrading, by the way.

For me it all works great with the latest nvidia drivers.  I had a minor problem with the symantic touchpad on my laptop, but that simply required changes to some entries in the xorg.conf file, and there is a solution posted on Arch forums in case anybody encounters this problem.

I don't use Compiz at the moment, so I don't know if much is improved in terms of performance, but it has been completely stable since I have installed it yesterday.  

I'm not getting rid of my xorg.conf file yet, by the way ;)

---

### Post by regomodo on 2007-09-23
Well, i've played with Archlinux for about a week now and i'm noticing hardly any benefits. KDEMOD works quickly and so does openbox however, a Debian Etch Gnome/Openbox setup works at equally the same amount of RAM and responsiveness with less setup issues. 

I think my main issue is with Udev Uevents. From a bare install it takes forever (~20seconds) to get through it. Bootchart reports that it takes ~85secs to boot up to KDM (which is frankly **** and i haven't added much). I can't knock the shutdown time, if running from the terminal. About 8secs to shutdown if i use the terminal. However, if i use the Shutdown/Restart option in KDEMOD it waits ~15secs before it does what i ask it to.

One last thing (and i don't know if it's Archlinux's fault) is that whole load of modules are loaded which are totally unrelated to my Laptop (even though i blacklist them in rc.conf). It could be a kernel thing but i have yet to create a successful custom kernel out of 5 attempts for Debian/Ubuntu/Arch.

FWIW I think I may go back to Debian or buy the LFS book (i feel Puppy/DSL is a bit of a con).

I do like pacman though. I much prefer it to apt/aptitude. Makes a whole lot more sense.

---

### Post by K.Mandla on 2007-09-24
If you turn off module autoloading you can tell it which modules to insert. That's what I do and it generally gives a speed improvement at boot time.

85 seconds to KDM is whacked. I'm getting 27 seconds from grub to desktop in Openbox, with no login manager, and that's a 1Ghz machine.

udev uevents is horrid, for me. I get the same 20-25 second lag while it does its thing. There used to be a flag you could tack onto the /etc/start_udev script that trimmed the default timeout way down. Look for the line that calls udevsettle, and set the timeout flag.

```
/sbin/udevsettle --timeout=5
```
It can shave down the boot time, but maybe one time out of four, the partitions won't mount before the timeout and so the system is unbootable, and you have to cycle the power. Not the best solution, but it can help.

I don't know of many other ways to avoid udev uevents. It's a shame it doesn't move a little faster.

---

### Post by K.Mandla on 2007-09-24
> **fwojciec said:**
> For those who can't wait for xorg-server 1.4, it has just appeared in the testing repo. ...
I haven't been following this; what's the benefit to 1.4 over the old version?

---

### Post by miggols99 on 2007-09-24
I've heard that it improves Compiz Fusion/Beryl's perfomance greatly. It also means some of your xorg.conf is not needed and will be detected automatically. I'm still waiting for the open source ATI driver with AIGLX...

---

### Post by regomodo on 2007-09-24
> **K.Mandla said:**
> If you turn off module autoloading you can tell it which modules to insert. That's what I do and it generally gives a speed improvement at boot time.
.

I have tried that. turning off the module autoloading and specifying the  necessary modules seemed to make any difference. Udev uevents still popped up and hung about for a bit. I know it was switched off as i lost the use of my trackpoint.

I'm curious how Puppy linux is quick to boot.

---

### Post by fwojciec on 2007-09-24
> **K.Mandla said:**
> I haven't been following this; what's the benefit to 1.4 over the old version?

My sense is that xorg is trying to become much better as far as detecting hot-pluggable devices (mice, monitors end such) is concerned.  With this release the xorg.conf file becomes "partially obsolete," though you still can and in many cases have to define particular settings there.  There are other significant changes such as new API for drivers, which brakes backwards compatibility in some cases, but also things such as a new "intel" driver which replaces "i810" among other things.  Like I said, a potentially quirky upgrade, though it went very smoothly here.

I don't know about particular benefits, I tend to think of the upgrade as inevitable at some stage, probably soon, so I thought I'd get my system ready for it that's all.  As far as performance is concerned - it performs good, just like the previous version :)  With Openbox I wouldn't be able to tell the difference anyways - it's always very fast here.

---

### Post by K.Mandla on 2007-09-24
Cool. Thanks everybody.

---

### Post by stlouis1 on 2007-10-02
well, i can't sit here and honestly say that i read through all 28 pages, i did read through the first 3 pages though.

anyway, figured id post that i've been using arch for almost 2 months now. i started using linux again about 4 months ago on my laptop. when i stumbled upon arch on the amarok site i did some reading on it. i checked out the repos to find that all the programs i've found over previous linux experience as windows alternatives for everything i use my computers for were available for arch, most were much newer than what was available for ubuntu that id been using for 2 months already. 

previously i mostly used fedora and found with ubuntu that everything i needed was working nicely which is probly what kept me motivated to using linux, so not a bad thing. im a microsoft guy, quite literally, i work for microsoft. but i guess i needed something different at home.

anyway, i ended up downloading arch that night i was reading about it (at work) and installed it on my test system. i had been planning on moving my main desktop to linux. honestly i found arch a little intimidating, but i had my mind set on what i needed, what programs i needed, so once i got around adjusting to a few differences it wasn't bad. the setup itself worried me being all text based and all, i was crossing my fingers for most of it. then when it brough me to a text login screen i thought i forgot something (didn't read enough in the wiki). but once i got passed that and figured out how to build packages from the unsupported repo, i was banging my head on the desk it was so easy.

currently my desktop was finally switched over roughty a month ago to arch 64 bit and loving it, few little things that still need tuning and some things that are a little different from the 32bit version. i'm liking it so much that i even ditched my ubuntu install on my laptop and put arch on there. up and running in about 90 minutes, fully set up, but i knew what i was doing at that point.

one thing i like about arch is definitely the speed. but i like the customized kde, kdemod. in kubuntu i was deleting k-menu shortcuts to hide all the components i didn't want but couldnt remove. i like arch, i'm not exactly new to linux, i've used it a fair bit over the last 2 years, but im new to linux, and that hasnt stopped me from loving arch even though i've found some challenges. i've had people on other forums tell me i make linux look easy, i found that amusing. if i make linux look easy, anyone can i tihnk

it beats having windows all the time, windows is just windows to me. no matter how many new versions of windows MS brings out, its still the same old windows, few things moved around, so updated and so called new features, its all the same troubleshooting at work. nothings ever really new

anyway, thats my 2c

---

### Post by manmower on 2007-10-02
stlouis1, I think yours is a familiar story among Arch users. Intimidated at first, but armed with the excellent guides from the wiki and the will to really learn how things work, you take the plunge and stop looking for anything else once you've discovered the speed and ease of Arch.

I'm so glad I tried Arch about a year ago, I was almost ready to give up on GNU/Linux altogether due to every single distribution having some sort of issue that really irked me. The most daunting bit when first installing Arch was configuring wireless internet (which is the only way my desktop connects to the net) entirely from CLI. But one evening I just went ahead with it and to my surprise, got it done quite rapidly and for the first time I actually had the feeling of truly knowing what I was doing as opposed to copying commands from a how-to. It's a feeling I've since experienced a lot while using Arch and I'm happier for it. Thanks to what I've learned from Arch, I think I could now pretty much use any distro to my satisfaction, but none offer the same combination of great features.

Especially now that [Judd is leaving](http://archlinux.org/news/350/), this seems like a good time to recall what a fantastic collection of software Arch really is.

---

### Post by ynnhoj on 2007-10-02
wow, thanks for pointing out that bit of news manmower.  i probably would have missed it.

---

### Post by Rumor on 2007-10-02
> **manmower said:**
> I'm so glad I tried Arch about a year ago, I was almost ready to give up on GNU/Linux altogether due to every single distribution having some sort of issue that really irked me. The most daunting bit when first installing Arch was configuring wireless internet (which is the only way my desktop connects to the net) entirely from CLI. But one evening I just went ahead with it and to my surprise, got it done quite rapidly and for the first time I actually had the feeling of truly knowing what I was doing as opposed to copying commands from a how-to. It's a feeling I've since experienced a lot while using Arch and I'm happier for it. Thanks to what I've learned from Arch, I think I could now pretty much use any distro to my satisfaction, but none offer the same combination of great features.

I can echo almost everything you've said here. I switched from Windows only to Linux only with Ubuntu 5.10 almost two year ago. When 6.06 was released, I upgraded (***very*** apprehensively). I repeated that process with 6.10. The monolithic upgrades frustrated me. The periodic upgrades also caused me a lot of frustration. Every time I saw that the restricted sources were being upgraded, I knew my X was going to break because I was using the most recent nVidia drivers. I don't know how many times I reinstalled Ubuntu (probably needlessly at times, I now realize).

During that period of time, I heard about Arch Linux in a podcast and I began trying to find information about it. I read this interview: [http://www.osnews.com/story.php/10142/The-Big-Arch-Linux-Interview/page1/](http://www.osnews.com/story.php/10142/The-Big-Arch-Linux-Interview/page1/) and was intrigued. I was absolutely riveted by what one of the developers said on the first page: 
> **Damir Perisa:** I run ArchLinux since 0.4 and since then i never had to reinstall the OS on this laptop. Besides no need to reinstall it, i have always the latest versions of software i need.
Never had to reinstall...

I installed Arch 0.72 Gimmick and for a long time I dual booted Ubuntu and Arch. When Ubuntu 7.04 was released, I backed up my files, redid all my hard drive partitions and installed Arch only. I've not looked back, nor have I had to reinstall my OS.

Well, that's not true, I had to reinstall it when I built my new system a couple months ago, but I do not foresee doing so again for a long time to come.

---

### Post by stlouis1 on 2007-10-02
> **manmower said:**
> stlouis1, I think yours is a familiar story among Arch users. Intimidated at first, but armed with the excellent guides from the wiki and the will to really learn how things work, you take the plunge and stop looking for anything else once you've discovered the speed and ease of Arch.

I'm so glad I tried Arch about a year ago, I was almost ready to give up on GNU/Linux altogether due to every single distribution having some sort of issue that really irked me. The most daunting bit when first installing Arch was configuring wireless internet (which is the only way my desktop connects to the net) entirely from CLI. But one evening I just went ahead with it and to my surprise, got it done quite rapidly and for the first time I actually had the feeling of truly knowing what I was doing as opposed to copying commands from a how-to. It's a feeling I've since experienced a lot while using Arch and I'm happier for it. Thanks to what I've learned from Arch, I think I could now pretty much use any distro to my satisfaction, but none offer the same combination of great features.

Especially now that [Judd is leaving](http://archlinux.org/news/350/), this seems like a good time to recall what a fantastic collection of software Arch really is.

i definitely think arch is the distro i learned the most from for sure since it forced me to do a little more configuring on the back end rather than using front end tools for everything. with other distros, i found just like you i was copying commands from guides and really have no idea whats happening. since i switched to arch, i know what im doing when i copy an "ln something something" command and know where my configuration files for my network settings are and know what someones talking about when they tell me to add a line to /etc/rc.conf or something.

so im continuing to use arch, fedora and (k)ubuntu definitely helped me get my feet in the water....but i think arch is the distro i learned the most from and will continue to learn from.

even one of my supers at work was saying he wanted to start toying with linux, i gave him some iso's of knoppix, dsl, arch, kubuntu, fedora and suse. he's using kubuntu right now to get a feel, but i think he'll be going to arch soon enough since i keep praising it so much

one thing though that i personally disagree with, is everyones comments about the arch wiki being so great. i find theres alot of info there, but i have found some of it to be a little vague at least maybe to less experience users. i could be wrong. but it is handled by the community and not everybody is great when it comes to writting documentation, but some info is always better than no info. and the wiki was definitely helpful, but some of it i still had to post on the arch forum to clarify some of it. that might just be me though. if i was any more knowledgable i'd try to contribute to the wiki myself, and i could go back through and submit content to maybe clarify some of the stuff that i found a little vague for the next person

like i said, i do work for microsoft, and some of the internal articles we use there are pretty vague and alot of articles are missing steps. i just finished training for tier 2 though, im hoping to get on the bug team where i could work with fixing of adding knowledge base content

---

### Post by K.Mandla on 2007-10-03
Big +1 to all these posts. 

And thanks for the news about Judd leaving. I hadn't seen that, since I'm offline for the next week or so (it's my own fault :( ). 

Phrakture is a good choice for a new overlord. Kneel before Zod!

---

### Post by drum on 2007-10-03
I too have been running arch on my main box and 2 laptops, A Thinkpad T61 and a Lenovo 3000/100 for the last 6 months and I think it has moved me up from a noob to a little below an intermediate user. :cool:
I got nvidia working and wireless and everything is so stable.
I can't give enough praises for arch. It's just so much fun to keep it up to date and learn all the little tweaks which you can find on their forums etc.
regards
:)

---

### Post by regomodo on 2007-10-03
I've switched to Arch for my desktop. I've seen the light and realised what Ubuntu is. I'm still going to keep using Debian Etch though on my lappy. Arch didn't want to play ball with it unfortunately.

---

### Post by Dimitriid on 2007-10-04
You guys sold me im installing as we speak. I used my ubuntu live cd and gparted to create a nice ext3 40gb partition for it. Now a question: I made a second primary partition, no need to format just need to point arch to mount / and /home there. But after I am done with that, do I need to install grub? Or should I just modify grub in ubuntu to add a line for Arch? Im guessing the second one but i'd like to confirm.

---

### Post by 5-HT on 2007-10-04
> **Dimitriid said:**
>  Im guessing the second one but i'd like to confirm.
Including a boot option for Arch in your Ubuntu menu.lst will do the trick. Arch by default also includes a fallback initrd image (allowing you to customize your default one), and it might be a good idea to include that as well.
I'm away from my Arch box now, but I can post a sample for you in a few hours when I get to it.

If you decide to just keep your existing grub setup, it would be best to avoid installing the bootloader in Arch (it's a separate option in the installer) or else you'll need to 1)just add ubuntu's options to your arch menu.lst, or 2) setup grub to  point to your Ubuntu root again.

cheers,

---

### Post by fwojciec on 2007-10-04
The second option should work fine.  The Arch grub entry for the default kernel should look something like this:

> # (1) Arch Linux
title  Arch Linux
root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/sdb5 ro vga=775
initrd /boot/kernel26.img
savedefault

# (2) Arch Linux Fallback
title  Arch Linux Fallback
root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/sdb5 ro vga=775
initrd /boot/kernel26-fallback.img

Obviously root device and vga= parameter need to be adjusted appropriately.  I also use the "savedefault" option, but it can be skipped if you don't need it.

Once you're done installing [Beginners Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") and [Arch Wiki]("http://wiki.archlinux.org/index.php/Main_Page") more generally are going to be your best friends so make sure you use them - even if you're not a beginner ;)

Welcome to Arch!

---

### Post by Dimitriid on 2007-10-04
Ok i got a bunch of errors, not sure if I selected the wrong partition or what but I get:

> 
Attempting to create root device '/dev/sdb5'
ERROR: Failed to parse block device name for '/dev/sdb5'
unknown
ERROR: Root fs cannot be detected. Try using the rootfstype= Kernel parameter.
Waiting for devices to settle...done.

Root device '/dev/sda5' doesn't exist, attempting to create it
ERROR: Failed to parse block device name for '/dev/sdb5'
ERROR: Unable to create/detect root device '/dev/sdb5'
Dropping to a recovery shell... type 'exit' to reboot
NOTE: klibc contains no 'ls' binary, use 'echo *' instead


Any clue what am i doing wrong?

---

### Post by fwojciec on 2007-10-04
What device (/dev/???) did you install Arch on?  And could you post what your customized Arch grub entry looks like?

---

### Post by Dimitriid on 2007-10-05
Its on /dev/sda3, primary and only IDE hdd so I believe it should be hd0,2 ?

Here's the entry I added for grub
> # (1) Arch Linux
title Arch Linux
root (hd0,2)
kernel /boot/vmlinuz26 root=/dev/sdb5 ro vga=0x317
initrd /boot/kernel26.img
savedefault

# (2) Arch Linux Fallback
title Arch Linux Fallback
root (hd0,2)
kernel /boot/vmlinuz26 root=/dev/sdb5 ro vga=775
initrd /boot/kernel26-fallback.img

One note though, I did mount this partition on ubuntu for a second a few boots ago and asked me for password, now it is not asking and just mounting....Is ubuntu taking over it perhaps? If so what to do short of starting the install over?

]

---

### Post by fwojciec on 2007-10-05
> # (1) Arch Linux
title Arch Linux
root (hd0,2)
kernel /boot/vmlinuz26 root=/dev/**sda3** ro vga=**773**
initrd /boot/kernel26.img
savedefault

# (2) Arch Linux Fallback
title Arch Linux Fallback
root (hd0,2)
kernel /boot/vmlinuz26 root=/dev/**sda3** ro vga=**773**
initrd /boot/kernel26-fallback.img

Try this.  Changes are in bold.  BTW, I've also changed the vga parameter, it should give you 1024x768 in 256 colors (you don't need more colors for framebuffer anyways).

---

### Post by Dimitriid on 2007-10-05
Ah yes of course! I changed one partition to point out to mine but now the other, I feel kinda dumb no ](*,)

Now im in root, time to make my account, get xorg and a WM. Debating between kdemod or just fluxbox atm.

---

### Post by fwojciec on 2007-10-05
> **Dimitriid said:**
> Ah yes of course! I changed one partition to point out to mine but now the other, I feel kinda dumb no ](*,)

Now im in root, time to make my account, get xorg and a WM. Debating between kdemod or just fluxbox atm.

Yay! :)

So now the adventure begins!  Take your time setting things up, read the wiki, and watch your appreciation of the genius of Linux grow :)  

You might want to set up an account on Arch forums as well, as you likely to run into problems every once in a while - things are moving a bit slower there than here usually, but it should be easier to find help there if you need it.

Have fun!

---

### Post by 5-HT on 2007-10-05
> **Dimitriid said:**
> 
Now im in root, time to make my account, get xorg and a WM. Debating between kdemod or just fluxbox atm.

Glad you got it. As for your user account, you may want to take a look at the 'groups' wiki page to see which groups your user should be a part of (optical, network, etc...) When I first installed suspend wasn't working and it ended up that I forgot to add myself to the power group.
cheers,

---

### Post by Pancetilla on 2007-10-05
> Now im in root, time to make my account, get xorg and a WM. Debating between kdemod or just fluxbox atm.

Kdemod is great.  It's a good way to install kde without all those kapplications you won't ever use, you'll only install what you need (being a gnome guy giving kde a try, this is a bless). It's faster and better, IMHO, than vanilla KDE...and maybe prettier too. Fluxbox is nice too, but Kdemod impressed me :guitar:

---

### Post by Dimitriid on 2007-10-05
I went for kdemod complete. Seems like a heavy download, but im sure it wont be on my system. Now with this one do I need to manually install some daemons like HAL and such?   Also this autoconfigures kdm to start up or should I do that manually?

I briefly tried fluxbox and while it looks nice but its a bit on the time consuming side, so though of trying kdemod for a while.

---

### Post by fwojciec on 2007-10-05
You need to set up the daemons manually - most things need to be configured manually in Arch, the distro philosophy is to install everything with default configuration (as the developers intended it to be) and let the user decide what he/she wants to do with it.

As far as KDEMod is concerned someone else will need to chime in.

---

### Post by Rumor on 2007-10-05
KDEMod Info here:: [http://kdemod.ath.cx/index.html](http://kdemod.ath.cx/index.html) I've only run it very briefly. I much prefer Gnome or Openbox.

As for your daemons, you'll need to set them up. You can start them manually with 
```
/etc/rc.d/*daemon_name* start|stop|restart
```
or you can put them into your /etc/rc.conf file such as
```
DAEMONS=(syslog-ng network netfs crond acpi sensors cups hal fam alsa ntp gdm)
```

In your case, you'd list **kdm** last if you want a graphical login.

---

### Post by pelle.k on 2007-10-05
> **Dimitriid said:**
> Now with this one do I need to manually install some daemons like HAL and such?   Also this autoconfigures kdm to start up or should I do that manually?.

Nothing is done automatically. You need "hal" if you wan't kde to mount stuff for you, etc (dbus is started as a depenency to hal automatically, so you won't have to start "dbus", unless you wan't it to run by itself, i.e without "hal")
And yes, you need the "kdm" daemon unless you coose another method to start it with...

You read the beginners guide, right? It will explain the basics to you.

---

### Post by Dimitriid on 2007-10-05
Alright thanks for the tips, got KDEmod and KDM ( and hal and fam ) set up and everything now. I used to swear by gnome and xfce but Arch + KDEmod feels so fast. You ever played a FPS game and saw an obvious speed hacker? Thats how it feels :guitar:

Im loving Arch, its so powerful and you have control of every single thing, even if you're just learning it feels like you are building your custom system just the way you like it.

---

### Post by K.Mandla on 2007-10-06
> **Rumor said:**
> KDEMod Info here:: [http://kdemod.ath.cx/index.html](http://kdemod.ath.cx/index.html) I've only run it very briefly. I much prefer Gnome or Openbox.
I tried it too, and I really liked it. If I wasn't completely infatuated with Openbox, KDEMod would definitely be my significant other.

---

### Post by finferflu on 2007-10-06
Not so Arch related, but using Arch I got into tiling WMs, so I really suggest you to try out Ratpoison, it's one of the most genial WM I've ever tried, and it's ultra lightweight too. Another one I suggest you is Xmonad. You'll not have a system tray icon, but when everything is tiled, what's the need of it? :)

---

### Post by leg on 2007-10-06
> **RAV TUX said:**
> Gentoo is not difficult at all to learn to use. No worries you'll be fine and the Gentoo Forums are very responsive and helpful(a lot like the Ubuntu forums here). Have fun.
 
I am sure you will be pleased.
Seconded. I also use Gentoo and I love it. It did take me a while to get the hang of but once you understand how to do things you won't look back.

---

### Post by kellemes on 2007-10-06
> **K.Mandla said:**
> 
And thanks for the news about Judd leaving. I hadn't seen that, since I'm offline for the next week or so (it's my own fault :( ). 

Phrakture is a good choice for a new overlord. Kneel before Zod!

Same here.. Just learned this news today..
I'm not worried, Arch has a small but very enthousiastic crew of developers and users, including myself.


[QUOTE=Dimitriid]
I went for kdemod complete. Seems like a heavy download, but im sure it wont be on my system. Now with this one do I need to manually install some daemons like HAL and such? Also this autoconfigures kdm to start up or should I do that manually?[/QUOTE]

If you need a login manager there are a couple of methods.. I'm currently on *another system* but as far as I remember I have it set in my ~/.xinitrc
(you can get a sample-file from /etc/skel/.xinitrc among other places)

If you need HAL you need to "pacman -S dbus hal" and add **hal** to daemonslist in /etc/rc.conf.

[COLOR="Red"]**Edit: Sorry Dimitriid, I didn't read your post about having setup KDM and KDEmod already..**[/COLOR]](*,)

---

### Post by Rumor on 2007-10-06
> **K.Mandla said:**
> I tried it too, and I really liked it. If I wasn't completely infatuated with Openbox, KDEMod would definitely be my significant other.

I've only recently gotten into OpenBox, setting it up on an older PC (pII/450 or so) with pypanel. I wanted to try ttm / tint but when I went to download it yesterday, all I could find was  a.deb file on the website. The last time I downloaded it, there was a link to the various bits of code.

I like the minimal lightweight feel of it. I downloaded the liberation font set and started using them and it really helped to make things much more attractive.

I think OpenBox and the various lightweight programs (abiword, kazehakase, sylpheed, etc.) makes for a really nice way to make older hardware realistically usable.

---

### Post by fwojciec on 2007-10-06
I don't think Openbox is only good for old hardware - I use it on both my laptop and my desktop (AMD X2 4400+ with good Nvidia card and so on) - it's not so much about speed or anything, Openbox it simply is my preferred way of organizing my desktop experience.  

Things that Openbox does extremely well:
+ impeccable twinveiw support (all windows/dialogue windows open where they should) - that's the big one for me
+ keyboard shortcuts for everything !!!
+ right click menu is a must once you get used to it
+ ability to define how particular windows are opened/displayed
+ everything controlled by a couple of easy to edit xml files
+ I would lie if I said that the fact that all window operations are pretty much immediate didn't matter to me :)

I imagine that it would be possible to realize what I have set up in Openbox by different means as well, but I also like how neatly it is all designed and how smoothly it all works...  I guess you could say that I've grown fond of Openbox ;)

---

### Post by fwojciec on 2007-10-06
> **Rumor said:**
> I wanted to try ttm / tint but when I went to download it yesterday, all I could find was  a.deb file on the website. The last time I downloaded it, there was a link to the various bits of code.

There is a PKGBUILD for tint in AUR, btw - I think it's called tint-svn or something like that.  I prefer pypanel though.

---

### Post by Rumor on 2007-10-07
> **fwojciec said:**
> I don't think Openbox is only good for old hardware - I use it on both my laptop and my desktop (AMD X2 4400+ with good Nvidia card and so on) - it's not so much about speed or anything, Openbox it simply is my preferred way of organizing my desktop experience.

No, not solely for old hardware. Your list of fine points is applicable across all levels of hardware. You could add to it that it is part of the overall Arch Linux "experience" in that a base install and execution of OpenBox gives you a blank canvas, much like a base install of an Arch snapshot ISO. From there you go on to add what you want, where you want it, when you want it the way you want it.

> **fwojciec said:**
> There is a PKGBUILD for tint in AUR, btw - I think it's called tint-svn or something like that.  I prefer pypanel though.

Cool, thanks for telling me this. I had not thought to check the AUR . . . kind of odd since I was installing a couple other packages from it.

I like to use pypanel as a desktop switcher / application launcher / clock across the top and has tint display at the bottom.

---

### Post by Dimitriid on 2007-10-09
After trying a few days i dont know why but i am experiencing some issues with KDEmod. First of all, a few moments ago some apps randomly decided not to open ( KWrite one of em ). Then the archiver thing crashed 4 times in a row when trying to open my directories.

Then I tried to open konqueror and it would not open. I decided to restart the machine ( not just X ) and everything seemed to work, except firefox took like 1 minute to start after the restart and like 2 minutes before my system stopped accessing my hdd.

Not sure if they are isolated cases but it doesnt feels right to me right now, I think I might just go with Arch + Gnome or Arch + XFCE. KDE is just acting up to much when it supposed to be stable and im barely using any applications and still decides to randomly act out.

---

### Post by r76 on 2007-10-09
> **Dimitriid said:**
> After trying a few days i dont know why but i am experiencing some issues with KDEmod. First of all, a few moments ago some apps randomly decided not to open ( KWrite one of em ). Then the archiver thing crashed 4 times in a row when trying to open my directories.

Then I tried to open konqueror and it would not open. I decided to restart the machine ( not just X ) and everything seemed to work

I had the exact same issues last night - kwrite and kate wouldn't open and my machine was scalding hot to touch as well - normally it's as cool as a cucumber - cooler than it ran in XP.  I did a restart too for that reason.  I don't know what it was but I've run kdemod base install for nearly a month with absolutely no trouble.

---

### Post by regomodo on 2007-10-10
for just over the past week i've been desperately wanting archlinux to work for me but so much has miffed me off . Just stupid stuff

Seg fault of firefox - crashes on load
abiword refuses to start
no fusesmb - aur installs but for some reason doesn't work as it should (no docs for it either)
xfce startup issue with no internet - same with gnome
despite being a bleeding edge distro (rolling release) it does have up to date apps. Blender being 1 behind - debian lenny at current release
wicd requiring root password  despite madwifi drivers - not needed on any other distro tried
jacman issues - not implemented into menus and no tasklist entry
gnome horrendously slow

I'm guess this is due to K.I.S.S but sod that when i'm struggling to find doc's

I'm surprised at the small package base and needing to use aur a lot but i guess that's being used to debian.

Oh well, i really wanted it to work. Off to Debian Lenny for my PC then

---

### Post by finferflu on 2007-10-10
Usually all sorts of errors appear if you didn't set up your hostname properly.. not sure it's your problem, but it may well be...

---

### Post by fwojciec on 2007-10-10
@regomodo:  abiword and firefox work fine here.  gnome and xfce issue sound like bad info in /etc/hosts file.  I'm not using fusesmb/wicd/jacman so dunno about that.  my arch systems (3 of them) are as fast as ever and completely stable.  sounds like something is seriously misconfigured on your system though... oh well, debian is a good distro as well :)

---

### Post by regomodo on 2007-10-11
> **finferflu said:**
> Usually all sorts of errors appear if you didn't set up your hostname properly.. not sure it's your problem, but it may well be...

yeah. It did complain about that so i did what the error told me to do. Still the same. 

So far i'm really enjoying Debian Lenny. I always liked etch but found it a touch out of date. So far no issues with using a testing release

---

### Post by finferflu on 2007-10-11
Just out of curiosity, what was the error?
Usually in order to set up your hostname you have to specify it in /etc/rc.conf and in /etc/hosts.
Curiously, I eventually got to try Arch by getting away from Debian, since things didn't seem to work properly (both on Etch and Lenny) :D

---

### Post by regomodo on 2007-10-11
> **finferflu said:**
> Just out of curiosity, what was the error?
Usually in order to set up your hostname you have to specify it in /etc/rc.conf and in /etc/hosts.
Curiously, I eventually got to try Arch by getting away from Debian, since things didn't seem to work properly (both on Etch and Lenny) :D

basically something about how it couldn't connect and complained about me not adding my host name to /etc/hosts which i did (the same as in rc.conf). It asked me to continue anyway or try again

I would be specific but i can't remember and recreate it.

---

### Post by fwojciec on 2007-10-11
regomodo - computers don't lie, if it says that there is a problem with /etc/hosts there is a problem with /etc/hosts.  I know exactly the problem you're describing...

for future reference...  this is an example of working /etc/hosts file (where the hostname is "ground_control32" and the domain is "space":

> #
# /etc/hosts: static lookup table for host names
#
 
#<ip-address>   <hostname.domain.org>   <hostname>
127.0.0.1               localhost.localdomain   localhost       ground_control32        ground_control32.space

# End of file

ground_control32.space at the end of the line is probably unnecessary, btw - but everything works as it should now so I'm not changing it...

---

### Post by regomodo on 2007-10-11
> **fwojciec said:**
> regomodo - computers don't lie, if it says that there is a problem with /etc/hosts there is a problem with /etc/hosts.  I know exactly the problem you're describing...

for future reference...  this is an example of working /etc/hosts file (where the hostname is "ground_control32" and the domain is "space":



ground_control32.space at the end of the line is probably unnecessary, btw - but everything works as it should now so I'm not changing it...

i just realised what i did wrong. I double-checked the wiki and for some reason i put my hostname in a new line for some reason. Back i go to Arch also because nvidia is hell in Lenny. Thank god i don't have any assignments atm

---

### Post by fwojciec on 2007-10-11
> **regomodo said:**
> i just realised what i did wrong. I double-checked the wiki and for some reason i put my hostname in a new line for some reason. Back i go to Arch also because nvidia is hell in Lenny. Thank god i don't have any assignments atm

lol, I bet you're becoming an expert at installing arch at this stage :P

---

### Post by Dimitriid on 2007-10-11
I reinstalled Arch and after wrestling with gnome a bit I finally have it customized to my liking, which looks minimalistic but does takes some time to set:

Normal:

[IMG]http://ubuntuforums.org/g/images/323051/large/1_Screenshot1.png[/IMG]

Busy:

[IMG]http://ubuntuforums.org/g/images/323051/large/1_Screenshotbusy.png[/IMG]

It so far has worked very nice. Its really fast, almost feel like Xubuntu really. Im pretty happy with the results although Im still debating between Openoffice or just Abiword + Gnumeric. Open Office might be overkill but its a good way to work across platforms with people.

---

### Post by regomodo on 2007-10-12
> **fwojciec said:**
> lol, I bet you're becoming an expert at installing arch at this stage :P

haha, yeah. I'm starting remember what xserver packages i need

(wtf wont they put it in a metapackage like they used to?)

---

### Post by kellemes on 2007-10-12
> **Dimitriid said:**
> I reinstalled Arch and after wrestling with gnome a bit I finally have it customized to my liking, which looks minimalistic but does takes some time to set:

Looks pretty fine..

---

### Post by fwojciec on 2007-10-12
> **Dimitriid said:**
> I reinstalled Arch and after wrestling with gnome a bit I finally have it customized to my liking, which looks minimalistic but does takes some time to set:

[pics removed]

It so far has worked very nice. Its really fast, almost feel like Xubuntu really. Im pretty happy with the results although Im still debating between Openoffice or just Abiword + Gnumeric. Open Office might be overkill but its a good way to work across platforms with people.

On my computer I don't really see a whole lot of difference between Gnome and Xfce on Arch - it's true that Xfce uses less memory, but not by much, and in terms of speed they are very similar.

As for office apps - I would suggest Openoffice if you do any serious writing.  I remember having some problems with footnotes in Abiword, for example, that I could not resolve for the life of me, also with long documents Abiword seems actually slower than Openoffice to me...  The new version of OO (2.3) is very nice, and it seems to work much faster (or at least has better start up times) than 2.2.

---

### Post by Dimitriid on 2007-10-12
> **fwojciec said:**
> On my computer I don't really see a whole lot of difference between Gnome and Xfce on Arch - it's true that Xfce uses less memory, but not by much, and in terms of speed they are very similar.

As for office apps - I would suggest Openoffice if you do any serious writing.  I remember having some problems with footnotes in Abiword, for example, that I could not resolve for the life of me, also with long documents Abiword seems actually slower than Openoffice to me...  The new version of OO (2.3) is very nice, and it seems to work much faster (or at least has better start up times) than 2.2.

Yea I always though xfce was a lot faster but I guess Xubuntu as a distro does more to trim Ubuntu than xfce does.

And thanks for the advice, OO it is ( though I might also install scribus for some flyers and newspaper work ) Is that version already on the repos or through AUR?

---

### Post by Rumor on 2007-10-12
OO.org 2.3.0-2 is in extra
OO.org 2.3.0-3 is in testing
Scribus 1.3.4-1 is in extra

---

### Post by finferflu on 2007-10-13
Since you're going minimalist, you might as well learn LaTeX, so you can use simple text editors (I always recommend Vim, which is not really simple, but it's genial indeed) to write very well formatted documents, and you can focus on the contents, rather than the formatting, while typing.

---

### Post by ynnhoj on 2007-10-13
hey finferflu, i've been meaning to start learning latex -- any tutorials in particular you might suggest?

---

### Post by K.Mandla on 2007-10-14
Random note. ...

I've been offline with two Arch systems for the past two weeks, and to be honest, it has gone a lot better than I thought it would. Back in July I was offline with an Ubuntu installation and things were okay. When I lost my connection at the end of last month, I thought for sure something would fall apart with my systems and I'd end up rebuilding a full Ubuntu system offline, on one or both.

But everything has been stable and solid, and no glitches anywhere. True, I only use Openbox and a few select GTK2 programs, but aside from the recurring nervous twitch from lack of 'net access, I think my Arch systems have proven just as dependable as the Ubuntu ones. 

That's all. See, I told you it was random. ... ;)

---

### Post by kelvin spratt on 2007-10-14
I Installed Arch a few weeks ago and was amazed at the speed using KDE, the whole polish and quality of the distro is amazing. Its the only KDE desktop i like so i won't change to Gnome, or my favorite E17 on this one.

---

### Post by regomodo on 2007-10-14
Been going well so far except 2 points. Network share browsing in XFCE and playing dvds.

I'm left feeling a little uncomfortable in the Archlinux forums. Definitely a lot quieter and with a subtle hint of elitism.

If Archlinux forums were as good as ubuntu's i would be wetting my pants with glee, perhaps.

---

### Post by distroman on 2007-10-14
I have been running arch in vmware for quit some time and have found myself spending hours in that installation, so I made a couple of partitions and installed it some ago with xfce. 

First of the wiki is really great, it took a long time before I felt the need to search it just feels very  friendly and accessible.

I am really happy with the installer, for instance, auto prepare will suggest, /boot, /, /home partitions, IMO this make a lot of sense, of cause with multi boot it's very flexible as well. 
Then there's the config files, I found them somewhat confusing but they are very well covered in the wiki and if you miss some it seems easy to adjust later.
All in all I found the installer to really follow the principles of KISS, cool and  fairly obvious.

I do think that you should create a user account during the install, I am not crazy about having to do it afterwards and then make sure you're in all the groups you're suppose to be in. 
So fare I have only had to add a few demons, mostly DM specific and adjust some locals, there's differently a learning curve here but when you got pacman <woohoo> you got time to spare.  

I did have some real trouble with my sound, it was starting to be a bugger but luckily it turned out to be a easy fix. 

It is some time ago I have been so excited about a distro and anyone that find themselves wanting to have a poke around should give arch a try.

---

### Post by Rumor on 2007-10-14
> **regomodo said:**
> If Archlinux forums were as good as ubuntu's i would be wetting my pants with glee, perhaps.

I took a shot at your DVD question. You're right that the forums there are quieter than those here. I've usually been able to get help in them. 

If your thread there does not yield results, you might want to ask in #archlinux on Freenode IRC. The channel is *very* active and there are some very knowledgeable users there.

Good luck!

---

### Post by regomodo on 2007-10-14
> **Rumor said:**
> I took a shot at your DVD question. You're right that the forums there are quieter than those here. I've usually been able to get help in them. 

If your thread there does not yield results, you might want to ask in #archlinux on Freenode IRC. The channel is *very* active and there are some very knowledgeable users there.

Good luck!

cheers for the help. Didn't work but thanks anyway. I've never like irc but looks like i'll have to go on it

---

### Post by Dimitriid on 2007-10-14
Im getting some updates on -Syu. By default I have gnome 2.18 installed and today I see  ```
Replace control-center with extra/gnome-control-center?"
```.

And one more update but the gnome control center goes to 2.20 and resolving all dependencies pushes it to 217mb...this means gnome 2.20 is released now? Im a little confused since I dont see it anywhere on the main site.

---

### Post by fwojciec on 2007-10-14
I don't have all of Gnome installed, but a bunch of Gnome packages I use were updated to 2.20 versions so I think that Gnome 2.20 has been moved to the main repo.

I did have a small issue with the update today - a problem with gcc and gcc-objc which I needed to install separately with force overwrite option enabled (pacman -Syf gcc gcc-objc) because pacman was complaining about files already existing in the system, but other than that the entire update (250MB of packages) went very smoothly.

---

### Post by finferflu on 2007-10-14
> **ynnhoj said:**
> hey finferflu, i've been meaning to start learning latex -- any tutorials in particular you might suggest?
Yes, the LaTeX [wiki book]("http://en.wikibooks.org/wiki/LaTeX") is the best so far for me. It's quite simple and straight forward, with useful practical examples ;)
I think I'll never use a word processor again, finally! I detest word processors.

@ **Dimitriid**
Woah! I got 386 MB of updates :D We'll have to consider I have installed Gnome, Xfce, Openbox, dwm, wmii, Xmonad, ratpoison and Ion3. I love testing suff :D

---

### Post by ynnhoj on 2007-10-14
> **finferflu said:**
> Yes, the LaTeX [wiki book]("http://en.wikibooks.org/wiki/LaTeX") is the best so far for me. It's quite simple and straight forward, with useful practical examples ;)
I think I'll never use a word processor again, finally! I detest word processors.
thanks for the quick response!  this is much better than the faqs i found through google.

---

### Post by mintcoffee on 2007-10-15
This is incredible. I was a long time Ubuntu user since warty, but switched to Arch a couple weeks ago.

I always liked arch's philosophy, but couldnt get past the installation, and never knew exactly what to do. Now, with a couple years of experience, I'm loving arch. :)

---

### Post by kellemes on 2007-10-15
> **mintcoffee said:**
> This is incredible. I was a long time Ubuntu user since warty, but switched to Arch a couple weeks ago.

I always liked arch's philosophy, but couldnt get past the installation, and never knew exactly what to do. Now, with a couple years of experience, I'm loving arch. :)

Welcome to Arch.
I'm surprised Arch isn't more popular since it gives an incredible amount of control over the environment. And this without to much hassle.

---

### Post by Enverex on 2007-10-15
> **xXx 0wn3d xXx said:**
> There is no splash in Arch because it aims to be simple, cutting-edge, and fast.

...

because Arch compiles everything from source, optimizing it for your system. It was great having something so fast.

...

 Now, I am getting ready to try Gentoo.

Trying not to laugh here. This is so obviously the prologue to someone who is going to be using "CFLAGS="--fomg-sofast --fruitloops"". Compiling things for your specific processor rarely gives a speed increase and when it does it is only small and on certain applications. The rest just sounds plain silly.

The only reason it seems faster is because you're used to Ubuntu which comes pre-loaded with everything for everything.

There's one critical issue with Arch that stops me from using it, it doesn't support Multilib or Multiarch which makes some apps unusable/uncompilable.

---

### Post by afonic on 2007-10-15
Actually Arch is optimized for i686 processors, that certainly gives even a small speed increase. Nowadays many people pay hunders of dollars to get hardware that will get them a 10% increase, if I can get 2% by running Arch instead of Ubuntu I'm happy. :P

---

### Post by 5-HT on 2007-10-15
> **Dimitriid said:**
> ...this means gnome 2.20 is released now? Im a little confused since I dont see it anywhere on the main site.
Yup :). No notice on the 'latest news' feed, but it's reflected in the package archive.

cheers,

---

### Post by kellemes on 2007-10-15
> **Enverex said:**
> Trying not to laugh here. This is so obviously the prologue to someone who is going to be using "CFLAGS="--fomg-sofast --fruitloops"". Compiling things for your specific processor rarely gives a speed increase and when it does it is only small and on certain applications. The rest just sounds plain silly.

The only reason it seems faster is because you're used to Ubuntu which comes pre-loaded with everything for everything.


+1
People often think Gentoo is all about performance.. not really he case.. the most important + of Gentoo is the control you have on features, each individual package can be compiled with a specific featureset using USE-flags; this *may* result in a better performing system but it all depends on the user's choices..
Binary-based systems mostly compile "one-size-fits-all", but obviously leaving a lot of people in the cold..

---

### Post by regomodo on 2007-10-17
looks like it's back to ubuntu for me. Getting nowhere with my dvd issue and now i find i can't run arduino in arch either.

Going to download gutsy.

---

### Post by finferflu on 2007-10-17
> **regomodo said:**
> looks like it's back to ubuntu for me. Getting nowhere with my dvd issue and now i find i can't run arduino in arch either.

Going to download gutsy.
Don't worry, we know you'll be back :D
Joking.... perhaps :P

---

### Post by regomodo on 2007-10-18
> **finferflu said:**
> Don't worry, we know you'll be back :D
Joking.... perhaps :P

I think you may be right. Just installed Gutsy today and its a bit odd despite only being away from Ubuntu ~2weeks. It feels sluggish and i can't figure out how to configure things with text files. It appears my DVD issue has followed me to Ubuntu as well, at least not as bad. 

I'm going to try my dvd drive with another distro and if dvd playback is still duff i'm going to buy a new one and slap archlinux back on. I just don't feel comfortable here despite the vast amount of info(forums) and supported packages.

I may even get the LFS book and build my own system.

---

### Post by finferflu on 2007-10-19
> **regomodo said:**
> I think you may be right. Just installed Gutsy today and its a bit odd despite only being away from Ubuntu ~2weeks. It feels sluggish and i can't figure out how to configure things with text files. It appears my DVD issue has followed me to Ubuntu as well, at least not as bad. 

I'm going to try my dvd drive with another distro and if dvd playback is still duff i'm going to buy a new one and slap archlinux back on. I just don't feel comfortable here despite the vast amount of info(forums) and supported packages.

I may even get the LFS book and build my own system.
That's exactly what I meant. When you get away from Arch you miss the feel of it..

Anyway, I can't reach the Archlinux website, it just times out, whereas I can reach it with services like [anonymouse](http://anonymouse.org) or [the cloak](http://the-cloak.com)... do you have any idea of what the problem could be? This is horrible, since with those services I can't even log in. :(

---

### Post by Vansinnesvisan on 2007-10-19
> **finferflu said:**
> That's exactly what I meant. When you get away from Arch you miss the feel of it..

Anyway, I can't reach the Archlinux website, it just times out, whereas I can reach it with services like [anonymouse](http://anonymouse.org) or [the cloak](http://the-cloak.com)... do you have any idea of what the problem could be? This is horrible, since with those services I can't even log in. :(

I have no issue getting to the site.

Would you happen to be trying to access the site through a school's or workplaces' network? Perhaps they are blocking sites.

---

### Post by regomodo on 2007-10-19
i'm reinstalling arch again. Can't get through to the website which is an **** as i can't remember all the xserver packages required. It looks like a UK thing

Virgin Media perhaps?

---

### Post by Vansinnesvisan on 2007-10-19
I think it is: xorg-server xf86-input-mouse xf86-input-keyboard xf86-video-<yourcard> xorg-xinit

Perhaps you could access the site via [google cache?]("http://64.233.167.104/search?q=cache:bXlSCjjM8YAJ:wiki.archlinux.org/index.php/Xorg+http://wiki.archlinux.org/index.php/Xorg&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")

---

### Post by distroman on 2007-10-19
You could try google cache if your desperate. ;-)
cache:[http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)

edit
amazing too late :lol:

---

### Post by finferflu on 2007-10-19
> **Vansinnesvisan said:**
> I have no issue getting to the site.

Would you happen to be trying to access the site through a school's or workplaces' network? Perhaps they are blocking sites.

Nope, I'm browsing from home...

> **regomodo said:**
> i'm reinstalling arch again. Can't get through to the website which is an **** as i can't remember all the xserver packages required. It looks like a UK thing

Virgin Media perhaps?

My ISP is NTL, anyway you can access the website through anonymouse or the cloak, the only thing is that you can't log in on the forums when using those services...

Good luck with your installation ;)

---

### Post by regomodo on 2007-10-19
> **finferflu said:**
> Nope, I'm browsing from home...



My ISP is NTL, anyway you can access the website through anonymouse or the cloak, the only thing is that you can't log in on the forums when using those services...

Good luck with your installation ;)

anonymouse didn't work for me. Couldn't find wiki/aur/bbs

---

### Post by finferflu on 2007-10-19
This one is working for me: [http://anonymouse.org/cgi-bin/anon-www.cgi/http://wiki.archlinux.org/index.php/Main_Page](http://anonymouse.org/cgi-bin/anon-www.cgi/http://wiki.archlinux.org/index.php/Main_Page)

---

### Post by pelle.k on 2007-10-19
You're both from the UK. Maybe it's something local?
[www.archlinux.org](www.archlinux.org) works just fine for me.

---

### Post by regomodo on 2007-10-19
> **pelle.k said:**
> You're both from the UK. Maybe it's something local?
[www.archlinux.org](www.archlinux.org) works just fine for me.

That's what i thought but it's fine now.

---

### Post by finferflu on 2007-10-19
Yep, it's working here now, too :)

---

### Post by crimesaucer on 2007-10-20
I've been on Archlinux for about 2 weeks, and I love the way it feels. I used to use xubuntu, and my Archlinux using Gnome 2.20 feels even faster... I'm loving pacman, plus using AUR to build packages with PKGBUILD and makepkg -s is so easy.


I loved doing the install with nano and tty, I love the fact that I'm on the newest Gnome 2.20, 2.6.23.1-3 kernel, the newest xorg-server, and the new xf86-video-intel for my 910GML... and my system feels very fast and solid.


It was a little difficult getting my bcm43xx to work, but ndiswrapper did the trick, and I have my eth0 using OpenDNS through my Wicd wireless/wired app.


during install, Xorg --configure left a few parts of my xorg.conf empty so I had to add modes and a few other things... and I had to redo the synaptics touchpad to make it work, but besides that everything has been nice.


Well, almost everything... I can't get AIGLX and Compiz to work, and I don't feel like trying to do it with Xgl, so I'm just using metacity right now, it's a little weird getting used to Gnome after only using xfce4 and Compiz/Beryl for my only year on Linux.

---

### Post by happy-and-lost on 2007-10-20
I'm moving back to Arch today. Gutsy's just *too* slow and buggy on my system.

Is there a good, definitive guide to setting Arch up on laptops out there?

---

### Post by regomodo on 2007-10-20
> **happy-and-lost said:**
> I'm moving back to Arch today. Gutsy's just *too* slow and buggy on my system.

Is there a good, definitive guide to setting Arch up on laptops out there?

Exactly the same reason for me. I've put Arch back on my Laptop and PC (i would use debian Lenny but it's easier if i use arch on both so i don't have to download packages twice for 2 distros).

I haven't had the time to sort everything out on my laptop but this may help

[http://wiki.archlinux.org/index.php/Laptop](http://wiki.archlinux.org/index.php/Laptop)

---

### Post by Dimitriid on 2007-10-21
> **crimesaucer said:**
> I've been on Archlinux for about 2 weeks, and I love the way it feels. I used to use xubuntu, and my Archlinux using Gnome 2.20 feels even faster... I'm loving pacman, plus using AUR to build packages with PKGBUILD and makepkg -s is so easy.


I loved doing the install with nano and tty, I love the fact that I'm on the newest Gnome 2.20, 2.6.23.1-3 kernel, the newest xorg-server, and the new xf86-video-intel for my 910GML... and my system feels very fast and solid.


It was a little difficult getting my bcm43xx to work, but ndiswrapper did the trick, and I have my eth0 using OpenDNS through my Wicd wireless/wired app.


during install, Xorg --configure left a few parts of my xorg.conf empty so I had to add modes and a few other things... and I had to redo the synaptics touchpad to make it work, but besides that everything has been nice.


Well, almost everything... I can't get AIGLX and Compiz to work, and I don't feel like trying to do it with Xgl, so I'm just using metacity right now, it's a little weird getting used to Gnome after only using xfce4 and Compiz/Beryl for my only year on Linux.

I also have a bcm43xx on my system and I got it to work now: I used the wiki from arch for the card: [http://wiki.archlinux.org/index.php/Wireless_Setup#BCM43XX](http://wiki.archlinux.org/index.php/Wireless_Setup#BCM43XX)
I did not had to install the drivers, during the install my card was detected and the module was already loaded on my rc.conf After googling for the correct firmware file ( the "link to ubuntu" forums was not very helpful and looking through this forums I found only old broken links to it, googling it was like the second or third hit )

After that I installed gnome-network-manager which is fairly simple: you install the package, and then open /etc/rc.conf to ! ( disable ) the network devices network manager will control, ! on the network daemon too and add the two daemons needed for gnome-network-manager.

Restarted and it worked. Its basically the exact same process you do on Ubuntu....only the arch way.

---

### Post by crimesaucer on 2007-10-21
> **Dimitriid said:**
> I also have a bcm43xx on my system and I got it to work now: I used the wiki from arch for the card: [http://wiki.archlinux.org/index.php/Wireless_Setup#BCM43XX](http://wiki.archlinux.org/index.php/Wireless_Setup#BCM43XX)
I did not had to install the drivers, during the install my card was detected and the module was already loaded on my rc.conf After googling for the correct firmware file ( the "link to ubuntu" forums was not very helpful and looking through this forums I found only old broken links to it, googling it was like the second or third hit )

After that I installed gnome-network-manager which is fairly simple: you install the package, and then open /etc/rc.conf to ! ( disable ) the network devices network manager will control, ! on the network daemon too and add the two daemons needed for gnome-network-manager.

Restarted and it worked. Its basically the exact same process you do on Ubuntu....only the arch way.

I had used the BCM43XX way as well (just like in xubuntu), and my wireless could detect my neighbor's wifi streams on both the Wicd wireless app, and the gnome-network-manager, since I tried them both... (I'm sure wifi-radar would have been the same)


... but, I couldn't actually connect to any of the streams, I tried it at a coffee shop, and random unsecured networks in my neighborhood, and the streams that I could detect at 60%-70%... would never connect. I previously had the same problems when trying to use wifi-radar and Wicd in xubuntu, and had only gotten it to connect twice at two different wifi hotspots... but the stream would get dropped and be difficult to connect back to.


So, I removed my wl_apst.o firmware and driver, and installed ndiswrapper with the proper driver from this list: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

...using these guides: 


[http://wiki.archlinux.org/index.php/Wireless#ndiswrapper](http://wiki.archlinux.org/index.php/Wireless#ndiswrapper)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/)

...and this network profile: [http://wiki.archlinux.org/index.php/Wireless#Using_the_Archlinux_Roaming_Network_Profiles](http://wiki.archlinux.org/index.php/Wireless#Using_the_Archlinux_Roaming_Network_Profiles)


...and now the same neighbor's streams that I had detected at 60% - 70% (3 green bars), were now at a more realistic 7% - 30% (1 yellow bar), which made sence because they were only 1 bar weak streams when using Windows Wireless Connection on Xp.


...but this time, my Wicd app could connect to the stream, as long as my firewall was set to allow "Internet connection sharing" for wlan0. 


And, for the first time, I had a properly working wireless Linux that could connect quickly and stay connected.


One last thing, my card is actually:

Card: Network controller: Broadcom Corporation BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev 02)

which was #46 on that ndiswrapper driver list.


...where as, every other BCM43XX on that list with the same pciid was named: 

Card: Broadcom Corporation BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev 02)

---

### Post by Dimitriid on 2007-10-21
Well I think it might also depend on the specific hardware configuration not just the chipset. Users who also have my integrated device on a laptop ( Acer 5100-5674 ) report similar success with it. It could be that Acer just ships the hardware with a better antenna and what not, or that the card itself, even if using the same exact chipset, ( although honestly I have to go check later ) its just working better.

I see this happen with broadcom cards on a daily basis at work: even with exact same models, some models work fairly good and others struggle constantly until we either replace the card or replace the wireless card AND the motherboard. In our case, we honestly just sheep a ton of "lemons" when it comes to broadcom wireless devices.

---

### Post by crimesaucer on 2007-10-21
Yeah, I will choose better next time I purchase a computer... I'll do my research to make sure I get the best working computer for Linux.


I'm on a HP Pavilion dv4230us 910GML celeron m, which was one of the least expensive HP notebooks available at the time I got it... which is before I knew anything about Linux or computers, so I hope to only be on this computer for another year or so.

---

### Post by Dimitriid on 2007-10-21
> **crimesaucer said:**
> Yeah, I will choose better next time I purchase a computer... I'll do my research to make sure I get the best working computer for Linux.


I'm on a HP Pavilion dv4230us 910GML celeron m, which was one of the least expensive HP notebooks available at the time I got it... which is before I knew anything about Linux or computers, so I hope to only be on this computer for another year or so.

Normally Id be inclined to say that your hardware is fine and that a buying decision shouldn't be centered on an easily replaceable card that is less than 10% of the value of the system.

But now that you mention your brand, I am encouraged to say otherwise about it and agree with you but I am not able. You see even if I was to say that this is **exactly** the case and the exact type of card issues I was describing from my job, company policy forbids me from disclosing said information so I never said that :popcorn:

---

### Post by crimesaucer on 2007-10-21
> **Dimitriid said:**
> Normally Id be inclined to say that your hardware is fine and that a buying decision shouldn't be centered on an easily replaceable card that is less than 10% of the value of the system.

But now that you mention your brand, I am encouraged to say otherwise about it and agree with you but I am not able. You see even if I was to say that this is **exactly** the case and the exact type of card issues I was describing from my job, company policy forbids me from disclosing said information so I never said that :popcorn:

Yeah, this is my first computer ever... I had ignored computers most my life as I lived out in the mountains of Lake Tahoe, where my life focused mainly on snowboarding and working as a chef (line cook).


If I ever got on one of my friends computers for a few moments, I would just surf the internet like a regular person. After Tahoe I moved to San Francisco, the only thing I ever did on a computer was look at craigslist for work, and surf websites (when I wasn't actually at the beach surfing). 


But, I had so many friends that were working tech jobs in San Jose, or designing websites in the city, that I became interested in it.


Finally in Oct. 2005, I stopped going to the Library to use the internet, and got a HP pavilion notebook.


I spent 1 year on Windows Xp, learned to write html/xhtml/css web pages, learned about open source programs and freeware... and read a lot about Linux.


So in Oct 2006, I did my first installs of xubuntu. Then I upgraded from 6.06 to 6.10 to 7.04 and learned a lot about CLI and config files... to the point of being able to successfully install Archlinux and configure OpenDNS, synaptics touchpad, ndiswrapper, and my xorg.conf, using all of the testing packages for everything.


In my short time on Linux, I also noticed a lot about my computer specs. I learned that my BCM43XX was difficult, and that my intel 910GML with the integrated graphics card wasn't the best for things like Beryl/Compiz, and that I needed to use AiGLX... and still couldn't use certain things like the water drops effect... not that any of that really matters... and 512MB ram isn't a lot... and neither is a 60GB hard drive.


I've been looking at the Lenovo Thinkpad series lately, but I still wouldn't know what the best notebook for Linux is... I'll have to do more research for that. I like how the options for different wifi or EVDO is available on the Lenovo series with the wifi antenna, and I like how it is designed to drain a spill because I had a few sips of root beer spill into my closed notebook, and it ruined the feel of my keypad.

---

### Post by distroman on 2007-10-23
ABS is wicked, wonder if it always this easy or if I am just getting lucky.
Also rolling release sure makes for bleeding edge, sure it has all been said before I am just repeating because I am really happy with it.

---

### Post by raul_ on 2007-10-23
It's nice to hear you are now a fellow Arch'er crimesaucer :)

I have yet to find a flaw in Arch

---

### Post by Dimitriid on 2007-10-23
Sadly arch was just unstable on my laptop. Not sure why, maybe its my hardware but things would just randomly fail without reason and work again after a restart...when the boot process didn't like to fail or take too long without reason.

Mostly things wouldn't open, hardware would hang for a very long time on the boot process, daemons and other things were very slow to load at times, very fast other times. Not sure why.

---

### Post by crimesaucer on 2007-10-25
> **raul_ said:**
> It's nice to hear you are now a fellow Arch'er crimesaucer :)

I have yet to find a flaw in Arch

I'm loving Arch, I got my Compiz Fusion working now and am very much loving my Archlinux. 


The only thing I miss is the program "Stellarium". The one in the Arch repos doesn't work, and the AUR one doesn't work either. I looked all through the forums and couldn't find a solution to fix it. I'll wait until someone makes a nice new working "Stellarium" package, but I do miss that app because I was learning a lot about the constellations.


I also couldn't build the app called "thewidgetfactory" and wish I knew of a gtk widget showcase that I could install in Arch, since "thewidgetfactory" said it couldn't be built for i686. I write a lot of gtk-2.0 themes and an app like "thewidgetfactory" really helps with making sure everything looks correct.

---

### Post by pelle.k on 2007-10-25
well, did you update the PKGBUILD to include
```
arch=('i686')
```
then?

---

### Post by crimesaucer on 2007-10-25
> **pelle.k said:**
> well, did you update the PKGBUILD to include
```
arch=('i686')
```
then?

Thanks, that worked perfectly:

Large View: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-4.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-4.png)
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-13.png[/IMG]

---

### Post by finferflu on 2007-10-26
> **crimesaucer said:**
> Thanks, that worked perfectly:

Large View: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-4.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-4.png)
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-13.png[/IMG]
Ah! You left Xfce for Gnome now :D

Anyway, I think you should look into ABS, it's not difficult at all, even I was able to create a couple of packages. It's very cool when you miss an application and you can provide it by yourself. Arch is the perfect DIY distro, it gives you a lot of independence.

---

### Post by gabrielmenini on 2007-10-26
> **xXx 0wn3d xXx said:**
> Thanks for the reassurance. The live cd was very nice so I have decided to install it.

Give :arrow:[Sabayon Linux]("http://www.sabayonlinux.org/") a try if you are interested in eye-candy KDE-based desktop :KS:KS:KS

---

### Post by crimesaucer on 2007-10-26
> **finferflu said:**
> Ah! You left Xfce for Gnome now :D

Anyway, I think you should look into ABS, it's not difficult at all, even I was able to create a couple of packages. It's very cool when you miss an application and you can provide it by yourself. Arch is the perfect DIY distro, it gives you a lot of independence.

Yeah, for the time being. I used xfce4 for my first year on Linux, and when I installed Archlinux, I gave Gnome 2.20 a try, and so far I like it except for a few things (the animation of the minimized windows). 


I also have xfce4 installed and Compiz Fusion, so I'm comparing the three of them (4 if you count xfce4 with compositing differently than regular xfce4). I have compared my used RAM and CPU usage and it's not really that much... of course xfce4 with no composting wins hands down at everything, but once I turn the composting on... it is more than regular metacity, and barely less than Compiz Fusion on either metacity or xfce4. So I'm liking the combo of Compiz Fusion/metacity for looks, and then metacity for a faster desktop with a nice look, and then regualr xfce4 if I really want to conserve on resources and have the fastest desktop I can get.



As for ABS, I have read the wikis about ABS, AUR, and Makepkg, and I've installed csup and wget, and will try to use ABS one of these days. I have been using the AUR a bunch because it's so easy with makepkg -s.


Basically, I really like my Archlinux, and I finally got the new AUR Stellarium-latest 0.9.0-1 package built correctly with qt4 and it works perfectly, even better than the one that was in the xubuntu 7.10 tribe5 and beta... (I don't know how the stable 7.10 is since I haven't tried it yet...)

---

### Post by pelle.k on 2007-10-26
Hey, what font is that in your gnome screenshot?

---

### Post by crimesaucer on 2007-10-26
> **pelle.k said:**
> Hey, what font is that in your gnome screenshot?

I use "URW Gothic L Book size 8", and then for my Window title font I use a font called "Ranger" size 9.


I looked for a link to the Ranger font, but it seems that the font has changed it's appearance.

---

### Post by finferflu on 2007-10-27
> **crimesaucer said:**
> Yeah, for the time being. I used xfce4 for my first year on Linux, and when I installed Archlinux, I gave Gnome 2.20 a try, and so far I like it except for a few things (the animation of the minimized windows). 


I also have xfce4 installed and Compiz Fusion, so I'm comparing the three of them (4 if you count xfce4 with compositing differently than regular xfce4). I have compared my used RAM and CPU usage and it's not really that much... of course xfce4 with no composting wins hands down at everything, but once I turn the composting on... it is more than regular metacity, and barely less than Compiz Fusion on either metacity or xfce4. So I'm liking the combo of Compiz Fusion/metacity for looks, and then metacity for a faster desktop with a nice look, and then regualr xfce4 if I really want to conserve on resources and have the fastest desktop I can get.


Back in time when I used to have Desktop Environments, I chose Xfce over Gnome because of usability and stability in the first place, especially on Archlinux, where speed was not a noticeable variable anymore, since at some point you don't notice the difference anymore. I find Xfce better for productivity and also, even when an app freezes, it doesn't lock up or slow down the whole DE, as it used to happen in Gnome...

But well, for the time being I'm sticking with Ratpoison, it looks like the most clever solution to me.

---

### Post by raul_ on 2007-10-27
> **finferflu said:**
> Back in time when I used to have Desktop Environments, I chose Xfce over Gnome because of usability and stability in the first place, especially on Archlinux, where speed was not a noticeable variable anymore, since at some point you don't notice the difference anymore. I find Xfce better for productivity and also, even when an app freezes, it doesn't lock up or slow down the whole DE, as it used to happen in Gnome...

But well, for the time being I'm sticking with Ratpoison, it looks like the most clever solution to me.

could you post a screenie of ratpoison?

---

### Post by ynnhoj on 2007-10-27
there's not really anything special to see in a screenshot of ratpoison.. :P

---

### Post by raul_ on 2007-10-27
> **ynnhoj said:**
> there's not really anything special to see in a screenshot of ratpoison.. :P

I was wondering if there is anything to see at all

---

### Post by ynnhoj on 2007-10-27
what you're going to see is pretty much just the application(s) that the user has running.  there isn't really anything like a panel/statusbar, or whatever else.  it's very plain jane (not that that's a bad thing).

---

### Post by K.Mandla on 2007-10-28
> **ynnhoj said:**
> what you're going to see is pretty much just the application(s) that the user has running.  there isn't really anything like a panel/statusbar, or whatever else.  it's very plain jane (not that that's a bad thing).
Exactly correct.

[http://img230.imageshack.us/my.php?image=img0008ky5.jpg](http://img230.imageshack.us/my.php?image=img0008ky5.jpg)

With the exception of that task switcher popup in the upper right hand corner, there's not much to see. You can windowpane certain areas and partition them off, but it's like tiling without any handles or titlebars.

Some people dig it. As for myself, I can't imagine why. ... :-k

---

### Post by finferflu on 2007-10-28
> **K.Mandla said:**
> Exactly correct.

[http://img230.imageshack.us/my.php?image=img0008ky5.jpg](http://img230.imageshack.us/my.php?image=img0008ky5.jpg)

With the exception of that task switcher popup in the upper right hand corner, there's not much to see. You can windowpane certain areas and partition them off, but it's like tiling without any handles or titlebars.

Some people dig it. As for myself, I can't imagine why. ... :-k
Sorry, I wasn't following the thread those 2 last days. Anyway, if you're familiar with GNU Screen, you'll get the feel of Ratpoison. 

I'll tell you why I dig it. First of all: tiling. Tiling is the best invention ever in the Window Managers world. You don't have to worry about positioning windows, and most of all, you don't have *annoying* overlapping windows. I really don't see the point of having floating windows overlapping each other, I don't think there's any benefit for the user in that. So with Ratpoison you can split the screen in as many regions as you wish, and have the windows share the full screen space, all in a matter of a couple of keystrokes on the keyboard. Also, managing the whole environment is very intuitive for me, you have an escape key that triggers the special Ratpoison functions. I have set it to the Win key, so if I want to split the screen horizontally, I just press Win key, then "s". Obviously the main advantage is that you'll never need a mouse. I love using the keyboard, and I love smart window management, and I found Ratpoison the most flexible solution. It just does the job, and lets you enjoy your work fully, without messing about with positioning, moving, iconizing, and such...

/marketing

---

### Post by K.Mandla on 2007-10-28
... And there's the answer for me. Thanks. It sounds like something I would enjoy, if I ever took the time to learn it. Like so many things in life. ... :roll: :mrgreen:

---

### Post by Dimitriid on 2007-10-28
The feature sounds nice but you're almost running plain X there, if you like the keyboard a lot it might be fun to just use CLI too.

---

### Post by finferflu on 2007-10-29
Oh yes! that's why I'm digging GNU Screen as well :D
I use X only because I need X applications, such as Firefox, Pidgin (Finch does not work properly for me), The Gimp, Inkscape, and so on. As for the rest, I use CLI whenever I can. For example I'm writing this post in Vim in Screen (thanks to the Mozex add on). I ditched OpenOffice for LaTeX, my music player is ncmpc (a ncurses MPD client), I play games such as Nethack and ADOM, and so on :D
Anyway, what's wrong with plain X? Isn't X supposed to run X applications? That's what it's doing on my machine :D
Lastly, Ratpoison is not difficult to learn, compared to wmii and Ion3 this is easy and fully functional. Also Escape key + ? brings on a dialog with all the keys and functions, so you can consult it anytime.

---

### Post by ahaslam on 2007-10-29
I tried Gutsy64 last week & was stunned with encoding speed being more than twice that of Arch64, here's the findings: [http://ubuntuforums.org/showthread.php?t=584925](http://ubuntuforums.org/showthread.php?t=584925) .

Any idea how this could be so much quicker? Arch is the fastest distro I've come across, but Ubuntu really kicks its 455 here. I've made custom builds of mplayer, lame & xvidcore for Arch, resulting in little/no improvement...

:popcorn:

---

### Post by ynnhoj on 2007-10-29
> **finferflu said:**
> Sorry, I wasn't following the thread those 2 last days. Anyway, if you're familiar with GNU Screen, you'll get the feel of Ratpoison. 

I'll tell you why I dig it. First of all: tiling. Tiling is the best invention ever in the Window Managers world. You don't have to worry about positioning windows, and most of all, you don't have *annoying* overlapping windows. I really don't see the point of having floating windows overlapping each other, I don't think there's any benefit for the user in that. So with Ratpoison you can split the screen in as many regions as you wish, and have the windows share the full screen space, all in a matter of a couple of keystrokes on the keyboard. Also, managing the whole environment is very intuitive for me, you have an escape key that triggers the special Ratpoison functions. I have set it to the Win key, so if I want to split the screen horizontally, I just press Win key, then "s". Obviously the main advantage is that you'll never need a mouse. I love using the keyboard, and I love smart window management, and I found Ratpoison the most flexible solution. It just does the job, and lets you enjoy your work fully, without messing about with positioning, moving, iconizing, and such...

/marketing
i agree 100% with all of this.  the only difference is that i use dwm, rather than ratpoison :)

---

### Post by finferflu on 2007-10-31
> **ynnhoj said:**
> i agree 100% with all of this.  the only difference is that i use dwm, rather than ratpoison :)
Yeah, I used dwm extensively, but the only thing that brought me away, apart from the inability to resize frames the way I wanted, was the lack of the possibility to have multiple layouts on multiple "desktops". Xmonad provides that, but then you miss the dwm "panel", which is fundamental for that type of WM. I've also tried wmii, but you can't resize frames using the keyboard, and I really don't see the point: you got a WM which tries to be mouse-independent, but the only way to resize frames is using a mouse :/
Finally, I have tried Ion3, but I don't see any benefit in the tabbed frames, it's just a lot of confusion for me. So I ended up with Ratpoison, which is not as automated as dwm, but at least I can manipulate windows the way I want :)

---

### Post by ynnhoj on 2007-11-01
> **finferflu said:**
> Yeah, I used dwm extensively, but the only thing that brought me away, apart from the inability to resize frames the way I wanted, was the lack of the possibility to have multiple layouts on multiple "desktops"
i think the explanation for this is: there really are not multiple desktops in dwm -- there are multiple *tags*.  you only have one "desktop" and you filter which applications are shown using tags.  tags and workspaces aren't quite the same thing (though the lines are kind of blurry :)).  since you're able to display the contents of a combination of tags at one time, it would become complicated and probably a bit confusing if each tag had its own layout.

---

### Post by brjoon1021 on 2007-11-02
Look into FaunOS. It is a more user friendly version of Arch.

---

### Post by ahaslam on 2007-11-02
I found the cause behind the slow xvid encoding. With a simple amendment to the 'makedepends', xvid now performs as it should - better than when under Xubuntu.
[http://bbs.archlinux.org/viewtopic.php?id=39296](http://bbs.archlinux.org/viewtopic.php?id=39296) ;)

---

### Post by fwojciec on 2007-11-02
> **ahaslam said:**
> I found the cause behind the slow xvid encoding. With a simple amendment to the 'makedepends', xvid now performs as it should - better than when under Xubuntu.
[http://bbs.archlinux.org/viewtopic.php?id=39296](http://bbs.archlinux.org/viewtopic.php?id=39296) ;)

I like the way you have handled this: from the discovery of the problem to all the way to finding the solution and filing the bugreport on the flyspray.  That's exactly how the system is supposed to work :)  Sorry I couldn't help out with it, but I've zero experience with video encoding...  Anyways, I hope the devs take care of that issue soon.

---

### Post by ahaslam on 2007-11-05
Thanks, squashing pesky little bugs can be quite satisfying ;)

---

### Post by Antman on 2007-11-05
> **brjoon1021 said:**
> Look into FaunOS. It is a more user friendly version of Arch.

Hey, thanks for the find... I never heard of that one.

---

### Post by finferflu on 2007-11-06
Ah well, after all my testing and trying, I'm moving back to some "big" DE, it looks like there's no place for the humble Window Managers as all the apps seem to be designed with specific DEs in mind. So I'll go either for Gnome or KDE, or both. I'm on Gnome right now, and I'm installing KDEmod. It's a pity not to find decent applications (meaning, working decently outside a specific DE) for very cool WM such as Ratpoison and dwm :(

---

### Post by Rumor on 2007-11-06
> **finferflu said:**
> Ah well, after all my testing and trying, I'm moving back to some "big" DE, it looks like there's no place for the humble Window Managers as all the apps seem to be designed with specific DEs in mind. So I'll go either for Gnome or KDE, or both. I'm on Gnome right now, and I'm installing KDEmod. It's a pity not to find decent applications (meaning, working decently outside a specific DE) for very cool WM such as Ratpoison and dwm :(

Did you give fvwm a try? It takes a bit of work to tweak out the way you want it, but the apps I've run on it (firefox, pan, abiword and a few games here and there) all worked properly.

Granted, I used fvwm-crystal and edited the conf files. Call me lazy O:)

---

### Post by finferflu on 2007-11-06
As far as I remember, fvwm is not a tiling WM, so if I have to use a traditional WM, I can stick with Gnome. I'm not so much concerned about speed as much as I am with functionality. So far I'm configuring keyboard shortcuts and I'm being able to use keyboard only even on Gnome :D
What I like is that it keeps the position of the apps even if you reboot, so I can create a layout and use it all the times. Not a so bad compromise.

---

### Post by K.Mandla on 2007-11-07
> **finferflu said:**
> I'm installing KDEmod. 
I tried that out a few months ago and surprisingly liked it. I'm no fan of big DEs, but if I had to pick one I'd probably go with that -- specifically.

---

### Post by Dimitriid on 2007-11-07
> **finferflu said:**
> Ah well, after all my testing and trying, I'm moving back to some "big" DE, it looks like there's no place for the humble Window Managers as all the apps seem to be designed with specific DEs in mind. So I'll go either for Gnome or KDE, or both. I'm on Gnome right now, and I'm installing KDEmod. It's a pity not to find decent applications (meaning, working decently outside a specific DE) for very cool WM such as Ratpoison and dwm :(

Well its not the early 90s anymore, most people want a full DE :popcorn: But nevertheless I sympathize with you, there are many apps I know I will never find and will have to program myself.

---

### Post by ynnhoj on 2007-11-08
> **finferflu said:**
> Ah well, after all my testing and trying, I'm moving back to some "big" DE, it looks like there's no place for the humble Window Managers as all the apps seem to be designed with specific DEs in mind. So I'll go either for Gnome or KDE, or both. I'm on Gnome right now, and I'm installing KDEmod. It's a pity not to find decent applications (meaning, working decently outside a specific DE) for very cool WM such as Ratpoison and dwm :(
you could try to find console applications to use as alternatives to the applications that misbehave in tiling environments..  it's not always easy, though :|

---

### Post by finferflu on 2007-11-08
What I have done to start with, was trying to find CLI applications to replace the GUI ones. Apart from the fact that there are not satisfactory ones, for most things today you need a GUI, first over all, for browsing. Images are too important for certain things. The sad thing is that at times even a terminal emulator misbehaves in a tiling environment. I don't know why, but most of the apps seem to completely hate tiling. Perhaps I know why, they were created with floating  in mind. 
At this point I can only hope they will be able to integrate some intelligent tiling (not like Kwin or Compiz) in the big DEs. What's the point of having all windows tiled (same width) if when you go to resize one it overlaps the other(s)? I don't really get it :P
Who knows, perhaps the guys at KDE will come up with something interesting for the next release, even though my hopes are very feeble.

---

### Post by bonzodog on 2007-11-08
Finerflu; 
Have you tried Openbox?
Openbox handles gtk theming,yet has a surprisingly simple layout. All it needs to complete it IMO is someone to write a tiling modification to it, so you can switch between floating or tiling.

I have used a lot of WM's in my day, and openbox even beats XFCE in my opinion.

---

### Post by RedSquirrel on 2007-11-08
I don't use a tiling window manager, but I do like to avoid using the mouse as much as I can.

I use Fluxbox. It can remember *size* and *position* of windows, among other attributes.

Fluxbox makes it very easy to setup keyboard shortcuts. 

I use these to move windows around when I don't feel like reaching for a mouse:

```
Control Mod1 KP_4       :MoveLeft 10
Control Mod1 KP_6       :MoveRight 10
Control Mod1 KP_8       :MoveUp 10
Control Mod1 KP_2       :MoveDown 10

```I also use (for example)

```
Control Mod1 KP_3       :SendToWorkspace 3
```to send the current window to Workspace 3.

Anyway, with highly configurable window managers such as Fluxbox or Openbox, you might be able to setup a comfortable working environment. :)

---

### Post by K.Mandla on 2007-11-08
> **bonzodog said:**
> Finerflu; 
Have you tried Openbox?
Openbox handles gtk theming,yet has a surprisingly simple layout. All it needs to complete it IMO is someone to write a tiling modification to it, so you can switch between floating or tiling.

I have used a lot of WM's in my day, and openbox even beats XFCE in my opinion.
+1. \\:D/

By the way, I don't know if this is what you mean by a tiling modification, but would this be of any help?

[http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/](http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/)

Should be compilable; debs work perfectly with Ubuntu Openbox.

---

### Post by finferflu on 2007-11-08
As I said (did I say that already? can't remember :P), the Gimp doesn't work for me on OpenBox, it sucks up all my RAM, don't know why. 
Anyway, it's not a tiling WM, and I really hope they're gonna do something about tiling, since I like it. But if I have to use traditional windows, I prefer wobbly ones :P

K.Mandla, I have already tried that, if you remember I had also commented on your blog about it... That app tiles windows using equal portions of screen, if you try to resize one window, it ovelaps the others, that's not real tiling to me.

I'm happy, though, that tiling is not my only concern.

---

### Post by K.Mandla on 2007-11-09
> **finferflu said:**
> K.Mandla, I have already tried that, if you remember I had also commented on your blog about it... 
I'm happy, though, that tiling is not my only concern.
Oops, sorry. You're right. I completely forgot about that. ... :oops: :)

---

### Post by Vansinnesvisan on 2007-11-09
I'm getting a bit annoyed with the lack of quality control with Arch. The Don't Panic release had a kernel panic; and it wasn't addressed for awhile - didn't even bother to take down the bad ISOs in the mean time. Recent updates broke most people's xorg and java. DHCPCD doesn't work. And an array of other applications that just don't work right. 

There was a post on the official forums where someone politely and respectively opened a debate about the lack of quality control only to be berated by Phrakture. 

It is disappointing someone would take things so personally than reevaluate and address some serious issues with Arch. I think I'll go back to Ubuntu. :(

---

### Post by fwojciec on 2007-11-09
> **Vansinnesvisan said:**
> I'm getting a bit annoyed with the lack of quality control with Arch. The Don't Panic release had a kernel panic; and it wasn't addressed for awhile - didn't even bother to take down the bad ISOs in the mean time. Recent updates broke most people's xorg and java. DHCPCD doesn't work. And an array of other applications that just don't work right. 

There was a post on the official forums where someone politely and respectively opened a debate about the lack of quality control only to be berated by Phrakture. 

It is disappointing someone would take things so personally than reevaluate and address some serious issues with Arch. I think I'll go back to Ubuntu. :(

I didn't have any problems - I only had to change some settings in xorg.conf to get the touchpad working, but that was already well documented on the forums, so it only took me a couple of minutes to do it - this wasn't a bug, by the way, just an upstream change.  When a bunch of people start posting about the problems they have on a low-traffic forum it is easy to create an impression that "most people" experience problems...

Arch has been extremely stable and reliable for me, but it does require that I am a little hands on about everything, especially major upgrades (it's still more convenient for me than upgrading the whole system every 6 months).  In a bleeding edge rolling release system the developers, generally, can only soften the shock of major upgrades - they can't prevent all problems from happening.  In the case of recent problems the majority of things that were mentioned on the forums were simply configuration issues (like my problem with synaptic touchpad) or upstream bugs (problems related to specific drivers and so on).  I think the only actual bug was the Java issue, and that got taken care of in a matter of hours from it was reported.

I don't agree with your estimation of Arch Linux "quality control", I think what you say is a completely unfair and unwarranted generalization, but everyone has their own experience and is entitled to their own opinion.  I would only say that if you want to leave the responsibility for having a working system completely to the developers and if you demand that everything "just works" without messing around with configurations then there are certainly better choices than Arch Linux - that's for sure.

---

### Post by pelle.k on 2007-11-09
At some point, packages just have to be moved to current / extra. They can't stay in testing forever. Besides that, you need people to actually test stuff out first, so the lack of "testers" might be the *real* issue. Xorg 7.3 has been in testing for quite some time now.
Kernel upgrades is always tricky, but there's really nothing one can do about it. Sure, you can patch some stuff, but that's not really how things are done in arch. Kernel upgrades have to be done, and they often break stuff for a lot of people.

You "get the whole package" when you run arch, and that often mean upstream bugs too. If one is looking for long term stability then clearly ubuntu/debian is the better choice.

---

### Post by david_2001 on 2007-11-09
> **Vansinnesvisan said:**
> I'm getting a bit annoyed with the lack of quality control with Arch. The Don't Panic release had a kernel panic; and it wasn't addressed for awhile - didn't even bother to take down the bad ISOs in the mean time. Recent updates broke most people's xorg and java. DHCPCD doesn't work. And an array of other applications that just don't work right. 
Do you have any examples of those applications that just don't work right?
> There was a post on the official forums where someone politely and respectively opened a debate about the lack of quality control only to be berated by Phrakture.

It is disappointing someone would take things so personally than reevaluate and address some serious issues with Arch. I think I'll go back to Ubuntu. :(
Do you have a link to that thread?  I cannot find it and would like to have a read just out of curiosity.

In the meantime, if you wanted to learn about truly poor QC you should have been using Mandrake 3 or 4 years ago and if you want to know what it's like to experience multiple broken updates just install and run Debian Sid for a few months.

---

### Post by Rumor on 2007-11-09
> **david_2001 said:**
> 
Do you have a link to that thread?  I cannot find it and would like to have a read just out of curiosity.

I may be mistaken, but I believe it is a reference to this thread: [http://bbs.archlinux.org/viewtopic.php?id=39551](http://bbs.archlinux.org/viewtopic.php?id=39551)

> **Vansinnesvisan said:**
> I'm getting a bit annoyed with the lack of quality control with Arch. The Don't Panic release had a kernel panic; and it wasn't addressed for awhile - didn't even bother to take down the bad ISOs in the mean time. Recent updates broke most people's xorg and java. DHCPCD doesn't work. And an array of other applications that just don't work right.

I have not had any issue with Arch, and I have found the process by which a package gets moved from testing to extra or wherever to be usually quite sound. 

I don't know if recent updates broke most user's xorg or not. Mine were not effected. I am running Arch on three systems and none of them have so much as hiccuped. 

dhcpcd works fine for me. I *have to* execute it here at work or I cannot otherwise get on the network. Granted, I may be an exception.

One of the things I appreciate about Arch is that the devs are very active in the community and I have found them to be helpfully responsive to the needs of users.

---

### Post by crimesaucer on 2007-11-09
What I like best about Arch is that it took a bit of effort to make it perfect, and I learned more about my OS, than if I had just installed it without having to edit the config files. 


On my first attempt to install Arch, the CD would not boot up... there were many people that couldn't get the 2007.08, and 2007.08-1 install CD's to boot properly... I almost gave up on Arch until I decided to try an older version that people in the forums had recommended since it definitely worked.


I installed Arch Duke using it's base packages, and then upgraded everything to 2007.08-1. 


I eventually upgraded to the testing packages to use the new Gnome and Xorg (when they were still in testing), as well as the new xf86-video-intel and the dependencies needed for Compiz Fusion.


I also ran into that Synaptics touchpad issue with the new Xorg, but it was easy to solve when I found the correct thread already discussing it.


After a successful install of almost everything I needed, I screwed my system up and had to do a reinstall (totally my fault).


That was at the time that 2007.08-2 was released, so I burnt that ISO and it installed perfectly... not a single problem. They had fixed the problem of the install CD not being able to boot past a point. They had also changed the way pacman and it's repositories were... so to me, it felt as if they were very concerned with making quality upgrades. 


There had been work-arounds and other install methods for 2007.08 and 2007.08-1 even before 2007.08-2, and when they fixed the problem with 2007.08-2 they had also upgraded pacman... 


Plus, I'm still seeing things getting fixed with the new Xorg and xf86-video-intel, for example, the last upgrade fixed my "caps lock" light which had not been working.

---

### Post by Vansinnesvisan on 2007-11-10
> **david_2001 said:**
> 

Do you have a link to that thread?  I cannot find it and would like to have a read just out of curiosity.


It looks like the thread was deleted. It was titled Open Letter To The Archlinux Community. I got the first [post]("http://64.233.167.104/search?q=cache:5j20PjkPiRAJ:bbs.archlinux.org/viewtopic.php%3Fpid%3D297122+arch+an+open+note+to+the+community&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")  and [page 2]("http://64.233.167.104/search?q=cache:5j20PjkPiRAJ:bbs.archlinux.org/viewtopic.php%3Fpid%3D297122+arch+an+open+note+to+the+community&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a") from google cache. Some developers chimed in with good ideas. I believe there was one about having another repo for older core files. I think that would be better than using /var/cache/pacman as sometimes it needs to get cleaned out from the size it gets - at least for me as I try out a lot of software.

---

### Post by Vansinnesvisan on 2007-11-10
> **fwojciec said:**
> 

I don't agree with your estimation of Arch Linux "quality control", I think what you say is a completely unfair and unwarranted generalization, but everyone has their own experience and is entitled to their own opinion.  I would only say that if you want to leave the responsibility for having a working system completely to the developers and if you demand that everything "just works" without messing around with configurations then there are certainly better choices than Arch Linux - that's for sure.

There is a difference between having to configure .conf files and software leaving unstable and testing repositories early. I have no issue with configuring Arch myself and that level of control is why I choose Arch. I believe you misunderstood my post.

I do not think offering a critique of Arch Linux should be attacked, silence, or shunned. That's no way to run a distribution; or anything for that matter. It seems a lot of people are taking these things personally; rather than taking a look at the current issues and amending them. I suppose that is understandable, but very unfortunate. It bodes poorly for Arch.

---

### Post by david_2001 on 2007-11-10
> **Vansinnesvisan said:**
> It looks like the thread was deleted. It was titled Open Letter To The Archlinux Community. I got the first [post]("http://64.233.167.104/search?q=cache:5j20PjkPiRAJ:bbs.archlinux.org/viewtopic.php%3Fpid%3D297122+arch+an+open+note+to+the+community&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")  and [page 2]("http://64.233.167.104/search?q=cache:5j20PjkPiRAJ:bbs.archlinux.org/viewtopic.php%3Fpid%3D297122+arch+an+open+note+to+the+community&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a") from google cache. Some developers chimed in with good ideas. I believe there was one about having another repo for older core files. I think that would be better than using /var/cache/pacman as sometimes it needs to get cleaned out from the size it gets - at least for me as I try out a lot of software.

For the record, I found three pages in the Google cache, including the original post: [COLOR="DarkOrange"][Page 1]("http://66.102.9.104/search?q=cache:roG5aMX41x4J:bbs.archlinux.org/viewtopic.php%3Fid%3D39551+open+letter+archlinux+community&hl=en&ct=clnk&cd=1&gl=uk")[/COLOR], [COLOR="DarkOrange"][Page 2]("http://64.233.183.104/search?q=cache:5j20PjkPiRAJ:bbs.archlinux.org/viewtopic.php%3Fpid%3D297122+site:bbs.archlinux.org+Open+Letter+To+The+Archlinux+Community&hl=en&ct=clnk&cd=3&gl=uk")[/COLOR], [COLOR="DarkOrange"][Page 3]("http://64.233.183.104/search?q=cache:N8I_ul84_R8J:bbs.archlinux.org/viewtopic.php%3Fpid%3D297555+Open+Letter+To+The+Archlinux+Community&hl=en&ct=clnk&cd=2&gl=uk")[/COLOR].

Now that I know what the fuss is about, I can only say that I went smoothly through that xorg change and hadn't realised that there was a problem.  The original post certainly prompted some wise words from iphitus on page 2 but didn't serve any other useful purpose.  My experience is also that numbers of forum posts is not a very good metric for the severity of a problem or the merit of a piece of software - if everybody did use posts as an absolute indicator then no Ubuntu user would ever install Envy or Automatix!

---

### Post by Dimitriid on 2007-11-10
Arch is by no means perfect. But this is to be expected cause

1) It expects you to be an "advanced" user or to at least know what you are doing.

2) It stays so up to date you will eventually run into bugs.

Now for many people the update to the new xorg went smoothly. But I bet everybody will eventually have to troubleshoot an issue with arch. In fact my particular issues I did not troubleshoot out of frustration but there were a lot more serious than a xorg issue ( complete and total system instability on my laptop, it would randomly freeze, randomly get stuck on the boot process at any point, different parts of gnome would decide to stop working randomnly. in short everything worked for a while and nothing worked in the long run ) but in my desktop ( which honestly has more Linux friendly hardware ) I haven't given up even after wrestling a bit  with Kdemod.

---

### Post by K.Mandla on 2007-11-10
I've had no problems with Don't Panic or anything after (except that the apostrophe in the file name confused my ISO burner application :roll: :mrgreen: ). I hadn't heard much about any issues either, but I think that's because I tend to solve my Arch problems with this thread. I know, it's not exactly sociable, but I have a commitment to the community here. ... :)

---

### Post by crimesaucer on 2007-11-10
> **K.Mandla said:**
> I've had no problems with Don't Panic or anything after (except that the apostrophe in the file name confused my ISO burner application :roll: :mrgreen: ). I hadn't heard much about any issues either, but I think that's because I tend to solve my Arch problems with this thread. I know, it's not exactly sociable, but I have a commitment to the community here. ... :)

I spend more time in the Ubuntu Community Forums than I do in any forum. 

And when I need to solve an issue with Arch, I use the Arch wiki and I search the Arch forums for other people's threads to solve my problems, usually there is an answer there somewhere. 

I even search the Ubuntu forums to reference any Arch question I have since there seems to be so much good Linux info in this forum. 

Plus... I have 1000 beans (as of this post!!!!!)... and I want to keep my number up.

---

### Post by raul_ on 2007-11-11
> **crimesaucer said:**
> I spend more time in the Ubuntu Community Forums than I do in any forum. 

And when I need to solve an issue with Arch, I use the Arch wiki and I search the Arch forums for other people's threads to solve my problems, usually there is an answer there somewhere. 

I even search the Ubuntu forums to reference any Arch question I have since there seems to be so much good Linux info in this forum. 

Plus... I have 1000 beans (as of this post!!!!!)... and I want to keep my number up.

You should try the gentoo forums and wiki :) very helpful

---

### Post by RedSquirrel on 2007-11-11
I installed Arch with the ftp installer and there were no problems. I've since pulled down a number of other packages and I've been keeping up to date. Everything seems to be working very well. (I even have nice-looking fonts, which is something I never got into seriously in Ubuntu.)

The only small issue for me occurred with the upgraded Xorg: it didn't use my DisplaySize setting in xorg.conf. That wasn't hard to fix. ;)

Oh, and my boot time is a little longer than I'd like, but I'll get around to that.

---

### Post by crimesaucer on 2007-11-11
> **raul_ said:**
> You should try the gentoo forums and wiki :) very helpful

I haven't tried Gentoo yet... but I might check it some day. At the moment I feel that I'm going to be using Arch for a while. 


I just went back to using the xfce4 desktop after trying Gnome 2.20 for a month, and my Archlinux and xfce4 is just really fast. Gnome seemed a bit resource heavy with Compiz Fusion running, xfce4 is a bit lighter, and Thunar is quicker than Nautilus (all though uglier). 


I miss the nice looks of the new Gnome and it's beautiful panel, but I think I would rather have a really fast computer that still looks good, than a really good looking computer that isn't as fast.

---

### Post by K.Mandla on 2007-11-12
> **raul_ said:**
> You should try the gentoo forums and wiki :) very helpful
Their wiki is awesome. That's the first place I look for anything Linux-related, if it's not distro-specific. ;)

---

### Post by crimesaucer on 2007-11-12
> **K.Mandla said:**
> Their wiki is awesome. That's the first place I look for anything Linux-related, if it's not distro-specific. ;)

Cool, I'll check it out. Thanks for the tip.

---

### Post by mivo on 2007-11-13
Well, this thread convinced me to try out Arch on my old desktop. ;) Just for learning more about Linux in general and brushing up my Linux skills a little. Ubuntu works really well for me, so there are relatively few learning opportunities (I'm grateful for the stability, mind you!). I meant to put Hardy on my spare machine, but that doesn't make much sense before the Debian import freeze in December, so I think Arch might be something to tinker and learn with in the meantime.

I'm intrigued by the rolling release system, and I actually like that the distro seems to be more bleeding edge. I also feel that most "normal" distros install quite a bit of stuff that isn't really needed. Good example here is OpenOffice, which I have no real use for (I work mostly with plain text and Abiword or Kword work just fine when/if I need a word processor), but since it is pre-installed with many distros, it tends to be hard to remove (completely remove, that is).

How does Pacman handle dependencies when packages are uninstalled? Are the packages that are no longer needed by any other package also removed? (i.e. similar to how Aptitude works if packages were installed by it?)

---

### Post by mivo on 2007-11-13
> **mivo said:**
> Are the packages that are no longer needed by any other package also removed? (i.e. similar to how Aptitude works if packages were installed by it?)

Responding to myself ... I learned about "pacman -Rs package_name", and yes, it does remove dependencies that are no longer used/needed by any other installed package. Hmm, the more I learn about pacman, the more attractive I find it.

It's installing on my other box as we speak. So far it's been not as intimidating as it seemed at first (thanks to the guides!).

---

### Post by Rumor on 2007-11-13
> **mivo said:**
> It's installing on my other box as we speak. So far it's been not as intimidating as it seemed at first (thanks to the guides!).

Welcome to Arch! Let us know how you make out. 

What desktop environment / window manager are you thinking of using?

---

### Post by mivo on 2007-11-13
> **Rumor said:**
> Welcome to Arch! Let us know how you make out. What desktop environment / window manager are you thinking of using?

I thought about it for a while, but I think I'll stick with Gnome since that is what I'm familiar with -- and I actually like it, too. I had used KDE a few months ago, but somehow it felt "too busy". Looked at Sabayon's Live CD (uses KDE) a while back and still got the "too busy" feeling. So, Gnome for now. :)

I'm really not an advanced or experienced Linux user, so I don't know if the distro is for me, but it's definitely a challenge and so far fun, and I seem to remember things I had learned when I used FreeBSD a number of years ago. Arch's wiki is well done and informative, too.

---

### Post by raul_ on 2007-11-13
Just remember to have a spare pc with internet so you can read the wiki. it's what works best for me, although printing the installation instructions also does the trick

---

### Post by K.Mandla on 2007-11-13
> **mivo said:**
> I thought about it for a while, but I think I'll stick with Gnome since that is what I'm familiar with -- and I actually like it, too. I had used KDE a few months ago, but somehow it felt "too busy". 
If you feel like experimenting, the KDEmod desktop is really beautiful, without being too busy (or at least I thought so, and I'm an Openbox freak, so that should say something ;) ).

---

### Post by K.Mandla on 2007-11-13
> **raul_ said:**
> Just remember to have a spare pc with internet so you can read the wiki. it's what works best for me, although printing the installation instructions also does the trick
Huge +1. I never do a reinstall without one machine online -- Arch or otherwise. Nothing ever goes like I expect, and I need to be able to find answers. :???:

---

### Post by allix on 2007-11-13
> **K.Mandla said:**
> Huge +1. I never do a reinstall without one machine online -- Arch or otherwise. Nothing ever goes like I expect, and I need to be able to find answers. :???:

The installation-guide from the wiki is available on the cd too. Its in /arch/archdoc.txt if i remember correctly. 

My best tip is to install a text-based webbrowser like lynx. If you screw up a config-file, or an update breaks your system, you can always google the problem from the terminal.

---

### Post by david_2001 on 2007-11-13
> **allix said:**
> My best tip is to install a text-based webbrowser like lynx. If you screw up a config-file, or an update breaks your system, you can always google the problem from the terminal.
Seconded.  That was exactly what I did when I was installing Arch - I realised that it was a good idea when I was doing practice installs in VirtualBox before moving from Ubuntu.

---

### Post by Dimitriid on 2007-11-13
I go with elinks and bitchx myself :popcorn:

---

### Post by Opeth115 on 2007-11-13
Hey everyone i just installed arch like 6 days ago and then went to florida.  I posted my problem on the arch forums but got absolutely no response so hgere it is:

Well, i just installed arch and want to install compiz fusion so i went to the wiki and followed the isntructions.  But, whenever i try to start compiz i get this error:

```
fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
Backend     : gconf
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon import interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 143, in <module>
    session_bus = dbus.SessionBus()
  File "/usr/lib/python2.5/site-packages/dbus/_dbus.py", line 216, in __new__
    mainloop=mainloop)
  File "/usr/lib/python2.5/site-packages/dbus/_dbus.py", line 105, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.5/site-packages/dbus/bus.py", line 121, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```
also, i have to start fusion-icon from root or it wont give me the correct permissions... any ideas?

---

### Post by fwojciec on 2007-11-13
I don't use compiz so I can't really help with your problem - still, the error message says that there is a problem with dbus - do you have dbus daemon enabled in rc.conf?

---

### Post by raul_ on 2007-11-13
dbus-launch fusion-icon

try that

---

### Post by crimesaucer on 2007-11-13
> **raul_ said:**
> Just remember to have a spare pc with internet so you can read the wiki. it's what works best for me, although printing the installation instructions also does the trick

I wrote my install instructions down with pen and paper because I had no access to any other computer... 

... over 22 pages of my chicken scratch writing!


After I installed the first time, (and then ruined it - my fault, not Arch's), and then re-installed again the 2nd time... I totally learned the Arch install process without needing to look at my notes other than for a few things on my "xorg.conf" and "rc.conf".


This was a pretty good guide with screenshots that I used: [http://www.raiden.net/?cat=&aid=276](http://www.raiden.net/?cat=&aid=276)

---

### Post by pelle.k on 2007-11-13
> I don't use compiz so I can't really help with your problem - still, the error message says that there is a problem with dbus - do you have dbus daemon enabled in rc.conf?
Yeah, that, and how exatly do you run your gnome session? Through gdm?

---

### Post by RedSquirrel on 2007-11-13
> **mivo said:**
> Hmm, the more I learn about pacman, the more attractive I find it.

++

One feature I really like is that pacman often provides informative messages after it installs the packages. 

For example, with the change to mlocate, it reminds users to run 'updatedb', and for gimp, it reminds users to look into gutenprint for printing. These sorts of messages are very helpful to new users and serve very well as reminders for experienced users. Great stuff.

---

### Post by crimesaucer on 2007-11-13
> **RedSquirrel said:**
> ++

One feature I really like is that pacman often provides informative messages after it installs the packages. 

For example, with the change to mlocate, it reminds users to run 'updatedb', and for gimp, it reminds users to look into gutenprint for printing. These sorts of messages are very helpful to new users and serve very well as reminders for experienced users. Great stuff.

Yes, pacman is a very nice package manager.

I find that maiking packages from the AUR is so much easier than any other time that I built packages with ./configure make and make install, or whatever the README and INSTALL files said to do.

With pacman and the AUR, just one simple "makepkg -s" command, and then the install command of "pacman -U package.0.1-i686-.pkg.tar.gz" and everything is all done...

---

### Post by K.Mandla on 2007-11-14
Another vote for pacman. I actually prefer it to aptitude. I love being able to feed it a local package and have it install dependencies across the Internet. For some reason I always end up doing that in two steps with Ubuntu -- *dpkg -i* and then *apt-get install -f*. ... 

It's a trivial difference, but for some reason it highlights Arch's simplicity and elegance -- for me, at least.

---

### Post by mivo on 2007-11-14
I got Arch installed just fine, and it was actually fun, but I ran into something that I am confused about: After I had Gnome running, I wanted to install Compiz-Fusion, but I could not find it in the repository (I went to the [Package Search]("http://www.archlinux.org/packages/search/")). In the forum I see plenty of people who use Compiz-Fusion in Arch, so there is probably another way. Any pointers to where I should look? :)

---

### Post by afonic on 2007-11-14
Wiki is your friend!

There are two packged versions of Compiz-Fusion, one in the community repository and one in a third party repo that has the latest git version.

See:
[http://wiki.archlinux.org/index.php/Compiz_fusion](http://wiki.archlinux.org/index.php/Compiz_fusion)
and
[http://wiki.archlinux.org/index.php/Compiz_Fusion_Git](http://wiki.archlinux.org/index.php/Compiz_Fusion_Git)

I use the Git version on Gnome and it works great.

---

### Post by mivo on 2007-11-14
Thank you. :) I see that the search doesn't consider the community repo (I'll have to figure out how to search this, then).

---

### Post by Acid7711 on 2007-11-14
> **xXx 0wn3d xXx said:**
>  It's really great but a little complex and difficult to use. My rating of Archlinux is 8/10. Now, I am getting ready to try Gentoo.
Please don't take this the wrong way, I honestly don't want to come off as an ***, but if you have trouble with Arch, please do yourself a favor and stay away from Gentoo.  I've been a LONG time supporter of Arch, coming from Gentoo from years of use before that.  Just speaking from personal experience. :)

I LOVE Arch, it's by far my favorite distro, but there are certain things that need to be worked out, thus my dual booting with Arch/Ubuntu.  I'm not here to bash or be an ***, just to help and offer my opinion like everyone else.  Arch isn't meant for the lightharded, although after years of Gentoo, I find it extremely easy to use.


Once I found Arch, I basically ditched all other distros..... The only reason I'm even on Ubuntu is because of a newer xorg bug that's driving me crazy, and I'm far too lazy at this point to go compiling a bunch of stuff to fix it with an older version ;)  Best of luck with whatever you choose.  Either way, Arch is a solid distro, and given time you'll work your way through it and love it.  Pacman truly is astounding. I love portage, aside from the compiling (some would call it a plus) it's the #1 tool for me, but Pacman comes in second, even toping portage in areas.  I'm a HUGE fan and supporter of rolling-release distros and I love bleeding edge software, it's the perfect distro for me.

---

### Post by epimer on 2007-11-14
> **mivo said:**
> Thank you. :) I see that the search doesn't consider the community repo (I'll have to figure out how to search this, then).

```
 pacman -Ss packagename
```

---

### Post by afonic on 2007-11-14
> **mivo said:**
> Thank you. :) I see that the search doesn't consider the community repo (I'll have to figure out how to search this, then).

You should uncomment the entries in /etc/pacman.conf to include community.

Have a look at:
[http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)

---

### Post by Opeth115 on 2007-11-14
Hey thanks for teh responses...  I tried the dbus-launch fusion-icon and compi actually starts now but no emerald is available and no icon appears in the tray.

DAEMONS=(syslog-ng network netfs crond alsa gdm hal fam dbus)

that's my daemons line in rc.conf and i do start gnome through gdm

---

### Post by david_2001 on 2007-11-14
> **Opeth115 said:**
> Hey thanks for teh responses...  I tried the dbus-launch fusion-icon and compi actually starts now but no emerald is available and no icon appears in the tray.

DAEMONS=(syslog-ng network netfs crond alsa gdm hal fam dbus)

that's my daemons line in rc.conf and i do start gnome through gdm
My suggestion would be to try something like this is rc.conf:
```
DAEMONS=(syslog-ng network netfs crond alsa hal fam gdm)
```
I think that the daemons get executed in list order from left to right, so it's probably a good idea to start gdm after the services that it might want to use.  Also there's a note somewhere in the wiki about not having both dbus and hal in the list of daemons - hal will start dbus if it's needed.  Otherwise, I'm not sure what's causing your problems.  I installed compiz fusion from source using the AUR PKGBUILDs - mostly for the practice because I'm new to the way of Arch - and it worked just fine.

---

### Post by handy on 2007-11-14
I installed Arch a month ago & everything went perfectly well until it was time to do the first system update & a worse dependency hell than I ever could have imagined unleashed itself.  So I through my hands up in the air & reinstalled Sabayon.

I know, I took the easy way out. :-)

---

### Post by pelle.k on 2007-11-14
> **handy said:**
> I installed Arch a month ago & everything went perfectly well until it was time to do the first system update & a worse dependency hell than I ever could have imagined unleashed itself.  So I through my hands up in the air & reinstalled Sabayon.

I know, I took the easy way out. :-)

My answer will make me look like a total jerk, i know. But i really have to say that in my two years using arch, i have *never* encountered a single dependency error. Did you miss the  switch from current to core, or did you add a testing/unofficial repo? i.e. human error?

---

### Post by mivo on 2007-11-14
> **afonic said:**
> 
[http://wiki.archlinux.org/index.php/Compiz_fusion](http://wiki.archlinux.org/index.php/Compiz_fusion)
and
[http://wiki.archlinux.org/index.php/Compiz_Fusion_Git](http://wiki.archlinux.org/index.php/Compiz_Fusion_Git)

What is the difference between the Git version of Compiz Fusion and the "vanilla" version? I looked at the pages, but the difference wasn't explained. (It's not important for my testing box, but I might at some point put Arch on my regular desktop).

---

### Post by pelle.k on 2007-11-14
Well, git, svn, cvs are just versioning systems and that often mean development versions, i.e. bleeding edge.

---

### Post by Acid7711 on 2007-11-14
> **Opeth115 said:**
> Hey thanks for teh responses...  I tried the dbus-launch fusion-icon and compi actually starts now but no emerald is available and no icon appears in the tray.

DAEMONS=(syslog-ng network netfs crond alsa gdm hal fam dbus)

that's my daemons line in rc.conf and i do start gnome through gdm

If you're using the GIT version of it, then it's split into two, fusion-icon (has to be run first), and fusion-icon-tray.  If you're using the community version, fusion-icon should be enough.  Not sure what one you're using.

---

### Post by Acid7711 on 2007-11-14
> **handy said:**
> I installed Arch a month ago & everything went perfectly well until it was time to do the first system update & a worse dependency hell than I ever could have imagined unleashed itself.  So I through my hands up in the air & reinstalled Sabayon.

I know, I took the easy way out. :-)

I also in my years of using Arch have never had a single dependency problem, and I've always enabled the testing repo and pulled in as much bleeding edge stuff as I could through ABS.

---

### Post by ssmithy on 2007-11-14
Hi all!  I installed Arch bout a month ago and I find myself loving it more every day.  I even used K.Mandla's blog [howto]("http://kmandla.wordpress.com/2007/10/27/howto-shut-down-linux-from-the-openbox-right-click-menu/") (thanks, btw!) to set up Openbox to shutdown using the right-click menu.  

I'm still mucking through a few things but overall my Linux knowledge has really beefed up over the last few weeks.  And the AUR is a great feature.  Simple and powerful.

---

### Post by mivo on 2007-11-14
Speaking of Compiz Fusion -- I installed the Git version now, added "compiz fusion" to the autostart programs (the eye as well), and it does start and works (cube), but none of my windows have title bars now. *metacity --replace &* fixes that, but then Compiz Fusion is no longer running. :)

---

### Post by fwojciec on 2007-11-14
> **ssmithy said:**
> I even used K.Mandla's blog [howto]("http://kmandla.wordpress.com/2007/10/27/howto-shut-down-linux-from-the-openbox-right-click-menu/") (thanks, btw!) to set up Openbox to shutdown using the right-click menu. 

Here is my take on the idea K.Mandla's howto describes...  One thing I've found annoying about having the "halt" command called directly from the OB menu was that occasionally, especially when using my laptop which has a touchpad that can work a bit erratically at times, I would accidentally choose it from the menu while trying to select something else - if that happens all windows instantly shut down which, obviously, makes you loose unsaved work and such... 

So I wanted to have "Shutdown" in OB menu call a dialog window that would let me confirm if I really wanted to shutdown or not.  This can be achieved by calling a little bash script instead of the halt command from the OB menu.  Here is a version of the script I use (it requires installing "**zenity**" package):
> #!/bin/bash
if zenity --question --title="Shutdown the Computer" --text="Are you sure you want to shutdown the computer?" ; then
    sudo /sbin/halt
fi
This script must be made executable with chmod +x before it will work; also the halt command must be in the sudoers file like K.Mandla's howto describes.  
Then it's just the matter of creating a menu item that will call the script, or one could also bind it to a key combination which works great and is safe - because you will be asked for a confirmation before anything drastic happens ;)

I also use similar scripts for suspending, hibernating and rebooting - it should be easy to use the script as a template and revise it to perform whatever function you'd like to confirm before executing.

---

### Post by ssmithy on 2007-11-14
Thanks for posting this.  Using a script as you've described sounds like a wonderful idea!  I'm going to try this out later tonight.

---

### Post by crimesaucer on 2007-11-14
> **mivo said:**
> Speaking of Compiz Fusion -- I installed the Git version now, added "compiz fusion" to the autostart programs (the eye as well), and it does start and works (cube), but none of my windows have title bars now. *metacity --replace &* fixes that, but then Compiz Fusion is no longer running. :)

For Compiz Fusion's emerald window themes:

```
emerald --repalce &
```

also, the real way to do it is to goto your menu's:

Settings-->--Compiz Fusion Icon and then click it.

Then select Emerald as your preferred window borders. That should make Emerald work when you run the "fusion-icon" command from either the Alt+f2 or from the command from the Autostarted Applications.

---

### Post by finferflu on 2007-11-14
> **crimesaucer said:**
> For Compiz Fusion's emerald window themes:

```
emerald --repalce &
```

also, the real way to do it is to goto your menu's:

Settings-->--Compiz Fusion Icon and then click it.

Then select Emerald as your preferred window borders. That should make Emerald work when you run the "fusion-icon" command from either the Alt+f2 or from the command from the Autostarted Applications.
ah! finally, I've been running Emerald from a terminal every time, since I had no window borders. Let's see if this does the trick now :D

---

### Post by RedSquirrel on 2007-11-14
> **crimesaucer said:**
> Yes, pacman is a very nice package manager.

I find that maiking packages from the AUR is so much easier than any other time that I built packages with ./configure make and make install, or whatever the README and INSTALL files said to do.

With pacman and the AUR, just one simple "makepkg -s" command, and then the install command of "pacman -U package.0.1-i686-.pkg.tar.gz" and everything is all done...

I had a bit of time today so I setup a PKGBUILD file which I use together with versionpkg to pull down the latest Fluxbox SVN code and build a package. Now that everything is in place, simply running 'versionpkg' in my build directory takes care of everything. Remarkably easy. (versionpkg does have a handful of options which may come in handy from time to time.)



> **K.Mandla said:**
> Another vote for pacman. I actually prefer it to aptitude. I love being able to feed it a local package and have it install dependencies across the Internet. For some reason I always end up doing that in two steps with Ubuntu -- *dpkg -i* and then *apt-get install -f*. ... 

It's a trivial difference, but for some reason it highlights Arch's simplicity and elegance -- for me, at least.

I didn't use aptitude all that much on Ubuntu. I used dpkg, apt-get, apt-cache, apt-mark,... so it's a big step up for me in terms of convenience to use one package manager command (pacman) for almost everything (installing, removing, querying, etc.).

Arch is looking better (to me) every day. :)

---

### Post by mivo on 2007-11-14
> **crimesaucer said:**
> also, the real way to do it is to goto your menu's: Settings-->--Compiz Fusion Icon and then click it. Then select Emerald as your preferred window borders. 

Thanks! That worked wonderfully. Turned out to be easier than I feared. :) Only a bit more involved than clicking "desktop effects" in Ubuntu, but there is also more choice now. (the 3D windows, Atlantis plugin, etc.)

---

### Post by PurposeOfReason on 2007-11-15
Hey, I have a quick question regarding wireless before I go out and get a new laptop. I've used arch before but never with wireless, this laptop comes with an Intel 4965 AGN wireless card. If I read the wiki right, I should just be able to do a 'pacman -S iwlwifi iwlwifi-4965-ucode' and then throw in 'ipw3945d' into the /etc/rc.conf file under the Daemons, preferably at the beginning and I should be all set. Then after that it's just up to me to play with the settings to choose networks and that's all I don't really understand with the wiki; probably because I just browsed it and am too tired. But that should be it, right? If anyone wants to share helpful hints on roaming and getting all that, I'm all ears. :) It'll probably be a lot easier with the computer actually in front of me.

---

### Post by raul_ on 2007-11-15
iwl and ipw are different modules. I just load my iwl3945 module and it's good to go

---

### Post by pelle.k on 2007-11-15
> **raul_ said:**
> iwl and ipw are different modules. I just load my iwl3945 module and it's good to go

I think you might be a bit tired too ;)
The iwl4965 module (+ firmware) is the module he needs (unless i missed something obvious). I had this card in a laptop i had (for two weeks), and the native driver was a bit temperamental. I had to manually bring it up, and trick it to associate with the AP by listing networks and stuff though...
I ended up using the windows driver (not the most recent) with ndiswrapper instead. But, from what i see, the native driver is updated quite often ATM, so maybe you'll have better luck than me.

[edit]the ipw3945 is, to my knowing, not something you need with this setup, because that is a whole other card...[/edit]

---

### Post by raul_ on 2007-11-15
That's what I mean. with the iwl module you don't need the ipw daemon running

---

### Post by mivo on 2007-11-15
I didn't mean to do it this soon, but I now installed Arch on my production desktop. Surprisingly, it turned out to be the first distro that didn't choke on the hardware or require special boot options (or throw errors while booting). I'll spend all day tomorrow customizing stuff and tweaking fonts (I hope I can reproduce Ubuntu's excellent font rendering), and it is all your guys' fault! ;)  My boot-up time got cut into half ...

---

### Post by david_2001 on 2007-11-15
> **mivo said:**
> I didn't mean to do it this soon, but I now installed Arch on my production desktop. Surprisingly, it turned out to be the first distro that didn't choke on the hardware or require special boot options (or throw errors while booting). I'll spend all day tomorrow customizing stuff and tweaking fonts (I hope I can reproduce Ubuntu's excellent font rendering), and it is all your guys' fault! ;)  My boot-up time got cut into half ...
Font rendering could easily be worse than what I got after no particular effort at all.

---

### Post by pelle.k on 2007-11-15
I'm either very lucky, or maybe i need glasses, because i've never even touched those font rendering settings, ever, in neither arch *or* ubuntu. I never noticed any big difference, but still, i've seen screenshots comparing diffrent distros, and the thing i react to is that people seem to think the "other" screenshot is better than the "first" (using different font rendering settings obviously), but from my perspective it's often the other way around. (the font rendering on the screenshots).
I think it depends largely on what monitor you've got, and not if the rendering is "good" or not. Does it "fit" your particular display setup that is.

---

### Post by Rumor on 2007-11-15
> **mivo said:**
> I didn't mean to do it this soon, but I now installed Arch on my production desktop. Surprisingly, it turned out to be the first distro that didn't choke on the hardware or require special boot options (or throw errors while booting). I'll spend all day tomorrow customizing stuff and tweaking fonts (I hope I can reproduce Ubuntu's excellent font rendering), and it is all your guys' fault! ;)  My boot-up time got cut into half ...

I always install the liberation fonts package and the ms-ttf package. From there I use the gnome theme panel to choose the default application fonts. The liberation fonts are quite nice, IMO.
```
pacman -S ttf-liberation ttf-ms-fonts
```

---

### Post by crimesaucer on 2007-11-15
> **pelle.k said:**
> I'm either very lucky, or maybe i need glasses, because i've never even touched those font rendering settings, ever, in neither arch *or* ubuntu. I never noticed any big difference, but still, i've seen screenshots comparing diffrent distros, and the thing i react to is that people seem to think the "other" screenshot is better than the "first" (using different font rendering settings obviously), but from my perspective it's often the other way around. (the font rendering on the screenshots).
I think it depends largely on what monitor you've got, and not if the rendering is "good" or not. Does it "fit" your particular display setup that is.

Using this "fonts.conf" file in my /home/folder:

```

<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>

```

My fonts look much better in apps like the mousepad and the terminal. The same was true for me with xubuntu.


With Archlinux, my fonts were very nice using the regular font settings in both Gnome and Xfce4. But this added .conf file fixes the written text in my mousepad app.

---

### Post by regomodo on 2007-11-16
Grr. I've run into a major roadblock with Arch recently. Just got a heap of new bits and Arch64 doesn't want to play with it. No matter what i try i get kernel panics. I'll list my new hardware just incase peeps know any issus with them and Arch. There shouldn't be as Kubuntu64 seems to work well with my setup

Intel C2D e6750
nvidia 8800gt
oztech 4GB ddr800 ram
xfx nvidia 680i sli lt motherboard

Ubuntu cd refused to boot up so i thought sod it and tried Kubuntu. So far i'm impressed with the hardware detected including my logitech cordless trackman and it's the first ever OS/distro to get my screen's resolution correct !
So far Kubuntu is nice but i want Arch's goodness.

---

### Post by mindtrick on 2007-11-16
W00t! After playing with Slackware for a week, I am back to Arch to stay. It makes you appreciate Arch more :mrgreen:

---

### Post by Rumor on 2007-11-16
> **regomodo said:**
> 
Intel C2D e6750
nvidia 8800gt
oztech 4GB ddr800 ram
xfx nvidia 680i sli lt motherboard


Well, I know the nVidia card isn't the issue as I have one too. I've also got 4 gigs of ram as well. I wouldn't think one brand would be much different than any other. My processor is a quad core and the motherboard is made by Gigabyte.

Have you tried re-installing the kernel from the CD and then updating to current?

---

### Post by afonic on 2007-11-16
> **regomodo said:**
> Grr. I've run into a major roadblock with Arch recently. Just got a heap of new bits and Arch64 doesn't want to play with it. No matter what i try i get kernel panics. I'll list my new hardware just incase peeps know any issus with them and Arch. There shouldn't be as Kubuntu64 seems to work well with my setup

Intel C2D e6750
nvidia 8800gt
oztech 4GB ddr800 ram
xfx nvidia 680i sli lt motherboard

Ubuntu cd refused to boot up so i thought sod it and tried Kubuntu. So far i'm impressed with the hardware detected including my logitech cordless trackman and it's the first ever OS/distro to get my screen's resolution correct !
So far Kubuntu is nice but i want Arch's goodness.

Can you start with the Fallback kernel?

There was an issue with one of the ISO releases recently which generated kernel panics. The solution is to boot the Fallback kernel (which does work) and run "mkinitcpio -p kernel26" as root.

---

### Post by mivo on 2007-11-16
> **pelle.k said:**
> I'm either very lucky, or maybe i need glasses, because i've never even touched those font rendering settings, ever, in neither arch *or* ubuntu. [...] I think it depends largely on what monitor you've got, and not if the rendering is "good" or not. Does it "fit" your particular display setup that is.

The fonts in Ubuntu, Fedora and Arch look different to me on the same machine, same monitor (22" LCD), same video card and with the same font settings. :-k It's really curious. With different settings I got the fonts to look superb in Arch now, though! Only problem child is Firefox, which renders web page fonts noticeably different than Epiphany, even though both use the Gecko engine. Even if I force both to use the same local fonts (rather than the web page's ones), they still produce different results. I actually use Epiphany now, which runs smoother and looks better. Just had to find out how you can actually configure it, since the preferences dialog offered very little in the way of options. ;)

Compiz-Fusion and AWN are running now as well, and the system is still snappier. Still have some smaller issues like Evolution ignoring aspell and not offering spellchecking (all other apps do), and I have yet to install a 32-bit alternate browser for "real" Java plugins (using arch64 here). But there's something in AUR. AUR, by the way, I am rapidly falling in love with.

---

### Post by regomodo on 2007-11-16
> **afonic said:**
> Can you start with the Fallback kernel?

There was an issue with one of the ISO releases recently which generated kernel panics. The solution is to boot the Fallback kernel (which does work) and run "mkinitcpio -p kernel26" as root.

On the 1st install attempt, no. I forgot to check other times as i changed from root being xfs to ext3. It was a vain attempt to figure out what was going on.

I'm going to try it again later with a different cd as i've been stung in the past with a dodgy burn (segfaults), which i never thought was possible until once with Arch

---

### Post by Frak on 2007-11-16
Does anybody else besides me use sudo in arch?
```
echo '**username** ALL=(ALL) ALL' >> /etc/sudoers
```

---

### Post by pelle.k on 2007-11-16
> I'm going to try it again later with a different cd as i've been stung in the past with a dodgy burn (segfaults), which i never thought was possible until once with Arch
Try the new installation cd. It isn't released yet, but you can still get it;
[http://bbs.archlinux.org/viewtopic.php?id=38964](http://bbs.archlinux.org/viewtopic.php?id=38964)

> Does anybody else besides me use sudo in arch?
Since i always run makepkg as a regular user (usesudo) to get dependencies installed, i have to install sudo.
Doing stuff like that as root is not a very bright idea...

---

### Post by crimesaucer on 2007-11-16
> **pelle.k said:**
> Try the new installation cd. It isn't released yet, but you can still get it;
[http://bbs.archlinux.org/viewtopic.php?id=38964](http://bbs.archlinux.org/viewtopic.php?id=38964)


Since i always run makepkg as a regular user (usesudo) to get dependencies installed, i have to install sudo.
Doing stuff like that as root is not a very bright idea...

Certain scripts like the "install-swiftfox.sh"  shell script have the sudo command in it. Plus, I needed to had to add a line to my sudoers file to be able to restart and shutdown from within the xfce4 desktop.

```
username ALL=(root) NOPASSWD: /usr/lib/xfce4/xfsm-shutdown-helper
```

---

### Post by Rumor on 2007-11-16
> **Frak said:**
> Does anybody else besides me use sudo in arch?

Yep, I use it. Usually only for reboot command or updatedb.

---

### Post by regomodo on 2007-11-16
> **Frak said:**
> Does anybody else besides me use sudo in arch?
```
echo '**username** ALL=(ALL) ALL' >> /etc/sudoers
```

yep. i use it

---

### Post by Opeth115 on 2007-11-16
Im using kdemod and it just wont recognize that i have java installed... Is there something i have to do specially?  I installed it with pacman -S jre and it didn't recognize it so i went and got the tarbell from the website and isntalled it from that and it still doesn't recognize it...

Im trying to get frostwire to work and am having some trouble with it too it says i don't have the latest java which i do because i jsut installed it from the website...

---

### Post by Frak on 2007-11-16
> **Opeth115 said:**
> Im using kdemod and it just wont recognize that i have java installed... Is there something i have to do specially?  I installed it with pacman -S jre and it didn't recognize it so i went and got the tarbell from the website and isntalled it from that and it still doesn't recognize it...

Im trying to get frostwire to work and am having some trouble with it too it says i don't have the latest java which i do because i jsut installed it from the website...
You'll probably have to update the script that executes it to lead it to the correct java path in /opt/

---

### Post by david_2001 on 2007-11-16
> **regomodo said:**
> yep. i use it

> **Frak said:**
> Does anybody else besides me use sudo in arch?
```
echo '**username** ALL=(ALL) ALL' >> /etc/sudoers
```
I use it too.

---

### Post by Opeth115 on 2007-11-16
> **Frak said:**
> You'll probably have to update the script that executes it to lead it to the correct java path in /opt/

how owuld i go about doing that?  It doesn't even say i have java installed if i do a:

java -version

---

### Post by raul_ on 2007-11-16
> **david_2001 said:**
> I use it too.

I think everybody does

---

### Post by david_2001 on 2007-11-16
> **raul_ said:**
> I think everybody does
There's no reason why not.  I've disabled the root account on mine as well.

---

### Post by afonic on 2007-11-16
> **Opeth115 said:**
> how owuld i go about doing that?  It doesn't even say i have java installed if i do a:

java -version
Thats because it is not installed in /usr/bin.

See:
> [afonic@afonic-arch ~]$ /opt/java/bin/java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)
[afonic@afonic-arch ~]$ 


---

### Post by Opeth115 on 2007-11-16
> **afonic said:**
> Thats because it is not installed in /usr/bin.

See:
 ok well i did this

```
[root@Matt's-Room matt]# /opt/java/jre/bin/java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

```

but would i get frostwire to use jave there? do i jsut move it to /usr/bin?
also how would i get konqueror to see it as being there?

---

### Post by Frak on 2007-11-16
> **Opeth115 said:**
> ok well i did this

```
[root@Matt's-Room matt]# /opt/java/jre/bin/java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

```

but would i get frostwire to use jave there? do i jsut move it to /usr/bin?
also how would i get konqueror to see it as being there?
You need to add /opt/ to your $PATH
```
PATH=$PATH:/opt/
```

EDIT
Forgot that changes aren't saved, so you'll have to add :/opt/ to your ~/.bashrc file

---

### Post by Opeth115 on 2007-11-16
> **Frak said:**
> You need to add /opt/ to your $PATH
```
PATH=$PATH:/opt/
```

All i do is just put that command in the terminal?  I did that and it still does the same thing...  Srry for sounding so noobish im still kinda new to this...

---

### Post by finferflu on 2007-11-16
You could also try to symlink it to /usr/bin, it should work:

```
ln -s /opt/java/jre/bin/java /usr/bin/java
```

I'm not sure this is the optimal solution, though...

---

### Post by Opeth115 on 2007-11-16
thanks for that finforflu it worked!  and thank you frak also!

im still looking for a solution to my compiz errors though...  The arch forums are really slow compared to here lol.

i get this error when trying to launch fusion-icon in kdemod

dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute dbus-launch to autolaunch D-Bus session

here is my daemons line in my /etc/rc/conf

DAEMONS=(syslog-ng hal network fam netfs crond alsa)

if i do a dbus-launch fusion-icon compiz starts and i ge tthe effects but no windowborders and no icon in the tray...

any ideas?

---

### Post by pelle.k on 2007-11-16
you *need* to run your session with dbus. This is normally done automatically with kdm/gdm. How do you start kde?

---

### Post by Frak on 2007-11-16
> **pelle.k said:**
> you *need* to run your session with dbus. This is normally done automatically with kdm/gdm. How do you start kde?
Did you add kdm to your daemons list?

---

### Post by Opeth115 on 2007-11-17
> **Frak said:**
> Did you add kdm to your daemons list?

i start my sessions with startx, is there a way to do it without kdm?

---

### Post by Frak on 2007-11-17
> **Opeth115 said:**
> i start my sessions with startx, is there a way to do it without kdm?
Why not just let the daemon do everything for you?

---

### Post by miggols99 on 2007-11-17
> **Opeth115 said:**
> thanks for that finforflu it worked!  and thank you frak also!

im still looking for a solution to my compiz errors though...  The arch forums are really slow compared to here lol.

i get this error when trying to launch fusion-icon in kdemod

dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute dbus-launch to autolaunch D-Bus session

here is my daemons line in my /etc/rc/conf

DAEMONS=(syslog-ng hal network fam netfs crond alsa)

if i do a dbus-launch fusion-icon compiz starts and i ge tthe effects but no windowborders and no icon in the tray...

any ideas?

For window borders I had to install libbonoboui (with a few gnome dependencies). For the tray icon I think it's fusion-icon-tray.

---

### Post by K.Mandla on 2007-11-17
Is anyone having trouble with audacious playing streaming mp3s? The last update a few days ago seemed to have disrupted its ability to play tunes off the Internet. Any suggestions? I'm thinking about dropping back to the previous version. (This happened before, maybe nine months ago, when it went from 1.2 to 1.3, I think.)

---

### Post by Opeth115 on 2007-11-17
> **Frak said:**
> Why not just let the daemon do everything for you?

well i added kdm to my daemons line and no i get the,


No GLX_EXT_texture_from_pixmap error gotta find a solution to that now lol...

I have a nvidia card and i know it supports it


EDIT:  Gah this is confusing me like hell....  IT's back to that original error message now with kdm loaded as a daemon...

here's my daemon's list

DAEMONS=(syslog-ng hal network fam netfs crond alsa kdm)

i don't understand why it's this complicated i've had arch up and running before with no problems....  Not that it's really a problem lol it's just an annoying tick i wanna get by really lol

ok wait if i start fusion-icon from my normal user it gives me that original error of dbus not being loaded...  But if i do it as root then it gives me the No GLX_EXT_texture_from_pixmap error...  how could this be?

---

### Post by Frak on 2007-11-17
Sounds like Fusion doesn't like your configuration. Make sure you changed your xorg.conf file to work with your card.

---

### Post by afonic on 2007-11-17
Actually I had some trouble with KDE and Compiz Fusion from the Git repository (although it works fine in Gnome)

Which repository did you install from? Maybe it is worth it uninstalling and trying the other one, if you are 100% sure your settings (xorg.conf etc) are correct.

---

### Post by Atreus12 on 2007-11-17
I have an older laptop running debian etch with fluxbox as a graphical interface.

I'm pretty happy with it, but I keep hearing about arch. Should I switch to arch? Is it as easy to use as Debian? With fluxbox as a gui on both, will it be faster than Debian?

Is the package selection and management as good as Debian?

Would Arch be beyond my skill level? I installed Debian and built it up using aptitude, but I've never compiled a kernel or stuff like that.

-Andrew

---

### Post by Rumor on 2007-11-17
If you like Fluxbox, you might want to look at Antix. [http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page) 
I have an old PII/266 laptop that runs it just fine. It has a very slick customized Fluxbox desktop running on it. It comes as a live CD with option to install.

Arch is whatever you make it to be. The base install will give you a working Linux environment with only a command line. From there you install whatever applications, desktops, window managers you like. You don't have to compile anything. Arch is binary, so it uses packages that are already built.

The package manager, pacman is (IMO) better than apt. It is fast, and very simple to learn. the package selection for Arch is not as enormous as for Debian, but then nothing is. I've found it to be very complete for what I do. You can search the repositories here: [http://www.archlinux.org/](http://www.archlinux.org/) but keep in mind that there are a lot of packages in the community repository which is not listed on the web site.

Arch is not for everyone, but for many users, there is no other distro that comes close.

Read the beginner's guide: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
Read the Arch Way: [http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)
Those two documents will help you decide if Arch is for you. If you decide to install, let us know how you make out!

---

### Post by mivo on 2007-11-18
> **Rumor said:**
> You can search the repositories here: [http://www.archlinux.org/](http://www.archlinux.org/) but keep in mind that there are a lot of packages in the community repository which is not listed on the web site.

The search option for the AUR community repository is here: [http://aur.archlinux.org/packages.php]("http://aur.archlinux.org/packages.php"). The packages here partly require compiling (this is as simple as typing *makepkg*). If they get enough votes from users, they will become regular binary packages and move on to the "normal" repositories. (Only explaining for Atreus12 because the difference between the regular repositories and the AUR was initially confusing to me. :))

---

### Post by Frak on 2007-11-18
> **Atreus12 said:**
> I have an older laptop running debian etch with fluxbox as a graphical interface.

I'm pretty happy with it, but I keep hearing about arch. Should I switch to arch? Is it as easy to use as Debian? With fluxbox as a gui on both, will it be faster than Debian?

Is the package selection and management as good as Debian?

Would Arch be beyond my skill level? I installed Debian and built it up using aptitude, but I've never compiled a kernel or stuff like that.

-Andrew
Only if you are ready to build your system, literally, from scratch.

---

### Post by raul_ on 2007-11-18
Don't scare him Frak =P
it's true that you build your system from scratch, but you'll see that you don't need many of the junk that comes pre installed in most linux distros.

Besides, most of the commands are in the Arch wiki. It's not really intimidating

---

### Post by Atreus12 on 2007-11-18
Thanks for the links, Rumor. Right now school is eating up all my free time, but I anticipate this as a winter break project.

Arch sounds really intriguing. I actually like the idea of building my own system (provided I can figure it out).

> **Frak said:**
> Only if you are ready to build your system, literally, from scratch.

How different will this be than a Debian install? All I got after my Debian install was a cli bash prompt, with the basics.

From there it was really easy though, I used apt-get to install aptitude, and then just browsed through a list of packages and marked the ones I wanted.

Is doing this in Arch more complicated? For example, when I installed Fluxbox in Debian, it automatically installed xorg as a dependency. Will there be a lot more package hunting / configuration in Arch?

-Andrew

Edit: Just browsed through the wiki. Yeah, looks more complicated than a Debian install, but I still want to try it.

---

### Post by pelle.k on 2007-11-18
Many packages seem to have a bare minimum of dependencies tied to them. There used to be a xorg metapackage, but it was removed, and i don't think it's back yet. Other than that, the essentials would be xorg (look in the forum for the bare minimum) + WM/DE + maybe hal/dbus.

It's pretty easy to add packages to that when you have something up and running already. You'll quickly find out what gstreamer/xine extras you need to play mp3s/div content and that sort of stuff. Just make a list of what to include the next time you plan to reinstall.

---

### Post by K.Mandla on 2007-11-18
> **Atreus12 said:**
> I have an older laptop running debian etch with fluxbox as a graphical interface.
Waitaminute. How old? Remember Arch technically only works on i686 and x86-64. If it's too old, it will refuse to run. There's [Lowarch]("http://www.lowarch.org") for i586 and lower, which is almost as good, but is the distro is dead. ...

---

### Post by mivo on 2007-11-18
> **pelle.k said:**
> There used to be a xorg metapackage, but it was removed, and i don't think it's back yet.

Two days ago the xorg meta package was there, for both architectures.

---

### Post by Atreus12 on 2007-11-18
> **K.Mandla said:**
> Waitaminute. How old? Remember Arch technically only works on i686 and x86-64. If it's too old, it will refuse to run. There's [Lowarch]("http://www.lowarch.org") for i586 and lower, which is almost as good, but is the distro is dead. ...

P3 600Mhz. I think this is 686?

---

### Post by miggols99 on 2007-11-18
> **Atreus12 said:**
> P3 600Mhz. I think this is 686?
I have an old P3 that runs Arch fine, so I assume it's i686.

---

### Post by Frak on 2007-11-18
> **miggols99 said:**
> I have an old P3 that runs Arch fine, so I assume it's i686.
All Pentium Pro and above are i686 Processors, that includes:

    * Pentium Pro
    * Pentium II
    * Pentium III
    * Pentium IV
    * Celeron
    * Pentium M
    * Xeon
    * Core

    * Athlon
    * Athlon XP
    * Duron
    * Sempron

    * VIA C3 (Only the Nehemiah or CoreFusion cores)
    * VIA C7

---

### Post by RedSquirrel on 2007-11-18
> **Atreus12 said:**
>  Edit: Just browsed through the wiki. Yeah, looks more complicated than a Debian install, but I still want to try it.

It's not hard. If you read the installation guide before installing, you'll have a good idea of what needs to be done. I found the separate page describing Xorg was helpful:

[http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)

As mentioned earlier in this thread, you might want to consider printing out the install guide and some other parts of the wiki that you want to read. They'll come in handy during the install and perhaps afterwards as well.

The stable version of Fluxbox (1.0.0) is available as a binary:

```
pacman -S fluxbox
```

---

### Post by afonic on 2007-11-19
> **pelle.k said:**
> Many packages seem to have a bare minimum of dependencies tied to them. There used to be a xorg metapackage, but it was removed, and i don't think it's back yet. Other than that, the essentials would be xorg (look in the forum for the bare minimum) + WM/DE + maybe hal/dbus.

It's pretty easy to add packages to that when you have something up and running already. You'll quickly find out what gstreamer/xine extras you need to play mp3s/div content and that sort of stuff. Just make a list of what to include the next time you plan to reinstall.

Actually it was added again, this time as a group:

> [root@afonic-arch afonic]# pacman -S xorg
:: group xorg:
    xf86-input-keyboard  xf86-input-mouse  xf86-video-vesa  xorg-fonts-100dpi  
    xorg-fonts-75dpi  xorg-res-utils  xorg-server  xorg-twm  xorg-xinit  xterm  
:: Install whole content? [Y/n] 


---

### Post by Stalafin on 2007-11-19
Just wanted to ask:
Is archlinux.org down for you guys too (i.e. including bbs.archlinux.org and wiki.archlinux.org).
I can't access any of them since yesterday evening (CET that is).

---

### Post by K.Mandla on 2007-11-19
> **Frak said:**
> All Pentium Pro and above are i686 Processors, that includes. ...
The sad part is that it *doesn't* include AMD's K6 line, which means you can have a 450Mhz machine that would just scream along with Arch ... except it's the i586 architecture, and Arch will stonewall you on it.

But if that's the case, I'm with you in that boat. :|

---

### Post by mivo on 2007-11-19
> **Stalafin said:**
> Just wanted to ask:
Is archlinux.org down for you guys too (i.e. including bbs.archlinux.org and wiki.archlinux.org).
I can't access any of them since yesterday evening (CET that is).

Works here, forums, the repos, and the rest of the site.

---

### Post by finferflu on 2007-11-19
> **Stalafin said:**
> Just wanted to ask:
Is archlinux.org down for you guys too (i.e. including bbs.archlinux.org and wiki.archlinux.org).
I can't access any of them since yesterday evening (CET that is).

Same here, *again*... oh noooo! :(

---

### Post by raul_ on 2007-11-19
Nothing wrong here. My ip is blocked at the KDEmod forums though. First time I saw anything like it

---

### Post by crimesaucer on 2007-11-19
[http://aur.archlinux.org/](http://aur.archlinux.org/) and the homepage are working for me, I just built Brasero from the AUR.

---

### Post by finferflu on 2007-11-20
Ok, it's finally back again for me... this is getting annoying...

---

### Post by handy on 2007-11-20
> **pelle.k said:**
> My answer will make me look like a total jerk, i know. But i really have to say that in my two years using arch, i have *never* encountered a single dependency error. Did you miss the  switch from current to core, or did you add a testing/unofficial repo? i.e. human error?

Sorry for the long time between posts, I hadn't expected any replies to my post.

Perhaps I made a mistake, though I certainly am a careful reader with a slow methodical mind, but I certainly have made mistakes & will make them again for sure ;-)

I had just spent days on a Gentoo install or two, reading very carefully & failing, quite possible due to my BIOS, but I can not be sure on that either...

---

### Post by Dimitriid on 2007-11-21
I need a Bon Echo specific tip: a minor thing is that some websites ( not all, depending on how they link ) open videos with whatever video plugin I use ( i tried mplayer and totem plugins ) even if its a link and not embedded. On the file types by clicking on "Manage" the list is usually blank so I can't change the behavior ( there is no create button to make the extension type myself )

I got a pluging called MIMO Edit and now they are on the list ( the ones I manually introduce with that plugin ) but changing the behavior does not seems to take effect. Any ideas?

---

### Post by crimesaucer on 2007-11-21
> **Dimitriid said:**
> I need a Bon Echo specific tip: a minor thing is that some websites ( not all, depending on how they link ) open videos with whatever video plugin I use ( i tried mplayer and totem plugins ) even if its a link and not embedded. On the file types by clicking on "Manage" the list is usually blank so I can't change the behavior ( there is no create button to make the extension type myself )

I got a pluging called MIMO Edit and now they are on the list ( the ones I manually introduce with that plugin ) but changing the behavior does not seems to take effect. Any ideas?

I use xine-ui with the Firefox "MediaPlayerConnectivity" plug-in. It works every time. 


The video isn't embedded, but it works good and usually is faster with a better picture. Plus, that Firefox add-on can choose which media player it uses for Windows Media, Real, Quicktime, MP3, OGG...

---

### Post by insane_alien on 2007-11-21
i've just got arch up and running (WICD is being a pain in the *** though, might hae to revert to WEP for a while) and wow. i like it.

thinking of switching to it because i like the rolling release aspect. the biggest problem i've had so far is that the time was wrong and refused to change. bu i got that sorted.

---

### Post by Dimitriid on 2007-11-21
Today on pacman I got the following ```
core is up to date
 extra is up to date
 community is up to date
:: Starting full system upgrade...
warning: cpufrequtils: forcing upgrade to version 002-3
warning: dnsutils: forcing upgrade to version 9.4.1_P1-3
warning: iwlwifi-3945-ucode: forcing upgrade to version 2.14.1.5-2
warning: iwlwifi-4965-ucode: forcing upgrade to version 4.44.1.18-2
resolving dependencies... done.

```

Then there is something like 120mb of updates. Are there really this many new updates? ( Front Arch Page says they were redoing core completely ) The first check saying up to date kinda throw me off a bit.

---

### Post by K.Mandla on 2007-11-22
Yeah, I had a whole slew of downloads yesterday and a clean install today is occasionally spitting out cryptic error messages. Nothing critical, but it does make me wonder.

---

### Post by ynnhoj on 2007-11-22
> **Dimitriid said:**
> Today on pacman I got the following ```
core is up to date
 extra is up to date
 community is up to date
:: Starting full system upgrade...
warning: cpufrequtils: forcing upgrade to version 002-3
warning: dnsutils: forcing upgrade to version 9.4.1_P1-3
warning: iwlwifi-3945-ucode: forcing upgrade to version 2.14.1.5-2
warning: iwlwifi-4965-ucode: forcing upgrade to version 4.44.1.18-2
resolving dependencies... done.

```

Then there is something like 120mb of updates. Are there really this many new updates?
yeah, they've rebuilt the core packages to take advantage of some recent gcc or glibc updates; i didn't realize they had moved everything from [testing] to [core] already, though..

---

### Post by mivo on 2007-11-22
I got the 120 MB updates on two different machines (one 32-bit installation, one 64-bit installation) and even though I was a little nervous about it, neither box experienced any trouble. No error messages that I could see, either.

Discovering yaourt made me appreciate the AUR even more. What a splendid packaging system Arch has!

---

### Post by finferflu on 2007-11-22
> **mivo said:**
> What a splendid packaging system Arch has!

Will you ever be able to stop saying that? I can't. :D
The more I use it, the more I love it. Talk about ideal distro.

---

### Post by Tenken on 2007-11-22
I justed installed Arch on my laptop and I'm trying openbox for the first time. I like the look of pypanel, can anyone point me to a good beginners guide? The Arch wiki and PyPanel home page don't have much for me to go on.

---

### Post by crimesaucer on 2007-11-22
> **finferflu said:**
> Will you ever be able to stop saying that? I can't. :D
The more I use it, the more I love it. Talk about ideal distro.

I think I'll be with this distro for a while. Everything has been a really good linux experience. My only negative comment would be that the forum is not very active like this forum is. But, usually, if it's a question that matters, it does get answered.

I also think that Archlinux expects their users to search a bit, and figure problems out for them-selves before posting and questions.

---

### Post by Frak on 2007-11-22
> **crimesaucer said:**
> I think I'll be with this distro for a while. Everything has been a really good linux experience. My only negative comment would be that the forum is not very active like this forum is. But, usually, if it's a question that matters, it does get answered.

I also think that Archlinux expects their users to search a bit, and figure problems out for them-selves before posting and questions.
It's the same on this forum. The experts expect you to have searched google and have had read the man page and/or documentation.

---

### Post by crimesaucer on 2007-11-22
> **Frak said:**
> It's the same on this forum. The experts expect you to have searched google and have had read the man page and/or documentation.

Yeah, but I've answered a lot of questions on this Ubuntu forum (mostly theme questions about gtkrc and the gtktr-2.0 for the panel), and I see a lot of the same questions asked (that are easily searched in the Ubuntu search, and Google search engines), and the difference is that there are so many people that are active on this forum, that it's almost a completion to answer the question first... even if it's a really simple question that could be found in a few minutes worth of searching. Sometimes it seems better to just save the 10-20 minutes of searching because so many users already know the answer and love to add to their bean count by answering it.


For example, how many times have you seen someone ask about the panels disappearing?


I know I've answered that one a bunch. I don't mind telling someone "xfce4-panel &". On the Arch Forums, it seems that the questions are usually more complicated and expert than that, and it usually takes a few days for a reply on any question no matter what type of question it is.

---

### Post by Frak on 2007-11-22
> **crimesaucer said:**
> Yeah, but I've answered a lot of questions on this Ubuntu forum (mostly theme questions about gtkrc and the gtktr-2.0 for the panel), and I see a lot of the same questions asked (that are easily searched in the Ubuntu search, and Google search engines), and the difference is that there are so many people that are active on this forum, that it's almost a completion to answer the question first... even if it's a really simple question that could be found in a few minutes worth of searching. Sometimes it seems better to just save the 10-20 minutes of searching because so many users already know the answer and love to add to their bean count by answering it.


For example, how many times have you seen someone ask about the panels disappearing?


I know I've answered that one a bunch. I don't mind telling someone "xfce4-panel &". On the Arch Forums, it seems that the questions are usually more complicated and expert than that, and it usually takes a few days for a reply on any question no matter what type of question it is.
Here, by forum rules, all answers are to be based upon the expectation that the user already searched all available information. That's why even the simplest questions are answered.

---

### Post by K.Mandla on 2007-11-22
> **Tenken said:**
> I justed installed Arch on my laptop and I'm trying openbox for the first time. I like the look of pypanel, can anyone point me to a good beginners guide? The Arch wiki and PyPanel home page don't have much for me to go on.
Hmm. I don't know if I've ever seen a pypanel howto around here. :-k I don't usually use it, because I prefer to run panelless. Maybe someone will share their configuration files. 

You might also check the random Openbox chatter thread. 

[http://ubuntuforums.org/showthread.php?t=190476](http://ubuntuforums.org/showthread.php?t=190476)

I'm fairly confident someone has a panel setup they'll share. It might take a while to sift through that thread though. :shock:

---

### Post by regomodo on 2007-11-22
Does the xorg metapackage include all the packages that were in the old "arch beginners guide".

I cannot for the life of me get ssh to work with the xserver anymore on my fresh install. 

I'm getting xlib errors.

Additionally, the Arduino IDE is still a pita to get working in arduino. It is really trying my patience and i'm about ready to throw my laptop out the window.

[edit] i'm saving my sanity(and laptop) and installing debian testing instead

Don't know if i'll return to arch, for the 3rd time.

---

### Post by crimesaucer on 2007-11-22
> **Frak said:**
> Here, by forum rules, all answers are to be based upon the expectation that the user already searched all available information. That's why even the simplest questions are answered.

Are you talking about Ubuntu Forums? Because if you like to help people in the Absolute Beginners section like I do, then you would see most people ask the easiest of questions... and even if they are the same repeated beginner questions, the mods and more knowledged users usually give a prompt answer with no attitude what so ever. 


Searching before asking may be in the rules, but it sure ain't the way it really is on here. 


But the positive thing about Ubuntu, is that people are so stoked on the distro (me included), that they don't mind answering an easy question that could be found on google or the ubuntu search, and people like to give as much beginner info to anybody interested in Ubuntu or Linux. I usually answer a question about Conky, Compiz Fusion, Emerald, transparent panels images, and gtk themes every other day on this forum, or deviant ART, and StumbleUpon. I enjoy helping with things I've learned from others.

---

### Post by TheRingmaster on 2007-11-22
I've been using arch linux now for a while. I switched from this distro (ubuntu) because i liked the package management alot better and the rolling release setup. I am concidering moving back to ubuntu now because firefox is refusing to start up and i'm forced to use opera :( If i could rate arch, i would put it at number 2 on distrowatch's list. ubuntu still being on top of course. 

If anyone has any questions about arch or needs support you can pm me here or email me. :popcorn:

---

### Post by K.Mandla on 2007-11-23
> **regomodo said:**
> Does the xorg metapackage include all the packages that were in the old "arch beginners guide".
Hmm. I think, although I'm not 100 percent sure, that the xorg metapackage is out. (Is that right, folks?) It was demoted to a group, or that was the plan a month or so ago. There was a big stink about it on the Arch forums because a dev yanked the metapackage without telling anyone, and as a result a buncha people got irritated.

I think now you need to ...

```
# pacman -Sy xorg-server xorg-xinit f86-input-{mouse,keyboard} xf86-video-<mycard> xorg-fonts-<mydpi>
# X -configure
# $EDITOR xorg.conf.new
# mv xorg.conf.new /etc/X11/xorg.conf
```
Is that what you're asking, or do I misunderstand? 8-[

---

### Post by mivo on 2007-11-23
The xorg meta package is out and it includes all the files listed in the Beginner's Guide. :)

```

:: group xorg:
    xf86-input-keyboard  xf86-input-mouse  xf86-video-vesa  xorg-fonts-100dpi
    xorg-fonts-75dpi  xorg-res-utils  xorg-server  xorg-twm  xorg-xinit  xterm

```

---

### Post by finferflu on 2007-11-23
> **TheRingmaster said:**
> I've been using arch linux now for a while. I switched from this distro (ubuntu) because i liked the package management alot better and the rolling release setup. I am concidering moving back to ubuntu now because firefox is refusing to start up and i'm forced to use opera :( If i could rate arch, i would put it at number 2 on distrowatch's list. ubuntu still being on top of course. 

If anyone has any questions about arch or needs support you can pm me here or email me. :popcorn:
I don't know if you're using Gnome, but you could give Epiphany a try. That's what I did, since Firefox was starting to annoy me seriously in matters of resources consumption. Epiphany has some of the Firefox extensions, such as Adblock and Greasemonkey, and it can also integrate with Delicious. In exchange you get a faster and lighter browser, which never hangs or hangs on scrolling a page.
I know it's not the solution, but it could be a good excuse to give it a (serious) go :P
I'm still missing the Vimperator extension though :(

---

### Post by regomodo on 2007-11-23
> **TheRingmaster said:**
> I've been using arch linux now for a while. I switched from this distro (ubuntu) because i liked the package management alot better and the rolling release setup. I am concidering moving back to ubuntu now because firefox is refusing to start up and i'm forced to use opera :( If i could rate arch, i would put it at number 2 on distrowatch's list. ubuntu still being on top of course. 

If anyone has any questions about arch or needs support you can pm me here or email me. :popcorn:

try to run it from a terminal. I got segfaults when my f'fox refused to work. The only cure for that was to reburn arch on a different cd, hoped it wasn't corrupted, and reinstalled arch.

---

### Post by afonic on 2007-11-23
> **mivo said:**
> The xorg meta package is out and it includes all the files listed in the Beginner's Guide. :)

```

:: group xorg:
    xf86-input-keyboard  xf86-input-mouse  xf86-video-vesa  xorg-fonts-100dpi
    xorg-fonts-75dpi  xorg-res-utils  xorg-server  xorg-twm  xorg-xinit  xterm

```

Thats a group not a metapackage. :P

---

### Post by mivo on 2007-11-23
Well, that is what you get with pacman -S xorg. :P Close enough!

---

### Post by Frak on 2007-11-23
Anybody else use yaourt? I find it a great resource.

---

### Post by kellemes on 2007-11-23
> **Frak said:**
> Anybody else use yaourt? I find it a great resource.

What is it?

---

### Post by Frak on 2007-11-23
> **kellemes said:**
> What is it?
It's a pacman frontend for building and installing the packages from AUR.

---

### Post by raul_ on 2007-11-23
I do

---

### Post by afonic on 2007-11-23
> **mivo said:**
> Well, that is what you get with pacman -S xorg. :P Close enough!

True. :)

I posted to let you know since this was the actual change, the metapackage was the removed and a group was added instead. The main difference in the user side is that you can select not to install the whole group and select which packages to install using pacman,

---

### Post by epimer on 2007-11-23
> **Frak said:**
> Anybody else use yaourt? I find it a great resource.

I started using it a couple of days ago. Very useful for AUR stuff, but it's a horrendous name for a CLI program. It takes me 3 or 4 times as long to type "yaourt" as it does "pacman" because it's so unintuitive. Here's hoping it's just a matter of getting used to it...

---

### Post by floke on 2007-11-23
> **TheRingmaster said:**
> I've been using arch linux now for a while. I switched from this distro (ubuntu) because i liked the package management alot better and the rolling release setup. I am concidering moving back to ubuntu now because firefox is refusing to start up and i'm forced to use opera :( If i could rate arch, i would put it at number 2 on distrowatch's list. ubuntu still being on top of course. 

If anyone has any questions about arch or needs support you can pm me here or email me. :popcorn:

You could try Netscape - it's compatible with Firefox plugins so has the same funtionality.

---

### Post by raul_ on 2007-11-23
> **epimer said:**
> I started using it a couple of days ago. Very useful for AUR stuff, but it's a horrendous name for a CLI program. It takes me 3 or 4 times as long to type "yaourt" as it does "pacman" because it's so unintuitive. Here's hoping it's just a matter of getting used to it...

yao<TAB> ;)

---

### Post by Frak on 2007-11-23
> **epimer said:**
> I started using it a couple of days ago. Very useful for AUR stuff, but it's a horrendous name for a CLI program. It takes me 3 or 4 times as long to type "yaourt" as it does "pacman" because it's so unintuitive. Here's hoping it's just a matter of getting used to it...
I just changed the name of yaourt to aurman in my path.

---

### Post by finferflu on 2007-11-23
I not only use yaourt, I also use tupac, which is great for searching packages. It's faster, and it has a nice interactive menu which makes you select multiple packages using number to match them, then it uses yaourt to install them. You don't even have to remember to use sudo to run it, since it asks for the password when needed (I am never prompted for it, since I use sudo without password).
I recommend it ;)

---

### Post by afonic on 2007-11-23
> **epimer said:**
> I started using it a couple of days ago. Very useful for AUR stuff, but it's a horrendous name for a CLI program. It takes me 3 or 4 times as long to type "yaourt" as it does "pacman" because it's so unintuitive. Here's hoping it's just a matter of getting used to it...

yao + TAB = yaourt

---

### Post by raul_ on 2007-11-23
> **finferflu said:**
> I not only use yaourt, I also use tupac, which is great for searching packages. It's faster, and it has a nice interactive menu which makes you select multiple packages using number to match them, then it uses yaourt to install them. You don't even have to remember to use sudo to run it, since it asks for the password when needed (I am never prompted for it, since I use sudo without password).
I recommend it ;)

AHA

me likes it :)

10 times faster than yaourt

---

### Post by afonic on 2007-11-24
And you spend 33% less energy too.

---

### Post by mivo on 2007-11-24
Now if it also brewed coffee, I'd be one happy Archer. ;) (Even happier, that is!)

---

### Post by K.Mandla on 2007-11-24
yaourt is mighty awesome.

---

### Post by raul_ on 2007-11-24
> **K.Mandla said:**
> yaourt is mighty awesome.

Did you try finferflu's sugestion? (tupac) it's really fast searching the aur.

---

### Post by jaybombalous on 2007-11-24
I am now officially a arch user myself. I have been using arch more then ubuntu lately thanks to this thread that got me interested in arch. :)

Love the AUR and pkgbuild's, apt-get is very nice, but I think I prefer pacman and the rolling release that arch linux provides.

---

### Post by epimer on 2007-11-24
> **raul_ said:**
> yao<TAB> ;)

Ah yes, but the problem is that I can never remember if it's "yaourt" or "yauort"! Which is really my fault and not that of the program, but still... :P

Going to check out tupac now.

---

### Post by Rumor on 2007-11-24
> **Tenken said:**
> I justed installed Arch on my laptop and I'm trying openbox for the first time. I like the look of pypanel, can anyone point me to a good beginners guide? The Arch wiki and PyPanel home page don't have much for me to go on.

I am no expert on pypanel. A screenshot of mine is below and the .pypanelrc file as well. If you install pypanel, you'll have a sample config file somewhere on your hard drive, or you can find one online and edit it to suit your preferences. It is fairly well commented. I don't know of any beginners guides. I looked through a few pypanelrc files and the related screenshots to learn what the different sections of the file configured and then made mine to suit my use.

[IMG]http://img.photobucket.com/albums/v304/WhirledPeas/pypanel.png[/IMG]

```
#------------------------------------------------------------------------------

#

#                         PyPanel v2.4 Configuration

#

# This configuration file is a Python script that will be executed when

# PyPanel is started.  In order for PyPanel to start properly, make sure that

# this file contains proper Python formatting and no syntax errors.

#------------------------------------------------------------------------------

VERSION         = 2.4           # Config file version



#------------------------------------------------------------------------------

# Colors: Format is hex triplet - 0xrrggbb

#------------------------------------------------------------------------------

BG_COLOR        = "0xd6d6d6"    # Panel background and tinting color

TASK_COLOR      = "0xFFFFFF"    # Normal task name color 

FOCUSED_COLOR   = "0x1826de"    # Focused task name color

SHADED_COLOR    = "0x808080"    # Shaded task name color 

MINIMIZED_COLOR = "0x808080"    # Minimized task name color 

DESKTOP_COLOR   = "0xFFFFFF"    # Desktop name color

CLOCK_COLOR     = "0xFFFFFF"    # Clock text color

LINE_COLOR      = "0x606060"    # Vertical line color



# Text Shadow Colors

TASK_SHADOW_COLOR      = "0xffffff"

FOCUSED_SHADOW_COLOR   = "0xffffff"

SHADED_SHADOW_COLOR    = "0xffffff"

MINIMIZED_SHADOW_COLOR = "0xffffff" 

DESKTOP_SHADOW_COLOR   = "0xffffff"

CLOCK_SHADOW_COLOR     = "0xffffff"



#------------------------------------------------------------------------------

# Panel Spacing and Location Options: Measured in pixels

#------------------------------------------------------------------------------

P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom

P_WIDTH         = 0             # Panel width: 0 = Use full screen width

P_START         = 0             # Starting X coordinate of the panel

P_SPACER        = 12            # Spacing between panel objects

P_HEIGHT        = 48            # Panel height



#------------------------------------------------------------------------------

# Icon Size Options: Measured in pixels

#------------------------------------------------------------------------------

I_HEIGHT        = 16            # Panel application icon height

I_WIDTH         = 16            # Panel application icon Width 

APPL_I_HEIGHT   = 48            # Application launcher icon height

APPL_I_WIDTH    = 48            # Application launcher icon width

TRAY_I_HEIGHT   = 24            # System tray icon height (usually 16 or 24)

TRAY_I_WIDTH    = 24            # System tray icon width  (usually 16 or 24)

                                # If TRAY_I_WIDTH is set to 0, then the

                                # width specified by the tray app will be used

                                

#------------------------------------------------------------------------------

# Panel Clock Format: 'man strftime' for detailed formatting options and help

#------------------------------------------------------------------------------

CLOCK_FORMAT    = "%A %m-%d-%Y %I:%M"    # Ex: 2004-09-25 17:45 



#------------------------------------------------------------------------------

# Clock Delay: Seconds between each clock update during periods of inactivity

#------------------------------------------------------------------------------

CLOCK_DELAY     = 20



#------------------------------------------------------------------------------

# Hidden Application List: Apps listed here will not be display on the panel

# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS

# Ex: ["xmms", "xine", "gDesklets"]

#------------------------------------------------------------------------------

HIDE_LIST       = []            

                   

#------------------------------------------------------------------------------

# Hidden Panel Size: Size of the panel when it's hidden/minimized

#------------------------------------------------------------------------------

HIDDEN_SIZE     = 2



#------------------------------------------------------------------------------

# Panel Text Font: This option takes either a traditional or Xft font string 

# Ex: "-schumacher-clean-medium-r-normal-*-12-*-*-*-*-*-*-*"

#     "aquafont-8" 

#------------------------------------------------------------------------------

FONT            = "bitstream vera sans-16"

#FONT		 = "LiberationSans-Regular-24"

#------------------------------------------------------------------------------

# Show All Applications: Show apps from all desktops or just the current

# 0: Disabled - Only applications on the current desktop will be displayed

# 1: Enabled  - Selected apps are moved to the current desktop

# 2: Enabled  - Current desktop is changed to the selected apps desktop

#------------------------------------------------------------------------------

SHOWALL         = 0             # 0, 1 or 2 - see descriptions above



#------------------------------------------------------------------------------

# Show Minimized/Iconified Applications: Show only minimized apps or all apps

# 0: Disabled - Show all applications on the panel

# 1: Enabled  - Show only minimized apps on the panel

#------------------------------------------------------------------------------

SHOWMINIMIZED   = 0



#------------------------------------------------------------------------------

# Application Icon List: List of custom icons for specific applications

# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS

#

# The "default" entry is used for applications with no icon.  If left "",

# PyPanel will use the default icon distributed with the source.

#

# Add entries using the following format -

#     "<application name>" : "<full path to icon>",

#------------------------------------------------------------------------------

ICON_LIST       = {

                   "default" : "",

                   "example" : "/usr/share/imlib2/data/images/audio.png",

                  }

                  

#------------------------------------------------------------------------------

# Application Launch List: Ordered list of icons and applications for the

#                          application launcher.

# 

# Add entries using the following format -

#     ("<executable>", "<full path to icon>")

#------------------------------------------------------------------------------

LAUNCH_LIST     = [

("nautilus", "/usr/share/icons/Tango/48x48/apps/kfm.png"),

("firefox", "/home/matthew/icons/mozilla-firefox.png"),

("pan", "/usr/share/pixmaps/pan.png"),
("liferea", "/usr/share/icons/hicolor/48x48/apps/liferea.png"),
("pidgin", "/usr/share/icons/hicolor/48x48/apps/pidgin.png"),
("miro", "/usr/share/pixmaps/miro-72x72.png"),

("gnome-terminal", "/usr/share/icons/Tango/48x48/apps/gnome-terminal.png"),

("/home/matthew/games/quake3/ioquake3", "/home/matthew/games/quake3/quake3.png"),

("etqw", "/home/matthew/games/etqw/etqw_icon.png"),

("/home/matthew/games/dominions3/dom3", "/home/matthew/games/dominions3/dom3icon.png"),

("pysol", "/usr/share/icons/hicolor/48x48/apps/gnome-freecell.png"),

("/opt/openoffice/program/soffice -writer", "/usr/share/icons/hicolor/48x48/apps/writer.png"),

("brasero", "/usr/share/icons/hicolor/48x48/apps/gnomebaker-48.png"),



                  ]



#------------------------------------------------------------------------------

# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)

# BG_COLOR is used for tinting

#------------------------------------------------------------------------------

SHADE           = 0



#------------------------------------------------------------------------------

# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No

#------------------------------------------------------------------------------

ABOVE           = 1             # Panel is always above other apps

APPICONS        = 1             # Show application icons

AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above

SHADOWS         = 0             # Show text shadows

SHOWLINES       = 0             # Show object seperation lines

SHOWBORDER      = 0             # Show a border around the panel



#------------------------------------------------------------------------------

# Desktop Names: Configure the names of your desktops

# If the option is [], PyPanel will attempt to use the desktop name specified

# by the XServer, if that fails it will use the desktop number as its name

# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]

#------------------------------------------------------------------------------

DESKTOP_NAMES   = ["Desktop 1", "Desktop 2", "Desktop 3", "Desktop 4"]



#------------------------------------------------------------------------------

# Panel Layout:       -----------------------------------

#                     [  1  ][  2  ][  3  ][  4  ][  5  ]

#                     -----------------------------------

#

# The panel layout is split into 5 sections numbered 1, 2, 3, 4 or 5 as shown

# in the diagram above.  Each of the following objects can be enabled by

# assigning it a section number or disabled by assigning it 0:

#------------------------------------------------------------------------------

DESKTOP         = 1             # Desktop name section

TASKS           = 5             # Task names section 

TRAY            = 0             # System tray section

CLOCK           = 0             # Clock section

LAUNCHER        = 2             # Application launcher section



#------------------------------------------------------------------------------

#                       Button Event Function Definitions

#------------------------------------------------------------------------------

# Left click   - button 1 

# Middle click - button 2

# Right click  - button 3

# Wheel up     - button 4

# Wheel down   - button 5 

#

# changeDesktop(x)

# - Change Desktop: Increase or decrease the current desktop by 'x' amount

# 

# toggleShade(task)

# - Shade or Unshade an application

#

# toggleHidden()

# - Minimize the panel to the top or bottom depending on its start location

#

# toggleMinimize(task, traise=1)

# - Minimize or Unminimize an application and optionally raise it

#

# taskRaise(task, focus=1)

# - Raise an application to the top of the window list and optionally focus it 

#

# taskLower(task, focus=0)

# - Lower an app to the bottom of the window list and optionally focus it

#

# taskFocus(task)

# - Give focus to the selected application, if it has focus then minimize it

#

# showDesktop()

# - Toggle between hiding and unhiding ALL applications

#------------------------------------------------------------------------------



#----------------------------------

def desktopButtonEvent(pp, button):

#----------------------------------

    """ Button event handler for the panel's desktop object """

        

    if button == 1:

        pp.changeDesktop(-1)

    elif button == 2:

        pp.changeDesktop(2)

    elif button == 3:

        pp.changeDesktop(1)

    elif button == 4:

        pp.changeDesktop(1)

    elif button == 5:

        pp.changeDesktop(-1)

        

#--------------------------------

def clockButtonEvent(pp, button):

#--------------------------------

    """ Button event handler for the panel's clock object """

    

    if button == 1:

        os.system("xclock &")

    elif button == 2:

        pass

    elif button == 3:

        pp.toggleHidden()  

    elif button == 4:

        pp.showDesktop()

    elif button == 5:

        pp.showDesktop()

        

#--------------------------------

def panelButtonEvent(pp, button):

#--------------------------------

    """ Button event handler for the panel with no active tasks """

    

    if button == 1:

        pass

    elif button == 2:

        pass

    elif button == 3:

        pass

    elif button == 4:

        pass

    elif button == 5:

        pass

        

#-------------------------------------

def taskButtonEvent(pp, button, task):

#-------------------------------------

    """ Button event handler for the panel's tasks """

    

    if button == 1:

        pp.taskFocus(task)

    elif button == 2:

        # Destroy the application

        task.obj.destroy()

    elif button == 3:

        # Ex. - XMMS doesn't shade, so we want to minimize it instead and

        #       still use button 3 to shade other applications

        #       task.tclass is the tasks class name (WM_CLASS)

        if "xmms" in task.tclass:

            pp.toggleMinimize(task)

        else:

            pp.toggleShade(task)

    elif button == 4:

        pp.taskRaise(task, focus=1)

    elif button == 5:

        pp.taskLower(task, focus=0)

```

---

### Post by Tenken on 2007-11-25
Thanks for the info, that's very. Trying to find info in the 100+ page  openbox thread was slow going.

---

### Post by PurposeOfReason on 2007-12-02
My new laptop came today and so far, arch has been treating it nicely. I'm down to the final things I have to do and none seem to want to work for me. 

The CUPS wiki seems to just stop and I have no idea on what to do now or if I got the right drivers (Epson stylus CX6000)

When I plug in my headphones, no sound comes out and the speakers keep going. Alsamixer only has options for master and pcm so I'm sure I missed a package there, but not sure what. Anything to control brightness would be amazing as well.

I'm using slim and right before it appears, it flashes the desktop as it was before I last shutdown.

Last, because it is least important, gensplash. No idea on what to do. I've read I'll have to patch the kernel but I'm not sure with what, or how.

Thanks if anyone can help me with any of these problems.

Sony vaod fv series

---

### Post by K.Mandla on 2007-12-02
> **PurposeOfReason said:**
> I'm using slim and right before it appears, it flashes the desktop as it was before I last shutdown.
Last shutdown or last reboot? I know I get leftover images from video memory if I don't shutdown completely for about 10 seconds or so. In other words, I believe that's normal.

---

### Post by PurposeOfReason on 2007-12-02
> **K.Mandla said:**
> Last shutdown or last reboot? I know I get leftover images from video memory if I don't shutdown completely for about 10 seconds or so. In other words, I believe that's normal.
Looks like reboot. With shutdown it just put some weird design, no big deal really. Got the printer to work, I just read the wiki wrong. Next most important, headphones. So does anyone know why I'd only have those two options?

---

### Post by fwojciec on 2007-12-02
> **PurposeOfReason said:**
> Looks like reboot. With shutdown it just put some weird design, no big deal really. Got the printer to work, I just read the wiki wrong. Next most important, headphones. So does anyone know why I'd only have those two options?

I just did some quick googling about this... Try adding something like "options snd-hda-intel model=laptop" to your /etc/modprobe.conf -  if your sound driver is snd-had-intel, that is.  For more configuration options for this module see this (maybe you'll find your specific laptop model there): [http://pastebin.ca/642405]("http://pastebin.ca/642405")

---

### Post by jseiser on 2007-12-03
got arch installed with openbox running.  All cli apps and it flies.  I have to admit, when i wanted to install conky i tried to apt-get out of habit :)    My biggest problem is getting used to the package manager.  I can Pacman -Sy whatever fine, but i read about some tupac program and yaour (sp?) and they are installed, but i dont really get how to use them lol.  I also had a hard time grasping the aur/abs thing.  Still dont really get it. :)  But... its alot faster then when i do this to a ubuntu Install, which is what im after.

---

### Post by jseiser on 2007-12-03
o0o, another bother.  I dont like going into root mode any longer then i have to.  is there a way to make sudo pacman -Sy   update and then get me out of root, like it is in ubuntu?  Im tired of typing
su
password
pacman -Sy 
exit
its 4 lines as oppossed to two :)

---

### Post by Frak on 2007-12-03
> **jseiser said:**
> got arch installed with openbox running.  All cli apps and it flies.  I have to admit, when i wanted to install conky i tried to apt-get out of habit :)    My biggest problem is getting used to the package manager.  I can Pacman -Sy whatever fine, but i read about some tupac program and yaour (sp?) and they are installed, but i dont really get how to use them lol.  I also had a hard time grasping the aur/abs thing.  Still dont really get it. :)  But... its alot faster then when i do this to a ubuntu Install, which is what im after.
when using yaourt, it is just like pacman.
To install a package with yaourt (out of the AUR repos), run
```
yaourt -S (package here)
```

Also, DO NOT run this as a root program, it knows when to do things.

---

### Post by david_2001 on 2007-12-03
> **jseiser said:**
> o0o, another bother.  I dont like going into root mode any longer then i have to.  is there a way to make sudo pacman -Sy   update and then get me out of root, like it is in ubuntu?  Im tired of typing
su
password
pacman -Sy 
exit
its 4 lines as oppossed to two :)
Just go to the Arch Wiki and search for sudo (takes you to [http://wiki.archlinux.org/index.php/Sudo](http://wiki.archlinux.org/index.php/Sudo)).  Once you have sudo working then follow the link at the bottom of the page to disable root password and gain su sudo with no [root] password.

---

### Post by Frak on 2007-12-03
> **david_2001 said:**
> Just go to the Arch Wiki and search for sudo (takes you to [http://wiki.archlinux.org/index.php/Sudo](http://wiki.archlinux.org/index.php/Sudo)).  Once you have sudo working then follow the link at the bottom of the page to disable root password and gain su sudo with no [root] password.
That is really bad security practice. Go for the root password when calling upon sudo.

---

### Post by david_2001 on 2007-12-03
> **Frak said:**
> That is really bad security practice. Go for the root password when calling upon sudo.
Even for a home-use computer?

---

### Post by raul_ on 2007-12-03
> **david_2001 said:**
> Even for a home-use computer?

yes

---

### Post by finferflu on 2007-12-03
I don't think it's a bad security practice. If somebody manages to break in with the root account disabled, it means that s/he already knows both your username and password... If you have a single user account, I don't see the point of typing the password every time.

---

### Post by Frak on 2007-12-03
> **david_2001 said:**
> Even for a home-use computer?
It's still a computer that could contain "Private Information".

---

### Post by raul_ on 2007-12-04
> **finferflu said:**
> I don't think it's a bad security practice. If somebody manages to break in with the root account disabled, it means that s/he already knows both your username and password... If you have a single user account, I don't see the point of typing the password every time.

it's bad practice having the root account disabled in the first place :)

---

### Post by omns on 2007-12-04
> **finferflu said:**
> I don't think it's a bad security practice. If somebody manages to break in with the root account disabled, it means that s/he already knows both your username and password... If you have a single user account, I don't see the point of typing the password every time.
That's a windows mindset and it's caused them nothing but grief. Not having root enabled removes an important safety valve. I wouldn't recommend it.

---

### Post by K.Mandla on 2007-12-04
Not to digress, but ...

Partly out of curiosity and partly out of troubleshooting some strange USB errors, what groups do you add your account to when you build your system? I'm used to adding a group called kmandla, putting the user kmandla into that group, then adding these as secondary groups

```
wheel,adm,users,audio,video,optical
```
I'm hoping adding "storage" makes my USB woes disappear. Any other suggestions?

---

### Post by Rumor on 2007-12-04
> **K.Mandla said:**
> Not to digress, but ...

Partly out of curiosity and partly out of troubleshooting some strange USB errors, what groups do you add your account to when you build your system?

Here's my list:
```
disk wheel log network video audio optical storage power users
```

---

### Post by raul_ on 2007-12-04
```
[raul@horus ~]$ groups
disk lp games network video audio optical storage camera power users
 
```

weird...no wheel group..hmmmm

---

### Post by pelle.k on 2007-12-04
```
audio,optical,storage,power,wheel
```
All i ever needed.

---

### Post by finferflu on 2007-12-04
Here's mine:
```
wheel dbus hal network video audio optical storage camera users
```

Just to comment on sudo. I used to have root enabled on other distros, but I found it useless. Really, what was the point? I don't think it's a Windows mindset, since I have left it 2 years ago now, and I didn't want Linux to behave the same way, I like the difference.
I only think it's annoying to type a difficult password everytime, and using sudo reminds me when I'm doing admin stuff. I don't think typing a password makes much of a difference. Also the system organisation is much different from Windows, with all the permissions system.
I think using sudo without password is a lot different than using the root account as a user. I also think disabling the root account is safer, because the root username is always the same, thus easier for a potential abuser to focus on the password only.

---

### Post by eljoeb on 2007-12-04
> **K.Mandla said:**
> Not to digress, but ...

Partly out of curiosity and partly out of troubleshooting some strange USB errors, what groups do you add your account to when you build your system? I'm used to adding a group called kmandla, putting the user kmandla into that group, then adding these as secondary groups

```
wheel,adm,users,audio,video,optical
```
I'm hoping adding "storage" makes my USB woes disappear. Any other suggestions?

You might want hal.

---

### Post by Dimitriid on 2007-12-04
I recently Installed openbox and im liking it, i want to go into a much more minimalistic system. I wonder if you guys could tell me however: how much performance that I "regain" by not using a full blown Desktop Environment I would waste if I decide to use a few GTK/Gnome applications? ( I mainly really really want Firefox and Exaile ). I think my machine might be fast enough that I won't be able to notice any difference but I might go openbox on another system I have with xubuntu atm.

---

### Post by david_2001 on 2007-12-04
> **Frak said:**
> It's still a computer that could contain "Private Information".
I encrypt all of the "sensitive" information on my PC.  Do you?  Watch out, there's a thief about... ;-)

---

### Post by david_2001 on 2007-12-04
> **finferflu said:**
> Here's mine:
```
wheel dbus hal network video audio optical storage camera users
```
I'm in disk, lp, wheel, video, audio, optical, floppy ('cos I still have one), storage, camera, scanner, vboxusers and usb.  I also keep a spare account for stuff that I don't want or need to backup regularly and add my main user to the group assigned to that account.

> Just to comment on sudo. I used to have root enabled on other distros, but I found it useless. Really, what was the point? I don't think it's a Windows mindset, since I have left it 2 years ago now, and I didn't want Linux to behave the same way, I like the difference.
I only think it's annoying to type a difficult password everytime, and using sudo reminds me when I'm doing admin stuff. I don't think typing a password makes much of a difference. Also the system organisation is much different from Windows, with all the permissions system.
I think using sudo without password is a lot different than using the root account as a user. I also think disabling the root account is safer, because the root username is always the same, thus easier for a potential abuser to focus on the password only.
From my perspective, the problem with Windows is that it's only really usable as a *personal* computer operating system if you log in as an administrator.  This gives you instant rights to change anything or install a virus without further authentication.  Use sudo even with root disabled and you have to enter a password to make administrative changes, so there's still some control.

---

### Post by smartboyathome on 2007-12-04
I am looking into Arch, but am wondering if there is a way to convert debian packages to arch packages (possibly using alien, like when converting rpms to debs)? I would like this because I use the e17-cvs package available on these forums, and would like to stay up to date on e17.

---

### Post by Frak on 2007-12-04
> **finferflu said:**
> Here's mine:
```
wheel dbus hal network video audio optical storage camera users
```

Just to comment on sudo. I used to have root enabled on other distros, but I found it useless. Really, what was the point? I don't think it's a Windows mindset, since I have left it 2 years ago now, and I didn't want Linux to behave the same way, I like the difference.
I only think it's annoying to type a difficult password everytime, and using sudo reminds me when I'm doing admin stuff. I don't think typing a password makes much of a difference. Also the system organisation is much different from Windows, with all the permissions system.
I think using sudo without password is a lot different than using the root account as a user. I also think disabling the root account is safer, because the root username is always the same, thus easier for a potential abuser to focus on the password only.
I agree, there is no reason for root to be enabled. I just use sudo.

---

### Post by Frak on 2007-12-04
> **david_2001 said:**
> I encrypt all of the "sensitive" information on my PC.  Do you?  Watch out, there's a thief about... ;-)
I use the wallet, so yes, my information is encrypted. Though, I still don't take chances, since there is currently no encryption available for normal users that is strong *enough*.

---

### Post by RedSquirrel on 2007-12-04
> **K.Mandla said:**
> I'm hoping adding "storage" makes my USB woes disappear. Any other suggestions?

Yeah, "storage" would be a good idea.

[http://wiki.archlinux.org/index.php/Group](http://wiki.archlinux.org/index.php/Group)


With regard to sudo, I haven't bothered to install it. I just use 'su -c' if I want to run something without actually having to switch to root. It's not as nice as sudo in some ways, but I'm managing just fine. ;)

---

### Post by crimesaucer on 2007-12-04
> **smartboyathome said:**
> I am looking into Arch, but am wondering if there is a way to convert debian packages to arch packages (possibly using alien, like when converting rpms to debs)? I would like this because I use the e17-cvs package available on these forums, and would like to stay up to date on e17.

Check this out: [http://wiki.archlinux.org/index.php/E17](http://wiki.archlinux.org/index.php/E17)

---

### Post by K.Mandla on 2007-12-04
Thanks everybody. For my own part, I sometimes run with sudo, sometimes not. I started with Ubuntu and sudo, so sometimes it feels creepy to do things without it. On the other hand, I don't have it when I'm setting up Arch, and so I do get used to just doing whatever I want. :|

---

### Post by pelle.k on 2007-12-04
And on the third hand (hehe) if you already are building packages as root, you should be ashamed of your selves, you naughty boys and girls (i like naughty girls though...)

This is how all the kool kids do it. With fakeroot and sudo of course. :popcorn:
```
~/kool-package$ makepkg -S
```

---

### Post by smartboyathome on 2007-12-04
> **crimesaucer said:**
> Check this out: [http://wiki.archlinux.org/index.php/E17](http://wiki.archlinux.org/index.php/E17)

Awesome, thanks for the link! I have the ISO and will try it out soon! :)

---

### Post by Dimitriid on 2007-12-05
I don't get sudo, typing su -c is just as easy. Having different passwords does not hurt and is not inconvenient for when you want to grant access to others.

In any case, openbox/fluxbox/other minimalist WM what is your preferred panel? I installed fbpanel but I don't like the look on the clock too much. I heard a lot about pypanel but the one on pacman repos refuses to even launch.

---

### Post by K.Mandla on 2007-12-05
I use no-panel which is quick and painless to set up. Configuration files are practically nonexistent and best of all no-panel doesn't burden the system nearly as much as other panel applications. :p

In all seriousness though, when I want a panel I use lxpanel. Pypanel is pretty, but takes too much time to configure. fbpanel is nice because you can run a top and bottom panel, but is a royal pain in the behind to configure. And after that ... are there any I'm missing?

---

### Post by Dimitriid on 2007-12-05
How can you get xterm to change colors by default? Its hard to read when changing certain things on nano on the defaults, and sometimes I like terminals with a background ( not sure if its possible on regular xterm )

Might just change the Menu to display only gnome-terminal instead. I  might go without a  panel cause I mainly just need a clock :D Whats a good clock desklet?

---

### Post by finferflu on 2007-12-05
> **Dimitriid said:**
> How can you get xterm to change colors by default? Its hard to read when changing certain things on nano on the defaults, and sometimes I like terminals with a background ( not sure if its possible on regular xterm )

Might just change the Menu to display only gnome-terminal instead. I  might go without a  panel cause I mainly just need a clock :D Whats a good clock desklet?
You might as well use conky...

---

### Post by finferflu on 2007-12-05
Just a question: does any of you find any improvement in performance using OpenBox only over Gnome+OpenBox? It doesn't seem noticeable to me. 
It's just that I'm not satisfied with the speed, it looks like my machine is dying slowly, otherwise I really can't understand what's going on... My CPU usage goes 100% too often.. I'm blaming browsers and Pidgin for that, but I'm not sure it's entirely due to them... The fact is that having just Pidgin and Epiphany open, sometimes slows down the system so much that there is a big delay when I type...
I have a Pentium 4, 2.60Ghz, 512MB RAM, I think I can expect more from it. 
Time for a clean reinstall? Please, no.

---

### Post by raul_ on 2007-12-05
> **finferflu said:**
> Just a question: does any of you find any improvement in performance using OpenBox only over Gnome+OpenBox? It doesn't seem noticeable to me. 
It's just that I'm not satisfied with the speed, it looks like my machine is dying slowly, otherwise I really can't understand what's going on... My CPU usage goes 100% too often.. I'm blaming browsers and Pidgin for that, but I'm not sure it's entirely due to them... The fact is that having just Pidgin and Epiphany open, sometimes slows down the system so much that there is a big delay when I type...
I have a Pentium 4, 2.60Ghz, 512MB RAM, I think I can expect more from it. 
Time for a clean reinstall? Please, no.

use "top" to see what's eating up your cpu

---

### Post by K.Mandla on 2007-12-06
> **finferflu said:**
> Just a question: does any of you find any improvement in performance using OpenBox only over Gnome+OpenBox? It doesn't seem noticeable to me. 
It's just that I'm not satisfied with the speed, it looks like my machine is dying slowly, otherwise I really can't understand what's going on... My CPU usage goes 100% too often.. I'm blaming browsers and Pidgin for that, but I'm not sure it's entirely due to them... The fact is that having just Pidgin and Epiphany open, sometimes slows down the system so much that there is a big delay when I type...
I have a Pentium 4, 2.60Ghz, 512MB RAM, I think I can expect more from it. 
Time for a clean reinstall? Please, no.
Something is not right there. I'd check what you have running in the background, or maybe check your hardware.

---

### Post by finferflu on 2007-12-06
I don't know, I actually did a clean reinstall (keeping my home though), and when I opened Firefox the system trashed. Uber-slowness. Now I don't know if I have to blame Firefox. I have deleted the .mozilla folder in my home and it was a bit faster, but still too slow. I really don't understand. With Epiphany it's a bit better but I would expect more. Could it be related to some of my configs in my home?  Or is just my machine getting old and dying slowly?
I tried with top, atop, htop, and it seems like Firefox uses about 30-50% of RAM average, X sometimes goes up to 80% of the CPU.

**Update**
Well, I think there was something wrong with my xorg.conf. I have reset it to the default hwd config and it's working fine now. I wish I knew an optimal configuration for my video card. I think I could still improve performance, but I don't know where to look for instructions...

---

### Post by raul_ on 2007-12-06
> **finferflu said:**
> I don't know, I actually did a clean reinstall (keeping my home though), and when I opened Firefox the system trashed. Uber-slowness. Now I don't know if I have to blame Firefox. I have deleted the .mozilla folder in my home and it was a bit faster, but still too slow. I really don't understand. With Epiphany it's a bit better but I would expect more. Could it be related to some of my configs in my home?  Or is just my machine getting old and dying slowly?
I tried with top, atop, htop, and it seems like Firefox uses about 30-50% of RAM average, X sometimes goes up to 80% of the CPU.

**Update**
Well, I think there was something wrong with my xorg.conf. I have reset it to the default hwd config and it's working fine now. I wish I knew an optimal configuration for my video card. I think I could still improve performance, but I don't know where to look for instructions...

what's your video card?

---

### Post by finferflu on 2007-12-06
An ATI Radeon Mobilty 7500.

---

### Post by Enverex on 2007-12-06
That's a very old and rather weak card. If you're using the radeon or ati driver in xorg.conf (compared to vesa) then you pretty much have the best performance you're going to get.

---

### Post by finferflu on 2007-12-06
Thanks for the info Enverex, not really a good news, but good to know. Yes, I am using the radeon driver. Responsiveness is not that bad, but if I could have more I would have been even happier. I'll just give up hoping now.

The only odd thing remaining now is that even though my resolution is set to 1024x768 in xorg.conf, it keeps displaying at 1400x1050. Odd...

---

### Post by david_2001 on 2007-12-06
> **finferflu said:**
> **Update**
Well, I think there was something wrong with my xorg.conf. I have reset it to the default hwd config and it's working fine now. I wish I knew an optimal configuration for my video card. I think I could still improve performance, but I don't know where to look for instructions...
ATi cards are totally outside my experience but there are a whole load of suggestions on the Gentoo Wiki page [COLOR="DarkOrange"][here]("http://gentoo-wiki.com/HOWTO_DRI_with_ATi_Open-Source_Drivers")[/COLOR].  You could try a few and see whether they have a positive effect.  Also just check through your xorg.conf to see that the rest is sensible and simple - I cannot say that I was overly impressed by the default that hwd came up with for my nVidia GeForce 7100 GS and the only part I've kept substantially intact is the Files section.

---

### Post by finferflu on 2007-12-07
Thanks for that link, but curiously, applying all those changes seems to make things worse. The default configuration that hwd provides seems to be the faster. When I add those options in windows are drawn slowly...

---

### Post by david_2001 on 2007-12-07
> **finferflu said:**
> Thanks for that link, but curiously, applying all those changes seems to make things worse. The default configuration that hwd provides seems to be the faster. When I add those options in windows are drawn slowly...
Well at least you tried.  Looks as though you will have to put up with what you have :-(

---

### Post by RedSquirrel on 2007-12-07
With regard to sudo (once again :)), I haven't had the need to build too many packages so far. The main one for me is Fluxbox SVN, but I simply installed its dependencies up front (as root). With that taken care of, I can build it as my regular user, and then install it as root.


> **Dimitriid said:**
> openbox/fluxbox/other minimalist WM what is your preferred panel?

On Fluxbox I'm currently using the default toolbar. For quite a while I used no-panel and no-toolbar and I just had fbpager+conky to give me some idea of what was going on.


> **Dimitriid said:**
> How can you get xterm to change colors by default? Its hard to read when changing certain things on nano on the defaults, and sometimes I like terminals with a background ( not sure if its possible on regular xterm )

No, you can't have backgrounds with xterm. Here is a link for xterm colours. I'm using the ones listed at the bottom of the page. ;)

[http://gentoo-wiki.com/TIP_Linux_Colors_in_Aterm/rxvt](http://gentoo-wiki.com/TIP_Linux_Colors_in_Aterm/rxvt)

---

### Post by LinuxGuy1234 on 2007-12-07
I'm downloading the ISO now.

EDIT: Done.

---

### Post by smartboyathome on 2007-12-07
:( The ISO doesn't even come graphically... I couldn't figure out which partition it thought each of my drives was...

---

### Post by raul_ on 2007-12-07
> **smartboyathome said:**
> :( The ISO doesn't even come graphically... I couldn't figure out which partition it thought each of my drives was...

Yeah, the installation is hardcore :)

it's just the environment that scares you, because it's pretty straightforward.
I have to say that I NEVER used the Arch partitioner. in fact, I have my own Gparted Live cd (it's worth burning it) and always create my partitions there, write them down, and then i know what to do.

But, you should be able to identify partitions for their type  / size through the partition manager

---

### Post by Frak on 2007-12-07
> **raul_ said:**
> Yeah, the installation is hardcore :)

it's just the environment that scares you, because it's pretty straightforward.
I have to say that I NEVER used the Arch partitioner. in fact, I have my own Gparted Live cd (it's worth burning it) and always create my partitions there, write them down, and then i know what to do.

But, you should be able to identify partitions for their type  / size through the partition manager
I agree, I find the Arch installer very "Get it, Get it done, Get it done now" in it's look and functionality. Something I like.

---

### Post by crimesaucer on 2007-12-08
> **smartboyathome said:**
> :( The ISO doesn't even come graphically... I couldn't figure out which partition it thought each of my drives was...

Yo, here is a link to a good "HOWTO" for everyting you need to know about the install.


It has screenshots of almost every step, and if you have a 2nd computer, just follow the steps from it and you should have it installed in no time:

[http://www.raiden.net/?cat=&aid=276](http://www.raiden.net/?cat=&aid=276)


... If you are like me, and you only have one computer and no access to anyone else's internet or computer... then you can always write the instructions down... word for word ... and follow them. 


The only instruction on that whole list I didn't like was the UTC time, I preferred the default localtime setting because I had trouble with the UTC setting.


Oh yeah, pick nano if you don't know vi, and here are some nano commands that help:

[http://www.nano-editor.org/dist/v2.0/nano.html](http://www.nano-editor.org/dist/v2.0/nano.html)

---

### Post by smartboyathome on 2007-12-08
Thanks Crimesaucer. I will try this in a few days (gonna be busy) and report back with what happens.

---

### Post by crimesaucer on 2007-12-08
> **smartboyathome said:**
> Thanks Crimesaucer. I will try this in a few days (gonna be busy) and report back with what happens.

Cool.

---

### Post by Dimitriid on 2007-12-08
Im trying to put gnome on a ram diet by tweaking it atm. Openbox looks very good as a window manager inside gnome, but I like the gnome panel. What I wanna ditch though is nautilus in favor of thunar. Another alternative im considering is using xfce but then ditching its panel for gnome-panel.

I know this ( thunar replacing nautilus ) has been done on this forums for Ubuntu, im just wondering if I could do it in Arch in this mini gnomemod thing im trying. I tried running just openbox and gnome-panel and my panel but gnome still launches nautilus for all file management which is self defeating so I'd have to either change all menus or just change the behavior ( certainly easier ).

---

### Post by fwojciec on 2007-12-08
> **Dimitriid said:**
> Im trying to put gnome on a ram diet by tweaking it atm. Openbox looks very good as a window manager inside gnome, but I like the gnome panel. What I wanna ditch though is nautilus in favor of thunar. Another alternative im considering is using xfce but then ditching its panel for gnome-panel.

I know this ( thunar replacing nautilus ) has been done on this forums for Ubuntu, im just wondering if I could do it in Arch in this mini gnomemod thing im trying. I tried running just openbox and gnome-panel and my panel but gnome still launches nautilus for all file management which is self defeating so I'd have to either change all menus or just change the behavior ( certainly easier ).

It this is what you're trying to do then I would just start regular openbox session with "gnome-panel&" and "thunar --daemon&" run from ~/.config/openbox/autostart.sh.  Gnome panel is pretty much a stand-alone application so you should be able to use it with any WM/DE.  You need to run thunar as daemon in case you use hal and need automounting and such.  Since in gnome nautilus takes care of desktop management you will need some other things for configuring themes (gtk-chtheme for example), choosing wallpaper (feh or nitrogen for example) and such but that shouldn't be a problem.  You might also need to run dbus - check the default openbox autostart.sh for an example of how to run it so it exits with session.

---

### Post by Dimitriid on 2007-12-08
Whats a good gnome menu editor? I want to at least have that menu use Thunar instead of nautilus.

---

### Post by Frak on 2007-12-08
> **Dimitriid said:**
> Whats a good gnome menu editor? I want to at least have that menu use Thunar instead of nautilus.
alacarte

---

### Post by crimesaucer on 2007-12-08
> **Dimitriid said:**
> Im trying to put gnome on a ram diet by tweaking it atm. Openbox looks very good as a window manager inside gnome, but I like the gnome panel. What I wanna ditch though is nautilus in favor of thunar. Another alternative im considering is using xfce but then ditching its panel for gnome-panel.

I know this ( thunar replacing nautilus ) has been done on this forums for Ubuntu, im just wondering if I could do it in Arch in this mini gnomemod thing im trying. I tried running just openbox and gnome-panel and my panel but gnome still launches nautilus for all file management which is self defeating so I'd have to either change all menus or just change the behavior ( certainly easier ).

Funny, I just did the same thing by going back to xfwm4 instead of Compiz Fusion. 

I can't believe how much more responsive and light everything feels now. Firefox 3 prebeta 2 Minefield is so fast now. All my apps pop up instantly... and I'm not using any of my SWAP file now.

---

### Post by adam.tropics on 2007-12-11
Hey,

Has anyone here gotten compiz etc running with catalyst and xorg-xserver-1.4?? (AIGLX) Or doeas anyone know where you get older packages, like 1.3?!

---

### Post by mthakur2006 on 2007-12-11
i'd so love to try it out but i just can't cuz the installer just hangs when it detects my wireless card :(

---

### Post by raul_ on 2007-12-11
> **adam.tropics said:**
> Hey,

Has anyone here gotten compiz etc running with catalyst and xorg-xserver-1.4?? (AIGLX) Or doeas anyone know where you get older packages, like 1.3?!

Not working here, got back to the open source driver.

I can't help you about downgrading because I don't use Ubuntu anymore, but google for "Ubuntu Downgrading a package". If I remember correctly:

Synaptic -> select the xorg package -> force version

---

### Post by floke on 2007-12-11
> **mthakur2006 said:**
> i'd so love to try it out but i just can't cuz the installer just hangs when it detects my wireless card :(

What hangs for you - Arch? Which wireless card do you have - mine's a 3945 intel pro and works fine - maybe you have the wrong driver or configuration?

---

### Post by mthakur2006 on 2007-12-11
> **floke said:**
> What hangs for you - Arch? Which wireless card do you have - mine's a 3945 intel pro and works fine - maybe you have the wrong driver or configuration?

mine's intel 2945 and when i put the cd in and press enter at start, it says a lot of stuff and then says  wireless card intel 2945 abg and just freezes there. :(

---

### Post by floke on 2007-12-11
Hmm. How long does it hang for? It 'could' be trying to establish a connection so you could wait and see if it times out? Failing that...you could try the Arch forum to see if anyone there has any clues. You might be able to pass something to the kernel at boot to get around it - maybe noeth or something. Its worth exploring the options, though sorry I can't be of more assistance (I don't have a cd to hand so can't see what's available).

EDIT - Someone called Cems has your laptop running Arch - see here [http://bbs.archlinux.org/viewtopic.php?pid=289381](http://bbs.archlinux.org/viewtopic.php?pid=289381)
You could drop them a line?

---

### Post by Tenken on 2007-12-11
How long does it hang? My Intel 2100 appeared to hang, but I just takes a minute to load.

Edit: you can pass it intel-wireless at the boot screen but I'm not sure it that applies to your card...

---

### Post by mthakur2006 on 2007-12-11
thanks guys :D
i'll have a look and let u know.

---

### Post by adam.tropics on 2007-12-12
> **raul_ said:**
> Not working here, got back to the open source driver.

I can't help you about downgrading because I don't use Ubuntu anymore, but google for "Ubuntu Downgrading a package". If I remember correctly:

Synaptic -> select the xorg package -> force version

My mistake, should explain things better! On ubuntu all is fine, including Catalyst and compiz, but problem is on Arch, never mind, will find it somewhere I'm sure.

---

### Post by raul_ on 2007-12-12
> **adam.tropics said:**
> My mistake, should explain things better! On ubuntu all is fine, including Catalyst and compiz, but problem is on Arch, never mind, will find it somewhere I'm sure.

I completely forgot the name of the thread :)

Downgrading a package in Arch is tricky, that's the price you pay for being bleeding edge. I did downgrade Xorg ONCE, but it got upgraded again, and since then I couldn't do it anymore. 

Just for curiosity, the packages you install (or download from pacman) are stored in /var/pacman/packages or something like that. You can cd to that directory, and then "pacman -U <package_name>".
Of course that this only works if you haven't cleared the cache since you installed the package to which you want to downgrade.

You can try downgrading. It broke X for me, but a pacman -S xorg-server upgraded it again. Bad things can happen though (I think)

---

### Post by floke on 2007-12-12
> **raul_ said:**
> I completely forgot the name of the thread :)

Downgrading a package in Arch is tricky, that's the price you pay for being bleeding edge. I did downgrade Xorg ONCE, but it got upgraded again, and since then I couldn't do it anymore. 

Just for curiosity, the packages you install (or download from pacman) are stored in /var/pacman/packages or something like that. You can cd to that directory, and then "pacman -U <package_name>".
Of course that this only works if you haven't cleared the cache since you installed the package to which you want to downgrade.

You can try downgrading. It broke X for me, but a pacman -S xorg-server upgraded it again. Bad things can happen though (I think)

Actually it's easy - you just add the name of the packages to avoid 're'upgrading to the ignore line in your /etc/pacman.conf. As long as you don't clear your cache then its as easy as doing a pacman -A [package].

---

### Post by raul_ on 2007-12-12
> **floke said:**
> Actually it's easy - you just add the name of the packages to avoid 're'upgrading to the ignore line in your /etc/pacman.conf. As long as you don't clear your cache then its as easy as doing a pacman -A [package].

It's easy keeping it ;) I didn't know that then

---

### Post by PurposeOfReason on 2007-12-15
I'm posting this here because the archlinux forums seem to be a bit slow right now. I was messing around with alsa and replaced /lib/modules/2.6.23-ARCH/kernel/sound/pci/hda/snd-hda-intel.ko with a different one, obviously one that I shouldn't have and being stupid, I didn't make a backup so now I get this whenever I try to play sound:
```
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.23-ARCH/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I've reinstalled alsa with pacman -S alsa-lib alsa utils but to no avail. What would I have to go about doing to restore it? Or if you just have the same sound controller, attach your file.


Thanks.

---

### Post by PurposeOfReason on 2007-12-15
Actually, recompiling the alsa driver did it, but I'm still not where I want. When I used Gutsy, I followed [this post](http://ubuntuforums.org/showpost.php?p=3844121&postcount=2) and it got my headphones to work where nothing else would. The only problem is the part right here:
```
sudo install -v -m644 pci/hda/snd-hda-intel.ko /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel
```

There is obviously no ubuntu folder and all my  browsing of /lib/modules/2.6.23-ARCH couldn't find anything similar.

---

### Post by raul_ on 2007-12-15
```

sudo updatedb
locate <whatever you want>

```

you'll have to install the locate package in case it's not installed

just in case:

```

[raul@osiris ~]$ locate hda-intel
/lib/modules/2.6.23-ARCH/kernel/sound/pci/hda/snd-hda-intel.ko

```

---

### Post by PurposeOfReason on 2007-12-15
Thanks, I was able to do that, but now my headphones don't work at all. Aumix used to show the PCM level and now it doesn't so I think that may be related; however, I still can control PCM with alsamixer.

---

### Post by K.Mandla on 2007-12-16
Anyone ever run into errors trying to set up abs?

I get weird FTP errors -- "Invalid PROTO command from server," or something like that -- and the command bombs. Wha ... ?

It's a little frustrating, although with yaourt I just grab the PKGBUILD manually, then makepkg. Not as pretty, but it's working.

Can anybody help?

---

### Post by Rumor on 2007-12-16
> **K.Mandla said:**
> Anyone ever run into errors trying to set up abs?


My tree updated fine this morning and I built unace from it without any errors.

maybe compare the PKGBUILD from your abs directory with the one from the AUR and see if they both point to the same source url? I'm sort of grasping at straws here, but it is the only thing I can think of.

---

### Post by k0rfain on 2007-12-16
arch is a very good distro.. Its one of my favorites now, Its very quick, light weighted, its just an all around good distro to try.

---

### Post by voteforpedro36 on 2007-12-16
I have downloaded Arch, and am ready to install. One question:

How do I go about putting Arch into a seperate partition? I see an option for an install that selects a hard drive to install on, does that mean partition (sorry haven't ran the installer yet)?

I will have to disconnect the phone, however, to have a wired connection so I can download the firmware for my Broadcom card, so it will be a while before I do this (a couple of hours, maybe more)...

---

### Post by Rumor on 2007-12-16
> **voteforpedro36 said:**
> I have downloaded Arch, and am ready to install. One question:

How do I go about putting Arch into a seperate partition? I see an option for an install that selects a hard drive to install on, does that mean partition (sorry haven't ran the installer yet)?


I'm guessing you mean separate so that you can dual boot?

You're a few options. You could boot the computer using the GParted live cd and set up your partitions using the existing free space on your hard drive. So if you're running Ubuntu, resize Ubuntu's / partition to free up some space for Arch. Then make two partitions, one for / and one for /home. Write down their new names as you'll need them for installing Arch. Then bot the Arch Cd and go into the setup. At the step for preparing the hard drive, select the option to choose file system mount points. Select your existing swap and then the new partitions for / and /home and proceed from there.

You can do the same thing from within Arch's installer. Choose to manually partition the disk and do the above steps when the installer takes you into cfdisk.                                       

If you are dual booting, you might want to install Arch's boot loader (Grub) somewhere other than the mbr, then boot into your normal OS and edit your existing bootloader to include options for Arch.

---

### Post by PurposeOfReason on 2007-12-16
Can anybody help me with gfx-boot? I've seen two ways to do it, one with PKGBUILD and the other by adding it go /etc/pacman.conf. The laster just tells me a bunch of files already exist and can't install and with the PKGBUILD method, I can't make the patch file.

Then I'll probably be back for gensplash if I get stuck there.

EDIT - And a way to control the PCM volume with keyboard shortcuts through alsamixer or something else lightweight.

---

### Post by voteforpedro36 on 2007-12-16
> **Rumor said:**
> I'm guessing you mean separate so that you can dual boot?

You're a few options. You could boot the computer using the GParted live cd and set up your partitions using the existing free space on your hard drive. So if you're running Ubuntu, resize Ubuntu's / partition to free up some space for Arch. Then make two partitions, one for / and one for /home. Write down their new names as you'll need them for installing Arch. Then bot the Arch Cd and go into the setup. At the step for preparing the hard drive, select the option to choose file system mount points. Select your existing swap and then the new partitions for / and /home and proceed from there.

You can do the same thing from within Arch's installer. Choose to manually partition the disk and do the above steps when the installer takes you into cfdisk.                                       

If you are dual booting, you might want to install Arch's boot loader (Grub) somewhere other than the mbr, then boot into your normal OS and edit your existing bootloader to include options for Arch.


Huh... I already have an empty partition, could I just format that (it's only 10 GB), and use it as both / and /home? I don't have another CD, although I could try the Ubuntu 7.04 one (7.10 stopped working, dunno why).

Or, I could use Arch's, but how hard is it to use in text-mode?

OK, in addition to that, here's what I've thought up, anyone wanna tell me how it will work out?
512MB- swap
13GB- Ubuntu (is that enough?)
13GB-Arch (once again, enough?)
~ 10GB- /home that I'll figure out how to share between both?

Anyone wanna tell me what would be better and how to do it in Arch's installer?

---

### Post by K.Mandla on 2007-12-16
> **Rumor said:**
> My tree updated fine this morning and I built unace from it without any errors.

maybe compare the PKGBUILD from your abs directory with the one from the AUR and see if they both point to the same source url? I'm sort of grasping at straws here, but it is the only thing I can think of.
Thanks, it must be something on my end. I have a feeling it's my network; I may have to mess with my router to make things work. Sigh.

---

### Post by pelle.k on 2007-12-16
> 13GB- Ubuntu (is that enough?)
13GB-Arch (once again, enough?)
~ 10GB- /home that I'll figure out how to share between both?
Shring /home is possible, but a bad idea i'm afraid.

Generally, 10GB should be more than enough for the root (/) partitions.

Make a dedicated partition, and mount it in both OS:es, if you wan't to share files between them.

---

### Post by Rumor on 2007-12-16
> **voteforpedro36 said:**
> 
512MB- swap
13GB- Ubuntu (is that enough?)
13GB-Arch (once again, enough?)
~ 10GB- /home that I'll figure out how to share between both?

Anyone wanna tell me what would be better and how to do it in Arch's installer?

As pelle.k has said, you don't want to share /home between distros.

If you currently have an OS on your computer that you want to keep, then download / burn / boot the GParted Live CD [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/).

Set up that empty 10 gig partition as 
One partition of 7.5 gigs to use as / for Arch format ext3 or  reiserfs
One partition of 2.5 gigs to use as /home in Arch, format as ext3 or reiserfs

When you run the Arch installer, you'll need to know those partitions' names (hdb,c or sdb,c or whatever) AND your swap partition's name. Set the file system mount points for swap, /, and /home and install away!

---

### Post by Dimitriid on 2007-12-17
Any clue as to why obmenu doesn't saves correctly? Im trying to put a few things on it and it correctly shows me the applications I wanna open on the menu now but they wont open. I tried putting the full path ( /usr/bin/exaile ) or just the bin name ( exaile ) and even using the ... thing to select the path to it.

Each time I save it and close obmenu, its gone. Its not saving the change or pointing to my apps.

---

### Post by K.Mandla on 2007-12-17
Is it saving to ~/.config/openbox/ ? Can you write to that directory? Are you running it as root and saving the configuration file to the root account?

Just ideas.

---

### Post by PurposeOfReason on 2007-12-17
What would be the best option for a boot splash? I've seen a lot of options for one and all I'm really looking for is something simple and clean looking, but still able to see the part of the text where it becomes colorful in case something goes wrong. If that makes sense.

---

### Post by pelle.k on 2007-12-17
Yeah, like in fedoras RHGB, or like ubuntu did it before feisty. Why is this hidden (in most distros) nowadays?!
Of course you want to know if a daemeon fails executing! :/

---

### Post by Dimitriid on 2007-12-17
> **K.Mandla said:**
> Is it saving to ~/.config/openbox/ ? Can you write to that directory? Are you running it as root and saving the configuration file to the root account?

Just ideas.

Yep. Even ran it as root and still no go. But by now I used menu maker and its good, has most of my stuff.

I also saw something wicked I think you might use, know about or at least be interested in: 
[http://www.directfb.org/wiki/index.php/Projects:GTK_on_DirectFB](http://www.directfb.org/wiki/index.php/Projects:GTK_on_DirectFB)

I stayed up like 5 hours into the night trying to install it. It says it has the packages in AUR and at first, I installed the wrong ones. Then I tried the right ones. Then I ran into many little things I did not have ( make, automake, autoconf, etc. ) Then I had to figure out the order to solve dependencies correctly.( I think its linux-fusion, directfb, cairo-dfb and then at the very end gtk-dfb )

When it was all said and done, gtk-dfb compilation just failed, neither AUR PKGBUILD works. I thought about trying it from source directly ( no AUR/pacman ) but I don't want to have to go through hell uninstalling later and plus it was like 7 am. Plus at the end of the wiki to compile yourself it says you have to recompile any GTK app you want to use on framebuffer with a special setting...not sure if true and/or needed for the packages too im not clear on that. But it would be a pain to reinstall so many GTK apps.

But the idea of running something like Gimp or Epiphany without even starting x really caught my attention. You could just uninstall Xorg altogether :guitar:

---

### Post by lpb331 on 2007-12-17
I was wondering if any of you had this issue. I installed OpenOffice 2.3.1 on Arch, but when I try to open it, I get this warning:

```

[b@b ~]$ /opt/openoffice/program/soffice
libGL warning: 3D driver claims to not support visual 0x58

```

and then it never opens. Any suggestions? (I have an ATI Radeon 7500.)

---

### Post by herbster on 2007-12-17
Just finished installing and setting up Arch linux over the weekend-- was a massive snowstorm here, wasn't going anywhere :D

Really, really love it. Have learned so much in 2 days installing and configuring it, it really forces you to go under the hood, and I needed it. Pacman works like a charm, boot time is a bit quicker than Ubuntu and I have a bunch of daemons in /etc/rc.conf. Still have a bunch of stuff to tweak and whatnot, but it's sweet so far :)

---

### Post by K.Mandla on 2007-12-17
> **Dimitriid said:**
> I also saw something wicked I think you might use, know about or at least be interested in: 
[http://www.directfb.org/wiki/index.php/Projects:GTK_on_DirectFB](http://www.directfb.org/wiki/index.php/Projects:GTK_on_DirectFB)
...
Oooh! Thanks for the tip. I might mess with that this weekend. :D

---

### Post by adam.tropics on 2007-12-18
Have any of you guys got vmware (just vmplayer) to run in Arch with the .23 kernel? Every time I try to run the configure script and then run  vmplayer, it tells me I need to run the configure script! Not desperate..just irritating. 

Also though, just having a look at the traffic on the other os subfora, do you guys think Arch deserves a subforum of its own?? (As with Fedora, Slackware, Gentoo et al)

---

### Post by Dimitriid on 2007-12-18
Well its not really a "mother" distro ( a distro that branches off many other major and minor ones ) But then again  think having one really big thread is worst on the server than several smaller ones.

---

### Post by K.Mandla on 2007-12-18
> **adam.tropics said:**
> Also though, just having a look at the traffic on the other os subfora, do you guys think Arch deserves a subforum of its own?? (As with Fedora, Slackware, Gentoo et al)
The staff has discussed it, but for now this thread suffices.

---

### Post by fwojciec on 2007-12-18
> **adam.tropics said:**
> Have any of you guys got vmware (just vmplayer) to run in Arch with the .23 kernel? Every time I try to run the configure script and then run  vmplayer, it tells me I need to run the configure script! Not desperate..just irritating.

This tends to be a probelm with Arch or rather, in fact, with Vmware because Arch generally uses the latest kernel and Vmware tends to take some time to come up with patches that assure compatibility with the current state of kernel development.  I don't know what the issue is with the .23 kernel since I haven't had the need to use vmware for a while.  A generic suggestion would be to make sure that you use the latest any-to-any patch in order to build the necessary vmware modules whenever there is a kernel change.  Or you could try virtualbox instead, though I don't know if it's any better than vmware in this regard...  If vmware is an important element of the system for you another distro, one that is more conservative when it comes to kernel updates might be a better choice for you.

---

### Post by voteforpedro36 on 2007-12-18
...so I tried to install Arch. Things went bad, as in GRUB just repeated it's name 480324038204 times. No joke. Now again I tried the FTP install, after 3 hours and 2 packages that didn't download, it boots to the text "GRUB", and that's all. Anybody have any kind of an idea what may be wrong? Please?

I just tried to boot from the Arch CD itself (arch root=/dev/sda3 at boot option), and it said:
kinit: Mounted root (ext3 filesystem) readonly.
kinit: init not found!
Kernal Panic - not syncing: Attempted to kill init!

Then it froze. Yeah... it's my only install on the computer (I used the default option). Any ideas?

PS: I'm having bad luck today. First Arch did that, then the Debian CD I burned (last CD I had too...) had a defect (burned at 4x too), then Ubuntu 7.10 froze while loading, and 7.04 wouldn't load either. Wow.

---

### Post by PurposeOfReason on 2007-12-18
For those running arch on a laptop, what do you use to dim the screen when the cord isn't connected? Laptop_mode didn't go too smooth with me.

---

### Post by Tenken on 2007-12-19
I'm running Arch on my laptop and the screen dims automatically when it switches to battery. I'm not using any extra mods with my kernel or any special laptop tools, but my laptop is ~4 years old.

---

### Post by kpkeerthi on 2007-12-19
> **PurposeOfReason said:**
> For those running arch on a laptop, what do you use to dim the screen when the cord isn't connected? Laptop_mode didn't go too smooth with me.

Nothing. The screen does dim for me. The screen power management is part of the display driver, if I am correct. I have nvidia driver installed.. btw.

---

### Post by PurposeOfReason on 2007-12-19
Well it's an intel x3000, latest driver and everything but it's not **that** supported . . .

---

### Post by PurposeOfReason on 2007-12-23
After the last update xbacklight works and I got it all going. But on the other hand, could someone help me patch my kernel? I'm looking at the fallen patchset and I assumed it'd be as simple as running a simple patch -p1 etc. but many of the tutorials I find around say a lot more than that and others, just that.

---

### Post by g2g591 on 2007-12-23
I installed through Ubuntu (pacman.static -S core -r /newarch) so I don't have any experiance with the official installer, but I like it, its lightweight, and is very easy to configure, and I can easily compile from source whatever official package I want (apt-get source package isn't that easy)

---

### Post by raul_ on 2007-12-23
> **g2g591 said:**
> I installed through Ubuntu (pacman.static -S core -r /newarch) so I don't have any experiance with the official installer, but I like it, its lightweight, and is very easy to configure, and I can easily compile from source whatever official package I want (apt-get source package isn't that easy)

How did you do that? sounds fun!

---

### Post by kpkeerthi on 2007-12-24
> **raul_ said:**
> How did you do that? sounds fun!

See [Install Arch from within another distro]("http://wiki.archlinux.org/index.php/Install_Arch_from_within_another_distro")

---

### Post by miggols99 on 2007-12-24
> **PurposeOfReason said:**
> After the last update xbacklight works and I got it all going. But on the other hand, could someone help me patch my kernel? I'm looking at the fallen patchset and I assumed it'd be as simple as running a simple patch -p1 etc. but many of the tutorials I find around say a lot more than that and others, just that.

The fallen patchset is unmaintained now. You could try the Zen kernel patchset.

---

### Post by K.Mandla on 2007-12-24
> **PurposeOfReason said:**
> Well it's an intel x3000, latest driver and everything but it's not **that** supported . . .
I think you might want the X settings for DPMS, which controls the screen timeout and power down for the monitor. That should run independent of the driver.

Under the "Monitor" section of your xorg.conf, try adding this:

```
Option "DPMS"
```

And under the &#8220;ServerLayout&#8221; section, add these lines:

```
Option "BlankTime" "3"
Option "OffTime" "5"
```

Those variables set the time in minutes it takes the screen to go blank, and the time it takes for screen (or in my case, the laptop panel) to be turned off completely. Restart X, and see if you like the results.

There're more ideas [here]("http://www.shallowsky.com/linux/x-screen-blanking.html") (old page, but still good).
> **miggols99 said:**
> The fallen patchset is unmaintained now. You could try the Zen kernel patchset.
Is that the zen-git kernel I keep hearing about? I saw that and glanced over it, then wondered if I should try it out. I tried the ck kernel back when it was all the rage, but got little improvement from it. Is zen worth the effort?

---

### Post by fwojciec on 2007-12-24
> **K.Mandla said:**
> Is that the zen-git kernel I keep hearing about? I saw that and glanced over it, then wondered if I should try it out. I tried the ck kernel back when it was all the rage, but got little improvement from it. Is zen worth the effort?

I used to be into all these kernels with funky patchsets but recently I've become much more conservative.  In my experience performance benefits are negligible and I much prefer the stability of the current kernel.  I still compile my own version of the Arch kernel because I need to add a patch so that my Ipod doesn't take 5 minutes to mount, but once that patch gets integrated into the kernel I think I'll use the standard kernel exclusively.

In general, I've found that the closer to the defaults I stay the more stable my system is -- this seems to be a good strategy, especially when using a rolling release distro, since all updates, even the tricky ones that cause a lot of trouble and grief for others, seem to go very smoothly on my systems.  

It's almost as if using Arch has changed my attitude to customization:  in Windows, and also in Ubuntu, I felt the need to customize everything because a particular default was imposed on me; on Arch, because my system is customized to begin with, I find that I standardize things instead of customizing -- since it makes my life easier in the long run.  I'm still open to new ideas, new solutions, and new ways of doing the tasks I do on my computers, but the way I end up implementing these solutions is by trying to make them as simple, transparent, and as close to the default as possible.

---

### Post by PurposeOfReason on 2007-12-24
I've yet to receive an answer for this at the archlinux forums so I'll ask it here too. I've set my cursor with ~/.Xdefaults, the default icon method, and both at the same time. No matter what I do, the cursor will go to the default pixel black one while bon echo loads a page. After the page is loaded, or I move the cursor over the desktop, it goes back.

Using the whiteglass cursor if it matters.

EDIT - It was the cursor theme. Tried a different one and it worked fine.

EDIT EDIT + RANT = all the good themes do it. Whiteglass, simpleandsoft. How would I go about editing a cursor theme?

---

### Post by PurposeOfReason on 2007-12-24
As I have an OCD about posting solutions, I got this one figured out. After editing the xdefaults and the index.theme file, copy all cursors to ~/.icons. Then go to the theme you're using, ~/.icons/simpleandsoft/cursors in my case, and run
```
ln -s left_ptr_watch 08e8e1c95fe2fc01f976f1e063a24ccd
```
Do this again in the old directory of /usr/share/icons/simpleandsoft/cursors/ and everything is fixed.

---

### Post by jseiser on 2007-12-26
Ok, my desktop runs arch perfectly, my laptop has trouble with the drivers.  Could you guy please look at my post, and see if you can offer some help :)

[http://bbs.archlinux.org/viewtopic.php?id=41297](http://bbs.archlinux.org/viewtopic.php?id=41297)

---

### Post by RedSquirrel on 2007-12-29
> **PurposeOfReason said:**
> I've yet to receive an answer for this at the archlinux forums so I'll ask it here too. I've set my cursor with ~/.Xdefaults, the default icon method, and both at the same time. No matter what I do, the cursor will go to the default pixel black one while bon echo loads a page. After the page is loaded, or I move the cursor over the desktop, it goes back.

Using the whiteglass cursor if it matters.

I'm using xcursor-vanilla-dmz-aa and I don't have that problem. All I did was install the package and add the following to ~/.Xdefaults:

```
Xcursor.theme: Vanilla-DMZ-AA
```

---

### Post by Dimitriid on 2007-12-30
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.Now this is a bit odd, I just reinstalled Arch on my laptop and wanted to just have it with openbox and a few gnome apps but no gnome. I tried to install firefox and I just can't seem to open it, I just get bash: command: firefox not fount. I installed firefox normally with "pacman -S firefox". I tried looking for the bin to no avail,tried to launch bonecho, Firefox, etc. Just wont start . I still haven't set up menus or icons so i have to start things from xterm.

Any clues?

---

### Post by kellemes on 2007-12-30
> **Dimitriid said:**
> Please click one of the Quick Reply icons in the posts above to activate Quick Reply.Now this is a bit odd, I just reinstalled Arch on my laptop and wanted to just have it with openbox and a few gnome apps but no gnome. I tried to install firefox and I just can't seem to open it, I just get bash: command: firefox not fount. I installed firefox normally with "pacman -S firefox". I tried looking for the bin to no avail,tried to launch bonecho, Firefox, etc. Just wont start . I still haven't set up menus or icons so i have to start things from xterm.

Any clues?

updatedb
locate firefox

---

### Post by K.Mandla on 2007-12-30
> **Dimitriid said:**
> Please click one of the Quick Reply icons in the posts above to activate Quick Reply.Now this is a bit odd, I just reinstalled Arch on my laptop and wanted to just have it with openbox and a few gnome apps but no gnome. I tried to install firefox and I just can't seem to open it, I just get bash: command: firefox not fount. I installed firefox normally with "pacman -S firefox". I tried looking for the bin to no avail,tried to launch bonecho, Firefox, etc. Just wont start . I still haven't set up menus or icons so i have to start things from xterm.

Any clues?
Yeah, I think it's somewhere in /opt, if I remember right.

---

### Post by Rumor on 2007-12-30
The default path is /opt/mozilla/bin/firefox, though just 'firefox' ought to launch it all the same.

---

### Post by fwojciec on 2007-12-30
> **Dimitriid said:**
> Please click one of the Quick Reply icons in the posts above to activate Quick Reply.Now this is a bit odd, I just reinstalled Arch on my laptop and wanted to just have it with openbox and a few gnome apps but no gnome. I tried to install firefox and I just can't seem to open it, I just get bash: command: firefox not fount. I installed firefox normally with "pacman -S firefox". I tried looking for the bin to no avail,tried to launch bonecho, Firefox, etc. Just wont start . I still haven't set up menus or icons so i have to start things from xterm.

Any clues?

I suppose you got it working by now, but for future reference...   In principle one should log out and back in after installing anything that ends up in opt - this is needed to update the paths.  Alternatively you can so "source /etc/profile" which will take care of updating the paths as well since it executes the scripts in /etc/profile.d.

---

### Post by jseiser on 2007-12-30
heh, i had to scour the arch forums for the whole log in log out thing when i first installed :) They should add it to the wiki.

---

### Post by Elvish Legion on 2007-12-30
After giving arch a run I must say, I feel WAY over my head, and don't know any where near what I thought I did.

I was unable to get my wifi working and couldnt afford the time to play with it, maybe another time when I'm off of work.

The install was really pretty easy though.

---

### Post by Dimitriid on 2007-12-30
I got it working, now im using kdemod however both on kdemod and openbox, I getting a strange screen artifacts but only when I use firefox to specifically see this website.

Since I don't think I am going to use 3d much I might switch to the open source ati driver but it is strange...should I worry about heat?

---

### Post by ynnhoj on 2007-12-30
> **Rumor said:**
> The default path is /opt/mozilla/bin/firefox, though just 'firefox' ought to launch it all the same.
i don't think your path gets updated upon installation, though..

it's already been covered, but... another way to find it would have been "whereis firefox".  the *whereis* and *which* commands are handy.

---

### Post by mips on 2008-01-03
I started installing Arch on my laptop last night to see what all the whoha is about.

The installation is not that hard, just follow the guide. I had zero issues getting the base system, Xorg & kdemod installed. I really love the fact that the system is so light, it runs like snot on my 1.4GHz Celeron/512MB laptop. There is a bit to much text file editing for my liking but it is actually teaching me a lot.

kdemod is what kde should have been like, nice and modular. I just wish I could find a detailed list of what every single package does as I just installed the entire kdemod-kdepim by mistake and I don't need all that crap so I will have to remove/purge most of it.

I still have some way to go before my system is done but i'm taking my time with this one and actually enjoying building my own system.

Oh, pacman is also a breeze to use, just had some issues with the repositories timing out and one corrupted package. What KDE GUI can I use as a frontend for pacman? (makes it easier for me to browse packages)

I think Arch is going to be a keeper for me, especially on my laptop ;)

---

### Post by fwojciec on 2008-01-03
> **mips said:**
> I started installing Arch on my laptop last night to see what all the whoha is about.

The installation is not that hard, just follow the guide. I had zero issues getting the base system, Xorg & kdemod installed. I really love the fact that the system is so light, it runs like snot on my 1.4GHz Celeron/512MB laptop. There is a bit to much text file editing for my liking but it is actually teaching me a lot.

kdemod is what kde should have been like, nice and modular. I just wish I could find a detailed list of what every single package does as I just installed the entire kdemod-kdepim by mistake and I don't need all that crap so I will have to remove/purge most of it.

I still have some way to go before my system is done but i'm taking my time with this one and actually enjoying building my own system.

Oh, pacman is also a breeze to use, just had some issues with the repositories timing out and one corrupted package. What KDE GUI can I use as a frontend for pacman? (makes it easier for me to browse packages)

I think Arch is going to be a keeper for me, especially on my laptop ;)

Welcome to Arch! :)

remove purge: pacman -Rscn [package name(s)] -- this will remove the package(s), everything it/they depends on (as long as it is not needed by other packages), everything that depends on the package(s), as well as any configuration files that were installed with the package.  pacman -R --help for more info.

If the repos are no working right try using a different mirror.  Mirror preferences are defined in files in the /etc/pacman.d directory - the one at the top is tried first.  Some mirrors are definitely better than others.

As far as pacman frontends are concerned -- not sure about gui ones, but you could try [yaourt]("http://archlinux.fr/yaourt-en/"), for example.  It allows you to search repos and aur repo for keywords and installs packages from the repos + builds automatically from aur.

---

### Post by eljoeb on 2008-01-03
> **mips said:**
> Oh, pacman is also a breeze to use, just had some issues with the repositories timing out and one corrupted package. What KDE GUI can I use as a frontend for pacman? (makes it easier for me to browse packages)

I just use the package browser on archlinux.org, or the package list on kdemod's site.

---

### Post by Elvish Legion on 2008-01-03
After giving arch a second go, a lot of wiki abuse, and a lot of abusing arch forums search button and a lot of  ynnhoj's help I'm home!

For years I used ubuntu, suse 9.3, debian, pclinux or  otherwords the "more user friendly" distros

When I first started arch, I Was over whelmed,  in the short time I've used it, the command line is like a second home for me...I first installed a pacman front endand now don't use it (never mind the fact that its buggy) I just google to make sure I have the package name right and then pacman -Syu

Elvish

---

### Post by herbster on 2008-01-03
Thought I might share some pacman aliases in my .bashrc:

```
alias pacsearch="pacman -Sl | cut -d' ' -f2 | grep " #lets you search through all available packages simply using 'pacsearch packagename'
alias pacup="sudo pacman -Syu" # sudo pacman -Syu by typing pacup (sudo must be installed and configured first ;) )
alias pac="sudo pacman -S" # sudo pacman -S by typing pac (sudo must be installed and configured first ;) )
alias pacinfo="sudo pacman -Qi"
alias pacrm="sudo pacman -R"
alias pacaur="sudo pacman -U"
```

Add in your /home/user/.bashrc file.

---

### Post by mips on 2008-01-06
> **Tenken said:**
> I'm running Arch on my laptop and the screen dims automatically when it switches to battery. I'm not using any extra mods with my kernel or any special laptop tools, but my laptop is ~4 years old.

That is not done in software but in hardware/bios. Most laptops will do this irrespective of OS loaded.

---

### Post by slimdog360 on 2008-01-06
arch rocks

---

### Post by mips on 2008-01-06
> **fwojciec said:**
> 
As far as pacman frontends are concerned -- not sure about gui ones, but you could try [yaourt]("http://archlinux.fr/yaourt-en/"), for example.  It allows you to search repos and aur repo for keywords and installs packages from the repos + builds automatically from aur.

I found something called PacKommander which relies on kommander. I have not tried it yet though but will probably later.

How do I get suspend & hibernate to work on my laptop, they aren't even options when I log off. I have klaptopdaemon installed which seems to be stuck at 95% charged?

---

### Post by K.Mandla on 2008-01-06
I apologize for pointing you at the wiki since you've probably already been there, but have you checked ...

[http://wiki.archlinux.org/index.php/Suspend_to_Disk](http://wiki.archlinux.org/index.php/Suspend_to_Disk)
[http://wiki.archlinux.org/index.php/Suspend_to_RAM](http://wiki.archlinux.org/index.php/Suspend_to_RAM)

There's another section which handles suspending to both.

[http://wiki.archlinux.org/index.php/Suspend_to_Disk#Combining_suspend_to_disk_with_suspend_to_RAM](http://wiki.archlinux.org/index.php/Suspend_to_Disk#Combining_suspend_to_disk_with_suspend_to_RAM)

Sorry I can't be of more help; my laptop is so old the battery lasts 45 seconds, and so I never use either option. :???:

---

### Post by jaz.spb on 2008-01-06
Archlinux is not difficult to install, just follow Archwiki instructions. I tried this and now I'm Archlinux user. May be installation of arch will be long, but the result will be great. 
Gentoo is not difficult too. I'm agree that Gentoo is more user friendly and may be I'll install it on my desktop computer. 

It will be better to install Arch, Gentoo, Ubuntu on desktop. And I advice to install Ubuntu on the laptop.

---

### Post by mips on 2008-01-06
> **K.Mandla said:**
> I apologize for pointing you at the wiki since you've probably already been there, but have you checked ...


Please don't apologise for giving me links as I'm happy with links :)
Truth be told I have been all over that wiki the last few days but for some odd reason I never came across those links. Spent so much time on that wiki that it is probably a case of 'can't see the forest for the trees'.

Thanks, I will look into those links.

---

### Post by Peyton on 2008-01-06
> **Elvish Legion said:**
> After giving arch a second go, a lot of wiki abuse, and a lot of abusing arch forums search button and a lot of  ynnhoj's help I'm home!

For years I used ubuntu, suse 9.3, debian, pclinux or  otherwords the "more user friendly" distros

When I first started arch, I Was over whelmed,  in the short time I've used it, the command line is like a second home for me...I first installed a pacman front endand now don't use it (never mind the fact that its buggy) I just google to make sure I have the package name right and then pacman -Syu

Elvish

Use pacman -Ss to search. ;)

---

### Post by aeto on 2008-01-08
Jacman is the man! Get rid of the l33t mindset and adapt to the leet mindset; practical efficiency over psychological deficiency. Certain tasks, like finding and trashing unneeded packages, are better done from within a GUI. Other things, Pacman vs Apt is like He-man vs Barney. Wait, I meant Phrakture vs uhhh...Somebody.

The problems faced here are funny to read about, hahah. Like the repos turning upside town and such, or the database turning inside out. Some people come on IRC talking about the same thing. I find no clue :( 

Btw, why isn't thread starter updating first post? At least, the thing about source-based package management must be edited. People who are interested are going to read that first after clicking on this thread. There is little relation between Arch and Gentoo. Gentoo is, after all, because the names rhyme, a source-based Ubuntu. On the other hand, Arch is a poem. New Arch reviews tend to paint a picture of Mount Everest, when it is really just the humble Andes.

"It is what you make it" - Hitla

---

### Post by fwojciec on 2008-01-08
> **aeto said:**
> Jacman is the man! Get rid of the l33t mindset and adapt to the leet mindset; practical efficiency over psychological deficiency. Certain tasks, like finding and trashing unneeded packages, are better done from within a GUI.

Who needs a gui...  I just memorize what I have installed :P

---

### Post by raul_ on 2008-01-08
> **fwojciec said:**
> Who needs a gui...  I just memorize what I have installed :P

what's wrong with that? :confused:

---

### Post by handy on 2008-01-08
> **raul_ said:**
> what's wrong with that? :confused:

My memory! :lolflag:

---

### Post by aeto on 2008-01-08
> **fwojciec said:**
> Who needs a gui...  I just memorize what I have installed :P

Repeat after me,

"I am NOT a magician"

"I am NOT a magician"

"I am NOT a magician"

...

---

### Post by bluefightingcat on 2008-01-09
Hey,

Try out "Yet another Pacman Gui".YAPG. I like it alot and works great.

BFC

---

### Post by bionnaki on 2008-01-09
I switched from ubuntu to arch. running openbox. works wonderfully & very fast.

---

### Post by K.Mandla on 2008-01-09
Anyone ever run without udev?

I hate that it takes almost 10 seconds (on my 1Ghz machine) for udev to finish. Sometimes I edit /etc/start_udev to add a timeout flag to /sbin/udevsettle, but that gets replaced at almost every kernel update.

I've heard it was possible to run without udev, but I can't find any information about it. Suggestions? Or should I just breathe deeply and count to 10?

---

### Post by RedSquirrel on 2008-01-09
> **K.Mandla said:**
> Anyone ever run without udev?

I hate that it takes almost 10 seconds (on my 1Ghz machine) for udev to finish. Sometimes I edit /etc/start_udev to add a timeout flag to /sbin/udevsettle, but that gets replaced at almost every kernel update.

I've heard it was possible to run without udev, but I can't find any information about it. Suggestions? Or should I just breathe deeply and count to 10?

In an odd coincidence, I was just tinkering with my boot without udev tonight. I must have left some modules out because I ended up with an unbootable system. I'm too tired now to play with it anymore, but I may have had the module order wrong. I might try again another time when I'm a little more alert. ;)

I just looked at the output of lsmod to get an idea of the modules I need.

From what I've read, the Arch devs (well, a portion of them anyway) recommend against running without udev. There are a few threads on the Arch forums about this. If you search for "udev uevents" you'll probably find them. "bootchart" is another good term to search for there.

Here's a bug report I saw a while ago:

[http://bugs.archlinux.org/task/8878](http://bugs.archlinux.org/task/8878)

Mine pauses about 10 seconds. My whole boot takes about 54 seconds. If I use acpi=off, that speeds things up, but it has other consequences.

On Ubuntu, I think it was less than 30 seconds with no long pauses...


EDIT: I neglected to mention that I did get everything working again (with udev). It was a bit of a hassle though because my fallback image also had an unrelated issue and would not boot. I'm glad the rescue CD wasn't too far out of reach. :grin:

---

### Post by K.Mandla on 2008-01-10
Hmm. That's an interesting bug report. Mine is nowhere near that bad, but I still grind my teeth every time I boot. 

For my own part I run *hwdetect --modules >> /etc/rc.conf* during the installation process and trim out all the stuff I don't use (parallel port, etc.) and turn off module autoloading there. Then I carve mkinitcpio.conf down to nothing, and rebuild it. 

It doesn't seem to be where the problem is for me, though. It's not module loading that's hanging, it's udev uevents. That timeout flag is the only thing I know to kick it in the

:D

---

### Post by aeto on 2008-01-10
10s? Just for udev? That's mighty long. Use bootchartd and check the real (somewhat) time it takes for the boot process.

Trust me, you don't wanna run without Udev unless you're 100% confident you have all the modules you need and ur kernel is at its happiest. Hwdetect is a joker, serious only to an extent. Loading manually does provide a speed increase of -1 to -2s though. My mkinitcpio:
```
MODULES="ahci ata_piix libata sd_mod jfs"
HOOKS="base resume"
``` and honestly it doesn't make a difference to ```
base autodetect sata filesystems resume
``` or even ```
base udev autodetect sata filesystems resume
```
Run with -v and it seems non-disk modules like USB and CD still get pulled in for the latter 2. Furthermore, the time it takes to create root with only base and resume will ultimately be equal to running with udev and autodetect. So, udev for life!

Or just make sure ur kernel is optimal and DON'T use any form of initrd/ramfs!

---

### Post by yabbadabbadont on 2008-01-10
Are there any hidden repercussions to just building a custom kernel?  If you only include the support you need directly in the kernel, with minimal modules, will it seriously mess up the Arch init system?  (Which I've read is pretty minimal actually)

---

### Post by K.Mandla on 2008-01-10
This is all the more interesting, because I've been recompiling custom kernels manually (not through makepkg) and running those without inserting modules. So I'm starting to wonder if I should carve udev out anyway.

This is all Crux's fault anyway. If I hadn't gotten a [450Mhz machine to boot in 25 seconds]("http://kmandla.wordpress.com/2008/01/05/video-25-second-boot-on-450mhz-k6-2/"), I never would have noticed how long it takes udev uevents to finish.

For the record, this is my mkinitcpio.conf now:

```
MODULES="piix ide_disk ide-cd ext2"
BINARIES=""
FILES=""
HOOKS="base"
```
And my modules ... well, I manually rebuild the kernel to include the modules I want, so it doesn't matter what I use in rc.conf, since they aren't inserted on boot.

---

### Post by aeto on 2008-01-11
yabba: nope, none at all. you just have to write a mini ebuild of sort if you want pacman to handle it. if you don't want pacman to know, then it's standard. building in everything makes it even better since you won't need udev at all. however, i don't think one can have a sane kernel and system that way.

mandla: nasty! how can you not makepkg? You build in everything? Hmm in that case, i don't see why you'd need udev in the first place, or maybe even an initrd :) But I've been noticing more people talking about this lengthy udev/uevents. Maybe leaving it to auto would be best?

---

### Post by yabbadabbadont on 2008-01-11
Udev isn't strictly required, no matter how you configure your kenrel (built-in or modules).  You just have to manually create the old static device nodes.  (mknod is your friend if you go that route ;))  I actually prefer the old static /dev method.  Of course, I cut my teeth on the 2.0 kernel.  :lol:

---

### Post by RedSquirrel on 2008-01-11
> **K.Mandla said:**
> And my modules ... well, I manually rebuild the kernel to include the modules I want, so it doesn't matter what I use in rc.conf, since they aren't inserted on boot.

Would you mind posting your MODULES array from rc.conf (before you put them in the kernel)? I just want to see what you had there. Thanks.

---

### Post by yabbadabbadont on 2008-01-12
In case anyone has been annoyed by the floppy drive light always being on.  I finally found that if I loaded the floppy module, it would go out as it should.  I have no idea why the drive was being continuously polled without the module being loaded.  Nor do I know why the module wasn't loaded automatically by udev.  Hopefully this will help someone else.

---

### Post by K.Mandla on 2008-01-12
> **yabbadabbadont said:**
> Udev isn't strictly required, no matter how you configure your kenrel (built-in or modules).  You just have to manually create the old static device nodes.  (mknod is your friend if you go that route ;))  I actually prefer the old static /dev method.  Of course, I cut my teeth on the 2.0 kernel.  :lol:
Could you give me a brief rundown on how to move back to static /dev? I've looked through the wiki and not seen anything. I just want to make sure I have a vague idea what I'm doing so it works once, without having to trial-and-error myself into a stupor.
> **RedSquirrel said:**
> Would you mind posting your MODULES array from rc.conf (before you put them in the kernel)? I just want to see what you had there. Thanks.
Sure. This is on a Dell Inspiron 8000 with an NEC ND-7550A DVD+-RW, PRO 100 NIC and Nvidia Geforce4 440 Go. I use an external mouse attached to the PS/2 port and an ESS Maestro3 sound card. I have to hard drives, both IDE (one 7200rpm, one 5400rpm), and the onboard USB1.1 ports. Since I don't use the PCMCIA port I don't bother with modules for that, or things like parallel ports and whatnot.
```
MODULES=(cdrom agpgart intel-agp evdev psmouse serio_raw pci_hotplug rtc-cmos rtc-core rtc-lib ac97_bus snd-page-alloc snd-pcm snd-timer snd snd-ac97-codec snd-maestro3 soundcore ata_generic sd_mod ata_piix e100 mii usbcore usb-storage uhci-hcd)
```
Most of that comes from *hwdetect --modules*, minus the stuff I don't want.

---

### Post by aeto on 2008-01-12
Static? Are you serious? That's what I meant by being "sane". One would want something like udev if hotplugging occurs regularly. So of course, if you have no hotplugging devices, there is no concern over plugging in something and the module not being inserted into the kernel.

But with udev, hotplug, devfs, you have only the nodes for devices that are actually plugged in. That's what these utilities are for, to make life easier and keep things neat :) And a sane kernel, will have modules, not everything built in. But yeah, I do have an insane K6 and I don't use any kind of initrd.

Actually, most of the problems faced usually are direct results of manually loading modules in rc.conf

---

### Post by mips on 2008-01-12
[http://wiki.archlinux.org/index.php/Speedup_boot](http://wiki.archlinux.org/index.php/Speedup_boot)

---

### Post by fwojciec on 2008-01-12
The ultimate "boot-up time" tweak: suspend and hibernate :D

My favorite method at the moment is uswsusp's "s2both" which saves the current state to disk and then suspends to ram -- it uses what was saved to disk only in case something happens to power while the computer is asleep.  It works great.

You can also use it on desktop computers, of course, which is what I do on mine -- my computer starts up in about 2-3 seconds...

BTW - those of you who don't really use the Arch website all that often should go and check out the awesome new look and logo :cool:

---

### Post by yabbadabbadont on 2008-01-12
> **aeto said:**
> blah blah blah

Real Linux users (started to say "men", but that's sexist ;)) know their hardware and include support for it directly in the kernel.  They can also recite, from memory, the major/minor node numbers for all the device nodes for said hardware...

:p :D :lol:

---

### Post by yabbadabbadont on 2008-01-12
> **K.Mandla said:**
> Could you give me a brief rundown on how to move back to static /dev? I've looked through the wiki and not seen anything. I just want to make sure I have a vague idea what I'm doing so it works once, without having to trial-and-error myself into a stupor.


You could use tar to create an archive of all of your active nodes.  Make sure that you have all of your pluggable hardware connected first.  You could also use it to archive ```
/dev/.static/dev
```  That will get you all of the standard device nodes.  For any that get missed, read the kernel documentation for the module/driver.  They generally list the names and major/minor numbers of the related device nodes.  (/usr/src/linux/Documentation is an interesting read)

---

### Post by aeto on 2008-01-13
yabbadaboop: hmm i have to say you are somewhat correct!

---

### Post by yabbadabbadont on 2008-01-13
> **aeto said:**
> yabbadaboop: hmm i have to say you are somewhat correct!

I win!  I win!  Yay!

(Where's my cookie?!?)

:lolflag:

---

### Post by RedSquirrel on 2008-01-13
> **K.Mandla said:**
> Sure. This is on a Dell Inspiron 8000 with ...

Most of that comes from *hwdetect --modules*, minus the stuff I don't want.

Thanks. That's similar to what I have now, except I have a few more sound-related modules (which I may remove at some point).

---

### Post by K.Mandla on 2008-01-13
For some reason, my sound wouldn't work without all those modules. I have a feeling they're all intertwined at some level. If I could trim them back I would.

---

### Post by K.Mandla on 2008-01-13
Not to change the subject but ...

I seem to have botched the whole pacman 3.1.0 move. Now makepkg spits out errors about BUILDSCRIPT being undefined, and I can't seem to compile anything except manually.
[quote=makepkg, who used to love me]==> ERROR: BUILDSCRIPT is undefined! Ensure you have updated /etc/makepkg.conf.[/quote]
What was I *supposed* to do? I tried replacing line 10 in makepkg.conf with the new array of web commands, but that didn't help. And what is meant by "merging" the old one with the new one? Copy and paste?

It might be that I've just wrangled my installation for too long. I'm overdue for a clean slate.

---

### Post by Dimitriid on 2008-01-13
I saw that change too, I don't make much use of ABS or AUR but why change it? It was fine imho, I don't like bleeding edge ( which is nice ) turning into "change for the sake of change" things like this update.

In any case after the upgrade pacman gave some information about the format change and other changes but I didn't followed too much sadly. Maybe the Arch forums and/or irc channel guys will explain more.

---

### Post by fwojciec on 2008-01-14
> **K.Mandla said:**
> Not to change the subject but ...

I seem to have botched the whole pacman 3.1.0 move. Now makepkg spits out errors about BUILDSCRIPT being undefined, and I can't seem to compile anything except manually.

What was I *supposed* to do? I tried replacing line 10 in makepkg.conf with the new array of web commands, but that didn't help. And what is meant by "merging" the old one with the new one? Copy and paste?

It might be that I've just wrangled my installation for too long. I'm overdue for a clean slate.

I had the same message as well after updating pacman.  I simply copied all my customizations (just the lines with compiler flags) from /etc/makepkg.conf to /etc/makepkg.conf.pacnew file and then copied the /etc/makepkg.conf.pacnew file as /etc/makepkg.conf.  That's probably the easiest way to do it -- it's essentially the same procedure as with the new pacman.conf file.

You might also need to install "abs" package since it is no longer included in "pacman" package and needs to be installed separately.

---

### Post by Drakx on 2008-01-14
I have the strangest of problems, when i starting compiz-fusion every thing changes as it should, yet... when i open another window be it gnome-terminal, firefox, deluge etc etc i have to restart compiz-fusion just so i can see whats happened 0.o

---

### Post by ekerazha on 2008-01-14
> **yabbadabbadont said:**
> In case anyone has been annoyed by the floppy drive light always being on.  I finally found that if I loaded the floppy module, it would go out as it should.  I have no idea why the drive was being continuously polled without the module being loaded.  Nor do I know why the module wasn't loaded automatically by udev.  Hopefully this will help someone else.

You can "fix" this also loading the "acpi" daemon, however it could happen if you start the OS from Grub before the led turns off after the "boot from floppy drive" attempt.

---

### Post by Drakx on 2008-01-14
can any one help with this...
[http://bbs.archlinux.org/viewtopic.php?id=42275](http://bbs.archlinux.org/viewtopic.php?id=42275)

---

### Post by kellemes on 2008-01-14
> **Drakx said:**
> can any one help with this...
[http://bbs.archlinux.org/viewtopic.php?id=42275](http://bbs.archlinux.org/viewtopic.php?id=42275)

You may need to include in your post..
- /etc/X11/xorg.conf
- /var/log/Xorg.0.log

and provide more info on your graphics-card and used driver.

---

### Post by Drakx on 2008-01-14
done thanks i forgot

---

### Post by mips on 2008-01-15
Ok, now I have my desktop on arch as well. Went arch64 this time.

I must say to get from grub to a working desktop(kdemod) in under 30 seconds just blows my mind, especially on my old hardware.

---

### Post by K.Mandla on 2008-01-16
KDEmod is beautiful; if I ever use KDE regularly it would only be KDEmod.

30 seconds is ... pretty good!

---

### Post by raul_ on 2008-01-16
> **Drakx said:**
> I have the strangest of problems, when i starting compiz-fusion every thing changes as it should, yet... when i open another window be it gnome-terminal, firefox, deluge etc etc i have to restart compiz-fusion just so i can see whats happened 0.o

sounds like you have 'loose binding' enabled

---

### Post by Drakx on 2008-01-16
> **raul_ said:**
> sounds like you have 'loose binding' enabled

Hi

I've got it fixed now it was some thing todo with Intel driver and my xorg.conf the more i use Arch the more i like it :D

---

### Post by Opeth115 on 2008-01-16
Hello all, i have archlinux installed with kdemod and whenever i try to install amarok, i get this error:

```
pacman -S amarok-base
resolving dependencies...
looking for inter-conflicts...

Targets: qt3-3.3.8-6.1  amarok-base-1.4.8-2

Total Download Size:    0.00 MB
Total Installed Size:   23.22 MB

Proceed with installation? [Y/n] y
checking package integrity...
(2/2) checking for file conflicts                   [#####################] 100%
error: could not prepare transaction
error: failed to commit transaction (conflicting files)
qt3: /opt/qt/bin/assistant exists in filesystem
qt3: /opt/qt/bin/designer exists in filesystem
qt3: /opt/qt/bin/linguist exists in filesystem
qt3: /opt/qt/bin/lrelease exists in filesystem
qt3: /opt/qt/bin/lupdate exists in filesystem
qt3: /opt/qt/bin/moc exists in filesystem
qt3: /opt/qt/bin/qm2ts exists in filesystem
qt3: /opt/qt/bin/qmake exists in filesystem
qt3: /opt/qt/bin/qtconfig exists in filesystem
qt3: /opt/qt/bin/uic exists in filesystem
qt3: /opt/qt/include/jri.h exists in filesystem
qt3: /opt/qt/include/jri_md.h exists in filesystem
qt3: /opt/qt/include/jritypes.h exists in filesystem
qt3: /opt/qt/include/npapi.h exists in filesystem
qt3: /opt/qt/include/npupp.h exists in filesystem
qt3: /opt/qt/include/private/qapplication_p.h exists in filesystem
qt3: /opt/qt/include/private/qcolor_p.h exists in filesystem
qt3: /opt/qt/include/private/qcom_p.h exists in filesystem
qt3: /opt/qt/include/private/qcomlibrary_p.h exists in filesystem
qt3: /opt/qt/include/private/qcomponentfactory_p.h exists in filesystem
qt3: /opt/qt/include/private/qcriticalsection_p.h exists in filesystem
qt3: /opt/qt/include/private/qdialogbuttons_p.h exists in filesystem
qt3: /opt/qt/include/private/qdir_p.h exists in filesystem
qt3: /opt/qt/include/private/qeffects_p.h exists in filesystem
qt3: /opt/qt/include/private/qeventloop_p.h exists in filesystem
qt3: /opt/qt/include/private/qfiledefs_p.h exists in filesystem
qt3: /opt/qt/include/private/qfontcodecs_p.h exists in filesystem
qt3: /opt/qt/include/private/qfontdata_p.h exists in filesystem
qt3: /opt/qt/include/private/qfontengine_p.h exists in filesystem
qt3: /opt/qt/include/private/qgfxdriverinterface_p.h exists in filesystem
qt3: /opt/qt/include/private/qgl_x11_p.h exists in filesystem
qt3: /opt/qt/include/private/qgpluginmanager_p.h exists in filesystem
qt3: /opt/qt/include/private/qimageformatinterface_p.h exists in filesystem
qt3: /opt/qt/include/private/qinputcontext_p.h exists in filesystem
qt3: /opt/qt/include/private/qinternal_p.h exists in filesystem
qt3: /opt/qt/include/private/qisciicodec_p.h exists in filesystem
qt3: /opt/qt/include/private/qkbddriverinterface_p.h exists in filesystem
qt3: /opt/qt/include/private/qlayoutengine_p.h exists in filesystem
qt3: /opt/qt/include/private/qlibrary_p.h exists in filesystem
qt3: /opt/qt/include/private/qlocale_p.h exists in filesystem
qt3: /opt/qt/include/private/qlock_p.h exists in filesystem
qt3: /opt/qt/include/private/qmousedriverinterface_p.h exists in filesystem
qt3: /opt/qt/include/private/qmutex_p.h exists in filesystem
qt3: /opt/qt/include/private/qmutexpool_p.h exists in filesystem
qt3: /opt/qt/include/private/qpainter_p.h exists in filesystem
qt3: /opt/qt/include/private/qpluginmanager_p.h exists in filesystem
qt3: /opt/qt/include/private/qprinter_p.h exists in filesystem
qt3: /opt/qt/include/private/qpsprinter_p.h exists in filesystem
qt3: /opt/qt/include/private/qrichtext_p.h exists in filesystem
qt3: /opt/qt/include/private/qscriptengine_p.h exists in filesystem
qt3: /opt/qt/include/private/qsettings_p.h exists in filesystem
qt3: /opt/qt/include/private/qsharedmemory_p.h exists in filesystem
qt3: /opt/qt/include/private/qsqldriverinterface_p.h exists in filesystem
qt3: /opt/qt/include/private/qsqlextension_p.h exists in filesystem
qt3: /opt/qt/include/private/qsqlmanager_p.h exists in filesystem
qt3: /opt/qt/include/private/qstyleinterface_p.h exists in filesystem
qt3: /opt/qt/include/private/qsvgdevice_p.h exists in filesystem
qt3: /opt/qt/include/private/qsyntaxhighlighter_p.h exists in filesystem
qt3: /opt/qt/include/private/qt_x11_p.h exists in filesystem
qt3: /opt/qt/include/private/qtextcodecinterface_p.h exists in filesystem
qt3: /opt/qt/include/private/qtextengine_p.h exists in filesystem
qt3: /opt/qt/include/private/qtextlayout_p.h exists in filesystem
qt3: /opt/qt/include/private/qthreadinstance_p.h exists in filesystem
qt3: /opt/qt/include/private/qtitlebar_p.h exists in filesystem
qt3: /opt/qt/include/private/qucom_p.h exists in filesystem
qt3: /opt/qt/include/private/qucomextra_p.h exists in filesystem
qt3: /opt/qt/include/private/qunicodetables_p.h exists in filesystem
qt3: /opt/qt/include/private/qwidget_p.h exists in filesystem
qt3: /opt/qt/include/private/qwidgetinterface_p.h exists in filesystem
qt3: /opt/qt/include/private/qwidgetresizehandler_p.h exists in filesystem
qt3: /opt/qt/include/q1xcompatibility.h exists in filesystem
qt3: /opt/qt/include/qabstractlayout.h exists in filesystem
qt3: /opt/qt/include/qaccel.h exists in filesystem
qt3: /opt/qt/include/qaccessible.h exists in filesystem
qt3: /opt/qt/include/qaction.h exists in filesystem
qt3: /opt/qt/include/qapp.h exists in filesystem
qt3: /opt/qt/include/qapplication.h exists in filesystem
qt3: /opt/qt/include/qarray.h exists in filesystem
qt3: /opt/qt/include/qasciicache.h exists in filesystem
qt3: /opt/qt/include/qasciidict.h exists in filesystem
qt3: /opt/qt/include/qassistantclient.h exists in filesystem
qt3: /opt/qt/include/qasyncimageio.h exists in filesystem
qt3: /opt/qt/include/qasyncio.h exists in filesystem
qt3: /opt/qt/include/qbig5codec.h exists in filesystem
qt3: /opt/qt/include/qbitarray.h exists in filesystem
qt3: /opt/qt/include/qbitarry.h exists in filesystem
qt3: /opt/qt/include/qbitmap.h exists in filesystem
qt3: /opt/qt/include/qbrush.h exists in filesystem
qt3: /opt/qt/include/qbttngrp.h exists in filesystem
qt3: /opt/qt/include/qbuffer.h exists in filesystem
qt3: /opt/qt/include/qbutton.h exists in filesystem
qt3: /opt/qt/include/qbuttongroup.h exists in filesystem
qt3: /opt/qt/include/qcache.h exists in filesystem
qt3: /opt/qt/include/qcanvas.h exists in filesystem
qt3: /opt/qt/include/qcdestyle.h exists in filesystem
qt3: /opt/qt/include/qcheckbox.h exists in filesystem
qt3: /opt/qt/include/qchkbox.h exists in filesystem
qt3: /opt/qt/include/qcleanuphandler.h exists in filesystem
qt3: /opt/qt/include/qclipboard.h exists in filesystem
qt3: /opt/qt/include/qclipbrd.h exists in filesystem
qt3: /opt/qt/include/qcollect.h exists in filesystem
qt3: /opt/qt/include/qcollection.h exists in filesystem
qt3: /opt/qt/include/qcolor.h exists in filesystem
qt3: /opt/qt/include/qcolordialog.h exists in filesystem
qt3: /opt/qt/include/qcombo.h exists in filesystem
qt3: /opt/qt/include/qcombobox.h exists in filesystem
qt3: /opt/qt/include/qcommonstyle.h exists in filesystem
qt3: /opt/qt/include/qcompactstyle.h exists in filesystem
qt3: /opt/qt/include/qconfig-dist.h exists in filesystem
qt3: /opt/qt/include/qconfig-large.h exists in filesystem
qt3: /opt/qt/include/qconfig-medium.h exists in filesystem
qt3: /opt/qt/include/qconfig-minimal.h exists in filesystem
qt3: /opt/qt/include/qconfig-small.h exists in filesystem
qt3: /opt/qt/include/qconfig.h exists in filesystem
qt3: /opt/qt/include/qconnect.h exists in filesystem
qt3: /opt/qt/include/qconnection.h exists in filesystem
qt3: /opt/qt/include/qcstring.h exists in filesystem
qt3: /opt/qt/include/qcursor.h exists in filesystem
qt3: /opt/qt/include/qdatabrowser.h exists in filesystem
qt3: /opt/qt/include/qdatastream.h exists in filesystem
qt3: /opt/qt/include/qdatatable.h exists in filesystem
qt3: /opt/qt/include/qdataview.h exists in filesystem
qt3: /opt/qt/include/qdatetime.h exists in filesystem
qt3: /opt/qt/include/qdatetimeedit.h exists in filesystem
qt3: /opt/qt/include/qdatetm.h exists in filesystem
qt3: /opt/qt/include/qdeepcopy.h exists in filesystem
qt3: /opt/qt/include/qdesktopwidget.h exists in filesystem
qt3: /opt/qt/include/qdial.h exists in filesystem
qt3: /opt/qt/include/qdialog.h exists in filesystem
qt3: /opt/qt/include/qdict.h exists in filesystem
qt3: /opt/qt/include/qdir.h exists in filesystem
qt3: /opt/qt/include/qdns.h exists in filesystem
qt3: /opt/qt/include/qdockarea.h exists in filesystem
qt3: /opt/qt/include/qdockwindow.h exists in filesystem
qt3: /opt/qt/include/qdom.h exists in filesystem
qt3: /opt/qt/include/qdragobject.h exists in filesystem
qt3: /opt/qt/include/qdrawutil.h exists in filesystem
qt3: /opt/qt/include/qdrawutl.h exists in filesystem
qt3: /opt/qt/include/qdropsite.h exists in filesystem
qt3: /opt/qt/include/qdstream.h exists in filesystem
qt3: /opt/qt/include/qeditorfactory.h exists in filesystem
qt3: /opt/qt/include/qerrormessage.h exists in filesystem
qt3: /opt/qt/include/qeucjpcodec.h exists in filesystem
qt3: /opt/qt/include/qeuckrcodec.h exists in filesystem
qt3: /opt/qt/include/qevent.h exists in filesystem
qt3: /opt/qt/include/qeventloop.h exists in filesystem
qt3: /opt/qt/include/qfeatures.h exists in filesystem
qt3: /opt/qt/include/qfile.h exists in filesystem
qt3: /opt/qt/include/qfiledef.h exists in filesystem
qt3: /opt/qt/include/qfiledialog.h exists in filesystem
qt3: /opt/qt/include/qfiledlg.h exists in filesystem
qt3: /opt/qt/include/qfileinf.h exists in filesystem
qt3: /opt/qt/include/qfileinfo.h exists in filesystem
qt3: /opt/qt/include/qfocusdata.h exists in filesystem
qt3: /opt/qt/include/qfont.h exists in filesystem
qt3: /opt/qt/include/qfontdatabase.h exists in filesystem
qt3: /opt/qt/include/qfontdialog.h exists in filesystem
qt3: /opt/qt/include/qfontinf.h exists in filesystem
qt3: /opt/qt/include/qfontinfo.h exists in filesystem
qt3: /opt/qt/include/qfontmet.h exists in filesystem
qt3: /opt/qt/include/qfontmetrics.h exists in filesystem
qt3: /opt/qt/include/qframe.h exists in filesystem
qt3: /opt/qt/include/qftp.h exists in filesystem
qt3: /opt/qt/include/qgarray.h exists in filesystem
qt3: /opt/qt/include/qgb18030codec.h exists in filesystem
qt3: /opt/qt/include/qgbkcodec.h exists in filesystem
qt3: /opt/qt/include/qgcache.h exists in filesystem
qt3: /opt/qt/include/qgdict.h exists in filesystem
qt3: /opt/qt/include/qgeneric.h exists in filesystem
qt3: /opt/qt/include/qgif.h exists in filesystem
qt3: /opt/qt/include/qgl.h exists in filesystem
qt3: /opt/qt/include/qglcolormap.h exists in filesystem
qt3: /opt/qt/include/qglist.h exists in filesystem
qt3: /opt/qt/include/qglobal.h exists in filesystem
qt3: /opt/qt/include/qgplugin.h exists in filesystem
qt3: /opt/qt/include/qgrid.h exists in filesystem
qt3: /opt/qt/include/qgridview.h exists in filesystem
qt3: /opt/qt/include/qgroupbox.h exists in filesystem
qt3: /opt/qt/include/qgrpbox.h exists in filesystem
qt3: /opt/qt/include/qguardedptr.h exists in filesystem
qt3: /opt/qt/include/qgvector.h exists in filesystem
qt3: /opt/qt/include/qhbox.h exists in filesystem
qt3: /opt/qt/include/qhbuttongroup.h exists in filesystem
qt3: /opt/qt/include/qheader.h exists in filesystem
qt3: /opt/qt/include/qhgroupbox.h exists in filesystem
qt3: /opt/qt/include/qhostaddress.h exists in filesystem
qt3: /opt/qt/include/qhttp.h exists in filesystem
qt3: /opt/qt/include/qiconset.h exists in filesystem
qt3: /opt/qt/include/qiconview.h exists in filesystem
qt3: /opt/qt/include/qimage.h exists in filesystem
qt3: /opt/qt/include/qimageformatplugin.h exists in filesystem
qt3: /opt/qt/include/qinputdialog.h exists in filesystem
qt3: /opt/qt/include/qintcach.h exists in filesystem
qt3: /opt/qt/include/qintcache.h exists in filesystem
qt3: /opt/qt/include/qintdict.h exists in filesystem
qt3: /opt/qt/include/qinterlacestyle.h exists in filesystem
qt3: /opt/qt/include/qiodev.h exists in filesystem
qt3: /opt/qt/include/qiodevice.h exists in filesystem
qt3: /opt/qt/include/qjiscodec.h exists in filesystem
qt3: /opt/qt/include/qjpegio.h exists in filesystem
qt3: /opt/qt/include/qjpunicode.h exists in filesystem
qt3: /opt/qt/include/qkeycode.h exists in filesystem
qt3: /opt/qt/include/qkeysequence.h exists in filesystem
qt3: /opt/qt/include/qlabel.h exists in filesystem
qt3: /opt/qt/include/qlayout.h exists in filesystem
qt3: /opt/qt/include/qlcdnum.h exists in filesystem
qt3: /opt/qt/include/qlcdnumber.h exists in filesystem
qt3: /opt/qt/include/qlibrary.h exists in filesystem
qt3: /opt/qt/include/qlined.h exists in filesystem
qt3: /opt/qt/include/qlineedit.h exists in filesystem
qt3: /opt/qt/include/qlist.h exists in filesystem
qt3: /opt/qt/include/qlistbox.h exists in filesystem
qt3: /opt/qt/include/qlistview.h exists in filesystem
qt3: /opt/qt/include/qlocale.h exists in filesystem
qt3: /opt/qt/include/qlocalfs.h exists in filesystem
qt3: /opt/qt/include/qmainwindow.h exists in filesystem
qt3: /opt/qt/include/qmap.h exists in filesystem
qt3: /opt/qt/include/qmemarray.h exists in filesystem
qt3: /opt/qt/include/qmenubar.h exists in filesystem
qt3: /opt/qt/include/qmenudata.h exists in filesystem
qt3: /opt/qt/include/qmenudta.h exists in filesystem
qt3: /opt/qt/include/qmessagebox.h exists in filesystem
qt3: /opt/qt/include/qmetaobj.h exists in filesystem
qt3: /opt/qt/include/qmetaobject.h exists in filesystem
qt3: /opt/qt/include/qmime.h exists in filesystem
qt3: /opt/qt/include/qmlined.h exists in filesystem
qt3: /opt/qt/include/qmngio.h exists in filesystem
qt3: /opt/qt/include/qmodules.h exists in filesystem
qt3: /opt/qt/include/qmotifplusstyle.h exists in filesystem
qt3: /opt/qt/include/qmotifstyle.h exists in filesystem
qt3: /opt/qt/include/qmovie.h exists in filesystem
qt3: /opt/qt/include/qmsgbox.h exists in filesystem
qt3: /opt/qt/include/qmultilinedit.h exists in filesystem
qt3: /opt/qt/include/qmultilineedit.h exists in filesystem
qt3: /opt/qt/include/qmutex.h exists in filesystem
qt3: /opt/qt/include/qnamespace.h exists in filesystem
qt3: /opt/qt/include/qnetwork.h exists in filesystem
qt3: /opt/qt/include/qnetworkprotocol.h exists in filesystem
qt3: /opt/qt/include/qnp.h exists in filesystem
qt3: /opt/qt/include/qobjcoll.h exists in filesystem
qt3: /opt/qt/include/qobjdefs.h exists in filesystem
qt3: /opt/qt/include/qobject.h exists in filesystem
qt3: /opt/qt/include/qobjectcleanuphandler.h exists in filesystem
qt3: /opt/qt/include/qobjectdefs.h exists in filesystem
qt3: /opt/qt/include/qobjectdict.h exists in filesystem
qt3: /opt/qt/include/qobjectlist.h exists in filesystem
qt3: /opt/qt/include/qpaintd.h exists in filesystem
qt3: /opt/qt/include/qpaintdc.h exists in filesystem
qt3: /opt/qt/include/qpaintdevice.h exists in filesystem
qt3: /opt/qt/include/qpaintdevicedefs.h exists in filesystem
qt3: /opt/qt/include/qpaintdevicemetrics.h exists in filesystem
qt3: /opt/qt/include/qpainter.h exists in filesystem
qt3: /opt/qt/include/qpair.h exists in filesystem
qt3: /opt/qt/include/qpalette.h exists in filesystem
qt3: /opt/qt/include/qpdevmet.h exists in filesystem
qt3: /opt/qt/include/qpen.h exists in filesystem
qt3: /opt/qt/include/qpicture.h exists in filesystem
qt3: /opt/qt/include/qpixmap.h exists in filesystem
qt3: /opt/qt/include/qpixmapcache.h exists in filesystem
qt3: /opt/qt/include/qplatinumstyle.h exists in filesystem
qt3: /opt/qt/include/qpmcache.h exists in filesystem
qt3: /opt/qt/include/qpngio.h exists in filesystem
qt3: /opt/qt/include/qpntarry.h exists in filesystem
qt3: /opt/qt/include/qpoint.h exists in filesystem
qt3: /opt/qt/include/qpointarray.h exists in filesystem
qt3: /opt/qt/include/qpolygonscanner.h exists in filesystem
qt3: /opt/qt/include/qpopmenu.h exists in filesystem
qt3: /opt/qt/include/qpopupmenu.h exists in filesystem
qt3: /opt/qt/include/qprintdialog.h exists in filesystem
qt3: /opt/qt/include/qprinter.h exists in filesystem
qt3: /opt/qt/include/qprndlg.h exists in filesystem
qt3: /opt/qt/include/qprocess.h exists in filesystem
qt3: /opt/qt/include/qprogbar.h exists in filesystem
qt3: /opt/qt/include/qprogdlg.h exists in filesystem
qt3: /opt/qt/include/qprogressbar.h exists in filesystem
qt3: /opt/qt/include/qprogressdialog.h exists in filesystem
qt3: /opt/qt/include/qpsprn.h exists in filesystem
qt3: /opt/qt/include/qptrcollection.h exists in filesystem
qt3: /opt/qt/include/qptrdict.h exists in filesystem
qt3: /opt/qt/include/qptrlist.h exists in filesystem
qt3: /opt/qt/include/qptrqueue.h exists in filesystem
qt3: /opt/qt/include/qptrstack.h exists in filesystem
qt3: /opt/qt/include/qptrvector.h exists in filesystem
qt3: /opt/qt/include/qpushbt.h exists in filesystem
qt3: /opt/qt/include/qpushbutton.h exists in filesystem
qt3: /opt/qt/include/qqueue.h exists in filesystem
qt3: /opt/qt/include/qradiobt.h exists in filesystem
qt3: /opt/qt/include/qradiobutton.h exists in filesystem
qt3: /opt/qt/include/qrangecontrol.h exists in filesystem
qt3: /opt/qt/include/qrangect.h exists in filesystem
qt3: /opt/qt/include/qrect.h exists in filesystem
qt3: /opt/qt/include/qregexp.h exists in filesystem
qt3: /opt/qt/include/qregion.h exists in filesystem
qt3: /opt/qt/include/qrtlcodec.h exists in filesystem
qt3: /opt/qt/include/qscrbar.h exists in filesystem
qt3: /opt/qt/include/qscrollbar.h exists in filesystem
qt3: /opt/qt/include/qscrollview.h exists in filesystem
qt3: /opt/qt/include/qsemaphore.h exists in filesystem
qt3: /opt/qt/include/qsemimodal.h exists in filesystem
qt3: /opt/qt/include/qserversocket.h exists in filesystem
qt3: /opt/qt/include/qsession.h exists in filesystem
qt3: /opt/qt/include/qsessionmanager.h exists in filesystem
qt3: /opt/qt/include/qsettings.h exists in filesystem
qt3: /opt/qt/include/qsgistyle.h exists in filesystem
qt3: /opt/qt/include/qshared.h exists in filesystem
qt3: /opt/qt/include/qsignal.h exists in filesystem
qt3: /opt/qt/include/qsignalmapper.h exists in filesystem
qt3: /opt/qt/include/qsignalslotimp.h exists in filesystem
qt3: /opt/qt/include/qsimplerichtext.h exists in filesystem
qt3: /opt/qt/include/qsize.h exists in filesystem
qt3: /opt/qt/include/qsizegrip.h exists in filesystem
qt3: /opt/qt/include/qsizepolicy.h exists in filesystem
qt3: /opt/qt/include/qsjiscodec.h exists in filesystem
qt3: /opt/qt/include/qslider.h exists in filesystem
qt3: /opt/qt/include/qsocket.h exists in filesystem
qt3: /opt/qt/include/qsocketdevice.h exists in filesystem
qt3: /opt/qt/include/qsocketnotifier.h exists in filesystem
qt3: /opt/qt/include/qsocknot.h exists in filesystem
qt3: /opt/qt/include/qsortedlist.h exists in filesystem
qt3: /opt/qt/include/qsound.h exists in filesystem
qt3: /opt/qt/include/qspinbox.h exists in filesystem
qt3: /opt/qt/include/qsplashscreen.h exists in filesystem
qt3: /opt/qt/include/qsplitter.h exists in filesystem
qt3: /opt/qt/include/qsql.h exists in filesystem
qt3: /opt/qt/include/qsqlcursor.h exists in filesystem
qt3: /opt/qt/include/qsqldatabase.h exists in filesystem
qt3: /opt/qt/include/qsqldriver.h exists in filesystem
qt3: /opt/qt/include/qsqldriverplugin.h exists in filesystem
qt3: /opt/qt/include/qsqleditorfactory.h exists in filesystem
qt3: /opt/qt/include/qsqlerror.h exists in filesystem
qt3: /opt/qt/include/qsqlfield.h exists in filesystem
qt3: /opt/qt/include/qsqlform.h exists in filesystem
qt3: /opt/qt/include/qsqlindex.h exists in filesystem
qt3: /opt/qt/include/qsqlpropertymap.h exists in filesystem
qt3: /opt/qt/include/qsqlquery.h exists in filesystem
qt3: /opt/qt/include/qsqlrecord.h exists in filesystem
qt3: /opt/qt/include/qsqlresult.h exists in filesystem
qt3: /opt/qt/include/qsqlselectcursor.h exists in filesystem
qt3: /opt/qt/include/qstack.h exists in filesystem
qt3: /opt/qt/include/qstatusbar.h exists in filesystem
qt3: /opt/qt/include/qstring.h exists in filesystem
qt3: /opt/qt/include/qstringlist.h exists in filesystem
qt3: /opt/qt/include/qstrlist.h exists in filesystem
qt3: /opt/qt/include/qstrvec.h exists in filesystem
qt3: /opt/qt/include/qstyle.h exists in filesystem
qt3: /opt/qt/include/qstylefactory.h exists in filesystem
qt3: /opt/qt/include/qstyleplugin.h exists in filesystem
qt3: /opt/qt/include/qstylesheet.h exists in filesystem
qt3: /opt/qt/include/qsyntaxhighlighter.h exists in filesystem
qt3: /opt/qt/include/qt.h exists in filesystem
qt3: /opt/qt/include/qtabbar.h exists in filesystem
qt3: /opt/qt/include/qtabdialog.h exists in filesystem
qt3: /opt/qt/include/qtabdlg.h exists in filesystem
qt3: /opt/qt/include/qtable.h exists in filesystem
qt3: /opt/qt/include/qtabwidget.h exists in filesystem
qt3: /opt/qt/include/qtextbrowser.h exists in filesystem
qt3: /opt/qt/include/qtextcodec.h exists in filesystem
qt3: /opt/qt/include/qtextcodecfactory.h exists in filesystem
qt3: /opt/qt/include/qtextcodecplugin.h exists in filesystem
qt3: /opt/qt/include/qtextedit.h exists in filesystem
qt3: /opt/qt/include/qtextstream.h exists in filesystem
qt3: /opt/qt/include/qtextview.h exists in filesystem
qt3: /opt/qt/include/qthread.h exists in filesystem
qt3: /opt/qt/include/qthreadstorage.h exists in filesystem
qt3: /opt/qt/include/qtimer.h exists in filesystem
qt3: /opt/qt/include/qtl.h exists in filesystem
qt3: /opt/qt/include/qtoolbar.h exists in filesystem
qt3: /opt/qt/include/qtoolbox.h exists in filesystem
qt3: /opt/qt/include/qtoolbutton.h exists in filesystem
qt3: /opt/qt/include/qtooltip.h exists in filesystem
qt3: /opt/qt/include/qtranslator.h exists in filesystem
qt3: /opt/qt/include/qtsciicodec.h exists in filesystem
qt3: /opt/qt/include/qtstream.h exists in filesystem
qt3: /opt/qt/include/qurl.h exists in filesystem
qt3: /opt/qt/include/qurlinfo.h exists in filesystem
qt3: /opt/qt/include/qurloperator.h exists in filesystem
qt3: /opt/qt/include/qutfcodec.h exists in filesystem
qt3: /opt/qt/include/quuid.h exists in filesystem
qt3: /opt/qt/include/qvalidator.h exists in filesystem
qt3: /opt/qt/include/qvaluelist.h exists in filesystem
qt3: /opt/qt/include/qvaluestack.h exists in filesystem
qt3: /opt/qt/include/qvaluevector.h exists in filesystem
qt3: /opt/qt/include/qvariant.h exists in filesystem
qt3: /opt/qt/include/qvbox.h exists in filesystem
qt3: /opt/qt/include/qvbuttongroup.h exists in filesystem
qt3: /opt/qt/include/qvector.h exists in filesystem
qt3: /opt/qt/include/qvfbhdr.h exists in filesystem
qt3: /opt/qt/include/qvgroupbox.h exists in filesystem
qt3: /opt/qt/include/qwaitcondition.h exists in filesystem
qt3: /opt/qt/include/qwhatsthis.h exists in filesystem
qt3: /opt/qt/include/qwidcoll.h exists in filesystem
qt3: /opt/qt/include/qwidget.h exists in filesystem
qt3: /opt/qt/include/qwidgetfactory.h exists in filesystem
qt3: /opt/qt/include/qwidgetintdict.h exists in filesystem
qt3: /opt/qt/include/qwidgetlist.h exists in filesystem
qt3: /opt/qt/include/qwidgetplugin.h exists in filesystem
qt3: /opt/qt/include/qwidgetstack.h exists in filesystem
qt3: /opt/qt/include/qwindefs.h exists in filesystem
qt3: /opt/qt/include/qwindow.h exists in filesystem
qt3: /opt/qt/include/qwindowdefs.h exists in filesystem
qt3: /opt/qt/include/qwindowsstyle.h exists in filesystem
qt3: /opt/qt/include/qwinexport.h exists in filesystem
qt3: /opt/qt/include/qwizard.h exists in filesystem
qt3: /opt/qt/include/qwmatrix.h exists in filesystem
qt3: /opt/qt/include/qworkspace.h exists in filesystem
qt3: /opt/qt/include/qxml.h exists in filesystem
qt3: /opt/qt/lib/libdesignercore.a exists in filesystem
qt3: /opt/qt/lib/libdesignercore.prl exists in filesystem
qt3: /opt/qt/lib/libeditor.a exists in filesystem
qt3: /opt/qt/lib/libeditor.prl exists in filesystem
qt3: /opt/qt/lib/libqassistantclient.a exists in filesystem
qt3: /opt/qt/lib/libqassistantclient.prl exists in filesystem
qt3: /opt/qt/lib/libqt-mt.prl exists in filesystem
qt3: /opt/qt/lib/libqt-mt.so exists in filesystem
qt3: /opt/qt/lib/libqt-mt.so.3 exists in filesystem
qt3: /opt/qt/lib/libqt-mt.so.3.3 exists in filesystem
qt3: /opt/qt/lib/libqt-mt.so.3.3.8 exists in filesystem
qt3: /opt/qt/lib/libqui.prl exists in filesystem
qt3: /opt/qt/lib/libqui.so exists in filesystem
qt3: /opt/qt/lib/libqui.so.1 exists in filesystem
qt3: /opt/qt/lib/libqui.so.1.0 exists in filesystem
qt3: /opt/qt/lib/libqui.so.1.0.0 exists in filesystem
qt3: /opt/qt/lib/pkgconfig/qt-mt.pc exists in filesystem
qt3: /opt/qt/man/man1/lrelease.1.gz exists in filesystem
qt3: /opt/qt/man/man1/lupdate.1.gz exists in filesystem
qt3: /opt/qt/man/man1/moc.1.gz exists in filesystem
qt3: /opt/qt/man/man1/uic.1.gz exists in filesystem
qt3: /opt/qt/man/man3/QAccel.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAccessible.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAccessibleInterface.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAccessibleObject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAction.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QActionGroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QApplication.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAsciiCache.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAsciiCacheIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAsciiDict.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAsciiDictIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAssistantClient.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxAggregated.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxBase.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxBindable.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxObject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxScript.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxScriptEngine.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxScriptManager.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QAxWidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QBig5Codec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QBig5hkscsCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QBitArray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QBitVal.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QBitmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QBoxLayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QBrush.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QBuffer.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QButton.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QButtonGroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QByteArray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCDEStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCString.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCache.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCacheIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvas.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasEllipse.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasItemList.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasLine.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasPixmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasPixmapArray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasPolygon.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasPolygonalItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasRectangle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasSpline.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasSprite.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasText.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCanvasView.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QChar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCharRef.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCheckBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCheckListItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCheckTableItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QChildEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QClipboard.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCloseEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QColor.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QColorDialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QColorDrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QColorGroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QComboBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QComboTableItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCommonStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QConstString.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QContextMenuEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCopChannel.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCursor.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCustomEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QCustomMenuItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDataBrowser.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDataStream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDataTable.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDataView.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDate.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDateEdit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDateTime.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDateTimeEdit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDateTimeEditBase.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDeepCopy.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDesktopWidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDial.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDict.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDictIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDir.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDirectPainter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDns.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDockArea.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDockWindow.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomAttr.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomCDATASection.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomCharacterData.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomComment.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomDocument.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomDocumentFragment.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomDocumentType.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomElement.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomEntity.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomEntityReference.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomImplementation.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomNamedNodeMap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomNode.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomNodeList.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomNotation.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomProcessingInstruction.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDomText.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDoubleValidator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDragEnterEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDragLeaveEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDragMoveEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDragObject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QDropEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QEditorFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QErrorMessage.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QEucJpCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QEucKrCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QEventLoop.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFile.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFileDialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFileIconProvider.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFileInfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFilePreview.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFocusData.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFocusEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFont.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFontDatabase.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFontDialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFontInfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFontManager.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFontMetrics.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFrame.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QFtp.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGL.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGLColormap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGLContext.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGLFormat.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGLWidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGLayoutIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGb18030Codec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGb2312Codec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGbkCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGfxDriverFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGfxDriverPlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGrid.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGridLayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGridView.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGroupBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QGuardedPtr.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHBoxLayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHButtonGroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHGroupBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHeader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHebrewCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHideEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHostAddress.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHttp.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHttpHeader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHttpRequestHeader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QHttpResponseHeader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIMEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIODevice.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIconDrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIconDragEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIconDragItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIconFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIconSet.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIconView.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIconViewItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QImage.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QImageConsumer.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QImageDecoder.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QImageDrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QImageFormat.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QImageFormatPlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QImageFormatType.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QImageIO.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QInputDialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIntCache.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIntCacheIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIntDict.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIntDictIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QIntValidator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QJisCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QKbdDriverFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QKbdDriverPlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QKeyEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QKeySequence.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLCDNumber.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLabel.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLayoutItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLayoutIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLibrary.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLineEdit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QListBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QListBoxItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QListBoxPixmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QListBoxText.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QListView.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QListViewItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QListViewItemIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLocalFs.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QLocale.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMacMime.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMacStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMainWindow.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMapConstIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMapIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMemArray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMenuBar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMenuData.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMessageBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMetaObject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMetaProperty.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMimeSource.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMimeSourceFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMotif.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMotifDialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMotifPlusStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMotifStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMotifWidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMouseDriverFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMouseDriverPlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMouseEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMoveEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMovie.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMutex.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QMutexLocker.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QNPInstance.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QNPStream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QNPWidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QNPlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QNetworkOperation.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QNetworkProtocol.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QObject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QObjectCleanupHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QObjectList.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QObjectListIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPNGImagePacker.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPaintDevice.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPaintDeviceMetrics.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPaintEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPainter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPair.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPalette.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPen.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPicture.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPixmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPixmapCache.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPlatinumStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPoint.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPointArray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPopupMenu.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPrinter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QProcess.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QProgressBar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QProgressDialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPtrCollection.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPtrDict.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPtrDictIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPtrList.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPtrListIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPtrQueue.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPtrStack.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPtrVector.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QPushButton.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QRadioButton.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QRangeControl.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QRect.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QRegExp.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QRegExpValidator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QRegion.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QResizeEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSGIStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QScreen.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QScrollBar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QScrollView.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSemaphore.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QServerSocket.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSessionManager.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSettings.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QShowEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSignal.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSignalMapper.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSimpleRichText.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSize.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSizeGrip.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSizePolicy.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSjisCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSlider.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSocket.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSocketDevice.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSocketNotifier.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSound.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSpacerItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSpinBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSplashScreen.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSplitter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSql.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlCursor.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlDatabase.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlDriver.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlDriverPlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlEditorFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlError.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlField.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlFieldInfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlForm.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlIndex.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlPropertyMap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlQuery.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlRecord.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlRecordInfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlResult.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSqlSelectCursor.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStatusBar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStoredDrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStrIList.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStrList.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStrListIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QString.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStringList.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStyleFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStyleOption.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStylePlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStyleSheet.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QStyleSheetItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QSyntaxHighlighter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTab.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTabBar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTabDialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTabWidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTable.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTableItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTableSelection.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTabletEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextBrowser.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextCodecPlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextDecoder.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextDrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextEdit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextEncoder.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextIStream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextOStream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTextStream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QThread.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QThreadStorage.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTime.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTimeEdit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTimer.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTimerEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QToolBar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QToolBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QToolButton.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QToolTip.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QToolTipGroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTranslator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTranslatorMessage.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QTsciiCodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QUriDrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QUrl.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QUrlInfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QUrlOperator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QUuid.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QVBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QVBoxLayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QVButtonGroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QVGroupBox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QValidator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QValueList.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QValueListConstIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QValueListIterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QValueStack.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QValueVector.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QVariant.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWMatrix.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWSDecoration.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWSInputMethod.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWSKeyboardHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWSMouseHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWSServer.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWSWindow.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWaitCondition.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWhatsThis.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWheelEvent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWidgetFactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWidgetItem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWidgetPlugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWidgetStack.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWindowsMime.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWindowsStyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWizard.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QWorkspace.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlAttributes.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlContentHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlDTDHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlDeclHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlDefaultHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlEntityResolver.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlErrorHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlInputSource.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlLexicalHandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlLocator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlNamespaceSupport.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlParseException.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlReader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/QXmlSimpleReader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/Qt.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaccel.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaccessible.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaccessibleinterface.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaccessibleobject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaction.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qactiongroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qapplication.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qasciicache.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qasciicacheiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qasciidict.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qasciidictiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qassistantclient.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxaggregated.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxbase.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxbindable.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxfactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxobject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxscript.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxscriptengine.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxscriptmanager.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qaxwidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbig5codec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbig5hkscscodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbitarray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbitmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbitval.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qboxlayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbrush.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbuffer.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbutton.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbuttongroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qbytearray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcache.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcacheiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvas.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvasellipse.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvasitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvasitemlist.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvasline.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvaspixmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvaspixmaparray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvaspolygon.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvaspolygonalitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvasrectangle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvasspline.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvassprite.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvastext.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcanvasview.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcdestyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qchar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcharref.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcheckbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qchecklistitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qchecktableitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qchildevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qclipboard.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcloseevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcolor.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcolordialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcolordrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcolorgroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcombobox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcombotableitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcommonstyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qconststring.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcontextmenuevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcopchannel.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcstring.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcursor.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcustomevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qcustommenuitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdatabrowser.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdatastream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdatatable.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdataview.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdate.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdateedit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdatetime.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdatetimeedit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdatetimeeditbase.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdeepcopy.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdesktopwidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdial.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdict.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdictiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdir.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdirectpainter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdns.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdockarea.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdockwindow.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomattr.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomcdatasection.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomcharacterdata.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomcomment.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomdocument.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomdocumentfragment.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomdocumenttype.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomelement.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomentity.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomentityreference.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomimplementation.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomnamednodemap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomnode.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomnodelist.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomnotation.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomprocessinginstruction.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdomtext.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdoublevalidator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdragenterevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdragleaveevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdragmoveevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdragobject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qdropevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qeditorfactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qerrormessage.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qeucjpcodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qeuckrcodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qeventloop.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfile.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfiledialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfileiconprovider.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfileinfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfilepreview.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfocusdata.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfocusevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfont.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfontdatabase.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfontdialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfontinfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfontmanager.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qfontmetrics.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qframe.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qftp.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgb18030codec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgb2312codec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgbkcodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgfxdriverfactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgfxdriverplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgl.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qglayoutiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qglcolormap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qglcontext.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qglformat.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qglwidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgrid.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgridlayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgridview.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qgroupbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qguardedptr.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhboxlayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhbuttongroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qheader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhebrewcodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhgroupbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhideevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhostaddress.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhttp.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhttpheader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhttprequestheader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qhttpresponseheader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qicondrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qicondragevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qicondragitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qiconfactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qiconset.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qiconview.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qiconviewitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimage.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimageconsumer.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimagedecoder.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimagedrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimageformat.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimageformatplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimageformattype.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimageio.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qimevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qinputdialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qintcache.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qintcacheiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qintdict.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qintdictiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qintvalidator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qiodevice.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qjiscodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qkbddriverfactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qkbddriverplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qkeyevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qkeysequence.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlabel.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlayoutitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlayoutiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlcdnumber.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlibrary.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlineedit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlistbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlistboxitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlistboxpixmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlistboxtext.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlistview.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlistviewitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlistviewitemiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlocale.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qlocalfs.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmacmime.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmacstyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmainwindow.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmapconstiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmapiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmemarray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmenubar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmenudata.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmessagebox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmetaobject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmetaproperty.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmimesource.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmimesourcefactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmotif.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmotifdialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmotifplusstyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmotifstyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmotifwidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmousedriverfactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmousedriverplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmouseevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmoveevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmovie.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmutex.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qmutexlocker.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qnetworkoperation.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qnetworkprotocol.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qnpinstance.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qnplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qnpstream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qnpwidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qobject.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qobjectcleanuphandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qobjectlist.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qobjectlistiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpaintdevice.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpaintdevicemetrics.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpainter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpaintevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpair.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpalette.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpen.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpicture.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpixmap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpixmapcache.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qplatinumstyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpngimagepacker.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpoint.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpointarray.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpopupmenu.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qprinter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qprocess.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qprogressbar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qprogressdialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qptrcollection.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qptrdict.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qptrdictiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qptrlist.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qptrlistiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qptrqueue.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qptrstack.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qptrvector.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qpushbutton.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qradiobutton.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qrangecontrol.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qrect.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qregexp.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qregexpvalidator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qregion.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qresizeevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qscreen.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qscrollbar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qscrollview.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsemaphore.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qserversocket.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsessionmanager.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsettings.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsgistyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qshowevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsignal.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsignalmapper.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsimplerichtext.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsize.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsizegrip.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsizepolicy.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsjiscodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qslider.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsocket.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsocketdevice.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsocketnotifier.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsound.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qspaceritem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qspinbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsplashscreen.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsplitter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsql.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlcursor.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqldatabase.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqldriver.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqldriverplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqleditorfactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlerror.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlfield.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlfieldinfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlform.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlindex.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlpropertymap.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlquery.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlrecord.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlrecordinfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlresult.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsqlselectcursor.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstatusbar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstoreddrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstrilist.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstring.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstringlist.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstrlist.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstrlistiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstylefactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstyleoption.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstyleplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstylesheet.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qstylesheetitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qsyntaxhighlighter.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qt.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtab.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtabbar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtabdialog.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtable.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtableitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtableselection.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtabletevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtabwidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextbrowser.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextcodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextcodecplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextdecoder.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextdrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextedit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextencoder.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextistream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextostream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtextstream.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qthread.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qthreadstorage.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtime.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtimeedit.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtimer.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtimerevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtoolbar.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtoolbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtoolbutton.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtooltip.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtooltipgroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtranslator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtranslatormessage.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qtsciicodec.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/quridrag.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qurl.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qurlinfo.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qurloperator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/quuid.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvalidator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvaluelist.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvaluelistconstiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvaluelistiterator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvaluestack.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvaluevector.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvariant.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvboxlayout.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvbuttongroup.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qvgroupbox.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwaitcondition.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwhatsthis.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwheelevent.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwidget.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwidgetfactory.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwidgetitem.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwidgetplugin.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwidgetstack.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwindowsmime.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwindowsstyle.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwizard.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwmatrix.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qworkspace.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwsdecoration.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwsinputmethod.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwskeyboardhandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwsmousehandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwsserver.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qwswindow.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlattributes.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlcontenthandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmldeclhandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmldefaulthandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmldtdhandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlentityresolver.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlerrorhandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlinputsource.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmllexicalhandler.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmllocator.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlnamespacesupport.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlparseexception.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlreader.3qt.gz exists in filesystem
qt3: /opt/qt/man/man3/qxmlsimplereader.3qt.gz exists in filesystem
qt3: /opt/qt/mkspecs/linux-g++-32/qmake.conf exists in filesystem
qt3: /opt/qt/mkspecs/linux-g++-32/qplatformdefs.h exists in filesystem
qt3: /opt/qt/mkspecs/linux-g++-64/qmake.conf exists in filesystem
qt3: /opt/qt/mkspecs/linux-g++-64/qplatformdefs.h exists in filesystem
qt3: /opt/qt/mkspecs/linux-g++/qmake.conf exists in filesystem
qt3: /opt/qt/mkspecs/linux-g++/qplatformdefs.h exists in filesystem
qt3: /opt/qt/plugins/designer/libcppeditor.so exists in filesystem
qt3: /opt/qt/plugins/designer/libdlgplugin.so exists in filesystem
qt3: /opt/qt/plugins/designer/libgladeplugin.so exists in filesystem
qt3: /opt/qt/plugins/designer/libkdevdlgplugin.so exists in filesystem
qt3: /opt/qt/plugins/designer/librcplugin.so exists in filesystem
qt3: /opt/qt/plugins/designer/libwizards.so exists in filesystem
qt3: /opt/qt/plugins/imageformats/libqjpeg.so exists in filesystem
qt3: /opt/qt/plugins/imageformats/libqmng.so exists in filesystem
qt3: /opt/qt/plugins/imageformats/libqpng.so exists in filesystem
qt3: /opt/qt/plugins/sqldrivers/libqsqlite.so exists in filesystem
qt3: /opt/qt/plugins/sqldrivers/libqsqlmysql.so exists in filesystem
qt3: /opt/qt/plugins/sqldrivers/libqsqlodbc.so exists in filesystem
qt3: /opt/qt/plugins/sqldrivers/libqsqlpsql.so exists in filesystem
Errors occurred, no packages were upgraded.

```

---

### Post by ch_123 on 2008-01-16
I had the same problem too. I found that its caused by Arch downloading QT3 from the Testing repository AND the KDEmod repositiory. Edit your repositories list so that the testing section is commented out, type pacman -Scc to clear out the downloaded content, and then try to install again.

---

### Post by Opeth115 on 2008-01-16
> **ch_123 said:**
> I had the same problem too. I found that its caused by Arch downloading QT3 from the Testing repository AND the KDEmod repositiory. Edit your repositories list so that the testing section is commented out, type pacman -Scc to clear out the downloaded content, and then try to install again.

worked like a charm thanks a bunch!  :popcorn:

---

### Post by raul_ on 2008-01-16
KDEmod doesn't support [testing]

---

### Post by JR Tyner on 2008-01-17
What do yall think about Pacman the software package manager developed as part of Arch Linux?

---

### Post by Drakx on 2008-01-17
I like it, from what I've seen I've yet to really read the manual for it..

---

### Post by Rumor on 2008-01-17
> **JR Tyner said:**
> What do yall think about Pacman the software package manager developed as part of Arch Linux?

I like pacman a lot. Pacman *is* Arch. it is lightweight, it is simple and versatile. All of the features I want in a package manager, searching, installing, updating, removing, etc. are part of pacman. Once you learn the option switches, you come to realize just how flexible and useful a tool it is for keeping your system both up to date and built exactly the way you want it built.

---

### Post by fwojciec on 2008-01-17
> **JR Tyner said:**
> What do yall think about Pacman the software package manager developed as part of Arch Linux?

Imagine a crossbreed of Debian's apt-get and BSD's ports system.  You can work with binaries or sources, it's easy to build your own packages, it's lightning fast.  In other words: pure awesomeness...  And it keeps getting better with each release.

---

### Post by cdiem on 2008-01-17
Is Arch, using its stablest repo, stable enough for running as a Desktop? I mean, as I've heard it's bleeding edge and have never tried it, does it crash often, as for instance Kubuntu does? I'm attracted very much by what I've heard about its speed, but I need my computer for work; would Arch be as stable as, say, Debian Testing or would it be a bit crashier? Also, are there packages of translations, as with Ubuntu - that's one thing I like very much, having my system in my own language (Bulgarian) and it's a thing I think I'd be missing, if nonexistent. 
See, I'm attracted by the speed, but I also need stability (I really do).

---

### Post by fwojciec on 2008-01-17
> **cdiem said:**
> Is Arch, using its stablest repo, stable enough for running as a Desktop? I mean, as I've heard it's bleeding edge and have never tried it, does it crash often, as for instance Kubuntu does? I'm attracted very much by what I've heard about its speed, but I need my computer for work; would Arch be as stable as, say, Debian Testing or would it be a bit crashier? Also, are there packages of translations, as with Ubuntu - that's one thing I like very much, having my system in my own language (Bulgarian) and it's a thing I think I'd be missing, if nonexistent. 
See, I'm attracted by the speed, but I also need stability (I really do).

No idea about Bulgarian translation, but it shouldn't be a problem I think.  You might want to ask about this on Arch forums, perhaps some Bulgarian Arch users might be able to let you know how it works.

Stability -- it really depends on how you set up your system.  I've not had Arch crash on me in any significant way since I'd installed about 6 months ago, but that doesn't mean that I didn't have to do little troubleshooting every once in a while.  Stability in Arch comes with knowing your system and being hands on about maintaining it, so if you know what you're doing Arch can be extremely stable.  In the worst case you'd have to temporarily roll back the package that causes problems or reconfigure something due to upstream changes on occasion.

If I needed a stable system for a server I wouldn't choose Arch, I would probably go for something like Debian Etch in such a case, but for desktop use Arch is great and I've never had any problems with it...  On the contrary, in fact -- because by using Arch I've learned so much about Linux now I'm actually more confident in my systems than ever before and I'm not really anxious about possible breakage because even if something broke most likely I'd be able to fix it quite easily.

YMMV - of course.

---

### Post by Rumor on 2008-01-17
cdiem: I have used Arch for over a year as my desktop, first dual booting with Ubuntu and then exclusively. It is very stable. It *can* be bleeding edge if you use the [unstable] or [testing] repositories, but they are not enabled by default. 

Packages are tested pretty well before they are introduced to the main repositories. When I first moved to Arch, I found it more stable than Ubuntu was then (7.04). 

If you want stability, you will be quite satisfied with the main repositories. You'll have the current kernel and newer packages than you enjoy in Ubuntu and you'll never need to reinstall. Arch updates everything with a simple pacman -Syu.

---

### Post by Drakx on 2008-01-17
> **cdiem said:**
> Is Arch, using its stablest repo, stable enough for running as a Desktop? I mean, as I've heard it's bleeding edge and have never tried it, does it crash often, as for instance Kubuntu does? I'm attracted very much by what I've heard about its speed, but I need my computer for work; would Arch be as stable as, say, Debian Testing or would it be a bit crashier? Also, are there packages of translations, as with Ubuntu - that's one thing I like very much, having my system in my own language (Bulgarian) and it's a thing I think I'd be missing, if nonexistent. 
See, I'm attracted by the speed, but I also need stability (I really do).

I've only had Arch on my laptop for a few days at most the only problem I really had was compiz-fusion which i got fixed the same day also exaile was complaining about gnome-python-extras which again i fixed the same day i just reinstalled the package from ABS (a ports like system, if you have used FreeBSD or gentoo you should feel right at home), I've not once had the system crash or an application crash on me I've got all of the best bits from ubuntu and the speed of Arch i.e my ideal distro!.

---

### Post by cdiem on 2008-01-17
Thanks a lot for all your answers; they sound really convincing as regarding the stability; I'll check out about the Bulgarian support on the Arch-forums. Thanks again.

---

### Post by jseiser on 2008-01-17
arch is stable, Ive never had a problem with it and I run testing.

---

### Post by ST.x on 2008-01-18
Im going to be moving to Arch x64 for my desktop soon. Im not sure which DE to choose between OpenBox, Xfce, KDEMod and Fluxbox. Can openbox be used with any of those other ones?

Also, i've been on gnome on gutsy so far and what happens to the 'Notification Area' on these other DE's that don't have a panel.

---

### Post by mips on 2008-01-18
> **ST.x said:**
> Im going to be moving to Arch x64 for my desktop soon. Im not sure which DE to choose between OpenBox, Xfce, KDEMod and Fluxbox. Can openbox be used with any of those other ones?

Also, i've been on gnome on gutsy so far and what happens to the 'Notification Area' on these other DE's that don't have a panel.

I moved my desktop to arch64 2 days ago and use KDEmod. There is no reason why you cannot install another DM or WM. Try kdemod and only do a base install of it and then only add what you need. There is also a kofficemod which i have not tried yet.

I honestly don't know about notifiers for the WMs.

---

### Post by Rumor on 2008-01-18
> **ST.x said:**
> Im going to be moving to Arch x64 for my desktop soon. Im not sure which DE to choose between OpenBox, Xfce, KDEMod and Fluxbox. Can openbox be used with any of those other ones?

Also, i've been on gnome on gutsy so far and what happens to the 'Notification Area' on these other DE's that don't have a panel.

Openbox will work very nicely with gnome, allowing you to use the various gnome panels as you see fit. I do not know how well (or even *if*) it works with the other desktop environments.

---

### Post by drum on 2008-01-18
I posted this to the Arch newbie forum but got no reply so maybe someone here can help me :)
Every time I reboot I have to restart the esd daemon to get system sounds to work. I use the GNOME desktop.
It always used to work till recently after I did a pacman -Syu and updated a few files (don't remember what they were)
I have esd in rc.conf daemons.
All other sounds such as cd's, dvd's, streaming audio work fine.
Is there a way to set esd permanently so that it won't "drop out" on shutdown? Or any other ideas would be great. Arch is so good but I like my ear candy:guitar:
Thanks
Cheers:)

Edit: After restarting esd daemon the system sounds work when I click on them in Gnome/Sound Preferences/Sound but not in actual practice when normally using the computer, if you see what I mean.

---

### Post by CM Xtasy on 2008-01-19
Arch hangs on me during install.  Text flows for many seconds to about a minute and hangs at detecting Intel 3945ABG Wireless.  Once it says it detects it, it just hangs and I can hear my CD drive stop spinning.

---

### Post by kellemes on 2008-01-19
> **drum said:**
> 
Is there a way to set esd permanently so that it won't "drop out" on shutdown? Or any other ideas would be great.


Adding "esd" to the daemons-section in rc.conf will probably do the trick..

---

### Post by yabbadabbadont on 2008-01-19
> **kellemes said:**
> Adding "esd" to the daemons-section in rc.conf will probably do the trick..

> I have esd in rc.conf daemons.
Someone didn't read closely enough...  ;)

---

### Post by kellemes on 2008-01-19
> **yabbadabbadont said:**
> Someone didn't read closely enough...  ;)


:oops:

---

### Post by aeto on 2008-01-19
I've noticed a post about conflicting files, so I just want to highlight some things for the benefit of future victims.

When you install kdemod, there are many kde-* packages that are already provided. For instance, qt-enhanced provides qt3. Since the package installs files which are already on the system, the package manager will naturally not replace those files unless you force it.

Currently there can be more than one reason for conflicts, the first being a different repo with a higher version, and the other a recent issue with the provision packaging standard where a rebuild with ABS or forced install with -d (--nodeps) would sove it.

Arch is stable, for a desktop and workstation. If I didn't have to change kernels often for audio tasks and testing patches my uptime would probably be 7 months :) 2 months more if I hadn't done stupid things. Another 2 months more if I got used to hybrid suspend earlier.

---

### Post by yabbadabbadont on 2008-01-19
Also be aware that with 3.1.0 of pacman on the loose, many community packages are now broken as far as dependencies are concerned.  Installing many of the core or extra packages will try to replace community packages that were fine before 3.1.0.  According to the open bug on pacman, AUR packages will probably stay broken until 3.1.1 is released sometime next week and the AUR PKGBUILD files are updated for the new dependency syntax.

---

### Post by fwojciec on 2008-01-19
> **CM Xtasy said:**
> Arch hangs on me during install.  Text flows for many seconds to about a minute and hangs at detecting Intel 3945ABG Wireless.  Once it says it detects it, it just hangs and I can hear my CD drive stop spinning.

It can sometimes "hang" for about a minute or so when detecting intel wireless drivers -- but id does continue afterwards so all that's required is a little patience.

---

### Post by Elvish Legion on 2008-01-19
I ran into a snag trying to reinstall

My configuration files aren't being generated like they need to (so in rc.conf its just a blank screen)

Any input?

Edit: this only happens on the cd install doing a ftp/http install works fine just none of the pretty colors :( I miss the pretty colors

---

### Post by PurposeOfReason on 2008-01-19
I did a reinstall just now (messed up with compiling a kernel and it went as bad as it could have) and decided to use gnome instead of xfce. Installed acpid and gnome-power-manager but when I unplug the A/C, the backlight stays the same even though the OSD says different. Cpufreq notices the change though.

---

### Post by Rumor on 2008-01-19
> **Elvish Legion said:**
> I ran into a snag trying to reinstall

My configuration files aren't being generated like they need to (so in rc.conf its just a blank screen)

Any input?

Edit: this only happens on the cd install doing a ftp/http install works fine just none of the pretty colors :( I miss the pretty colors

I saw a thread about this some time ago and tracked it back to this bug report: [http://bugs.archlinux.org/task/8898?project=1](http://bugs.archlinux.org/task/8898?project=1)

You might want to add a comment to it. Here's the thread that was recently posted: [http://bbs.archlinux.org/viewtopic.php?id=42097](http://bbs.archlinux.org/viewtopic.php?id=42097)

Sorry it is not much help, though :(

---

### Post by raul_ on 2008-01-19
> **PurposeOfReason said:**
> I did a reinstall just now (messed up with compiling a kernel and it went as bad as it could have) and decided to use gnome instead of xfce. Installed acpid and gnome-power-manager but when I unplug the A/C, the backlight stays the same even though the OSD says different. Cpufreq notices the change though.

That's weird. I find it annoying though. I always crank up the brightness :twisted:

---

### Post by PurposeOfReason on 2008-01-19
> **raul_ said:**
> That's weird. I find it annoying though. I always crank up the brightness :twisted:
But on a laptop I go for battery life over screen. :/

---

### Post by ~LoKe on 2008-01-19
I'm considering install Arch and giving it a try.  But before I do, what are the downsides?  Are there any "features" that Ubuntu has, but Arch doesn't?  How about the other way around?  How often are packages updates?

**EDIT**: 5 minute download for the 64bit version.  166MB...mmm...bare minimum.

---

### Post by yabbadabbadont on 2008-01-20
It is rare that a day goes by without at least one package being updated.  One of the downsides is that you have to manage your rc.d init scripts yourself in the /etc/rc.conf file.  Not a big deal for a veteran Linux user, but it could cause noobs trouble.

---

### Post by PurposeOfReason on 2008-01-20
> **~LoKe said:**
> I'm considering install Arch and giving it a try.  But before I do, what are the downsides?  Are there any "features" that Ubuntu has, but Arch doesn't?  How about the other way around?  How often are packages updates?

**EDIT**: 5 minute download for the 64bit version.  166MB...mmm...bare minimum.
Pacman is your new apt-get, there is no GUI though with what I see in your screens, I don't think that is an issue. I recommend the beginners guide no matter how much you think you know. I've done over ten arch installations and I still double check it with that as it is well written. 

Even script you'll need is will commented so don't worry about that.

Updates, that depends what you install and what repositories you enable. If you use the testing and unstable you can bet your bottom dollar you'll get something daily.

The only "feature" Ubuntu has is it's already done for you. However, for every .deb you'll ever find you'll find ten times as much in the AUR. That and they all work with x86_64 so that is never an issue. Arch also has a much better wiki so I guess that is a feature. 

The only downside I find to arch is that it is too addicting, lol. But seriously, when I finally got suspend to work properly with my laptop, the auto-dim goes out on batter. Good think I have a three day weekend. :)

---

### Post by ~LoKe on 2008-01-20
Ah, my main concern was that Arch wouldn't be able to keep up with Debian in terms of packages.  If it's as you say, and especially a bare install, I'll give it a shot in the morning.  Ubuntu has become too bloated for me.

---

### Post by PurposeOfReason on 2008-01-20
> **~LoKe said:**
> Ah, my main concern was that Arch wouldn't be able to keep up with Debian in terms of packages.  If it's as you say, and especially a bare install, I'll give it a shot in the morning.  Ubuntu has become too bloated for me.
For a taste, look through here:
[http://aur.archlinux.org/packages.php](http://aur.archlinux.org/packages.php)

Then you can look here for update times:
[http://www.archlinux.org/packages/search/?sort=-last_update](http://www.archlinux.org/packages/search/?sort=-last_update)

EDIT - Is there a program to "find" the cursor with the ctrl key? Whiteglass + white window = where did it go?

---

### Post by yabbadabbadont on 2008-01-20
As I noted above, you are going to want to hold off on installing AUR packages until pacman 3.1.1 is released.  The current PKGBUILD files are incompatible with the new dependency syntax in 3.1.0 and won't be fixed until 3.1.1 comes out sometime next week.  At least that was what was said by the pacman developers in their bug tracker.

---

### Post by ~LoKe on 2008-01-20
Well, I suppose I'll be installing in a few minutes.  Just gonna wipe out my current installation (assuming the arch installer allows me to re-mount my /home partition).  Not very fond of this install (32bit was faster than 64, it seems).

I'll take a quick look at the wiki....but while I do, could anyone tell me what I'm in for?  As in, what are the big differences between Arch and Ubuntu that I'll notice right away.  Basically, will I have to set up sudo, networking, yadda yadda, before I can use them?

**[EDIT**: Wiki looks interesting.  Looks like I'll fubar everything at least once, probably five times.  Oh well, why not?

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> Ah, my main concern was that Arch wouldn't be able to keep up with Debian in terms of packages.  If it's as you say, and especially a bare install, I'll give it a shot in the morning.  Ubuntu has become too bloated for me.

I told we all started like that :lolflag:

Just have a spare pc with internet OR print the begginer's guide /installation guide, so you won't end up stuck somewhere. The installation is pretty straightforward, and the only thing you have to do is edit some configuration files (mainly rc.conf, I can't live without it), but it's really easy.

As for pacman gui's, I think the best one is YAPG (yet another pacman gui), but it's for kde. I think you won't need a gui though. You can always  browse through the packages both in the Arch and AUR site.

---

### Post by ~LoKe on 2008-01-20
Yeah, post-installation I'll find my way around and get everything working.  It's the initial install I'm slightly worried about.  I've never had to load modules manually, modify config files, etc, during an install.  I'll be back to let you know how it went (eventually).

---

### Post by PurposeOfReason on 2008-01-20
Forget sudo. It's all about su, password, and being root. But if you need sudo, you'll have to install it (pacman -S sudo) and set it up (AKA, uncomment a few lines). If you have a spare computer, printer, notes, whatever, take them up to the point you can get to a GUI.

Have an ethernet connection. To sum up the install.

Partition using c-disk
Mount points
Edit main files (like two lines per one [/etc/rc.conf, /etc/hosts, /etc/locale.gen]).
Edit /etc/pacman.conf to enable which repositories you want (community, core, extra for sure).
Run a pacman -Syu
Make a user
Install xorg
Install a desktop environment

Really, it's not that bad and to get a full gnome enviroment with compiz it took me 3 hours to have it perfect with a max internet speed of 130kbs.

EDIT - Don't worry about modules. HWdetect (make sure to run it, it will ask) will do it for you. Everything is WELL commented so don't worry.

---

### Post by ~LoKe on 2008-01-20
Alright, that puts me at ease.

Rebooting.

---

### Post by ~LoKe on 2008-01-20
Well, the installer was much simpler than I thought it would be.

Now I've got an issue.  **pacman -Sy** gives me problems:
> error: failed to synchronize any databases
After a list of "error: failed retrieving file..."

Sounds like I messed up my internet connection.

---

### Post by PurposeOfReason on 2008-01-20
> **~LoKe said:**
> Well, the installer was much simpler than I thought it would be.

Now I've got an issue.  **pacman -Sy** gives me problems:

After a list of "error: failed retrieving file..."

Sounds like I messed up my internet connection.
Try a ping -c 3 [www.google](www.google) to find out. if that works, look at your /etc/pacman.conf. 

Make sure your /etc/rc.conf internet line is like:
```
lo="lo 127.0.0.1"
eth0="dhcp"
wlan0="dhcp"
#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
INTERFACES=(lo !eth0 !wlan0)
```

and your hostname in your /etc/rc.conf matches the /etc/hosts one. I'm just going to post both of my files to give you an idea. Keep in mind I have my interfaces banged out as well as network in my daemons because I use wicd. Don't do that yet.

/etc/rc.conf
```
#
# /etc/rc.conf - Main Configuration for Arch Linux
#

#
# -----------------------------------------------------------------------
# LOCALIZATION
# -----------------------------------------------------------------------
#
# LOCALE: available languages can be listed with the 'locale -a' command
# HARDWARECLOCK: set to "UTC" or "localtime"
# TIMEZONE: timezones are found in /usr/share/zoneinfo
# KEYMAP: keymaps are found in /usr/share/kbd/keymaps
# CONSOLEFONT: found in /usr/share/kbd/consolefonts (only needed for non-US)
# CONSOLEMAP: found in /usr/share/kbd/consoletrans
# USECOLOR: use ANSI color sequences in startup messages
#
LOCALE="en_US.utf8"
HARDWARECLOCK="localtime"
TIMEZONE="Canada/Pacific"
KEYMAP="us"
CONSOLEFONT=
CONSOLEMAP=
USECOLOR="yes"

#
# -----------------------------------------------------------------------
# HARDWARE
# -----------------------------------------------------------------------
#
# Scan hardware and load required modules at bootup
MOD_AUTOLOAD="yes"
# Module Blacklist - modules in this list will never be loaded by udev
MOD_BLACKLIST=()
#
# Modules to load at boot-up (in this order)
#   - prefix a module with a ! to blacklist it
#
MODULES=(acpi-cpufreq cpufreq_ondemand cpufreq_powersave sky2 iwl4965 snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm snd-timer snd snd-hda-intel soundcore sony_laptop)
# Scan for LVM volume groups at startup, required if you use LVM
USELVM="no"

#
# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
HOSTNAME="reasons"
#
# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available
# interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
#
# Note: to use DHCP, set your interface to be "dhcp" (eth0="dhcp")
#
lo="lo 127.0.0.1"
eth0="dhcp"
wlan0="dhcp"
#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
INTERFACES=(lo !eth0 !wlan0)
#
# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
#
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network-profiles
#
#NET_PROFILES=(main)

#
# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng @hal !dhcdbd !networkmanager @wicd !network @netfs crond @acpid @alsa @cups @fam @mpd @gdm)


# End of file
```

/etc/hosts
```
#
# /etc/hosts: static lookup table for host names
#

#<ip-address>	<hostname.domain.org>	<hostname>
127.0.0.1		localhost.localdomain	localhost reasons

# End of file
```

/etc/pacman.conf
```
#
# /etc/pacman.conf
#
# See the pacman manpage for option directives

#
# GENERAL OPTIONS
#
[options]
LogFile     = /var/log/pacman.log
HoldPkg     = pacman glibc
#XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u

#
# REPOSITORIES
#   - can be defined here or included from another file
#   - pacman will search repositories in the order defined here
#   - local/custom mirrors can be added here or in separate files
#   - repositories listed first will take precedence when packages
#     have identical names, regardless of version number
#
[testing]
Include = /etc/pacman.d/testing

[core]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/core

[extra]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/extra

[community]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/community

#[unstable]
# Add your preferred servers here, they will be used first
#Include = /etc/pacman.d/unstable

# An example of a custom package repository.  See the pacman manpage for
# tips on creating your own repositories.
#[custom]
#Server = file:///home/custompkgs

```


EDIT - LOOK AT THAT COFFEE CUP!

---

### Post by raul_ on 2008-01-20
You're not using the latest pacman huh? :P

All the repositories now use the "mirrorlist" file in /etc/pacman.d instead of the file with their name. Much simpler. Throw in rankmirrors, and you can't beat that.

Loke: Can you access web pages at least? Should be something about rc.conf, if your connection isn't working, just as PurposeOfReason stated

---

### Post by ~LoKe on 2008-01-20
Looks about the same.  However, I get "Unknown host XXX.com" when I try to ping an address.  This makes me thing it's a problem with my /etc/hosts

> 127.0.0.1 localhost.localdomain myhost

"myhost" is unfortunately my system's name (oops).

---

### Post by ~LoKe on 2008-01-20
> **raul_ said:**
> You're not using the latest pacman huh? :P
I don't know.  I just downloaded the CD on the website and installed.

> **raul_ said:**
> Loke: Can you access web pages at least? Should be something about rc.conf, if your connection isn't working, just as PurposeOfReason stated

I haven't even installed xorg or a DE yet. ;)

**EDIT**: /etc/resolv.conf is empty. o_O

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> Well, the installer was much simpler than I thought it would be.

Now I've got an issue.  **pacman -Sy** gives me problems:

After a list of "error: failed retrieving file..."

Sounds like I messed up my internet connection.

That means that the network is not properly set up.  

Can you post the output of ifconfig and iwconfig (if your network is is wireless) - both run as root - as well as your rc.conf?

---

### Post by ~LoKe on 2008-01-20
**ifconfig eth0**
> eth0     link encap:Ethernet HWaddr 00:50:8D:9F:56:6D
inet addr:192.168.0.2 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
--- RX/TX packet stuff, no errors, drops, etc ---
RX/TX bytes:0 (0.0 b)
Interrupt:18

**/etc/rc.conf** (relevant lines)
> HOSTNAME="myhost"
lo="lo 127.0.0.1"
eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
INTERFACES=(lo eth0)

gateway="default gw 192.168.0.1"
ROUTES=(!gateway)

*whew*

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> I don't know.  I just downloaded the CD on the website and installed.



I haven't even installed xorg or a DE yet. ;)

**EDIT**: /etc/resolv.conf is empty. o_O

I was talking to PurposeOfReason on that one :D sorry about that
just for testing, try commenting your eth0 line, and adding 

```

eth0="dhcp"

```

then do a 

sudo /etc/rc.d/network restart

and try pinging something

---

### Post by ~LoKe on 2008-01-20
On **/etc/rc.d/network restart** while it's starting, I get an error, "Error, eth0:timed out"

Tried a second time and no error.  ping still doesn't work.

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> On **/etc/rc.d/network restart** while it's starting, I get an error, "Error, eth0:timed out"

Tried a second time and no error.  ping still doesn't work.

Humm..those settings worked for the FTP install? Or you installed from the CD?

If you installed from the cd, maybe those settings are wrong. Did you copy those from PurposeOfReason?

Where are you posting from right now?

---

### Post by ~LoKe on 2008-01-20
I installed from CD, and none of the settings are different from the way they came (with the exception of the modification you told me to try with /etc/rc.conf).

I'm posting from a laptop right now.

If I re-install, what do I have to look out for in order to not have this problem again?

---

### Post by raul_ on 2008-01-20
Well, it's not really an installation problem, is more of a network settings problem :-k


. If your laptop has a working internet connection , you could write down the laptop's internet settings and copy them to your rc.conf file. Like ip, gateway, etc...

---

### Post by ~LoKe on 2008-01-20
They're all the same. :(

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> **ifconfig eth0**


**/etc/rc.conf** (relevant lines)


*whew*

Remove the exclamation mark from before gateway in the ROUTES line (exclamation mark is only needed if you use dhcp).

---

### Post by raul_ on 2008-01-20
Ok, try undoing what I told you, and now remove the ! from the ROUTE list. After that, do a network restart and try again

---

### Post by Gigamo on 2008-01-20
Not that it might be a help, but you could try doing the FTP installation. That way you're sure your network works, as it will automatically set it up with dhcp and keep the settings in the installation. Also by doing this you will already install all latest packages, instead of upgrading them from the ones you installed with the core CD.

---

### Post by ~LoKe on 2008-01-20
Yeah, I'm going to re-install  Thanks for all the effort, though!

---

### Post by raul_ on 2008-01-20
Keep us posted :) good luck

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> Yeah, I'm going to re-install  Thanks for all the effort, though!

If problem is, I'm 99% sure, to do with the exclamation mark in the routes line, so you don't have to reinstall -- you shouldn't have to reinstall Arch ever (that's one of the differences compared to Ubuntu).

EDIT: Also, as Rumor points out below, change eth0= to eth= (see his post)

---

### Post by PurposeOfReason on 2008-01-20
Talk to me about this new pacman as in link to AUR (I'm assuming that where I'll get it). Or is it coming out soon and I should just wait?

---

### Post by Rumor on 2008-01-20
> **~LoKe said:**
> HOSTNAME="myhost"
lo="lo 127.0.0.1"
eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
INTERFACES=(lo eth0)


I would change your eth0= line to eth0="dhcp" and then do an /etc/rc.d/network restart and then try pinging a site. The rest of the lines above look fine as they are to me.

---

### Post by PurposeOfReason on 2008-01-20
> **fwojciec said:**
> If problem is, I'm 99% sure, to do with the exclamation mark in the routes line, so you don't have to reinstall -- you shouldn't have to reinstall Arch ever (that's one of the differences compared to Ubuntu).

Sometimes it's easier though, like when you brake your kernel like I have so many times. :(

---

### Post by raul_ on 2008-01-20
> **PurposeOfReason said:**
> Talk to me about this new pacman as in link to AUR (I'm assuming that where I'll get it). Or is it coming out soon and I should just wait?

[http://www.archlinux.org/news/378/]("http://www.archlinux.org/news/378/")

should be available. I got it from [testing]

---

### Post by PurposeOfReason on 2008-01-20
```
[shawn] pacman -V

 .--.                  Pacman v3.1.0 - libalpm v2.0.0
/ _.-' .-.  .-.  .-.   Copyright (C) 2002-2007 Judd Vinet <jvinet@zeroflux.org>
\  '-. '-'  '-'  '-'
 '--'
                       This program may be freely redistributed under
                       the terms of the GNU General Public License

```

I guess I have it. So should I be configuring pacman.conf differently?

---

### Post by mips on 2008-01-20
pacman -S pacman

There are currently issues with pacman wich will be sorted by next week.

---

### Post by raul_ on 2008-01-20
> **PurposeOfReason said:**
> ```
[shawn] pacman -V

 .--.                  Pacman v3.1.0 - libalpm v2.0.0
/ _.-' .-.  .-.  .-.   Copyright (C) 2002-2007 Judd Vinet <jvinet@zeroflux.org>
\  '-. '-'  '-'  '-'
 '--'
                       This program may be freely redistributed under
                       the terms of the GNU General Public License

```

I guess I have it. So should I be configuring pacman.conf differently?


Check if you have a mirrorlist file in /etc/pacman.d/

---

### Post by PurposeOfReason on 2008-01-20
This look right?
/etc/pacman.d/mirrorlist

```
#
# $repo: Arch Linux @REPO@ repository
#

# United States
Server = ftp://ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.nethat.com/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://locke.suu.edu/linux/dist/archlinux/$repo/os/x86_64
Server = ftp://mirrors.unixheads.org/archlinux/$repo/os/x86_64
Server = ftp://ftp-linux.cc.gatech.edu/pub/linux/distributions/archlinux/$repo/os/x86_64
Server = ftp://mirror.cs.vt.edu/pub/ArchLinux/$repo/os/x86_64
Server = http://mirrors.easynews.com/linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.ibiblio.org/pub/linux/distributions/archlinux/$repo/os/x86_64
Server = http://holmes.umflint.edu/archlinux/$repo/os/x86_64

# South America
# - Brazil
Server = http://archlinux.c3sl.ufpr.br/$repo/os/x86_64
Server = ftp://archlinux.c3sl.ufpr.br/archlinux/$repo/os/x86_64

# Europe
# - Austria
Server = ftp://gd.tuwien.ac.at/opsys/linux/archlinux/$repo/os/x86_64
# - Belgium
Server = ftp://ftp.belnet.be/mirror/archlinux.org/$repo/os/x86_64
# - Czech Republic
Server = ftp://ftp.sh.cvut.cz/MIRRORS/arch/$repo/os/x86_64
# - Estonia
Server = ftp://ftp.estpak.ee/pub/archlinux/$repo/os/x86_64
# - Finland
Server = ftp://ftp.sixnix.net/pub/archlinux/$repo/os/x86_64
# - France
Server = ftp://mir1.archlinuxfr.org/archlinux/$repo/os/x86_64
Server = ftp://mir2.archlinuxfr.org/archlinux/$repo/os/x86_64
Server = ftp://distrib-coffee.ipsl.jussieu.fr/pub/linux/archlinux/$repo/os/x86_64
Server = http://mir.archlinux.fr/$repo/os/x86_64
Server = ftp://ftp.free.fr/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Germany
Server = ftp://ftp.tu-chemnitz.de/pub/linux/sunsite.unc-mirror/distributions/archlinux/$repo/os/x86_64
Server = ftp://ftp.hosteurope.de/mirror/ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.archlinuxppc.org/i686/$repo/os/x86_64
# - Great Britain
Server = http://www.mirrorservice.org/sites/ftp.archlinux.org/$repo/os/x86_64
# - Greece
Server = ftp://ftp.ntua.gr/pub/linux/archlinux/$repo/os/x86_64
# - Hungary
Server = ftp://ftp.mfa.kfki.hu/pub/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Ireland
Server = ftp://ftp.heanet.ie/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Italy
Server = ftp://mi.mirror.garr.it/mirrors/archlinux/$repo/os/x86_64
# - Netherlands
Server = ftp://ftp.nluug.nl/pub/metalab/distributions/archlinux/$repo/os/x86_64
Server = ftp://ftp.surfnet.nl/pub/os/Linux/distr/archlinux/$repo/os/x86_64
# - Poland
Server = ftp://ftp.icm.edu.pl/pub/Linux/sunsite/distributions/archlinux/$repo/os/x86_64
Server = ftp://mirror.icis.pcz.pl/archlinux/$repo/os/x86_64
# - Portugal
Server = ftp://cesium.di.uminho.pt/pub/archlinux/$repo/os/x86_64
# - Romania
Server = ftp://ftp.iasi.roedu.net/mirrors/archlinux.org/$repo/os/x86_64
# - Russia
Server = ftp://archlinux.org.ru/pub/archlinux/$repo/os/x86_64
Server = ftp://mirror.yandex.ru/archlinux/$repo/os/x86_64
Server = http://archlinux.freeside.ru/$repo/os/x86_64
# - Sweden
Server = ftp://ftp.ds.hj.se/pub/os/linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.gigabit.nu/$repo/os/x86_64
# - Switzerland
Server = ftp://archlinux.puzzle.ch/$repo/os/x86_64
# - Turkey
Server = http://server.elsistech.com/archlinux/$repo/os/x86_64
# - Ukraine
Server = ftp://hell.org.ua/archlinux/$repo/os/x86_64
Server = ftp://ftp.linux.kiev.ua/pub/Linux/ArchLinux/$repo/os/x86_64

# Asia
# - Israel
Server = http://mirror.isoc.org.il/pub/archlinux/$repo/os/x86_64

# Australia
Server = ftp://mirror.pacific.net.au/linux/archlinux/$repo/os/x86_64
Server = ftp://mirror.aarnet.edu.au/pub/archlinux/$repo/os/x86_64

```

Never touched it or read about rankmirrors.

---

### Post by raul_ on 2008-01-20
That's it :)

Well, rankmirrors is a program, it's pretty neat. You just run

rankmirrors -n 2 /etc/pacman.d/mirrorlist

and it will output the 2 fastest mirrors in that list. After that, you can move those mirrors to the top os the list.

Now with pacman 3.1, you don't need to edit file by file. You just change mirrorlist, and make every repo use it. Here's my relevant part of pacman.conf:

```

[testing]
Include = /etc/pacman.d/mirrorlist

[core]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

[extra]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

[community]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

[unstable]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist


```

You can see that they all use mirrorlist

---

### Post by PurposeOfReason on 2008-01-20
So I don't even have to put them in any order? I may have just died.

EDIT - running rankmirrors right now. So when that is done, the two it gives me I comment out and the put at the top? Do they have to be in the same country category or can I put them at the top of the file before everything?

---

### Post by raul_ on 2008-01-20
> **PurposeOfReason said:**
> So I don't even have to put them in any order? I may have just died.

Well, the mirrors in 'mirrorlist' have to be in order, so just copy the output of rankmirrors to the top of the list, and that way you'll always use the fastest mirrors. I use 2, because in case one of them is down, i always have backup.

The big thing about mirrorlist, is that if your preferred server was down, you had to manually edit every single file in /etc/pacman.d/

Really painful. But no more! :D

---

### Post by PurposeOfReason on 2008-01-20
Seems faster. Just making sure this all looks right:
mirrorlist:
```
#
# $repo: Arch Linux @REPO@ repository
#

Server = http://mirrors.easynews.com/linux/archlinux/$repo/os/x86_64
Server = http://holmes.umflint.edu/archlinux/$repo/os/x86_64


# United States
Server = ftp://ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.nethat.com/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://locke.suu.edu/linux/dist/archlinux/$repo/os/x86_64
Server = ftp://mirrors.unixheads.org/archlinux/$repo/os/x86_64
Server = ftp://ftp-linux.cc.gatech.edu/pub/linux/distributions/archlinux/$repo/os/x86_64
Server = ftp://mirror.cs.vt.edu/pub/ArchLinux/$repo/os/x86_64
Server = http://mirrors.easynews.com/linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.ibiblio.org/pub/linux/distributions/archlinux/$repo/os/x86_64
Server = http://holmes.umflint.edu/archlinux/$repo/os/x86_64

# South America
# - Brazil
Server = http://archlinux.c3sl.ufpr.br/$repo/os/x86_64
Server = ftp://archlinux.c3sl.ufpr.br/archlinux/$repo/os/x86_64

# Europe
# - Austria
Server = ftp://gd.tuwien.ac.at/opsys/linux/archlinux/$repo/os/x86_64
# - Belgium
Server = ftp://ftp.belnet.be/mirror/archlinux.org/$repo/os/x86_64
# - Czech Republic
Server = ftp://ftp.sh.cvut.cz/MIRRORS/arch/$repo/os/x86_64
# - Estonia
Server = ftp://ftp.estpak.ee/pub/archlinux/$repo/os/x86_64
# - Finland
Server = ftp://ftp.sixnix.net/pub/archlinux/$repo/os/x86_64
# - France
Server = ftp://mir1.archlinuxfr.org/archlinux/$repo/os/x86_64
Server = ftp://mir2.archlinuxfr.org/archlinux/$repo/os/x86_64
Server = ftp://distrib-coffee.ipsl.jussieu.fr/pub/linux/archlinux/$repo/os/x86_64
Server = http://mir.archlinux.fr/$repo/os/x86_64
Server = ftp://ftp.free.fr/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Germany
Server = ftp://ftp.tu-chemnitz.de/pub/linux/sunsite.unc-mirror/distributions/archlinux/$repo/os/x86_64
Server = ftp://ftp.hosteurope.de/mirror/ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.archlinuxppc.org/i686/$repo/os/x86_64
# - Great Britain
Server = http://www.mirrorservice.org/sites/ftp.archlinux.org/$repo/os/x86_64
# - Greece
Server = ftp://ftp.ntua.gr/pub/linux/archlinux/$repo/os/x86_64
# - Hungary
Server = ftp://ftp.mfa.kfki.hu/pub/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Ireland
Server = ftp://ftp.heanet.ie/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Italy
Server = ftp://mi.mirror.garr.it/mirrors/archlinux/$repo/os/x86_64
# - Netherlands
Server = ftp://ftp.nluug.nl/pub/metalab/distributions/archlinux/$repo/os/x86_64
Server = ftp://ftp.surfnet.nl/pub/os/Linux/distr/archlinux/$repo/os/x86_64
# - Poland
Server = ftp://ftp.icm.edu.pl/pub/Linux/sunsite/distributions/archlinux/$repo/os/x86_64
Server = ftp://mirror.icis.pcz.pl/archlinux/$repo/os/x86_64
# - Portugal
Server = ftp://cesium.di.uminho.pt/pub/archlinux/$repo/os/x86_64
# - Romania
Server = ftp://ftp.iasi.roedu.net/mirrors/archlinux.org/$repo/os/x86_64
# - Russia
Server = ftp://archlinux.org.ru/pub/archlinux/$repo/os/x86_64
Server = ftp://mirror.yandex.ru/archlinux/$repo/os/x86_64
Server = http://archlinux.freeside.ru/$repo/os/x86_64
# - Sweden
Server = ftp://ftp.ds.hj.se/pub/os/linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.gigabit.nu/$repo/os/x86_64
# - Switzerland
Server = ftp://archlinux.puzzle.ch/$repo/os/x86_64
# - Turkey
Server = http://server.elsistech.com/archlinux/$repo/os/x86_64
# - Ukraine
Server = ftp://hell.org.ua/archlinux/$repo/os/x86_64
Server = ftp://ftp.linux.kiev.ua/pub/Linux/ArchLinux/$repo/os/x86_64

# Asia
# - Israel
Server = http://mirror.isoc.org.il/pub/archlinux/$repo/os/x86_64

# Australia
Server = ftp://mirror.pacific.net.au/linux/archlinux/$repo/os/x86_64
Server = ftp://mirror.aarnet.edu.au/pub/archlinux/$repo/os/x86_64

```
```

#
# /etc/pacman.conf
#
# See the pacman manpage for option directives

#
# GENERAL OPTIONS
#
[options]
LogFile     = /var/log/pacman.log
HoldPkg     = pacman glibc
#XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u

#
# REPOSITORIES
#   - can be defined here or included from another file
#   - pacman will search repositories in the order defined here
#   - local/custom mirrors can be added here or in separate files
#   - repositories listed first will take precedence when packages
#     have identical names, regardless of version number
#
[testing]
Include = /etc/pacman.d/mirrorlist

[core]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

[extra]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

[community]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

#[unstable]
# Add your preferred servers here, they will be used first
#Include = /etc/pacman.d/unstable

# An example of a custom package repository.  See the pacman manpage for
# tips on creating your own repositories.
#[custom]
#Server = file:///home/custompkgs


```

---

### Post by raul_ on 2008-01-20
Exactly :)

I'm starting to worry about Loke :-k

---

### Post by ~LoKe on 2008-01-20
Maybe Arch isn't for me.   I spent an excessive amount of time downloading packages at 50kbps (I usually max out at 800...) only to find that, once again, my networking connection doesn't work.  This is getting stupid.

---

### Post by ~LoKe on 2008-01-20
DHCP works now, but I still get the package errors in pacman.  Oh well, I'll figure that out later.

Where to go from here?  How do I use pacman to install something, like xorg?

---

### Post by Gigamo on 2008-01-20
> **~LoKe said:**
> DHCP works now, but I still get the package errors in pacman.  Oh well, I'll figure that out later.

Where to go from here?  How do I use pacman to install something, like xorg?

run "pacman -S xorg"

---

### Post by PurposeOfReason on 2008-01-20
Does anyone (back to a question a few pages ago) know what command controls the brightness of a laptop screen? I figure since my cpu goes to powersave mode when I unplug the computer, the cord is noticed to be unplugged. The screen tries to dim as the OSD comes up. I'm thinking the problem is it is giving off a bad command that isn't executing properly.

---

### Post by Ub1476 on 2008-01-20
Hi, I decided to try Arch after reading only positive feedback about it, but can I run it?

I have a Intel Centrino Duo, which I'm quite sure is i386. From Archs wiki it says:

> Arch Linux is optimized for the i686 processor and therefore will not run on any lower or incompatible generations of x86 CPUs (i386,i486,i586). A Pentium II or AMD K6-2 processor or higher is required. x86-64 architectures are also officially supported. 

Am I out of luck, or will it run "slow"?

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> DHCP works now, but I still get the package errors in pacman.  Oh well, I'll figure that out later.

Where to go from here?  How do I use pacman to install something, like xorg?

read my post about rankmirrors for speed issues

[http://wiki.archlinux.org/index.php/Main_Page]("http://wiki.archlinux.org/index.php/Main_Page")

---

### Post by PurposeOfReason on 2008-01-20
> **Ub1476 said:**
> Hi, I decided to try Arch after reading only positive feedback about it, but can I run it?

I have a Intel Centrino Duo, which I'm quite sure is i386. From Archs wiki it says:

Am I out of luck, or will it run "slow"?

Perfectly fine. I'm not sure which version to go with though. The i686 works on basically everything (was it made within the last ten years basically) and 86_64 for dual cores. If you can run (I'm sorry as I don't know much how to do this) 'cpufreq-info in the terminal and see if it tells you if you have two cores. If you do, go for the 86_64. Flash is easily fixed with ndispluginwrapper.

---

### Post by ~LoKe on 2008-01-20
> **raul_ said:**
> read my post about rankmirrors for speed issues

Yep, I did that now that my connection is working.  It was an issue for the initial install, but it's done now.

And Arch works!  Yeah!!!  

I have to add myself to the sudoers file then get everything "back to normal".  I used to install the nVidia drivers using the installer from the nvidia website, that should work just the same, right?

---

### Post by PurposeOfReason on 2008-01-20
> **~LoKe said:**
> Yep, I did that now that my connection is working.  It was an issue for the initial install, but it's done now.

And Arch works!  Yeah!!!  

I have to add myself to the sudoers file then get everything "back to normal".  I used to install the nVidia drivers using the installer from the nvidia website, that should work just the same, right?
With how bleeding edge arch can be, it might be just as good to use their driver. However, a kernel is a kernel so if you want to use the nvidia website, go for it. :)

---

### Post by raul_ on 2008-01-20
> **Ub1476 said:**
> Hi, I decided to try Arch after reading only positive feedback about it, but can I run it?

I have a Intel Centrino Duo, which I'm quite sure is i386. From Archs wiki it says:



Am I out of luck, or will it run "slow"?

Well, unless your pc is like 10 years old, I don't think it's i386

---

### Post by raul_ on 2008-01-20
I don't know about these drivers, because I don't use nVidia, but have a look at this, maybe it's useful:

[http://wiki.archlinux.org/index.php/NVIDIA#How_to_install_Nvidia_Driver_with_pacman]("http://wiki.archlinux.org/index.php/NVIDIA#How_to_install_Nvidia_Driver_with_pacman")

---

### Post by Ub1476 on 2008-01-20
Well, the Centrino processors were introduced in 2006, is a x86 architecture, dual-core (CPU 0 and CPU 1). I guess I'm fine then?

*Download core now*

---

### Post by PurposeOfReason on 2008-01-20
You're great. Get the 86_64 if you want to take as much advantage of it as possible. Is there a quick way to get all the fonts from pacman? Some sites are using fonts I don't have and I'd really just like to do a pacman -S *-font but that doesn't work.

EDIT - (for my own records if I reinstall ever)
```
pacman -S artwiz-fonts font-bh-ttf font-bitstream-speedo ftgl ttf-bitstream-vera ttf-cheapskate ttf-dejavu xorg-fonts-alias xorg-fonts-cyrillic xorg-fonts-encodings xorg-fonts-misc xorg-fonts-type1 font-mathematica oldstand-font ttf-freefont ttf-liberation ttf-mgopen
```

---

### Post by Gigamo on 2008-01-20
Nice LoKe, keep us posted :D


Makes me tingle as well... But I'm gonna stick to ubuntu a little longer :D

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> I used to install the nVidia drivers using the installer from the nvidia website, that should work just the same, right?

Right - that's what I do.  You'll have to reinstall manually after major kernel updates as well (and sometimes it is also a good idea after xorg-server updates also).

---

### Post by PurposeOfReason on 2008-01-20
To my previous post which installed basically every font, what font does this page use where all the info is? It's really bad for me.

[http://dotfiles.org/~krib/.screenrc](http://dotfiles.org/~krib/.screenrc)

---

### Post by ~LoKe on 2008-01-20
It'll take a while to get used to pacman, but I like it so far. =]

My fonts and whatnot are all messed.  Time to learn all over again.  Oh, and it'll take a while to get used to type rc.d instead of init.d. ;)

---

### Post by Gigamo on 2008-01-20
> **PurposeOfReason said:**
> To my previous post which installed basically every font, what font does this page use where all the info is? It's really bad for me.

[http://dotfiles.org/~krib/.screenrc]("http://dotfiles.org/%7Ekrib/.screenrc")

Very bad for me as well.

[quote=~LoKe]
My fonts and whatnot are all messed. Time to learn all over again. Oh, and it'll take a while to get used to type rc.d instead of init.d.[/quote]

I had that problem too when I gave Arch a spin. Would be cool if you would let me know how you fixed that.

---

### Post by ~LoKe on 2008-01-20
> (2/2) checking for file conflicts                   [########################] 100%
error: could not prepare transaction
error: failed to commit transaction (conflicting files)
nvidia-utils: /usr/bin/nvidia-bug-report.sh exists in filesystem
nvidia-utils: /usr/bin/nvidia-settings exists in filesystem
nvidia-utils: /usr/bin/nvidia-xconfig exists in filesystem
nvidia-utils: /usr/lib/libGL.so.1 exists in filesystem
nvidia-utils: /usr/lib/libGL.so.169.07 exists in filesystem
nvidia-utils: /usr/lib/libGLcore.so.1 exists in filesystem
nvidia-utils: /usr/lib/libGLcore.so.169.07 exists in filesystem
nvidia-utils: /usr/lib/libXvMCNVIDIA.a exists in filesystem
nvidia-utils: /usr/lib/libXvMCNVIDIA.so.169.07 exists in filesystem
nvidia-utils: /usr/lib/libXvMCNVIDIA_dynamic.so.1 exists in filesystem
nvidia-utils: /usr/lib/libcuda.so.1 exists in filesystem
nvidia-utils: /usr/lib/libcuda.so.169.07 exists in filesystem
nvidia-utils: /usr/lib/libnvidia-tls.so.1 exists in filesystem
nvidia-utils: /usr/lib/libnvidia-tls.so.169.07 exists in filesystem
nvidia-utils: /usr/lib/xorg/modules/drivers/nvidia_drv.so exists in filesystem
nvidia-utils: /usr/lib/xorg/modules/extensions/libglx.so.169.07 exists in filesystem
nvidia-utils: /usr/lib/xorg/modules/libnvidia-wfb.so.169.07 exists in filesystem
nvidia-utils: /usr/share/applications/nvidia-settings.desktop exists in filesystem
nvidia: /lib/modules/2.6.23-ARCH/kernel/drivers/video/nvidia.ko exists in filesystem
Errors occurred, no packages were upgraded.
Eh?

---

### Post by PurposeOfReason on 2008-01-20
> **~LoKe said:**
> It'll take a while to get used to pacman, but I like it so far. =]

My fonts and whatnot are all messed.  Time to learn all over again.  Oh, and it'll take a while to get used to type rc.d instead of init.d. ;)
This should do the fonts:
pacman -S ttf-ms-fonts ttf-dejavu ttf-bitstream-vera


In general, read:
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by cardinals_fan on 2008-01-20
I am finally getting a little sick of Ubuntu.  It seems to be getting very wizardy and most configuration is gui-based.  I was also horrified to see that booting up in "Recovery mode" lands the user with ***root privileges*** - without a password prompt!  This is not secure!

Anyway, I've checked out many other distros.  So far Zenwalk was my favorite, but it also felt a bit dumbed down.  Now I am looking at Arch, and really like what I see.  It seems to be far more configurable and command-line based.  Since I'm not going to try it until school gets out (~May 25), I might as well get some input regarding its pros/cons.  Any Arch users willing to summarize their experience?  I know that that has been the entire point of this thread from the beginning, but it would be nice to hear whether anybody in my position made the switch and has more detailed advice.

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> Eh?

Are you trying to install nvidia driver pacman package after trying to install the nvidia driver manually?  If so you should be able to overwrite these files (force it be adding -f switch to the pacman command).  As long as you know what it is that you're overwriting it is usually ok to use that switch.

---

### Post by PurposeOfReason on 2008-01-20
My only advice, you'll mess up your first install so don't panic. I mean, it was all working fine (internet, DE, compiz) but it wasn't exactly clean looking or fast as I did things . . .differently. Really, start reading the wiki now and there is a good chance you'll be fine on your first try.

EDIT - loke, did you install anything else as far as graphics go?

---

### Post by raul_ on 2008-01-20
> **cardinals_fan said:**
> I am finally getting a little sick of Ubuntu.  It seems to be getting very wizardy and most configuration is gui-based.  I was also horrified to see that booting up in "Recovery mode" lands the user with ***root privileges*** - without a password prompt!  This is not secure!

Anyway, I've checked out many other distros.  So far Zenwalk was my favorite, but it also felt a bit dumbed down.  Now I am looking at Arch, and really like what I see.  It seems to be far more configurable and command-line based.  Since I'm not going to try it until school gets out (~May 25), I might as well get some input regarding its pros/cons.  Any Arch users willing to summarize their experience?  I know that that has been the entire point of this thread from the beginning, but it would be nice to hear whether anybody in my position made the switch and has more detailed advice.


Zenwalk is cool, but it's package management is nowhere near Arch. At least for me. 

have a read [http://wiki.archlinux.org/index.php/The_Arch_Way]("http://wiki.archlinux.org/index.php/The_Arch_Way")

---

### Post by cardinals_fan on 2008-01-20
I read The Arch Way - it's part of what attracted me to Arch in the first place ;-)

---

### Post by Ub1476 on 2008-01-20
Alright, I'm at the package step now. I select CD and get the to choose base, devel, lib and support. But I do not know how to tick any of them! Pressing enter will either choose all or none. Also, any suggestion which I should install? It's a laptop, mostly Intel except for the ATI graphic card.

EDIT: Figured I just need to press space to tick them^^

Help with packages is appreciated though:)

---

### Post by Gigamo on 2008-01-20
> **Ub1476 said:**
> Alright, I'm at the package step now. I select CD and get the to choose base, devel, lib and support. But I do not know how to tick any of them! Pressing enter will either choose all or none. Also, any suggestion which I should install? It's a laptop, mostly Intel except for the ATI graphic card.

Press space.

---

### Post by PurposeOfReason on 2008-01-20
> **Ub1476 said:**
> Alright, I'm at the package step now. I select CD and get the to choose base, devel, lib and support. But I do not know how to tick any of them! Pressing enter will either choose all or none. Also, any suggestion which I should install? It's a laptop, mostly Intel except for the ATI graphic card.
space key

---

### Post by Ub1476 on 2008-01-20
Thanks, I figured it out. Anyway I wonder about these "support" packages:

iptables
ipw3945 - This is a driver, right?
madwifi - What's this?
screen - What's this?
wireless-tools - What's this?

---

### Post by PurposeOfReason on 2008-01-20
> **Ub1476 said:**
> Thanks, I figured it out. Anyway I wonder about these "support" packages:

iptables
ipw3945 - This is a driver, right?
madwifi - What's this?
screen - What's this?
wireless-tools - What's this?
In this order:
driver
support type driver
addition to the terminal, don't need
tools for wireless networking

---

### Post by Gigamo on 2008-01-20
I think screen is pretty nice and useful with a nice config tho :)

---

### Post by Ub1476 on 2008-01-20
Thanks for your help!

Anyway, I'm configuring now, an I know I have a SATA or Raid HDD, but not sure which type! Should I say yes on:

Do you need support for booting from software raid arrays?

EDIT: Figured out it's a SATA, so I'll say no then.

---

### Post by ~LoKe on 2008-01-20
Can't log into the Arch forums.  Clicking the "Login" button does nothing.  Boo!

I'm gonna have to ask here...Can I get Firefox3 from the repositories/whatever?  Or do I have to compile it from source?

---

### Post by PurposeOfReason on 2008-01-20
> **~LoKe said:**
> Can't log into the Arch forums.  Clicking the "Login" button does nothing.  Boo!

I'm gonna have to ask here...Can I get Firefox3 from the repositories/whatever?  Or do I have to compile it from source?
It's in the AUR, so get the tarball from there, extract it, run makepkg. Once that is done, install it with a pacman -U *.tgz.gz
[http://aur.archlinux.org/packages.php?do_Details=1&ID=14351&O=0&L=0&C=0&K=firefox3&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd](http://aur.archlinux.org/packages.php?do_Details=1&ID=14351&O=0&L=0&C=0&K=firefox3&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd)

---

### Post by raul_ on 2008-01-20
Have a look at yaourt:

[http://bbs.archlinux.org/viewtopic.php?id=25718]("http://bbs.archlinux.org/viewtopic.php?id=25718")

---

### Post by ~LoKe on 2008-01-20
Never really realized how slow FF3 was until now.   Dear God..

---

### Post by Ub1476 on 2008-01-20
Alright, now I feel sort of stupid.. I'm going to install X and Gnome now, but when using packman, the command "packman" is not found.

Everything else works alright, and I have create a new "wheel" user.

> 
Never really realized how slow FF3 was until now. Dear God..

It's really fast for me on Gutsy, at least compared to FF2, both in speed and resources. I think Opera 9.5 still  beats it though.

---

### Post by fwojciec on 2008-01-20
Try pacman without "k" ;)

---

### Post by Majorix on 2008-01-20
Why isn't Arch updated lately? I was going to test it, so I paid their site a little visit, and saw that the distro which was usually updated like once every month wasn't updated in the last 3 months or so. What could be the reason? What should I do?

---

### Post by Ub1476 on 2008-01-20
> **fwojciec said:**
> Try pacman without "k" ;)

Thanks, that's what I get from copying in a GUI.. But it doesn't look like I have an internet connection. I get a "sync db" error. Tried to connect via  wire/cable, but it's not working. Is it possible to set up wireless network from the terminal?

---

### Post by raul_ on 2008-01-20
> **Majorix said:**
> Why isn't Arch updated lately? I was going to test it, so I paid their site a little visit, and saw that the distro which was usually updated like once every month wasn't updated in the last 3 months or so. What could be the reason? What should I do?

Arch isn't updated. It doesn't have releases like Ubuntu. It uses a rolling release system, which means that whenever the programs are updated, the packages land in the repositories. The versions you download of the site, are just snapshots of the current repositories.

---

### Post by Majorix on 2008-01-20
> **raul_ said:**
> Arch isn't updated. It doesn't have releases like Ubuntu. It uses a rolling release system, which means that whenever the programs are updated, the packages land in the repositories. The versions you download of the site, are just snapshots of the current repositories.

Hmm I see...

What's a good guide to install it and get it running with an ATI card then?

Thanks.

---

### Post by Drakx on 2008-01-20
check out the arch wiki look for beginners guide :)

---

### Post by fwojciec on 2008-01-20
> **Ub1476 said:**
> Thanks, that's what I get from copying in a GUI.. But it doesn't look like I have an internet connection. I get a "sync db" error. Tried to connect via  wire/cable, but it's not working. Is it possible to set up wireless network from the terminal?

Everything in arch is possible from the terminal but it's likely that you will have to connect directly to the router and get your cable connection to work in order to download the drivers necessary to get the wifi working.

The best thing to do is to use the [http://wiki.archlinux.org/index.php/Beginners_Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide"), read through it and try to figure out the issues as they come up.  Arch is not like Ubuntu, it'll not configure everything automatically and you'll have to set up things like users, groups, network, xorg, daemons, etc. manually.

---

### Post by ~LoKe on 2008-01-20
Heh...just realized that I have no sound whatsoever.  Maybe I was right in that Arch wasn't for me...not as knowledgeable as I thought I was. ;)

**EDIT**: > mplayer -ao alsa ~/Movies/Rush*/*
mplayer: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS32

Never ends, does it? =/

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> Heh...just realized that I have no sound whatsoever.  Maybe I was right in that Arch wasn't for me...not as knowledgeable as I thought I was. ;)

**EDIT**: 

Never ends, does it? =/

You have to set it up. Take a look at the alsa section in the wiki.

Don't worry, after the initial set up, you don't have to do anything anymore.

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> Heh...just realized that I have no sound whatsoever.  Maybe I was right in that Arch wasn't for me...not as knowledgeable as I thought I was. ;)

**EDIT**: 

Never ends, does it? =/

It looks like you're trying to run a 32 bit library on a 64bit system...  Not quite sure how you've managed that.  In either case, the error doesn't say anything about problems with sound.

Arch requires a bit of patience at first.  Don't get discouraged, you'll appreciate it in the end and learn a lot very quickly.

---

### Post by ~LoKe on 2008-01-20
I installed mplayer using pacman, so if it pulled a 32bit app...what the heck is going on?

So far I haven't seen too much appeal in Arch...I like the package manager (less so if my problems should be blamed on it) and the formatting of the boot messages.

But otherwise...?

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> I installed mplayer using pacman, so if it pulled a 32bit app...what the heck is going on?

So far I haven't seen too much appeal in Arch...I like the package manager (less so if my problems should be blamed on it) and the formatting of the boot messages.

But otherwise...?

Did you manually change the mirrors by any chance?  Make sure that your mirrors are pointing to "x86_64" not "i686" directories on the server (or whichever ones are appropriate for the architecture you're using).

---

### Post by ~LoKe on 2008-01-20
/etc/pacman.d/mirrorlist
> # United States
Server = ftp://ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.nethat.com/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://locke.suu.edu/linux/dist/archlinux/$repo/os/x86_64
Server = ftp://mirrors.unixheads.org/archlinux/$repo/os/x86_64
Server = ftp://ftp-linux.cc.gatech.edu/pub/linux/distributions/archlinux/$repo/os/x86_64
Server = ftp://mirror.cs.vt.edu/pub/ArchLinux/$repo/os/x86_64
Server = http://mirrors.easynews.com/linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.ibiblio.org/pub/linux/distributions/archlinux/$repo/os/x86_64
Server = http://holmes.umflint.edu/archlinux/$repo/os/x86_64

# South America
# - Brazil
#Server = http://archlinux.c3sl.ufpr.br/$repo/os/x86_64
#Server = ftp://archlinux.c3sl.ufpr.br/archlinux/$repo/os/x86_64

# Europe
# - Austria
Server = ftp://gd.tuwien.ac.at/opsys/linux/archlinux/$repo/os/x86_64
# - Belgium
Server = ftp://ftp.belnet.be/mirror/archlinux.org/$repo/os/x86_64
# - Czech Republic
Server = ftp://ftp.sh.cvut.cz/MIRRORS/arch/$repo/os/x86_64
# - Estonia
Server = ftp://ftp.estpak.ee/pub/archlinux/$repo/os/x86_64
# - Finland
Server = ftp://ftp.sixnix.net/pub/archlinux/$repo/os/x86_64
# - France
Server = ftp://mir1.archlinuxfr.org/archlinux/$repo/os/x86_64
Server = ftp://mir2.archlinuxfr.org/archlinux/$repo/os/x86_64
Server = ftp://distrib-coffee.ipsl.jussieu.fr/pub/linux/archlinux/$repo/os/x86_64
Server = http://mir.archlinux.fr/$repo/os/x86_64
Server = ftp://ftp.free.fr/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Germany
Server = ftp://ftp.tu-chemnitz.de/pub/linux/sunsite.unc-mirror/distributions/archlinux/$repo/os/x86_64
Server = ftp://ftp.hosteurope.de/mirror/ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.archlinuxppc.org/i686/$repo/os/x86_64
# - Great Britain
Server = http://www.mirrorservice.org/sites/ftp.archlinux.org/$repo/os/x86_64
# - Greece
Server = ftp://ftp.ntua.gr/pub/linux/archlinux/$repo/os/x86_64
# - Hungary
Server = ftp://ftp.mfa.kfki.hu/pub/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Ireland
Server = ftp://ftp.heanet.ie/mirrors/ftp.archlinux.org/$repo/os/x86_64
# - Italy
Server = ftp://mi.mirror.garr.it/mirrors/archlinux/$repo/os/x86_64
# - Netherlands
Server = ftp://ftp.nluug.nl/pub/metalab/distributions/archlinux/$repo/os/x86_64
Server = ftp://ftp.surfnet.nl/pub/os/Linux/distr/archlinux/$repo/os/x86_64
# - Poland
Server = ftp://ftp.icm.edu.pl/pub/Linux/sunsite/distributions/archlinux/$repo/os/x86_64
Server = ftp://mirror.icis.pcz.pl/archlinux/$repo/os/x86_64
# - Portugal
Server = ftp://cesium.di.uminho.pt/pub/archlinux/$repo/os/x86_64
# - Romania
Server = ftp://ftp.iasi.roedu.net/mirrors/archlinux.org/$repo/os/x86_64
# - Russia
Server = ftp://archlinux.org.ru/pub/archlinux/$repo/os/x86_64
Server = ftp://mirror.yandex.ru/archlinux/$repo/os/x86_64
Server = http://archlinux.freeside.ru/$repo/os/x86_64
# - Sweden
Server = ftp://ftp.ds.hj.se/pub/os/linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.gigabit.nu/$repo/os/x86_64
# - Switzerland
Server = ftp://archlinux.puzzle.ch/$repo/os/x86_64
# - Turkey
Server = http://server.elsistech.com/archlinux/$repo/os/x86_64
# - Ukraine
Server = ftp://hell.org.ua/archlinux/$repo/os/x86_64
Server = ftp://ftp.linux.kiev.ua/pub/Linux/ArchLinux/$repo/os/x86_64

# Asia
# - Israel
Server = http://mirror.isoc.org.il/pub/archlinux/$repo/os/x86_64

# Australia
Server = ftp://mirror.pacific.net.au/linux/archlinux/$repo/os/x86_64
Server = ftp://mirror.aarnet.edu.au/pub/archlinux/$repo/os/x86_64

# Setup-Entry
Server = [ftp://ftp.tu-chemnitz.de/pub/linux/sunsite.unc-mirror/distributions/archlinux/mirrorlist/os/x86_64](ftp://ftp.tu-chemnitz.de/pub/linux/sunsite.unc-mirror/distributions/archlinux/mirrorlist/os/x86_64)

---

### Post by raul_ on 2008-01-20
Everything's fine there.

---

### Post by ~LoKe on 2008-01-20
The thing is, I've installed plenty of other applications before/after mplayer that worked.

---

### Post by ~LoKe on 2008-01-20
> sudo pacman -S mplayer
Password: 
warning: mplayer-1.0rc2-2 is up to date -- reinstalling
resolving dependencies...
looking for inter-conflicts...

Targets: mplayer-1.0rc2-2  

Total Download Size:    0.00 MB
Total Installed Size:   8.44 MB

Proceed with installation? [Y/n]     
checking package integrity...
(1/1) checking for file conflicts                   [########################################] 100%
(1/1) upgrading mplayer                             [########################################] 100%
**/sbin/ldconfig: libraries libGL.so.1.2 and libGL.so.169.07 in directory /usr/lib have same soname but different type.**

o_O

**EDIT**: Does this have to do with my nVidia drivers?  libGL.so.169.07....169.07 is the version of the nvidia driver I installed.

---

### Post by fwojciec on 2008-01-20
libGL belongs to the nvidia driver if this helps...

EDIT: reinstalling nvidia + nvidia-utils (with -f to overwrite) should help, I think

---

### Post by ~LoKe on 2008-01-20
Yep, that did it.  Thanks!

Here's the new problem...
> [AO_ALSA] alsa-lib: conf.c:3949:(snd_config_expand) Unknown parameters AES0=6
[AO_ALSA] alsa-lib: pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM iec958:AES0=6
[AO_ALSA] alsa-lib: pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
[AO_ALSA] Playback open error: No such file or directory
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 560 x 240 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.33:1 - prescaling to correct movie aspect.
[swscaler @ 0xf6b710]SwScaler: using unscaled yuv420p -> bgr24 special converter
VO: [gl2] 560x240 => 560x240 BGR 24-bit
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
[gl2] no GLX support present
FATAL: Cannot initialize video driver.

FATAL: Could not initialize video filters (-vf) or video output (-vo).

I take it I need to add the glx module to /etc/X11/XF86Free...but the audio...

---

### Post by raul_ on 2008-01-20
Well, looking on the bright side, once you've got it working, it will be a boost to your ego :D

my first setup didn't go smoothly either. I just was a little stubborn, and never had a problem since.

did you setup alsa or oss? Like, is your user in the audio group, etc etc?

[http://wiki.archlinux.org/index.php/ALSA]("http://wiki.archlinux.org/index.php/ALSA")

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> Yep, that did it.  Thanks!

Here's the new problem...


I take it I need to add the glx module to /etc/X11/XF86Free...but the audio...

The glx driver error has to do with video drivers - you should restart X after installing nvidia driver, or, in fact, log out of X, reinstall them again, and then log back in.  

As for the sound -- no idea, check out the wiki entry for alsa and see if you'll find anything useful there.

---

### Post by ~LoKe on 2008-01-20
I give up.  Back to Ubuntu until I become a little more experienced...or patient.

However, Arch isn't ready to let me give up.

> growisofs -dvd-compat -Z /dev/scd0=/home/loke/hardy-desktop-i386.iso -speed=16
:-( unable to open64("/dev/scd0",O_RDONLY): Permission denied

> sudo mount /dev/scd0
sudo mount /dev/scd0
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**cat /etc/fstab**
> # 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


/dev/cdrom /mnt/cdrom   iso9660   user,noauto   0      0
**/dev/scd0 /mnt/dvd   udf,iso9660   user,noauto   0      0**
#/dev/fd0 /mnt/fd0   vfat   user,noauto   0      0
/dev/sda2 / ext3 defaults 0 1
/dev/sda3 swap swap defaults 0 0
/dev/sda1 /home/ ext3 defaults 0 0

---

### Post by Peyton on 2008-01-20
Have you tried the Arch forums?

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> I give up.  Back to Ubuntu until I become a little more experienced...or patient.

However, Arch isn't ready to let me give up.





**cat /etc/fstab**

just comment out the dvd and the cdrom lines

---

### Post by ~LoKe on 2008-01-20
> **Peyton said:**
> Have you tried the Arch forums?

Can't log into the Arch forums.  Yet another problem. ;)

---

### Post by fwojciec on 2008-01-20
> **~LoKe said:**
> I give up.  Back to Ubuntu until I become a little more experienced...or patient.

However, Arch isn't ready to let me give up.





**cat /etc/fstab**

from what I know growisofs is used for burning dvd not cd images...  have a look here and see if anything helps [http://wiki.archlinux.org/index.php/CD_Burning_Tips#Commandline_CD-burning]("http://wiki.archlinux.org/index.php/CD_Burning_Tips#Commandline_CD-burning")

Sorry, I've no real experience with command line burning tools.

---

### Post by yabbadabbadont on 2008-01-20
Edit: previous poster's answer is more likely correct.

---

### Post by fedex1993 on 2008-01-20
yeah i am finally installing arch. I tried it out ina  virtual machine and i loved. Now my only question how do i install awesome and get it configured correctly. My only question is with startx and what sessions manager should i use gdm kdm xdm excetra.

---

### Post by ~LoKe on 2008-01-20
> **raul_ said:**
> just comment out the dvd and the cdrom lines

> sudo mount /dev/scd0
mount: can't find /dev/scd0 in /etc/fstab or /etc/mtab

Heh.

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> Heh.

I had that issue, and commenting out those lines worked, as HAL just handled it fine. 

Why don't you reboot with the Ubuntu cd?

---

### Post by ~LoKe on 2008-01-20
> **raul_ said:**
> Why don't you reboot with the Ubuntu cd?

Trying to **burn** the Ubuntu CD. :lolflag:

---

### Post by Peyton on 2008-01-20
> **fedex1993 said:**
> yeah i am finally installing arch. I tried it out ina  virtual machine and i loved. Now my only question how do i install awesome and get it configured correctly. My only question is with startx and what sessions manager should i use gdm kdm xdm excetra.

Just install it through pacman and then put "exec awesome" in .xinitrc.

Loke, maybe you would have been better off trying Arch out in a virtual machine. :-P

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> Trying to **burn** the Ubuntu CD. :lolflag:

oh! sorry about that then :)

Does any gui work?

Just to be sure, what didn't work out for you, besides the sound?

---

### Post by ~LoKe on 2008-01-20
> **raul_ said:**
> Just to be sure, what didn't work out for you, besides the sound?

A lot of small things that just add up.

Installed a few KDE apps (k3b, k9copy, etc) and they didn't end up in /usr/bin, but rather /opt/kde/bin.  A few font problems, not entirely pleased with pacman (though it's my fault, not something I'm ready to get used to), etc.

Not a big deal, just not in my interest at this time.

---

### Post by raul_ on 2008-01-20
> **~LoKe said:**
> A lot of small things that just add up.

Installed a few KDE apps (k3b, k9copy, etc) and they didn't end up in /usr/bin, but rather /opt/kde/bin.  A few font problems, not entirely pleased with pacman (though it's my fault, not something I'm ready to get used to), etc.

Not a big deal, just not in my interest at this time.

yeah kde ends up in /opt...there's a discussion going on about it i think.

about the fonts..err...did you install them?

Anyway, i'm disappointed it didn't work out for you. You would've been a good addition to the community  (i love your screenies, and good screenshots are always good additions :D )

I hope you try again though :D

---

### Post by mips on 2008-01-21
> **Ub1476 said:**
> Hi, I decided to try Arch after reading only positive feedback about it, but can I run it?

I have a Intel Centrino Duo, which I'm quite sure is i386. From Archs wiki it says:

Am I out of luck, or will it run "slow"?

Centrino Duo is the branding Intel uses for their laptop processors. You actually have a Dual Core 64bit cpu from what I have read up. So you can install either the i686 or x86_64 versions. I would go full 64bit but keep in mind there is no flash for 64bit but you can run gnash which supports flash7 + some later stuff.

It will run like greased lightning on your pc. If you like kde (or even if you don't) then have a look at KDEmod.

---

### Post by mips on 2008-01-21
> **~LoKe said:**
> I used to install the nVidia drivers using the installer from the nvidia website, that should work just the same, right?

pacman -S nvidia

Which will install 100.14.19, well thats what I have on my pc anyway.

---

### Post by ST.x on 2008-01-21
anyone tried lArch? - [http://larch.berlios.de/doc/larch_docindex.html](http://larch.berlios.de/doc/larch_docindex.html)

---

### Post by mips on 2008-01-21
> **fedex1993 said:**
> My only question is with startx and what sessions manager should i use gdm kdm xdm excetra.


Well the session manager basically depends on what DM you are going to use.

X - xdm
KDE - kdm
Gnome - gdm

---

### Post by mips on 2008-01-21
For those complaining about fonts, if you have a LCD/Laptop then see:
[http://wiki.archlinux.org/index.php/Fonts#Beautify_Fonts_for_LCD_in_X](http://wiki.archlinux.org/index.php/Fonts#Beautify_Fonts_for_LCD_in_X)

---

### Post by Ub1476 on 2008-01-21
Thanks for the help everyone. I got it up and running with Gnome and the the ATI 7.12 drivers. I were amazed that direct rendering worked and X didn't crash. Anyway, I have a few issues, and I guess it's due to some missing packages. 

First of, the "notification" area won't show anything. It shows no errors when I add it to the panel. 

II installed Compiz-Fusion through the comunity repos (I think), and it installs fine, but when running it I get this:

```
compiz --replace
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering

```

No window borders, windows list on panel doesn't work etc..
I recall that when I installed catalyst, it said that libGL had to be removed due to some issues. 

Thirdly the fonts.. I followd the link provided above and the first issue was the PKGBUILD. I read a little about it on the Wiki, grapped the file on [AUR]("http://aur.archlinux.org/packages.php?do_Details=1&ID=12283&O=0&L=0&C=0&K=freetype2-lcd&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd")
, and put it in my home directory, but when running the makekg command I get this error:

```
[kasper@myhost ~]$ makepkg -ci /full/path/freetype2-lcd_ 2.3.5-1.tar.gz
==> Making package: freetype2-lcd_ 2.3.5-1  (Mon Jan 21 13:30:11 PST 2008)
==> Checking Runtime Dependencies...
==> Checking Buildtime Dependencies...
==> Retrieving Sources...
  -> Found freetype-2.3.5.tar.bz2 in build dir
==> ERROR: There is no agent set up to handle freetype-2-quantization_fix.patch URLs. Check /etc/makepkg.conf.
    Aborting...
  -> Downloading freetype-2-quantization_fix.patch...
/usr/bin/makepkg: line 472: freetype-2-quantization_fix.patch: command not found
==> ERROR: Failure while downloading freetype-2-quantization_fix.patch
    Aborting...

```

The last thing is about sudo/su priviligies. When I type sudo with the wheel user I created, it asks for the password, and when I write it and press enter it does nothing. I wrote the root password as well, but the it says it's incorrect. Currently, I have to write "su", then "exit" again, when I have to use root priviligies..

---

### Post by Rumor on 2008-01-21
> **Ub1476 said:**
> 
The last thing is about sudo/su priviligies. When I type sudo with the wheel user I created, it asks for the password, and when I write it and press enter it does nothing. I wrote the root password as well, but the it says it's incorrect. Currently, I have to write "su", then "exit" again, when I have to use root priviligies..

Glad you got Arch up and running. That first install can be pretty daunting.

Regarding sudo, read the wiki entry for sudo. It wil tell you what to install and how to edit your /etc/sudoers file.

[http://wiki.archlinux.org/index.php/Sudo](http://wiki.archlinux.org/index.php/Sudo)

---

### Post by Ub1476 on 2008-01-21
> **Rumor said:**
> Glad you got Arch up and running. That first install can be pretty daunting.

Regarding sudo, read the wiki entry for sudo. It wil tell you what to install and how to edit your /etc/sudoers file.

[http://wiki.archlinux.org/index.php/Sudo](http://wiki.archlinux.org/index.php/Sudo)

It says I can only use the terminal, no gedit. How would I save the file in terminal?

---

### Post by ST.x on 2008-01-21
> **Ub1476 said:**
> It says I can only use the terminal, no gedit. How would I save the file in terminal?
using vi

---

### Post by ~LoKe on 2008-01-21
> **ST.x said:**
> using vi

Nano is easier.

---

### Post by Rumor on 2008-01-21
> **Ub1476 said:**
> It says I can only use the terminal, no gedit. How would I save the file in terminal?

Navigate using the arrow keys to the line to be edited.
Type i to enter insert mode and make your edit.
Press esc to exit insert mode.
Type ZZ to save your file and exit the session.

> **~LoKe said:**
> Nano is easier.

Yes, but the file is not editable even in a root session of nano or gedit. You have to use visudo for this one file.

---

### Post by ~LoKe on 2008-01-21
> **Rumor said:**
> Yes, but the file is not editable even in a root session of nano or gedit. You have to use visudo for this one file.

Woops, didn't notice that he was trying to edit the sudoers file.

```
visudo
```
and escape :wq to exit.

---

### Post by yabbadabbadont on 2008-01-21
I think that if you export EDITOR=nano visudo will use nano instead of vi.

---

### Post by raul_ on 2008-01-21
Well, my desktop just went completely berserk (I just have to learn not to play so much with config files and such..)and I removed Arch. I'm actually installing Linux Mint, 'cause I don't have the time to configure Arch :( I just want a working "media center". 

I'll keep Arch on my laptop though, where I spend most of my time. It's my distro of choice. Plus, I was just curious about Mint (it has a nice interface, what can I say?)

---

### Post by kazuya on 2008-01-22
doing the same. Arch linux runs awesome and looks great on my laptop. For my desktop, it puts most other distros to shame performance-wise, but I am itching to get Linux mint back on the desktop. It simply looks better for my desktop.

---

### Post by Ub1476 on 2008-01-22
Thank again everyone. Now Alch isn't just running, but working:D

I still get this Compiz error though. I copied my xorg.conf file from Ubuntu over to Alch, which should work, yet I still get this:

```
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
```

I came over [this]("http://bbs.archlinux.org/viewtopic.php?id=42283") thread, and it appears there is a problem with the driver not supporting Archs xorg? Is it possible to downgrade (without issues) or will Catalyst 8.01 fix this. How long time does it usually take before it reach the Arch repos? Any other fix?

The AUR is awesome though, and yaourt, I don't have words:KS

---

### Post by raul_ on 2008-01-22
> **kazuya said:**
> doing the same. Arch linux runs awesome and looks great on my laptop. For my desktop, it puts most other distros to shame performance-wise, but I am itching to get Linux mint back on the desktop. It simply looks better for my desktop.

Actually I had Mint installed for like 20 minutes before i thought "ah screw it, I'm gonna lose a night to set up Arch again"

So I stayed up late, and now Arch is running again. I don't even need a wiki anymore :)

Mint is a good distro though. I liked the feeling of "just working",

---

### Post by Sunflower1970 on 2008-01-22
> **Rumor said:**
> Glad you got Arch up and running. That first install can be pretty daunting.

Yes it is! I decided to try out some different distros over the weekend. Arch being one of them. Don't think I'm quite ready yet for this. I could get the system installed (yay!), but since the computer has a wireless connection I had trouble installing the madwifi driver to get it to connect so I could continue on. At one point I thought I had it... but then something screwed up...I  gave up for the time being

I'm really curious about this one, but I need time away from it for a bit before I tackle it again. :)

---

### Post by Drakx on 2008-01-22
heh, my arch laptop just went tits up on me :S too much configuring i guess so as a quick and nasty way to get the laptop up and running i put vista x64 on and omg shoot me please the damn thing takes 2gb ram for idle and wont show that my laptop has 4gb ram it tells me its 3.062gb ram wtf is that about i ask you... oh well ill get arch installed again and go from there teach me not to play all the time :)

---

### Post by fackamato on 2008-01-22
Just curious, what files are you guys messing with to fsck up your systems? And always cp file file.back before you edit it, so it can easily be changed back to "working state". ;)

---

### Post by raul_ on 2008-01-23
> **fackamato said:**
> Just curious, what files are you guys messing with to fsck up your systems? And always cp file file.back before you edit it, so it can easily be changed back to "working state". ;)

Well, my arch installation was fine, the thing was that I couldn't install Gnome or XFCE on it(no panels, things crashing, etc, etc), but KDEmod was working fine. Since I'm sick of KDE, and couldn't upgrade to KDEmod4, I couldn't live with it anymore. 

Now I have a fully working Gnome installation. Even Compiz is snappier :)

---

### Post by Rumor on 2008-01-23
> **fackamato said:**
> Just curious, what files are you guys messing with to fsck up your systems? And always cp file file.back before you edit it, so it can easily be changed back to "working state". ;)

Arch is for tweakers, IMO. Tweakers are rarely satisfied with things, or are insatiably curious about how things work. They took clocks apart as young children. From there it progressed to toasters, vacuum cleaners, automobiles and most of the major appliances in their home (Yes, dear. I will put the washing machine back together).

The odds are that the more one tweaks something, the greater the chance that doing so will break it.

And besides, fixing it is fun!

---

### Post by fackamato on 2008-01-23
> **Rumor said:**
> Arch is for tweakers, IMO. Tweakers are rarely satisfied with things, or are insatiably curious about how things work. They took clocks apart as young children. From there it progressed to toasters, vacuum cleaners, automobiles and most of the major appliances in their home (Yes, dear. I will put the washing machine back together).

The odds are that the more one tweaks something, the greater the chance that doing so will break it.

And besides, fixing it is fun!


I know. I'm a tweaker. ;)

---

### Post by Drakx on 2008-01-23
> **Rumor said:**
> Arch is for tweakers, IMO. Tweakers are rarely satisfied with things, or are insatiably curious about how things work. They took clocks apart as young children. From there it progressed to toasters, vacuum cleaners, automobiles and most of the major appliances in their home (Yes, dear. I will put the washing machine back together).

The odds are that the more one tweaks something, the greater the chance that doing so will break it.

And besides, fixing it is fun!

Omg you more or less describe my childhood lmao.

---

### Post by K.Mandla on 2008-01-24
> **Rumor said:**
> Arch is for tweakers, IMO. Tweakers are rarely satisfied with things, or are insatiably curious about how things work. They took clocks apart as young children. From there it progressed to toasters, vacuum cleaners, automobiles and most of the major appliances in their home (Yes, dear. I will put the washing machine back together).

The odds are that the more one tweaks something, the greater the chance that doing so will break it.

And besides, fixing it is fun!
#-o I wish I had written that.

---

### Post by aeto on 2008-01-24
You are all WRONG.

[THIS](http://uncyclopedia.org/wiki/Archlinux) is the FINAL authority.

Arch is for overlords and friends of Thor. Only. No tweaker/lumberjack comes close. Maybe hunters are an exception, but that's because phrik feasts on them!

---

### Post by pelle.k on 2008-01-24
HAHA! :)
That was the best link i've seen in a long time. Check out the debian section. A little quote;
> Many popular applications from the twentieth century, which are no longer available via more mainstream channels, are preserved in Debian. For instance, as of 2007, the latest version of Debian (4.0, codenamed Retch) includes the following software titles, among others:

    * Netscape Navigator, version 3.2 Gold
    * Lotus 123, version 3.5
    * Pacman
    * Zork, version zero.
    * Pong
    * Hunt the Wumpus
    * Microsoft Bob Beta 4
    * Compuserve
    * Difference Engine Emulator
    * Microsoft Windows XP Professional Edition
    * Petris 

Debian stable does not include any version of the X Window System whatsoever, because all the versions which meet Debian Stable's guidelines violate a small, obscure portion of the Debian Free Software Guidelines. Likewise, support for high-speed networking isn't present in Debian stable yet for similar reasons. X Windows and high-speed networking can be found in Debian unstable, but Debian developers strongly recommend against using unstable - and instead recommend learning to like text-based computing and dial-up modems.

And of course, from the ubuntu section;
> Each time a new version of Ubuntu is released, Shuttleworth chooses a new and wacky release name. In the past these have included:

    * Lazy Lemming
    * Mouldy Mongoose
    * Paraplegic Pigeon
    * Pissing Panda
    * Retarded Rhino
    * Shitty Shark
    * Slutty Salamander
    * Suffering Suckatash!
    * Surly Snail
    * Wista Windows
    * Wobbly Whale
    * Zany Zebra
    ......
> Ubuntu is an ancient Swahili word (pronounced OOOBOOONTOOO, and in several dialects has many more o's) which may mean one or more of these:

    * White man come, give us computer. Not taste good.
    * I am because you are.
    * I know you are, but what am I?
    * Oh, the humanity!
    * Pictures of naked people are work-friendly.
    * Brown
    * I can't figure out Debian.
    * An ancient African drum-solo ritual performed by a gnome, dressed in brown.
    * Boom, tsk, boom, splash.
    * What You See Is What You Get From Debian 

As these lists suggest, there is no general agreement between scientists about the real meaning of the word.

Some suggest that the lack of any vowels different from "u" in the name could be further investigated. Others are still trying to install Ubuntu on their laptops and cannot be reached for an opinion. 

---

### Post by kellemes on 2008-01-24
Great link indeed.. :-)

GNOME's logo.. [http://uncyclopedia.org/wiki/Image:Footprint.png](http://uncyclopedia.org/wiki/Image:Footprint.png)

---

### Post by mips on 2008-01-24
Any OS could be for tweakers.

I'm running arch+kdemod on my desktop & laptop and have not really tweaked anything as my installs are the defaults. I'm happy, it's lite and it is fast, I don't see what else I have to tweak. I tweakeked more with (K)ubuntu to try and make it faster and leaner.

---

### Post by nat6138 on 2008-01-25
I tried putting Arch on my laptop, but I couldn't get internet to work at all, even trying the guides on their website. 

So I said screw it.

---

### Post by K.Mandla on 2008-01-26
What kind of network connection do you use? or is it not worth chasing?

---

### Post by raul_ on 2008-01-26
That's weird, cause Locke had the same problem. I wonder if these network problems are a serious issue?

---

### Post by Dark Star on 2008-01-26
I installed Arch Linux after I tried to install Grub I got an error that failed installing grub /dev/tty or something like that . That didn't bother me since I have Ubuntu installed and I can use its grub.. I added Arch Linux entry in Ubuntu grub but it didn't boot .. Here is my Arch Linux Entry .. I have installed it in /dev/sda7 


```
# (0) Arch Linux
title  Arch Linux
root   (hd0,6)
kernel /boot/vmlinuz26 root=/dev/sda7 ro
initrd /boot/kernel26.img
```

---

### Post by miggols99 on 2008-01-26
> **Dark Star said:**
> I installed Arch Linux after I tried to install Grub I got an error that failed installing grub /dev/tty or something like that . That didn't bother me since I have Ubuntu installed and I can use its grub.. I added Arch Linux entry in Ubuntu grub but it didn't boot .. Here is my Arch Linux Entry .. I have installed it in /dev/sda7 


```
# (0) Arch Linux
title  Arch Linux
root   (hd0,6)
kernel /boot/vmlinuz26 root=/dev/sda7 ro
initrd /boot/kernel26.img
```
My GRUB entry looks like this:

```
# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/sda1 ro resume=/dev/sda3
initrd /boot/kernel26.img

```
Try changing your root (hd0,6) to something else.

---

### Post by 5-HT on 2008-01-26
> **Dark Star said:**
> I added Arch Linux entry in Ubuntu grub but it didn't boot .. Here is my Arch Linux Entry .. I have installed it in /dev/sda7 

Any error messages?


> **Dark Star said:**
> I installed Arch Linux after I tried to install Grub I got an error that failed installing grub /dev/tty or something like that . That didn't bother me since I have Ubuntu installed and I can use its grub... 
One guess is that the failed install may have corrupted your MBR a bit (or were you trying to install GRUB in your Arch partition), though it looks like you can boot into Ubuntu without issue. 
I can't see anything wrong with the menu entry, what about reinstalling grub if you're not getting any specific error messages to go on?

---

### Post by Dark Star on 2008-01-27
> **miggols99 said:**
> My GRUB entry looks like this:

```
# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/sda1 ro resume=/dev/sda3
initrd /boot/kernel26.img

```
Try changing your root (hd0,6) to something else.

Thanks added that resume part it booted. . But it asked me login name and password while I hasn't set any password .. Does the Core ver. doen't have desktop /? No Desktop Manager ? How to install it /:lolflag:

---

### Post by PurposeOfReason on 2008-01-27
It's impossible to have installed arch without a password. You should have a root account with a password set during the install.

---

### Post by fackamato on 2008-01-27
> **Dark Star said:**
> Thanks added that resume part it booted. . But it asked me login name and password while I hasn't set any password .. Does the Core ver. doen't have desktop /? No Desktop Manager ? How to install it /:lolflag:

Er. Sigh.. Archlinux users are required to actually use their brains. So, you will have to install the things you want, yourself. Easy. Read the wiki on [http://wiki.archlinux.org/](http://wiki.archlinux.org/) , you should have very few questions left after reading that.

---

### Post by Rumor on 2008-01-27
> **Dark Star said:**
> Thanks added that resume part it booted. . But it asked me login name and password while I hasn't set any password .. Does the Core ver. doen't have desktop /? No Desktop Manager ? How to install it /:lolflag:

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

During the install routine, you were given the option to configure your system. This is a rather critical step. There are options on that screen to set the root passwrd and choose your pacman mirror. You are given the option to edit your /etc/rc.conf file which is the heart of your Archlinux install.

If you did not set a root password, then login as root with no password and set one using the passwd command. From there follow the steps in the beginner's guide to finishing your install.

---

### Post by regomodo on 2008-01-27
i've decided to leave Archlinux. Actually i've not used for 2 weeks now. The pain in not being able to use the Arduino IDE is too much. I've spent way too much time trying to get such a simple thing to work that i have decided to give up.

I may go back again one day but i haven't felt the urge the last 2 weeks since i wiped my install with Debian. Oh well.

---

### Post by aeto on 2008-01-27
what urge are you referring to? if Debian was serving you fairly _OK_, why bother with another Linux? Furthermore, why even wipe it?

[Arduino in AUR](http://aur.archlinux.org/packages.php?do_Details=1&ID=8388&O=0&L=0&C=0&K=arduino&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd) - Outdated, but at least it's there. Or do you mean you have issues with it run-time?

Yes, if you aren't getting productivity more than work done after 2 weeks, you should go back to Debian or check out another distro where your purpose of using a computer can be salvaged.

---

### Post by PurposeOfReason on 2008-01-27
I'm asking this here because less Ubuntu users use urxvt. 

I know how to make it transparent with the alpha channel, but is there a way to make it more transparent? I'd like it to be slightly more so. My Xdefaults if it matters to you:

```

URxvt.termName: rxvt
URxvt.transparent: true
URxvt.inheritPixmap: False
URxvt.imLocale: pl_PL.UTF-8
URxvt.scrollBar: false
URxvt.saveLines: 500
URxvt.urlLauncher:      firefox
URxvt.cursorBlink: true
URxvt.geometry: 80x21
URxvt.fading: 25%
urxvt.font:             xft:Bitstream Vera Sans Mono:pixelsize=8
urxvt.boldFont:         xft:Bitstream Vera Sans Mono:bold:pixelsize=9
#URxvt*background:      #000000
urxvt.depth: 32
urxvt.background: rgba:0000/0000/0000/dddd
URxvt.foreground: #ffffff
URxvt.tintColor: #262626
URxvt.borderLess: true
URxvt.borderColor: #000000
URxvt.externalBorder: 1
!URxvt.internalBorder: 25

*foreground:     rgba:1000/1000/1000/dddd
*background:     rgb:10/10/10
!black
*color0:         rgb:20/20/20
*color8:         rgb:75/77/73
!red
*color1:         rgb:cc/00/00  
*color9:         rgb:ef/29/29
!green
*color2:         rgb:4e/9a/06
*color10:        rgb:8a/e2/34
!brown/yellow
*color3:         rgb:c4/a0/00
*color11:        rgb:fc/e9/4f
!blue
*color4:         rgb:34/65/a4
*color12:        rgb:72/9f/cf
!magenta
*color5:         rgb:75/50/7b
*color13:        rgb:ad/7f/a8
!cyan
*color6:         rgb:06/98/9a
*color14:        rgb:34/e2/e2
!white
*color7:         rgb:d3/d7/cf
*color15:        rgb:ee/ee/ec


```

---

### Post by Gigamo on 2008-01-27
While you ask that question, I'm stuck with this: I have tried using your exact Xdefaults, but I get no transparency at all (while you do in your screenshots with it). Is this because I don't run xcompmgr? The only way I can get transparency atm is with inheritPixmap.

---

### Post by PurposeOfReason on 2008-01-27
You need beryl, compiz, xcompmgr or something running.

Also (not related) I remember there was a howto for the ubunt wallpapaer (the default brown with curved lines), and I lost it. Does anyone have that as I'm going to do a wall based off of that.

Found it.
[http://gimp-tutorials.net/node/106](http://gimp-tutorials.net/node/106)

---

### Post by Ub1476 on 2008-01-27
Anyone around here who know how to downgrade xorg from 1.4 to 1.3? Catalyst won't work with 1.4 (god damn ATI).

---

### Post by PurposeOfReason on 2008-01-27
> **Ub1476 said:**
> Anyone around here who know how to downgrade xorg from 1.4 to 1.3? Catalyst won't work with 1.4 (god damn ATI).
I know how to hold a release but to roll back I'd check the pacman wiki. I'll check right now too.

Some walls I made.
[http://gnome-look.org/content/show.php?content=74346](http://gnome-look.org/content/show.php?content=74346)

---

### Post by yabbadabbadont on 2008-01-27
@PurposeOfReason: If you didn't find an answer to your transparency issue, it could be because you didn't have a "shading" entry in your .Xdefauls for Uxrvt.

Example: ```
URxvt*shading: 25
```

---

### Post by Dimitriid on 2008-01-28
Can the mods reconsider an Arch Linux sub forum? This thread has over 900 posts yet the entire BSD sub forum has 819 posts according to my calculation. 

Its clearly too hard to follow a single thread anymore.

---

### Post by PurposeOfReason on 2008-01-28
> **yabbadabbadont said:**
> @PurposeOfReason: If you didn't find an answer to your transparency issue, it could be because you didn't have a "shading" entry in your .Xdefauls for Uxrvt.

Example: ```
URxvt*shading: 25
```
Tried it with no difference.

---

### Post by regomodo on 2008-01-28
> **aeto said:**
> what urge are you referring to? if Debian was serving you fairly _OK_, why bother with another Linux? Furthermore, why even wipe it?

[Arduino in AUR](http://aur.archlinux.org/packages.php?do_Details=1&ID=8388&O=0&L=0&C=0&K=arduino&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd) - Outdated, but at least it's there. Or do you mean you have issues with it run-time?

Yes, if you aren't getting productivity more than work done after 2 weeks, you should go back to Debian or check out another distro where your purpose of using a computer can be salvaged.
That is very outdated and doesn't work. I helped with the archwiki on how to get the arduino's dependencies (which were also outdated in the aur) to install and get the IDE to start up without spitting errors everywhere.
The main issue was getting the IDE to see the correct port. Despite a "cat /devttyUSB0" worked (if the arduino was told to send data), the ide refused to see it even though the config files were set correctly. 
I spent way too much time just to get that far and it appeared only 2 other people actually use the arduino in Archlinux. Not worth my time at all.

---

### Post by K.Mandla on 2008-01-28
> **Dimitriid said:**
> Can the mods reconsider an Arch Linux sub forum? This thread has over 900 posts yet the entire BSD sub forum has 819 posts according to my calculation. 

Its clearly too hard to follow a single thread anymore.
I think at this point it would be best to start a thread requesting a new subforum in Forum Feedback and Help. Make sure you explain why it's necessary, and what benefits you see coming from it.

I'm sure if you present the idea politely and logically, with lots of reasons, the admins will do their best to satisfy the community's requests.

For my own part I'm going to stay on the sidelines for this one, because I'm biased on the issue (I use it pretty much all the time :roll: ).

---

### Post by nat6138 on 2008-01-28
> **K.Mandla said:**
> What kind of network connection do you use? or is it not worth chasing?

It's a wireless, but I also have wired, and neither worked at all. 

And everything was setup correctly.

---

### Post by fackamato on 2008-01-28
> **nat6138 said:**
> It's a wireless, but I also have wired, and neither worked at all. 

And everything was setup correctly.

If "Everything was setup correctly" and you didn't manage to get a working network, there was either a kernel bug, or some hardware error. Was the module for your network loaded? Did you see it in dmesg? Did you notice any errors in dmesg? Did you manage to get a working (pingable) network connection when set up manually with a static IP, with ifconfig? Did you set up rc.conf correctly in the network section, and then restarted /etc/rc.d/network ?

:lolflag:

---

### Post by Rumor on 2008-01-28
> **K.Mandla said:**
> I think at this point it would be best to start a thread requesting a new subforum in Forum Feedback and Help. Make sure you explain why it's necessary, and what benefits you see coming from it.

I'm sure if you present the idea politely and logically, with lots of reasons, the admins will do their best to satisfy the community's requests.

For my own part I'm going to stay on the sidelines for this one, because I'm biased on the issue (I use it pretty much all the time :roll: ).

I'll undertake this task. I can probably even manage polite :)

Ok, I've posted in the Forum Feedback and Help sub-forum . . . if this were an election, I'd tell you to go vote twice! :D

---

### Post by nat6138 on 2008-01-28
> **fackamato said:**
> If "Everything was setup correctly" and you didn't manage to get a working network, there was either a kernel bug, or some hardware error. Was the module for your network loaded? Did you see it in dmesg? Did you notice any errors in dmesg? Did you manage to get a working (pingable) network connection when set up manually with a static IP, with ifconfig? Did you set up rc.conf correctly in the network section, and then restarted /etc/rc.d/network ?

:lolflag:

Lets see, drivers were on there, ip's were all set up, according to what is I know, trying pinging, told me to screw off, and I said screw it.

Considering that when I log onto Ubuntu, everything is setup and working good.

So, I guess Arch just isn't my cup of tea.

---

### Post by fackamato on 2008-01-28
> **nat6138 said:**
> Lets see, drivers were on there, ip's were all set up, according to what is I know, trying pinging, told me to screw off, and I said screw it.

Considering that when I log onto Ubuntu, everything is setup and working good.

So, I guess Arch just isn't my cup of tea.

That is exactly my point. Arch is not your cup of tea. That is no reason to diss arch. Arch is not meant to set everything up for you, a lá Windows style. Ops, I mean ubuntu. ;)

---

### Post by nat6138 on 2008-01-28
> **fackamato said:**
> That is exactly my point. Arch is not your cup of tea. That is no reason to diss arch. Arch is not meant to set everything up for you, a lá Windows style. Ops, I mean ubuntu. ;)

Didn't diss Arch, said it didn't work with the internet, and I didn't like it. 

Who would?

---

### Post by PurposeOfReason on 2008-01-28
> **nat6138 said:**
> Didn't diss Arch, said it didn't work with the internet, and I didn't like it. 

Who would?
I do and right now (after an update) I can't unplug my laptop or it'll lock and have to restart. First it was saying my battery was stuck at 0%, now it says I have 2 batteries. It'll be fixed soon. I'm going to have to do a clean install before I go to the dorms and make sure I only use stable things and lock important packages.

---

### Post by Tenken on 2008-01-29
[QUOTE=nat6138]Didn't diss Arch, said it didn't work with the internet, and I didn't like it.

Who would?[/QUOTE]

Lots of people do, and  saying that it's hard to believe that anyone would like it sounds like a diss to me.

Also, +1 for the Arch Sub Forum, there are lots of questions/problems posted in this thread that get kind of lost in a jumble going from Urxvt settings to install troubles to battery issues.

---

### Post by p_quarles on 2008-01-29
> **nat6138 said:**
> Didn't diss Arch, said it didn't work with the internet, and I didn't like it. 

Who would?
Yeah, that sounds like a diss to me. You've made your opinion on Arch clear, and I don't see any reason for you to post further in this thread.

---

### Post by mips on 2008-01-29
> **Rumor said:**
> I'll undertake this task. I can probably even manage polite :)

Ok, I've posted in the Forum Feedback and Help sub-forum . . . if this were an election, I'd tell you to go vote twice! :D

I gave you some backup ;)

---

### Post by Drakx on 2008-01-29
Looks like we got a sub forums for arch now :P good work guys

---

### Post by mips on 2008-01-29
> **Drakx said:**
> Looks like we got a sub forums for arch now :P good work guys

I think a 'thank you' would be in order here [http://ubuntuforums.org/showthread.php?t=681565](http://ubuntuforums.org/showthread.php?t=681565)

---

### Post by pelle.k on 2008-01-29
Well deserved IMO. Thankyou moderators/forum staff. :)
Can i suggest someone puts a sticky thread with links to the beginners guide, and the official install guide since these two are the most common advice arch nubies get...?
The FAQ might also be of interest, especially item no. 1
> Q) I am a complete Linux beginner. Should I use Arch?

A) This question has had much debate. Arch is targeted at more-advanced Linux users, but some people feel "Arch is a good place to start". If you are a beginner and want to use Arch, just be warned that you MUST be willing to learn. Before asking any question, do your own independent research by googling, searching the Wiki, and searching the forum (and reading past FAQs). If you do that, you should be fine. **Also know that many people do not want to answer the same basic questions over and over, so you are exposing yourself to that environment. There is a reason these resources were created/made available to you**. You could reference the ArchLinux Newbie Guide. 

[http://wiki.archlinux.org/index.php/FAQ](http://wiki.archlinux.org/index.php/FAQ)
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

---

### Post by aeto on 2008-01-29
This must also be highlighted: > Unlike other distros, Arch is not primarily concerned about the user. The user is important, sure, but most important are simplicity and elegance. The user is important as long as it does not interfere with these doctrines.

---

### Post by floke on 2008-01-29
> **Ub1476 said:**
> Anyone around here who know how to downgrade xorg from 1.4 to 1.3? Catalyst won't work with 1.4 (god damn ATI).

This question got lost so I will try to answer.
If you haven't cleared your cache with pacman -Scc then you need to use pacman -A /var/cache/pacman/[name-of-package]

You might have to remove first - and you can then pin it in your pacman.conf so that it doesn't get upgraded back again

hope this helps

(am currently in debian so can't check the exact filepath - but i think that's right!)

---

### Post by aeto on 2008-01-29
Right, /var/cache/pacman/pkg/$package

-A is deprecated. -U should be used.

One can grab a package from anywhere on the web. Pacman takes URIs. So look out for laggy mirrors, they can help you in this case.

The option in pacman.conf is IgnorePkg. Add it, it's not there by default. Syntax is same as the rest, like HoldPkg.

---

### Post by Rumor on 2008-01-29
> **pelle.k said:**
> Well deserved IMO. Thankyou moderators/forum staff. :)
Can i suggest someone puts a sticky thread with links to the beginners guide, and the official install guide since these two are the most common advice arch nubies get...?
The FAQ might also be of interest, especially item no. 1


[http://wiki.archlinux.org/index.php/FAQ](http://wiki.archlinux.org/index.php/FAQ)
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

I don't mind undertaking something like this. A sort of "Welcome to the Arch sub-forum" introduction with sections for introducing Arch, useful links etc. I can post it to the forum here for suggestions and once we're happy with it, K.Mandla or someone with admin abilities can sticky it for us.

Unless someone else wants to undertake this?

---

### Post by K.Mandla on 2008-01-29
Is this sufficiently KISS?

[http://ubuntuforums.org/showthread.php?t=682160](http://ubuntuforums.org/showthread.php?t=682160)

We can start another one if there are additional resources that are worth mentioning.

---

### Post by Rumor on 2008-01-29
> **K.Mandla said:**
> Is this sufficiently KISS?

[http://ubuntuforums.org/showthread.php?t=682160](http://ubuntuforums.org/showthread.php?t=682160)

We can start another one if there are additional resources that are worth mentioning.

Whoops . . . you and I must have posted moments apart :-)

---

### Post by K.Mandla on 2008-01-29
I saw that. I copy and pasted your version in, since it was better and more complete. :) Cheers!

---

### Post by raul_ on 2008-01-30
Last time I tried downgrading Xorg, it went bad, very bad...

well, not so bad actually, because I just installed the new version again =P I just removed catalyst and went back to the Open Source radeon drivers, that were working fine (and still are)

---

### Post by PurposeOfReason on 2008-01-31
> **PurposeOfReason said:**
> Tried it with no difference.

Future reference to all who want a more transparent urxvt, change the alpha channel from dddd to aaaa.

---

### Post by raul_ on 2008-02-09
Is the site down? I can't open any arch's sites. It's weird because I can ping them...

---

### Post by yabbadabbadont on 2008-02-09
Yep, it's been down for a couple of hours at least.

---

### Post by ST.x on 2008-02-09
hmm i just found out that creative x-fi cards arent really supported in linux, i know about the first beta driver for x64 but it doesnt sound promising. Any arch users have this card working? i have an xtremeMusic.

---

### Post by rocknrolf77 on 2008-02-12
Then you are in luck. Creative has finally decided to release spesifications :)

[http://www.theinquirer.net/gb/inquirer/news/2008/02/11/creative-labs-releases-specs](http://www.theinquirer.net/gb/inquirer/news/2008/02/11/creative-labs-releases-specs)

---

### Post by ST.x on 2008-02-12
> **rocknrolf77 said:**
> Then you are in luck. Creative has finally decided to release spesifications :)

[http://www.theinquirer.net/gb/inquirer/news/2008/02/11/creative-labs-releases-specs](http://www.theinquirer.net/gb/inquirer/news/2008/02/11/creative-labs-releases-specs)

sweet, mm ill just my onboard sound until this comes out then. After all I cant let something stop me from going to arch : )

---

### Post by handy on 2008-03-31
I've just successfully installed Arch.  This was my 2nd attempt, the first failed attempt was directly after my first 3 days of trying to get Gentoo to install, both of these were about 8 months ago.

X in Gentoo just would not under any circumstances do what it was supposed to.  Someone said it was a problem in the BIOS of my motherboard?  I don't know.

The first install of Arch was so much easier than Gentoo, but collapsed in a heap during the install the first time, & I was about out of perseverance at the time. 

Anyway 2nd time with Arch went really well except for getting the nVidia proprietary drivers to work for my AGP XFX nVidia 7950GT card.  I spent over 12 hours on that problem (split over 2 days with a few days off in between :-) )  any way cracked that today which made me so happy, because I really like Arch but would not have been able to stay with it without the card working properly. 

[***_Here is a link to the simple solution (as usual) for anyone that is interested._***]("http://ubuntuforums.org/showpost.php?p=4621147&postcount=42")

I think I might try & install Arch on my Alu' 24" iMac.  Has anyone here had succes on that hardware?

---

### Post by 4KvRMU7Nnv on 2008-03-31
I have found arch to be easier to use than ubuntu becuase I don't find myself needing to reinstall the OS every 6 months....With a rolling release system it is constantly up to date, and I don't find myself wistfully looking for the latest version of software that I have becuase it will be in the repo's of arch within days.  Also, pacman is ridiculously fast.

---

### Post by handy on 2008-03-31
> **d3br074 said:**
> I have found arch to be easier to use than ubuntu becuase I don't find myself needing to reinstall the OS every 6 months....With a rolling release system it is constantly up to date, and I don't find myself wistfully looking for the latest version of software that I have becuase it will be in the repo's of arch within days.  Also, pacman is ridiculously fast.

I need to use NeroLinux, as it is the most reliable on my hardware, so I looked for it via pacman, it was not available so then I tried yaourt & the latest 3.5.0.1 version which was like less than 2 days old was there! :-D

With pacman & yaourt supplying binaries, they are so much simpler & quicker to use than the Gentoo system that I have been using on Sabayon.  Everything under portage took me 20 minutes or more to download, compile & install.

Having just installed Arch, I'm still setting up & learning about it, so I'm yet to truly appreciate the rolling release process from experience, but I like what I have read.  

Also, there are no more trashed X's from kernel & graphic card driver updates!

Speedy Arch seems to be a time saver on multiple fronts!

---

### Post by rocknrolf77 on 2008-04-14
Pacman and yaourt is one of the main reasons arch is my main distro. It's the fastest package manager out there. And with AUR you have a lot of updated packages all the time.

But for my laptop I use ubuntu, because everything just works. Things like suspend is working from a fresh install.

---

### Post by raul_ on 2008-04-14
For me rolling release + pacman + AUR = life saver

---

### Post by Frak on 2008-04-14
> **raul_ said:**
> For me rolling release + pacman + AUR = life saver
Agreed

I also add ABS to the mix.

---

### Post by will1911a1 on 2008-04-18
Threw Arch on a second drive a few days ago and I'm loving it.  Took a while to get some things configured the way I wanted them, but in the end I'm left with a sleek installation that run only the stuff I want.

It's a great distro. :D

---

### Post by mips on 2008-04-18
> **will1911a1 said:**
> Took a while to get some things configured the way I wanted them, but in the end I'm left with a sleek installation that run only the stuff I want.


Takes a while to get it going, especially the first time but it ends up like a well cut suite from a tailor, you have to love it.

---

### Post by will1911a1 on 2008-04-18
> **mips said:**
> Takes a while to get it going, especially the first time but it ends up like a well cut suite from a tailor, you have to love it.

That's the truth!  It being my first installation, I think I was at it for about an hour (reading the beginner's guide VERY carefully), but it was well worth it.

Took some work to get the clock right (needed to install openntpd and make sure the network daemon was NOT running in the background) and to get fluxbox to run in 1280x1024 everytime (had to edit the fluxbox startup to auto run xarandr -s).

I'm still tinkering with it, but just for fun. :)

---

### Post by mips on 2008-04-18
> **will1911a1 said:**
> 
I'm still tinkering with it, but just for fun. :)

The weird thing is once I got everything running the way I wanted it I never tinkered or tweaked it again.

---

### Post by will1911a1 on 2008-04-18
> **mips said:**
> The weird thing is once I got everything running the way I wanted it I never tinkered or tweaked it again.

Once my curiosity is satisfied I'll most likely never touch it again, but for now I'm having a lot of fun playing with it.  It's already to the point where I could use it as an everyday computer but there's something about playing with it's guts that puts a smile on my face.

Makes my wife think I'm crazy too. ;)

---

### Post by derekr44 on 2008-04-18
> **mips said:**
> The weird thing is once I got everything running the way I wanted it I never tinkered or tweaked it again.

+1 That's why I like Arch so much.  Make it the way you want it and there is a heck of a lot less hassle later on.

---

### Post by Gigamo on 2008-04-19
> **mips said:**
> The weird thing is once I got everything running the way I wanted it I never tinkered or tweaked it again.

+2

---

### Post by Frak on 2008-04-19
> **mips said:**
> The weird thing is once I got everything running the way I wanted it I never tinkered or tweaked it again.
+3

---

### Post by finferflu on 2008-04-19
> **mips said:**
> The weird thing is once I got everything running the way I wanted it I never tinkered or tweaked it again.
-1

---

### Post by MisfitI38 on 2008-04-20
> **finferflu said:**
> -1

-2 ;)
Hehe. I can't stop customizing, building up, tearing down, rearranging and abusing Arch.,
I just can't seem to break it. :D

---

### Post by will1911a1 on 2008-04-20
> **MisfitI38 said:**
> -2 ;)
Hehe. I can't stop customizing, building up, tearing down, rearranging and abusing Arch.,
I just can't seem to break it. :D

That's what's so fun about it!

---

### Post by Barrucadu on 2008-04-20
What's the point of a computer if not for fun? :P

---

### Post by will1911a1 on 2008-04-20
> **Barrucadu said:**
> What's the point of a computer if not for fun? :P

Some people do this "work" thing on their computers.  I've never understood it. ;)

But seriously, most of the reason I own a computer at all is for fun.  I sometimes use it for information and only occasionally for work (that's what the computer at the office is for :P).

---

### Post by Barrucadu on 2008-04-20
"Work"? I do not understand this concept. Could someone explain it to me? :lol:

---

### Post by raul_ on 2008-04-20
> **Barrucadu said:**
> "Work"? I do not understand this concept. Could someone explain it to me? :lol:

It's a myth.

but yeah, while tinkering is fun, I think Arch steals less (none?) time because once you have your system running, you don't have to reinstall every six months, and go through the whole backup,download,install,install all my favorite apps/themes again. 

Once you go rolling release you don't go back

---

### Post by will1911a1 on 2008-04-20
> **Barrucadu said:**
> "Work"? I do not understand this concept. Could someone explain it to me? :lol:

It has something to do with "life" but I couldn't tell you more than that. :(

> Once you go rolling release you don't go back

Amen!

---

### Post by shearn89 on 2008-04-30
hey, i didn't know this thread was here... *yay*

---

### Post by finferflu on 2008-04-30
In case you haven't noticed, we have a [whole subforum](http://ubuntuforums.org/forumdisplay.php?f=321) :D

---

### Post by shearn89 on 2008-04-30
W00t!!!

---

### Post by kaiju on 2008-06-24
> **finferflu said:**
> In case you haven't noticed, we have a [whole subforum](http://ubuntuforums.org/forumdisplay.php?f=321) :D

sweet. :)

---

