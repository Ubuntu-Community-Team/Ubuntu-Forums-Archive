---
title: "Does my dream distro actually exist?"
date: 2011-11-09
forum: Any Other OS
---

### Post by Psyael on 2011-11-09
I'm tired of wiping Ubuntu to try a distro and coming back with my tail between my legs in the morning.

This is what I use my computer for: Web browser (Chrome), IM, playing music, watching videos with gstreamer or VLC, playing World of Warcraft over WINE as well as older or less complicated Windows software. I share a folder over Samba to a Windows machine.

Here's my wishlist:

**Designed with GNOME in mind:** This knocks out current versions of Ubuntu, as I'm not happy with the current level of support for GNOME Shell in Oneiric. The gnome-tweak-tool, which is pretty critical for managing extensions and such, is almost hidden and there's no extensions binaries or effort to improve the shell with Javascript addons. It's not that GNOME is unusable in Ubuntu, it just really isn't their focus. Unity is.

**No compiz baloney:** I use an NVidia card with the proprietary drivers and compiz causes all kinds of screen tearing in video players and/or 3D accelerated WoW. I think this isn't a problem with GNOME Shell, as I've done both in Oneiric+GNOME. I know it has been an issue with Unity and Xubuntu, so I have to log into 2D mode. I'm fine with that, just so long as there's *some* way to turn that off.

**A basic amount of usability for common macdows users:** This knocks out Fedora among others. I tried F16 today and had to reinstall about four times trying to get the proprietary NVidia drivers to work, because of outdated information and SELinux related issues. After turning off SE entirely, I installed Samba and looked to see how to share a folder and it was far more complicated than the kind of "Right click, properties, share" that I had become accustomed to. Maybe I'm a pushover (I probably am), but it seemed very config file oriented instead of GUI integrated.

**At least some way for me to install third-party proprietary ('restricted') software:** Alternate/third party repositories, etc. Codecs and the like out of the box like the *buntus are nice but not strictly necessary provided instructions exist on how to install it yourself.

... And that's about it. Any feedback is appreciated. I know OpenSUSE is releasing a GNOME3-focused distro in about a week, and at some point in the near-future Mint is going to as well. I figure I'll give those a shot, but if it doesn't work for me I'm going to just going to sit back and kick back and live with Unity (it needs improvement, but isn't horrible or anything) unless anyone can name something specific I should try.

---

### Post by hhh on 2011-11-10
Well, if you don't want to just use the last Ubuntu LTS (Long Term Support) release, which I thought used GNOME 2, you could try Debian Squeeze Live (GNOME)...

[http://live.debian.net/archive/images/6.0.3/](http://live.debian.net/archive/images/6.0.3/)

Choose your architecture (i386 or amd64), choose iso-hybrid and download/burn the GNOME iso to a DVD or USB drive. You'll see from the package list that there is no Compiz included by default. The desktop is GNOME 2 and will be supported for 3 years. Iceweasel (Firefox) is the installed browser but Chromium (Chrome) is in the Debian repos...
[http://packages.debian.org/squeeze/chromium-browser](http://packages.debian.org/squeeze/chromium-browser)

It's a Live install so you can try it out before installing it. Ubuntu is Debian based so package management is the same. You can even use Ubuntu PPAs, though it's not recommended for stability/security reasons. Debian is well known for it's stability, security and huge package repositories.

If you do install it and don't like the "quick restart" feature which bypasses Grub, uninstall the package kexec-tools. You'll also need to fix /etc/apt/sources list and add "non-free" to it. See this link for a mirror near you...
[http://www.debian.org/mirror/list](http://www.debian.org/mirror/list)

Once the non-free repo is added, you can install the nvidia blob via terminal with...```
sudo apt-get install nvidia-kernel-dkms nvidia-glx nvidia-settings nvidia-xconfig
```
After the install and before rebooting, run```
sudo nvidia-xconfig
```
When you reboot the module should be active and you can tweak your resolution/refresh rate by running...```
gksu nvidia-settings
```

PM me if you try this but run into problems.

-edit- The next release of Debian, Wheezy, will use GNOME 3 (shell) but it isn't going to be released for about least 2 years. If you want to use Shell, maybe look into gNatty...
[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

---

### Post by boydrice on 2011-11-10
> **Psyael said:**
> Does my dream distro actually exist?

No, not at this time.

---

### Post by hhh on 2011-11-10
@boydrice, pthfthffththtppppptththth. No distro is perfect for anyone out-of-the-box.

For gnome-shell, I just read about the Linux Mint 12 preview...
[http://blog.linuxmint.com/?p=1851](http://blog.linuxmint.com/?p=1851)

Download link...
[http://ftp.heanet.ie/pub/linuxmint.com/testing/](http://ftp.heanet.ie/pub/linuxmint.com/testing/)

---

### Post by boydrice on 2011-11-10
> **hhh said:**
> @boydrice, pthfthffththtppppptththth. No distro is perfect for anyone out-of-the-box.

For gnome-shell, I just read about the Linux Mint 12 preview...
[http://blog.linuxmint.com/?p=1851](http://blog.linuxmint.com/?p=1851)

Download link...
[http://ftp.heanet.ie/pub/linuxmint.com/testing/](http://ftp.heanet.ie/pub/linuxmint.com/testing/)

I agree, based off the OP's dream distro requirments he should check out Mint 12.  Given his aversion to any tweaking and fiddling he should wait till it is released though.

---

### Post by Psyael on 2011-11-10
Thanks for the replies. I've thought about Debian, but they're pretty hardcore on the free software philosophy front (still remember the Firefox -> Iceweasel thing) so I figured it'd be heavily limited in terms of media formats and the like. Do I just install some sort of Restricted package and it's all there?

Mint 12 really does sound good. I don't mind fiddling, tweaking, and copying some terminal commands I don't really understand just to get things started and working regularly from then on, but having to mess with configs for routine tasks, like modifying smb.conf every time I wanted to activate or deactivate sharing a folder turned me off.

GNOME 2 or 3 doesn't make a big difference to me, I find 3 curious and exciting and want to move to it when it's ready (out of the box, as Fedora and Ubuntu provide it, is not ready) but moreover I just want a stable system that works. My favourite Unity/Shell feature can be added to the old panel system by installing GNOME Do.

---

### Post by hhh on 2011-11-10
Mint might be your ticket, try the Mint 11 Live CD and see what you think.

> **Psyael said:**
> I've thought about Debian, but they're pretty hardcore on the free software philosophy front (still remember the Firefox -> Iceweasel thing) so I figured it'd be heavily limited in terms of media formats and the like. Do I just install some sort of Restricted package and it's all there?
I haven't used Synaptic or any other GUI for package management in about a year, but yes. The manual way is to edit /etc/apt/sources.list to this (using a reasonable mirror for your location)...```
deb http://mirror.anl.gov/debian/ main contrib non-free
deb http://www.debian-multimedia.org squeeze main non-free

```

Then run...```
sudo apt-get update
```

Then install these packages for flash, in-browser media viewing, decent web fonts, dvd playback, mp3 ripping and playback...```
sudo apt-get install flashplugin-nonfree gecko-mediaplayer msttcorefonts unifont libdvdcss2 lame w32codecs
```

That'll get everything except Java that I can think of off the top of my head (you can install Java too, I just haven't but I can talk you through it). You'll get an error about the Debian Multimedia repo being unauthorized which you can fix by installing debian-multimedia-keyring and running another sudo apt-get update.

@boydrice, right on, and thanks for not getting offended at my playful raspberry. :cool:

---

### Post by jackdale on 2011-11-11
Ever thought of LFS 7.0? :D

Seriously, though, it sounds like Ubuntu with gnome-shell or Mint 11 (or 12 when it comes) might be as good as it gets.

However, the following is a little disturbing:
> I'm tired of wiping Ubuntu to try a distro and coming back with my tail between my legs in the morning.

I love to try different distributions before installing, but I don't like how (relatively) slow liveCDs are.  So I use VirtualBox to test them out.  I hope you don't mind me recommending this.  It has the advantage of not having to worry about the hardware too much (after installing guest additions, of course).  In this way I have tried Fedora 15 & 16 and other RHEL clones, Mint (various versions), Sabayon (various), VectorLinux (various), OpenSUSE (various) and OpenSolaris (various - before it met an untimely death).  They all have interesting things about them and features that are absent from the *buntus, but I have deleted most of them without ever installing in a separate partition.  I have kept a few useful ones (Caine2.5, TAILS, LIPOSE, PC-BSD 8.1, trixbox), but my main distro remains Ubuntu as it meets my current needs (post-tweaking).

The advantage of this is that I can add functionality to Ubuntu by just booting up a virtual machine.  For example the trixbox is helpful if I want to run a PBX/Asterix server on my network.  I *could* try to install the relevant packages in Ubuntu, but if I know there is a specialised distro that meets the needs that Ubuntu doesn't, I can use it along with ubuntu rather than instead of it.

---

### Post by GERGE on 2011-11-11
Arch is the dream distro for everyone, but only if you know how to set it up.

Take a look.

---

### Post by Gatemaze on 2011-11-11
> **Psyael said:**
> I'm tired of wiping Ubuntu to try a distro and coming back with my tail between my legs in the morning.

This is what I use my computer for: Web browser (Chrome), IM, playing music, watching videos with gstreamer or VLC, playing World of Warcraft over WINE as well as older or less complicated Windows software. I share a folder over Samba to a Windows machine.

Here's my wishlist:

**Designed with GNOME in mind:** This knocks out current versions of Ubuntu, as I'm not happy with the current level of support for GNOME Shell in Oneiric. The gnome-tweak-tool, which is pretty critical for managing extensions and such, is almost hidden and there's no extensions binaries or effort to improve the shell with Javascript addons. It's not that GNOME is unusable in Ubuntu, it just really isn't their focus. Unity is.

**No compiz baloney:** I use an NVidia card with the proprietary drivers and compiz causes all kinds of screen tearing in video players and/or 3D accelerated WoW. I think this isn't a problem with GNOME Shell, as I've done both in Oneiric+GNOME. I know it has been an issue with Unity and Xubuntu, so I have to log into 2D mode. I'm fine with that, just so long as there's *some* way to turn that off.

**A basic amount of usability for common macdows users:** This knocks out Fedora among others. I tried F16 today and had to reinstall about four times trying to get the proprietary NVidia drivers to work, because of outdated information and SELinux related issues. After turning off SE entirely, I installed Samba and looked to see how to share a folder and it was far more complicated than the kind of "Right click, properties, share" that I had become accustomed to. Maybe I'm a pushover (I probably am), but it seemed very config file oriented instead of GUI integrated.

**At least some way for me to install third-party proprietary ('restricted') software:** Alternate/third party repositories, etc. Codecs and the like out of the box like the *buntus are nice but not strictly necessary provided instructions exist on how to install it yourself.

... And that's about it. Any feedback is appreciated. I know OpenSUSE is releasing a GNOME3-focused distro in about a week, and at some point in the near-future Mint is going to as well. I figure I'll give those a shot, but if it doesn't work for me I'm going to just going to sit back and kick back and live with Unity (it needs improvement, but isn't horrible or anything) unless anyone can name something specific I should try.

ubuntu 10.04 LTS

---

### Post by boydrice on 2011-11-11
> **GERGE said:**
> Arch is the dream distro for everyone, but only if you know how to set it up.

Take a look.

There we go.  I had wondered how long it would take for the Arch fanboys to show up.

---

### Post by giowuu on 2011-11-11
I just completed the  arch installation process. It is sooo coool. I feel like a new human being. Guys!? Guys??????

---

### Post by boydrice on 2011-11-11
> **giowuu said:**
> I just completed the  arch installation process. It is sooo coool. I feel like a new human being. Guys!? Guys??????

I know, I learned so much by following the beginners guide on the wiki.  I feel more 1337 everyday.  Did you know Arch is a rolling release and KISS?  Oh and I did I mention the wiki?

---

### Post by arkanabar on 2011-11-12
If you have enough space, and a modest understanding of fstab and partitioning, you can fit quite a stack of different distros onto one computer.  Here's the sort of partitioning scheme you can use (presuming they can all use the same version of WINE):

Give each distro a / partition of about 10-15Gigs, and a /home partition of about 10 gigs.  About 1/4 of the way into the disk, make a partition of about 50 gigs.  Give it a label like wine.  Partition 4 will have to be extended, and 5 & up will have to be logical partitions.  Put a swap directory at the very end of the disk, no larger than 1.5x RAM.

in each /home/(username) directory, create a .wine directory, and then run ```
sudo blkid > /home/(username)/uuid.txt
```  The file created will have UUID values for every partition on the system.  Note that UUID values change every time a partition is formatted.

then modify /etc/fstab to include a line like

```
UUID=(40 character hexidecimal value) /home/(username)/.wine (filesystemtype) defaults 1 2
```

then install wine and run winecfg, and copy your WoW directory over to ~/.wine/drive_c/Program Files.

I had something like 4 different distros all using the same WoW install with a setup like this at one point.  Most of them were Ubuntu variants (#! 9.04 lite was a favorite), but also SalixOS, Sabayon, and openSUSE, and these days I suspect simplyMEPIS and antiX would also work well.

---

### Post by 1clue on 2011-11-12
Not going to go into a distro war, but I can help you test them without having to scrape off and return to Ubuntu.

Install VMware, VirtualBox, whatever your favorite virtualization engine might be.  Install any new distro as a virtual machine, and test it there.

This lets you practice on the installation, and also lets you run in what is mostly a native mode.  The only thing you don't get is a reliable test of driver software for your specific hardware, but if you have it working with Ubuntu then there exists a driver for Linux for that hardware.

---

### Post by 1clue on 2011-11-12
Oh, heck.  I guess I will give a distro recommendation.

You might want to try a source-based distro like Gentoo.  It's my other favorite distro.

Advantage:  You get guided through a bare-bones installation, are taught how to configure your system and then you literally install everything yourself.  Absolutely every piece of software on the system is compiled by you, so you can choose the compilation options and everything to suit your needs.

Disadvantage:  You have to compile everything.  You have to know at least what you want to accomplish, even if you don't know exactly how to do it.

This is a labor-intensive distro, but you will learn more about Linux than you ever thought there was to know.  You'll need to read a whole lot, and you should have a pretty quick system.  I have ... look at my signature, my system runs it pretty well.  Not sure I would run it on any less than a dual core.

The reason I recommend it is because it is exactly what you choose to make it.  During the initial installation process you compile the kernel, then you pull updates as source from the repository and compile those, and then you start adding stuff.  They don't even tell you which system logger to use.  The entire point of the distro is you do it your way.  They have a system that works really well, you configure how you want things to work and what options to use in general, and the package manager takes care of most of the rest.

Good luck and have fun.

---

### Post by wolfen69 on 2011-11-12
So far, my "dream distro" is ubuntu. It "just works" compared to most distros.

---

### Post by Dlambert on 2011-11-12
I recommend Sabayon 7 Gnome edition! Which is pre-configured Gentoo and bleeding edge if you want!

---

### Post by 1clue on 2011-11-13
Oh yeah.

There are two basic approaches in Linux distributions.  First is like Ubuntu, where they try to balance stability with having current software.  The longer the release cycle, the more stable everything is (in theory) but also the more "stale" the software gets.

Generally they have two or three options for "stability" and "newness".  You have an alpha/unstable release which is under active development and not especially stable.  Then they have the next one down which is considered stable and mainstream, then you have a long term support version which has a really long release cycle to make enterprise environments happy.

Gentoo uses a rolling release.  You still have "unstable" and "stable" but there isn't any version number, and you never need to upgrade to the next release, only updating packages as they come available.  When a package is well integrated and essentially bug free as installed, then it goes to the stable release.

---

### Post by Psyael on 2011-11-13
Thanks for the suggestions. I've tried Mint 12 RC and I have issues that are temporary/beta related (GDebi freaking out the Chrome .deb) and some that are more permanent (can't use WineHQ repository for Ubuntu apparently, and I *like* to have auto update binaries of experimental but it's not super critical.) I think at the end of the day what I really want is that much-fabled GNObuntu that people talk about, hopefully the gNatty/Riome stuff will lead to that someday.

I tried installing Slackware in 1997 and never got anywhere because compiling from source was a nightmare for me then and still was, and I got as far as booting the old MIT interface for X.org before giving up. Then came back in 1999 to run Q3Test, and RPMs felt like a dream. Point of this history lesson being, I can't run without packages. Heh.

I still maintain that I will give SUSE a try in a few days and if that doesn't work, probably take up that LTR suggestion.

---

### Post by lolpenguin on 2011-11-13
Arhc Linux can be everyones' dream distro. You can customize to your preference, with no limitations.
BUT it is annoying to set up, with a text based installer, and X Server not installed by default.

---

### Post by Psyael on 2011-11-13
I do have some Arch friends. When I get around to VirtualBox, I'll give it a go.

I got Chrome onto Mint 12 RC by avoiding the .deb entirely and adding the repository it adds manually with apt-get. I'm now 'happy' enough to stick around with it until I come across some reason to drop it.

---

### Post by 1clue on 2011-11-13
> **Psyael said:**
> Thanks for the suggestions. ...

I tried installing Slackware in 1997 and never got anywhere because compiling from source was a nightmare for me then and still was, and I got as far as booting the old MIT interface for X.org before giving up. Then came back in 1999 to run Q3Test, and RPMs felt like a dream. Point of this history lesson being, I can't run without packages. Heh.



Gentoo is not as difficult as old-world slackware was.  You still have a package manager, and it still works pretty much the same way, but you set your compile options for your personal preferences.  Quite a few people use it as a first-time distro, believe it or not.

My main point of mentioning it is that the installation is exactly what the user chooses it to be.  It's a make-your-own-distro distro.

---

### Post by Psyael on 2011-11-17
So I've played with a lot of distros the past few days. I've come to the conclusion that I need to be able to have the following with a reasonable amount of work:

* NVidia drivers
* Media codecs
* Truetype fonts with smoothing (i.e. Ubuntu/Mint style)
* Samba

Once I have that going, I can pretty much set up Chrome and WINE and be off and running.

So, here's my take on the distros I've played around with:

**Mint 12 RC:** Comes about as close as we can get to making GNOME3 usable until the project gets their big extension repository website online. MATE is a bit janky at times but still works. I ming use this going forward unless I can think of a reason why not.

**OpenSUSE 12.1:** This is the system that I really want to use, but I just can't. It looks on the outside like it's Fedora for people who just want to stop tweaking with things and start getting work done. NVidia binaries are temporarily unavailable, which I won't knock against it since it's only a few hours old. It shares a complaint with Fedora: the fonts are ugly as heck. The MSTT fonts are easy enough to install, but figuring out the subpixel rendering software is difficult since the docs for that stuff are still about the old GNOME2 version. They've also removed a few things I really like about GNOME-shell: the alt-tab (there's no alt tab at all!!) and the superkey bringing up the activities screen (it does nothing.) And it's not an extension you can turn off in gnome-control-center, either.


My next few experiments will be Lubuntu and, failing that, Debian. Lubuntu kind of interests me as it reads like a *buntu with a solid replacement for gnome 2's panels and no compiz effects to interfere with my videos or gaming. I did enjoy my brief time with Xubuntu, so we'll see how this goes.

---

### Post by wolfen69 on 2011-11-18
Why not just get more hard drives, then you can run a bunch of different os's. You can keep your stable install of ubuntu, and still play around.

---

### Post by Psyael on 2011-11-19
You're pretty much describing what I already do.

I keep my critical files on another device that I've unplugged for the time being. I have a Windows 7 install and the rest of the drive for linux. When I change distros, I just launch the GParted liveCD, delete the ext4 partitions, and reboot into the next distro's disc.

---

