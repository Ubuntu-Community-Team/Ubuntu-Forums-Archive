---
title: "First Impression of PCBSD from an OS Whore"
date: 2007-10-03
forum: BSD
---

### Post by Scheater5 on 2007-10-03
I previously wrote about my struggles with PCBSD 1.3 and ultimately installing and trying [DesktopBSD]("http://ubuntuforums.org/showthread.php?t=491664").  I never got the kinks worked out of that DesktopBSD install, and that partition went basically unused until I decided to give PCBSD 1.4 a go.
I've spoken pretty harshly against BSD as a desktop OS in the past.  I never really meant the idea of BSD as a desktop was unsound, just that everything I tried worked very poorly.  Well, PCBSD 1.4 is a vastly different story.  
The install went flawlessly, and in a very short amount of time (even compared to Ubuntu installs - both with the Desktop and the Alternate install) I had a fully functional KDE desktop awaiting me.  
I'm still not so sure BSD is as useful as a desktop OS for the typical user as linux.  I would love to have an updated Knetworkmanager, as the default network manager in PCBSD 1.4 is pretty clumsy to use.  Effective, but not efficient.  No Open Office by default also costs it points - but only in light of the fact that it is designed to be more oriented to the desktop user.  And I've had some trouble with Compiz-Fusion, and I'm not sure it was a very smart move to include that by default when BSD's idea seems to be to use only very stable software.  But I can't really blame BSD for my problems with experimental software, so I won't dock them for that.  
Other than that, it works great.  It is as responsive as Kubuntu.  The PBI system takes longer than, say Ubuntu's repos, that's only because the mirrors are relatively slow.  It's certainly faster than compiling everything from source, and well suited for the target audience.  
I haven't had a chance to test everything out just yet, but thus far I'm liking what I see.  I have a desktop that I use as a bittorrent box, and I will probably replace Kubuntu with PCBSD on it in the near future.  Kubuntu will probably stay on my laptop as my main OS, but I'm keeping my eye on PCBSD.  If nothing else, experimenting with it will keep me occupied until Gusty comes out.

---

### Post by the_darkside_986 on 2007-10-05
Cool. I've been wanting to try PC-BSD 1.4 very much now but I accidentally deleted all the partitions from my drive somehow... So I'll have to go home later and reinstall Ubuntu and then PC-BSD 1.4, but before that I must use gparted to properly make well-sized partitions since both PC-BSD and Ubuntu installers lack a decent partitioning tool. PC-BSD won't even look at free space and try to allocate it. It only wants to eat existing Windows NTFS partitions.

---

### Post by the_darkside_986 on 2007-10-05
I finally got the grub entry right and it works, but this release seems quite disappointing compared to 1.3. 

It has been a complete mess trying to get KDevelop to actually built a simple project. It claims that autoconf isn't there even though I am sure that I installed it. I installed KDevelop from CD2 during the installation so I was hoping that the necessary build tools and dependencies would have gotten installed.

Also, KPorts was difficult to install and doesn't seem to do anything useful. Where is the install button? I had to use portinstall and pkg_add at the command line before getting KPorts to update its information. This completely defeats its purpose. That is one PBI that needs some serious repackaging.

Also, PBI looks flashy and runs in a GUI but it is as useful as getting deb packages in Ubuntu and forcing them all to load without resolving dependencies. PBI is obviously inspired by Windows' system of installation, but that is even worse because Windows doesn't contain a decent packaging system that properly resolves dll issues like deb packages do.

I tried enabling Compiz after selecting a proprietary nvidia card driver (the 9.... one since the 100.* one failed to function), but Compiz runs horribly slow and is completely unusable so I had to disable it. glxgears is reporting a FPS of over 1100 FPS so I do not know what the issue is.

So I am asking, since I downloaded the CD's via bittorrent protocol, did I accidentally pick up the development version instead of release? Should I try to download it via ftp and reburn the disks? The md5 sums match what is on the page, though.

FreeBSD is obviously the technically superior system but the PCBSD must work harder to make it as usable as Ubuntu.  I am looking forward to the coming Ubuntu release. Maybe it will not be such a mess or I will actually get the right release version when I download it via torrent. This is still better than opensolaris since it actually boots. I was thinking about updating the install on my g/f's PC from 1.3 to 1.4 but now I think I should wait a few more PCBSD releases.

---

### Post by Scheater5 on 2007-10-06
Well, when you say FreeBSD is the "technically superior" release, keep in mind that PC-BSD *is* FreeBSD with a GUI installer and a binary package manager.  While the relationship is not exactly the same, it is not far off to compare FreeBSD to Gentoo and PCBSD to Sabayon.  When all is said and done, you're left with a highly configured, end-user-friendly FreeBSD.  
  And it's difficult to blame PCBSD for the problems with Compiz Fusion.  No one ever claimed it was bug free, and few will claim it's ready for the end user.  BSD has a different outlook on what makes a good OS, and flash is not it.  
  As for the PBI system, yes it's essentially a blatant rip of the Windows installer, but that's kind of the point.  It's friendly and familiar, and if you want to use ports instead well then knock yourself out.  
  As for what version you got off bittorrent, I can't help ya there.  I had remarkable difficult getting 1.3 install, but 1.4 runs like a champ.  I guess in theory 1.3 could work fine for you and 1.4 break the system on your particular hardware.  And while that's no reason not to give 1.4 a try, if you have no reason to upgrade, then why waste your time?  If 1.3 works fine for your girlfriend, leave it be.

---

### Post by the_darkside_986 on 2007-10-06
I am finally getting things to work though, but I still can't get the kernel source code tree installed. I can't install the newest nvidia driver until I figure that one out.

I mean that FreeBSD, the system on which PC-BSD is based, is technically superior to most easy-to-use graphical Linux systems. It seems to be more capable of handling heavy applications such as Sauerbraten (a first-person shooter).

Plain FreeBSD 6.2 is nice but I never could get my nvidia card drivers to install properly in 6.2-RELEASE. In PCBSD, there is a usable (older) 3d driver and I was actually able to configure my wireless card in a FreeBSD distro for the first time ever.

---

### Post by Frak on 2007-10-06
I kept hearing from the PC-BSD community that it is superior to Linux, so I tried it (didn't believe them, just wanted to see for myself). It had horrible hardware detection, it was kinda clunky, and slow, not much apps for it.

Most of all, I ran into a problem, asked the community, and got criticized for it.

I stayed with the penguin.

---

### Post by Bachstelze on 2007-10-06
I kept hearing from the Linux community that it is superior to Windows, so I tried it (didn't believe them, just wanted to see for myself). It had horrible hardware detection, and there was not much apps for it...

You get the idea.

---

### Post by ramjet_1953 on 2007-10-06
Downloaded 1.4 from the distrowatch website and had no problems with install.

In fact, it was easier than Ubuntu and recognised all of my hardware. It even saw that I had an intel grapics chipset and automatically configured my laptop's screen to 1280 X 800 @ 24 bit. This is something that Ubuntu needs to look at, as other Linux distros also do this.

I had no problems with customizing it to my tastes and so far, it seems to be solid.

Haven't tried Compiz Fusion yet, as I find all of the effects distracting and the wow factor wears off quickly.

Also another plus is that VCD's and DVD's play straight-up. In Ubuntu, ever since Feisty, VCD playback has been flakey, requiring you to manually play them through VLC. As I live in Thailand, this feature is important as the vast majority of movies over here are released as VCD's.

So far, a good experience for me, which would be even better, if there were a local mirror site for the repos.

Regards,
Roger :cool:

---

### Post by angryfirelord on 2007-10-07
I was impressed as well, but not enough to make me a full BSD user. The nvidia drivers gave me issues, showing a "Input Not Supported" when trying to switch to a virtual console & DVD playback was really slow to load for some reason. Also, when I tried a 3D game, it ran well, but the graphics looked more grainy for some reason (Bzflag). Plus, the PBI system makes me nervous because it inherits the same flaws as an .exe file because someone could easily make a script with malicious code and disguise it as a PBI. Other than that, it is a good OS to play around with.

---

### Post by Bachstelze on 2007-10-07
Someone can easily make malicious code ans disguise it as a DEB, too.

---

### Post by Frak on 2007-10-07
> **HymnToLife said:**
> Someone can easily make malicious code ans disguise it as a DEB, too.
Not if you use the repos.

And if you argue "Well PBI's have a repo too" well, your right, but... Anybody can replace the file with a malicious one on the mirror.

---

### Post by Ireclan on 2007-10-07
I just came back from a sojourn in BSD land with PC-BSD. It didn't work out with me. My screen was stuck in one resolution, and when I went to change it X would crash. Surfing the internet was a nightmare, as it kept crashing. Let's see....There was less software and hardware support, less developers....The PBI system needs SERIOUS work (no up to date documentation on how to create them, and they don't work on any release of PC-BSD other than the one they were designed for)...The only things it did right was playing all my media files out of the box, and having a great community. Perhaps it's just that it needs more time to mature, I don't know....But until then, I'll stick with Ubuntu, thanks.

---

### Post by Scheater5 on 2007-10-07
In the last week or so of messing with PCBSD and reading your comments (wow, a bunch of people decided to post today!) I generally agree with you.  There are some issues inherent with the PBI system.  And yes, the hardware detection still has much work left to be done.  But put all of this in light of where it came from, the general mindset of the BSDs (none of which has which has ever claimed to be designed for the desktop) and what hardware BSD is generally used on, and PCBSD is quite an accomplishment in a reasonably short amount of time.  Besides, couldn't many of the complaints that have been said (including by me) against PCBSD1.4 have been said about Breezy?  Or even Dapper?  

A torrent file I recently download filled up my Feisty partition without me noticing so that when I rebooted I couldn't log in.  It's a relatively common, well documented problem - I'm not blaming Kubuntu for that.  But it has forced me to use PCBSD almost exclusively for several days now (out of laziness against logging in under console mode and deleting a file or two).  And I've found that there's not much of my daily activities I can't do under PCBSD.  So, think about the number of developers on PCBSD (peanuts compared to Ubuntu) and that merely one release ago I couldn't even get X to load, and now all my hardware short of the scroll function of my laptop touchpad work out-of-the-box.  I'm very impressed by PCBSD for taking a great OS that was never meant for the desktop and making it work rather well in that situation.  

I don't understand just why it is that everyone says BSD is more secure than Linux (I understand why Linux is more secure than Windows) but if it's true, then PCBSD's wrangling of a server OS into a desktop-friendly OS could serve a valuable service (I earlier mentioned using it as a bittorrent box, or perhaps in a government office where menial tasks such as word processing are done on sensitive documents).  If it doesn't work on your hardware now, well, give it a while.  When the next release rolls around, give it another shot.  It certainly impressed the heck out of me.  Is it ready for prime-time?  No.  Is it ready for you? More likely than you may think.  Is it ready for me?  Yes.

---

### Post by angryfirelord on 2007-10-07
> **HymnToLife said:**
> Someone can easily make malicious code ans disguise it as a DEB, too.
That's why most Linux distros have a trusted repository with some GPG key that prevents the whole "malicious" mess. Pbidir & its links doesn't seem to have this kind of backing.

The problem I'm expressing is that if I can hack the pbidir site, I can edit the links so that they download to something else. Someone may notice in time, but all I need is one exploit and everyone panics. With distros like Ubuntu, Debian, Fedora, etc., the "path" to get packages can only be one source defined in some configuration file where only root can edit it. I know in Fedora, yum checks md5sums which prevents exploited packages from being downloaded because the md5 changes as the package size changes.

---

### Post by the_darkside_986 on 2007-10-08
I finally gave up on PC-BSD 1.4 after I never could get KDevelop to build a simple KDE application, even after installing it from ports. I do like how I was able to configure stuff from a GUI easily, like my graphics card and wireless.

But I think the switch from FreeBSD 5 to 6 as their base system has caused too many problems that they haven't been able to fix yet but I expect the next release to be better. 

The PBI system is terrible and doesn't provide any real solution to unsatisfied dependencies. It doesn't provide a packaging solution for systems that can't have a network card because the PBI's still lack important libraries sometimes. Maybe with a lot more work, the install system could be good, but until then, ports and packages win.

So anyway, yesterday I finally installed plain FreeBSD 6.2-RELEASE, and after reinstalling the nvidia 100.14.11 drivers numerous times, it finally started working. I also had to look up my freebsd notes where I wrote down how to configure my wireless card in FreeBSD. This is a system that has better hardware support out-of-the-box than some Linux distributions. 

It was a lot of work but now I have a usable FreeBSD desktop that is stable and solid. It can be fun and challenging, but the satisfaction of having it finally working makes it worth it. But I still have to manually alter the C/C++ source code of SDL library to get sound to work right :) I did that a long time ago but I forgot how.

When I have lots more time, I might even try to get NetBSD or OpenBSD running on a desktop. But I won't try that on my current system, which uses too many proprietary foss-unfriendly hardware components. When I build a new PC with foss-friendly components, then I'll try it.

---

### Post by Frak on 2007-10-08
Actually, PBI's are good because they have all the dependencies built in, yet are bad for the same reason. There's just no sense in having the same file multiple times.

---

### Post by angryfirelord on 2007-10-08
> **Frak said:**
> Actually, PBI's are good because they have all the dependencies built in, yet are bad for the same reason. There's just no sense in having the same file multiple times.
I agree and it probably can be fixed too. Rather than just make a separate directory for each program, they could use the pbi to install/update libraries that need be rather than installing the same library file 5 times.

Personally, I'm still waiting for the Debian/kFreeBSD port to mature.

---

### Post by Frak on 2007-10-08
> **angryfirelord said:**
> I agree and it probably can be fixed too. Rather than just make a separate directory for each program, they could use the pbi to install/update libraries that need be rather than installing the same library file 5 times.

Personally, I'm still waiting for the Debian/kFreeBSD port to mature.
I mayself find the Debian package system to be simply amazing. There is plenty of documentation
[http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)
[http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html)

And its amazingly easy to create a .deb, all you need is the source, some well documented tools (stated at the beginning), a makefile, and some patience and you'll be fine.

I'm lost when it comes to PBI's.

---

### Post by kazuya on 2007-10-15
PCBSD 1.4 seems promising, but not quite in the same ball pack in terms of ease of getting apps. Not nearly. For one, I have never done an install where I could not at least use vesa or safe mode to get a basic gui or CLI. Installation steps with PCBSD 1.4 was very straight-forward until it came time to startx or restart computer into PCBSD. This failed in an annoying way. I tried selecting 1024X768, nv, or vesa or nvidia which is my PC videocard.. All failed. 

DesktopBSD 1.3RC was much better for me than this release which was not fully tested at all on more hardware. My PC was a 3 yr HP PC a1410n.. with nvidia 6150 on board.

I tested on a much older 2002  Dell PC and it ran, but it did so much much slower than with even Linux Mint or Zenwalk or Arch linux.. It took a little longer to launch any application..
Sorry for my rants..

I had too much expectation. The Debian-based distros are to date, still the most capable on various hardware... Closest to them are the slack-based distros and some rpm-based one like PClinuxos..

Desktop BSD is not bad either.

---

### Post by Frak on 2007-10-15
> **kazuya said:**
> PCBSD 1.4 seems promising, but not quite in the same ball pack in terms of ease of getting apps. Not nearly. For one, I have never done an install where I could not at least use vesa or safe mode to get a basic gui or CLI. Installation steps with PCBSD 1.4 was very straight-forward until it came time to startx or restart computer into PCBSD. This failed in an annoying way. I tried selecting 1024X768, nv, or vesa or nvidia which is my PC videocard.. All failed. 

DesktopBSD 1.3RC was much better for me than this release which was not fully tested at all on more hardware. My PC was a 3 yr HP PC a1410n.. with nvidia 6150 on board.

I tested on a much older 2002  Dell PC and it ran, but it did so much much slower than with even Linux Mint or Zenwalk or Arch linux.. It took a little longer to launch any application..
Sorry for my rants..

I had too much expectation. The Debian-based distros are to date, still the most capable on various hardware... Closest to them are the slack-based distros and some rpm-based one like PClinuxos..

Desktop BSD is not bad either.
1. ALWAYS lower your expectations. Nothing ever lives up to hype.
2. Desktop BSD and FreeBSD are the only two BSD OS's I'll actually use.

---

### Post by motang on 2007-10-15
> **Scheater5 said:**
> I previously wrote about my struggles with PCBSD 1.3 and ultimately installing and trying [DesktopBSD]("http://ubuntuforums.org/showthread.php?t=491664").  I never got the kinks worked out of that DesktopBSD install, and that partition went basically unused until I decided to give PCBSD 1.4 a go.
I've spoken pretty harshly against BSD as a desktop OS in the past.  I never really meant the idea of BSD as a desktop was unsound, just that everything I tried worked very poorly.  Well, PCBSD 1.4 is a vastly different story.  
The install went flawlessly, and in a very short amount of time (even compared to Ubuntu installs - both with the Desktop and the Alternate install) I had a fully functional KDE desktop awaiting me.  
I'm still not so sure BSD is as useful as a desktop OS for the typical user as linux.  I would love to have an updated Knetworkmanager, as the default network manager in PCBSD 1.4 is pretty clumsy to use.  Effective, but not efficient.  No Open Office by default also costs it points - but only in light of the fact that it is designed to be more oriented to the desktop user.  And I've had some trouble with Compiz-Fusion, and I'm not sure it was a very smart move to include that by default when BSD's idea seems to be to use only very stable software.  But I can't really blame BSD for my problems with experimental software, so I won't dock them for that.  
Other than that, it works great.  It is as responsive as Kubuntu.  The PBI system takes longer than, say Ubuntu's repos, that's only because the mirrors are relatively slow.  It's certainly faster than compiling everything from source, and well suited for the target audience.  
I haven't had a chance to test everything out just yet, but thus far I'm liking what I see.  I have a desktop that I use as a bittorrent box, and I will probably replace Kubuntu with PCBSD on it in the near future.  Kubuntu will probably stay on my laptop as my main OS, but I'm keeping my eye on PCBSD.  If nothing else, experimenting with it will keep me occupied until Gusty comes out.
I am glad to hear this as I have recenlty have gotten the itch to try out PC-BSD, just for myself and maybe even set it up as a server to host my personal built web apps.  Thanks for the insight.

---

### Post by andhar on 2007-11-04
Being a n00b to linux/*nix I am running Ubuntu 7.04 ,7.10 & xubuntu on different systems (I dove in) and I got bored and tried PCBSD on a pretty decent system, old but decent. 

In my opinion it's much more polished than FreeBSD and had better support for the hardware I was running than ubuntu 7.10 which had issues with the IGP and with an ATI 9x card I had in the system.

My gripe with PCBSD is the PBI system, I guess I've gotten so used to using apt-get that I found it very clunky to use, other than that I liked the OS the eye candy by default was nice but blah until it grows up a lil I will stick to x/ubuntu.

---

