---
title: "Arch Linux -- My first week"
date: 2013-01-26
forum: Any Other OS
---

### Post by kevdog on 2013-01-26
So I finally did it -- my first Arch install.  No I didn't abandon Ubuntu -- far from it -- I just wanted to see how the other side lives in a "more advanced distro".  Here are my general impressions for any one else considering a similar experiment

Arch -- it can be complicated. I've used Ubuntu for a long time - 5 or more years and really like the command line.  Most terminal commands are not foreign to me, and if they are, I'm very comfortable with how to find help. My first impression is that you actually have to configure everything about Arch and your hardware manually (well almost everything). The Arch beginner guide wiki is very well written -- don't skip any steps, however its somewhat incomplete?? if you have problems with your hardware.  Getting the main system up and running particularly if you have an ethernet cable is actually pretty quick.  Your left with a tty terminal for a log in.  But that is where basically the guide ends and a little bit of the work (and frustration starts).  Getting the wireless adapter up and running is always a pain, but doable, but the commands for configuring the adapter are just slightly different than in ubuntu -- a process whereby I know what I want to do, but I've got to look up the exact syntax for the commands.

Configuring the video adapter -- yet another 4-5 hour experiment.  I have a radeon 3650 "legacy" graphics card.  I took me a while -- meaning a few hours -- to actually discover that the catalyst legacy drivers don't actually with the most recent versions of the linux kernel.  This information isn't really specified in black and white anywhere.  I ended up defaulting back to the open source drivers.  A process that was easy, but I ended up wasting a lot of time

Desktop and window manager --  I currently still run the 11.10 Ubuntu version.  On this system I run gnome-fallback with compiz.  It took me awhile to get the system fine tuned to how I wanted it. When new versions of Ubuntu are released, I usually just install from scratch, however this means I'm just reinventing the wheel again when it comes to installing a different desktop than the now default Unity.  I've done this every release since Edgy Eft.  Frankly I've become crabby at doing the same thing over and over. When installing Arch (as with Ubuntu), you can choose whatever desktop you want (yes and window manager).  I can't say I've ever had to install these items from scratch before except for my brief dabble with E17.  It definitely takes a few hours to get things tweaked to how you want it - and I'm not sure I'll ever be done tweaking.  For those interested I'm currently running Cinnamon.  

Some of the fun and frustration at the same time is that I'm setting things up which I've actually taken for granted with the Ubuntu installation.   A lot of the information on the web in general is Ubuntu centered -- very Ubuntu centered and more applicable to the apt packaging system. Arch documentation is usually a lot more scant, and I can't say I've found their forums to be overly friendly.  Arch uses pacman which is a wonderful piece of package management software.  Yaourt is another tool to access the AUR -- yet another gem.  One of main problems however is setting systems to run at start.  Ubuntu uses Upstart -- a process I've become very comfortable with -- even writing upstart scripts which are very straightforward. Arch uses systemmd -- something I'm still struggling to get my head around.  Again the documentation is available, but its very technical and not for beginners.

I'll stop my blogging here.  Arch is definitely fun to see how another side lives, particularly a more advanced side and a distribution that adheres to a rolling release cycle which hopefully will keep me on the cutting edge but also not force me to keep upgrading every 6 months.  It's definitely however not for beginners.  Maybe I'll change my attitude with time -- as I do with most things in life as I become more comfortable with the new change.

---

### Post by trent.josephsen on 2013-01-26
Hmm, seems you've had a lot more trouble than I have with hardware problems. Maybe I'm just more accustomed to the process.

See you on the other side. Hopefully you get your Citrix issues straightened out ;)

---

### Post by SparkyPrawn on 2013-01-26
I always had problems with wireless drivers, and I have never been bothered to get it to work if Ubuntu has no problems for me on that side :D, especially since Arch seems to have less of a community than Ubuntu (their forums, as you mentioned).

I hope to eventually make enough time to test out Arch (again?) sometime soon, but as for now, I'm happy with Ubuntu.

---

### Post by malspa on 2013-01-26
Thanks for that post, kevdog -- enjoyed it quite a bit. I've never tried Arch and probably never will, but who knows?

---

### Post by kevinmchapman on 2013-01-27
Arch documentation is definitely "just the facts, ma'am". The Beginners Guide is just that, so any specific hardware issues will be covered in separate articles, rather than duplicated in the installation pages. For example, the Wireless page covers the firmware (where required), and any quirks, and you would be expected to locate and read that.

The forums are definitely lessy chatty than here, but typically of better technical content, as the users are, on average, somewhat more advanced :)

---

### Post by ACubed10 on 2013-01-27
I see a lot of people on here are also running Arch. Always been curious but never went ahead and tried it

---

### Post by kevdog on 2013-01-28
Update:

Speaking like a newbie using Arch, however its not all that different than Ubuntu.  Yes the setup is more work since you have to really know your system, however once things are setup, iptables, libreoffice, firefox, etc are the same no matter what linux distribution you are using. 

One big difference is package management -- pacman vs apt. I'll probably be able to comment more on this in detail the more I use pacman.  I really like the apt packaging system.  One thing that is really nice is the Arch AUR (Arch User Repository).  If you like to compile things on the bleeding edge such as firefox nightly or chrome nightly or other programs that just don't make it into the official repositories, the AUR is a very useful dumping ground for such things.  It really makes installing programs from git a piece of cake!!!  Very simple!!  I could see something like this being a very useful edition to apt.

---

### Post by hydn79 on 2013-01-28
For anyone who finds Arch too complicated to get started/installed, give [http://www.cinnarch.com/](http://www.cinnarch.com/) (CinnARCH) a try! All the benefits of Arch with easy full install that takes you right to Cinnamon DE.

Now I've only tested this distro for a few hours, I prefer still prefer Arch on my work laptop and Ubuntu on some of my servers and wife's laptop.

---

### Post by Rukiri on 2013-01-28
I like arch, keep it stupid simple but hate systemd I prefer openrc (easy to git clone in ubuntu and get it setup).  

Honestly I wouldn't call it a more advanced distro, sure it does require you to modify some config files however recently since systemd you simply don't have to everything should work out of the box.  Just install the proper drivers and your good to go.  Don't try Unity on arch... it's a mess, it is in a somewhat usable state on gentoo but if you like unity well stay with ubuntu.

You won't learn 'much' about linux from arch, you will learn 'somewhat more' on gentoo but if you really want to learn linux you may need a few weekends, a mr.coffee, about 6 cases of coke and mountain dew and probably call in sick to learn linux and install linux from scratch (it's honestly not that hard and I don't know why people find it hard, sure takes me a few hours because I'm installing linux manually but it's pretty simple)

I mean if you want a more arch approach for ubuntu you can install ubuntu from scratch, where you just select the apps you want on your system.   

Don't forget to compile your kernels, stay away from the aur(it's a nightmare, the pkgbuilds most of the time are poorly written)  stay within the official repos, I only use the aur for git packages.

In terms of package management, there's only 2 great package management systems for linux they're called apt-get and portage.  Packman is great, but remember arch started in 2002 and debian started way back in 1993(I think, or was it '94?)    

The new install is pretty straight forward it literally takes 5 minutes to install arch(not counting the download time for base and base-devel)  just keep in mind, arch isn't about a stable system actually it's probably the best distro for testing things out I personally would not use it on a desktop because of that (use slackware and pacman or apt-get)   

Like I said, if you want to learn linux you simply won't with arch or even gentoo for the most part, the only way is to completely install linux from the ground up.  I plan to when I have the time, my original experience with linux was installing it from scratch (stage 1)  but a lot has changed since 1998.

---

### Post by rushikesh988 on 2013-01-28
i was planning to install arch but after reading this I think I should stick with ubuntu only

---

### Post by kevdog on 2013-01-28
> **Rukiri said:**
> I like arch, keep it stupid simple but hate systemd I prefer openrc (easy to git clone in ubuntu and get it setup).  

Honestly I wouldn't call it a more advanced distro, sure it does require you to modify some config files however recently since systemd you simply don't have to everything should work out of the box.  Just install the proper drivers and your good to go.  Don't try Unity on arch... it's a mess, it is in a somewhat usable state on gentoo but if you like unity well stay with ubuntu.

You won't learn 'much' about linux from arch, you will learn 'somewhat more' on gentoo but if you really want to learn linux you may need a few weekends, a mr.coffee, about 6 cases of coke and mountain dew and probably call in sick to learn linux and install linux from scratch (it's honestly not that hard and I don't know why people find it hard, sure takes me a few hours because I'm installing linux manually but it's pretty simple)

I mean if you want a more arch approach for ubuntu you can install ubuntu from scratch, where you just select the apps you want on your system.   

Don't forget to compile your kernels, stay away from the aur(it's a nightmare, the pkgbuilds most of the time are poorly written)  stay within the official repos, I only use the aur for git packages.

In terms of package management, there's only 2 great package management systems for linux they're called apt-get and portage.  Packman is great, but remember arch started in 2002 and debian started way back in 1993(I think, or was it '94?)    

The new install is pretty straight forward it literally takes 5 minutes to install arch(not counting the download time for base and base-devel)  just keep in mind, arch isn't about a stable system actually it's probably the best distro for testing things out I personally would not use it on a desktop because of that (use slackware and pacman or apt-get)   

Like I said, if you want to learn linux you simply won't with arch or even gentoo for the most part, the only way is to completely install linux from the ground up.  I plan to when I have the time, my original experience with linux was installing it from scratch (stage 1)  but a lot has changed since 1998.

Any instructions on a page of how to do this?? I'd be game for this.

---

### Post by offgridguy on 2013-01-28
Arch looks out of my league, cinnarch looks intriguing though.

---

### Post by ACubed10 on 2013-01-28
> **rushikesh988 said:**
> i was planning to install arch but after reading this I think I should stick with ubuntu only
I agree with this.  I love linux, but I don't have a lot of time to try and learn another :lolflag:

---

### Post by Nr90 on 2013-01-28
> **kevdog said:**
> Any instructions on a page of how to do this?? I'd be game for this.

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)


I ran arch for a while. It was good fun, but switched to debian for stability.

---

### Post by oscarivera9 on 2013-01-28
> **hydn79 said:**
> For anyone who finds Arch too complicated to get started/installed, give [http://www.cinnarch.com/](http://www.cinnarch.com/) (CinnARCH) a try! All the benefits of Arch with easy full install that takes you right to Cinnamon DE.

Now I've only tested this distro for a few hours, I prefer still prefer Arch on my work laptop and Ubuntu on some of my servers and wife's laptop.

Hey,
thanks for the info.  I'm actually one of the people who's been trying Arch lately.  The Ubuntu community has been awesome in pointing me in the right direction as far as Arch is concerned.  I tried twice to install Arch in VirtualBox and it is definitely a project that needs a long time, especially when comparing it with installing Ubuntu which is a piece of cake.
I will check out CinnArch, thanks!

---

### Post by SparkyPrawn on 2013-01-28
> **Nr90 said:**
> [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)


I ran arch for a while. It was good fun, but switched to debian for stability.

LFS is good. I'm working my way through an install on a virtual machine when I have time, which seems to be rarer and rarer nowadays.

---

### Post by sammiev on 2013-01-28
I played with Arch for a few days and it seemed to setup well on my laptop. The only big issue I had was my wireless Internet. I likely would have tested it more but I needed my laptop for a trip and did not want to bring my USB HD on the road with me. I will try it again. :popcorn:

---

### Post by kevdog on 2013-01-29
Linux from Scratch -- Perusing the web site I could see it being very educational but possibly lacking on useability? I don't see a single thing mentioned about a package management utility.  Is this correct?

---

### Post by GrouchyGaijin on 2013-01-29
> **rushikesh988 said:**
> i was planning to install arch but after reading this I think I should stick with ubuntu only

This almost makes me think Jung and his collective unconscious theory might be more than nonsense. 
Last week I was toying with the idea of trying to set up Arch, then I found this thread.
Now I realize this is a project for vacation.

---

### Post by raphifix on 2013-01-29
> **sammiev said:**
> I played with Arch for a few days and it seemed to setup well on my laptop. The only big issue I had was my wireless Internet. I likely would have tested it more but I needed my laptop for a trip and did not want to bring my USB HD on the road with me. I will try it again. :popcorn:

I have installed Arch a couple of times since coming from Ubuntu, and I agree that setting up wifi can be tricky. What problem were you having exactly?

---

### Post by sffvba[e0rt on 2013-01-29
I installed Arch a few years ago, wasn't "easy" but with the wiki doable.  Tried it today, wow!  Why did they make it even more complicated (so I installed Xubuntu, took 15 minutes and everything works :p)


404

---

### Post by trent.josephsen on 2013-01-29
Yeah, it's a bit different without the old install script. Not really a big deal though. Installation is a one-time thing; the everyday stuff like package management (and vanilla XFCE) is the reason I use Arch.

---

### Post by Habitual on 2013-01-29
> **rushikesh988 said:**
> i was planning to install arch...

Well, I did install it in Vbox and it took a couple of tries to get xfce4, dhcpd and sshd working on reboot.

Installed slim for grins and giggles.

Reminds me of the bad ol' days when c-li was "king" and it took hours and hours of ./configure && make && sudo make install'ing everything you needed for a Generic Desktop.

I'll beat on it some more as time goes by...

It's all the same "under the hood" I always like to say (*except* for Package Management)

---

### Post by kevdog on 2013-01-30
I wrote my own pkgbuild to install some fonts downloaded from dafont. Took me about an hour since I had no idea what I was doing although I knew about the goal in general. Unfortunately with most things dealing with computers the devil is in the details.  

Worked real well.  I wish I could generate apt packages so easily.  It's nice that packages can be custom installed by feeding them directly through the pacman package manager

---

### Post by kevdog on 2013-01-31
New update

Installed all the android sdk and android platform tools and udev.  I've done this in Ubuntu and its taken me awhile.

In arch, I installed 3 packages from the AUR, and plugged in the phone to the USB port -- and boom!!!! connected via adb. Painless.  I'm just wondering why ubuntu couldn't create a ppa that would be so painless!!!!

---

### Post by cecilpierce on 2013-01-31
I have a few Arch Linux installs they all work fine except Cinnarch, its crashed after two installs, goes into a root terminal and when I try to use pacman it says command not found ???

Really a bummer...:mad:

---

### Post by ubume2 on 2013-01-31
Thanks for the blog kevdog.  I can relate to it.

I made a couple of attempts to install Arch on my hard drive, and failed.

Then I discovered Virtualbox.  With the beginners guide up on the browser in my host OS, and after 3 or 4 attempts to install Arch I succeeded in getting a working Arch XFCE.  

Having detailed notes I had taken during the install, I successfully installed Arch on the hard drive.  And I had a working XFCE (for the most part) on my hard drive.  

Arch has recently made it a little more difficult to install, and it seems that the new install is a little bit closer to installing from scratch.

I'm glad I tried Arch. I've learned a lot about linux.  I will keep on fiddling with it, but I appreciate Ubuntu, Xubuntu, and Kubuntu all the more!

---

### Post by fantab on 2013-01-31
> **kevdog said:**
> I wrote my own pkgbuild to install some fonts downloaded from dafont. Took me about an hour since I had no idea what I was doing although I knew about the goal in general. Unfortunately with most things dealing with computers the devil is in the details.  

Worked real well.  I wish I could generate apt packages so easily.  It's nice that packages can be custom installed by feeding them directly through the pacman package manager

I installed my favorite fonts directly from 'font viewer'... but they install in ~/.local/share/fonts and not in /usr/share/fonts, not an issue really as long as they available for use.

Every distro has its own idea of what a distro should be like... Arch has [The Arch Way]("https://wiki.archlinux.org/index.php/The_Arch_Way"). Ubuntu has its own and so does Debian or Fedora... Gentoo has its own 'way' of doing things... 

Of all the package managers I tried, I find **pacman** to be the best out there.  I dual boot Ubuntu and Arch ... looks like I have more or less settled with my distro hopping.  

I really appreciate the simplicity of Arch. What I dislike about arch  is the AUR... 

My two cents...

---

### Post by kevinmchapman on 2013-01-31
The new installation method is an interesting one. The old scripts were dropped simply for lack of a maintainer, not to put anyone off. Not even Arch is that harsh :)

I upgraded to an SSD on one laptop last week and so had to reinstall for the first time with the new method and was not looking forward to it. OK, I have used Arch for five years, but I found the new procedures surprisingly simple. As ever, the Wiki told me all I needed to know, and it did not seem to require more work or time than the old installer.

---

### Post by viperdvman on 2013-02-01
I decided to jump into the Arch realm of distros during my winter vacation. And no, I didn't mess with ArchBang!, Manjaro, Bridge Linux, KahelOS, or CinnArch first... I went with straight vanilla Arch Linux. Part of the fun *(and _pain_)* of using Arch is the installation process. All I would've had with the Arch-based distros was the rolling-release model, the **pacman** package manager, and the repos *(including the AUR)*. It might've been nice to try one of the derivatives first since they came pre-installed with a working DE, but I decided on the straight Arch install.

For me, I had the Beginner's Guide and Installation Guide through their wiki that I ran on my netbook while I was installing Arch on my desktop. I also had some extra help from one of my buddies on a Nintendo-theme IRC who's also an Arch user *(though his help wasn't quite step-by-step with the wikis)*. The only two hiccups I had were with my built-in ethernet adapter and getting GRUB installed correctly. Both were oversights on my part and quite easy to fix and get working.

But after a good process of going through the wikis and my friend's help, I got Arch *(at least in CLI mode)* working perfectly. I even got xorg, a DE, and even my NVidia drivers all working very well. And for my Arch install... I went with KDE.

-----

As far as running Arch goes, I've found it every bit as much of a blast to run as (K)Ubuntu. Once you learn pacman syntax, using [COLOR="Navy"]sudo pacman -S "package"[/COLOR] and [COLOR="Navy"]sudo pacman -Syu[/COLOR]becomes every bit as second-nature as using [COLOR="navy"]sudo apt-get install "package"[/COLOR] and [COLOR="navy"]sudo apt-get update && sudo apt-get upgrade[/COLOR].

I've come to like the AUR as well. It's certainly an excellent one-stop shop for all kinds of apps, games, packages, etc. that aren't in the repos... unlike having to set up tons of PPA's in Ubuntu. In fact, I'm starting to prefer the AUR instead over having to find PPA's for whatever app I'm wanting to install. And I can do it both manually *(download and compile)* and with **yaourt**. Yaourt is definitely an excellent tool to use when working with the AUR, as it works almost exactly like using pacman. I don't know what others' beef with the AUR is, but I've had no problems with installing packages from the AUR, but the only PITA I've had with installing packages from the AUR is when said packages have dependencies that must also be installed from the AUR. It's even more of a PITA when **those** dependencies require more dependencies from the AUR.

The other pain with Arch compared to Ubuntu: I'm running 64-bit Arch. Ubuntu has excellent multiarch support. If it doesn't have the 32-bit libraries that some apps you may run require, it installs them all automagically. This wasn't a problem for me in Arch since Arch has the multilib repository for that. However, stuff like Netflix, Second Life, and a few other apps that are obtained from the AUR required extra 32-bit libraries and even 32-bit NVidia libraries to get working right... most of them also from the AUR. And **THAT** was where I ran into the chain of dependencies that had to be installed from AUR. Good thing I was using yaourt for that and not the manual method, or that would really have been a PITA.

Other than that... I love running pacman, running Arch once everything's installed is a blast, and other than a couple of minor hiccups with installing stuff I've had absolutely no problems running Arch. It's been very stable for me, I've had no errors, no segfaults, nothing but smooth sailing. I'm definitely going to keep it on my desktop... at least as a toy to play around with.

---

### Post by mips on 2013-02-02
> **viperdvman said:**
> 
I've come to like the AUR as well. It's certainly an excellent one-stop shop for all kinds of apps, games, packages, etc. that aren't in the repos... unlike having to set up tons of PPA's in Ubuntu.

+1 AUR beats multiple PPAs for me. To use AUR you don't even have to do anything, just use yaourt or packer as you pacman.

---

### Post by kevdog on 2013-02-02
I've written know a couple of homebrewed PKGBUILDs.  I'm wanting to step up my game some.  If I'm writing a PKGBUILD that requires dependencies -- how would direct a user to install a dependency if it were another AUR package?  I'm sure this is possible, but its not really explained in the wiki.

---

### Post by Rukiri on 2013-02-02
Most packages in the AUR usually list the deps and reequire you to install them before going through installing the package from the aur.  It saves time, but honestly who goes to aur.archlinux.org to find this out?  Doubt most arch users use man pages(not sure but this isn't gentoo)

Really wish pacman had eselect news integrated, you know how useful that would be?  I know I'm a long time gentoo user but that would be awesome.

---

### Post by trent.josephsen on 2013-02-02
What percent of Arch users install AUR packages that depend on other AUR packages? I don't. I only have a handful of AUR packages to begin with.

Not sure what you mean about man pages, can't imagine who doesn't use man pages...

As for news, it's on [www.archlinux.org](www.archlinux.org) and you will be castigated on the forums for not keeping an eye on it. Although I forget frequently and it's never been a problem yet.

---

### Post by fantab on 2013-02-03
> **kevdog said:**
> I've written know a couple of homebrewed PKGBUILDs.  I'm wanting to step up my game some.  If I'm writing a PKGBUILD that requires dependencies -- how would direct a user to install a dependency if it were another AUR package?  I'm sure this is possible, but its not really explained in the wiki.

I hope you post this in Arch Forums- [AUR Issues, Discussion &PKGBUILD Requests]("https://bbs.archlinux.org/viewforum.php?id=38"). that is, if you haven't already.

---

### Post by mips on 2013-02-03
> **kevdog said:**
> I've written know a couple of homebrewed PKGBUILDs.  I'm wanting to step up my game some.  If I'm writing a PKGBUILD that requires dependencies -- how would direct a user to install a dependency if it were another AUR package?  I'm sure this is possible, but its not really explained in the wiki.

What happens if you use packer or yaourt to install your package and specify the dependencies from AUR in your pkgbuild? I think that might work.

---

### Post by kevdog on 2013-02-20
Well I haven't updated this thread in a while and I'm like maybe 3 weeks into the Arch setup??

I took a break from the PKGBLD process for a while.

Things have kind of settled in on the installation front.  Last few days have been spent setting up basic iptables, and port knocker utility (fwknop).  These configurations are standard for any linux box so nothing to arch specific.  sshfs is a beautiful thing!!

The one benefit I've seen from Arch and its rolling release model is the packages are always up to date.  I could see this as a double edge sword, however one thing I did find very useful was the ability to install gvfs-git from the AUR.  I know most people find the prospect of compiling programs terrifying, and even use of git packages, however the AUR is very simplistic and it really automates the entire process so its almost seemless (almost -- some stumbles on a few packages).

The latest gvfs release contains a built in mtp monitor which automounts my Android phone when connected to the USB.  The phone's sdcard is immediately accessible in nemo (thunar).  What a big time savings this is!!! Ubuntu has a ppa package for the 13.04 build that is capable of backporting this gvfs release.  I'd highly recommend it if you have an Android phone and want to use something else other than adb.

I've also discovered that utilizing Picassa 3.9 through wine is a no go.  The program installs fine, but it cant access the picassa online galleries.  This despite trying tricks trying to employ winetricks with ie6.  I'm really disappointed in Google for giving up on Picassa support for linux. It really should be better.

---

### Post by mips on 2013-02-20
> **kevdog said:**
> ... however one thing I did find very useful was the ability to install gvfs-git from the AUR.  I know most people find the prospect of compiling programs terrifying...

The process is basically the same as doing a pacman -S <package name>. The only thing different is you get prompted to edit the package build which you can ignore. It's nothing like Gentoo in my book.

---

### Post by offgridguy on 2013-02-20
> **hydn79 said:**
> For anyone who finds Arch too complicated to get started/installed, give [http://www.cinnarch.com/](http://www.cinnarch.com/) (CinnARCH) a try! All the benefits of Arch with easy full install that takes you right to Cinnamon 
I was real interested in cinnarch, joined the forum and posted a thread with a couple of
questions, had my thread removed, no explanation, kinda gives me the impression  'we
don't want you here'.

---

### Post by cecilpierce on 2013-02-20
I installed Cinnarch twice and both times it crashed after about a week ??? So I gave up...:(

Manjaro still working good...:D

ps I have cinnamon DE in one manjaro install but its slow to open the menu.

---

### Post by kevdog on 2013-02-20
Holy crap!!!

Compiling and installing ffmpeg using the AUR was simply a breeze!!!
Edit the config file -- add your codecs -- and boom! -- Done!!

I remember the time this actually took to do in Ubuntu using Andrew46's guide (very comprehensive).  Compiling in Arch however was so damn easy it almost felt like cheating!!!

I'm just curious why the apt-get system isn't setup for easy compilation?  Maybe I'm just not as experienced enough with other package managers, however using yaourt at least for this task was just plain simple!

---

### Post by FakeOutdoorsman on 2013-02-21
Welcome to Arch. I left Ubuntu for Arch in 2008 and never regretted it...especially now with semi-recent Ubuntu developments that I strongly disagree with.

> **kevdog said:**
> I'm just curious why the apt-get system isn't setup for easy compilation?

Ubuntu doesn't have a ports-like system. Arch has the advantage of already having a decent repo in addition to the AUR and ABS if you want something that is not in the repo or if you want to monkey around with something.

> **kevdog said:**
> ...using yaourt at least for this task was just plain simple!

I've never used yaourt. I just choose what I want from AUR, wget the tarball and extract, or make my own PKGBUILD (which is your next objective on this mission), review and possibly edit the PKGBUILD, and then run "makepkg -sif".

---

### Post by andrew.46 on 2013-02-21
> **kevdog said:**
> Compiling and installing ffmpeg using the AUR was simply a breeze!!!
Edit the config file -- add your codecs -- and boom! -- Done!!

I remember the time this actually took to do in Ubuntu using Andrew46's guide (very comprehensive).  Compiling in Arch however was so damn easy it almost felt like cheating!!

I would like to take credit for the FFmpeg guide but of course that was / is Fakeoutdoorsman's work :). You perhaps remember my MPlayer guide that is now unfortunately falling into disuse.

Like FakeOutdoorsman and yourself I no longer use Ubuntu exclusively, my home distro is Slackware -current and here too are found build scripts which make compiling and package management a breeze!

---

