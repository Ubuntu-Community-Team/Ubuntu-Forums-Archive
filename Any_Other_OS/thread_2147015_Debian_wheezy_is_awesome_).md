---
title: "Debian wheezy is awesome :)"
date: 2013-05-20
forum: Any Other OS
---

### Post by screaminj3sus on 2013-05-20
I've never really tried pure debian before, and definitely never considered using it as my main desktop operating system, but I recently gave the newly released wheezy a try and am loving it :)

It is a little trickier to install and setup than ubuntu (but not really that difficult at all, I found the installer to be straightforward enough and things worked reasonable well out of the box in debian. I did have to make a few tweaks that I don't need to do in ubuntu such as adding my user to the sudo group, adding myself to the lpadmin group, installing system-config-printer, and tweaking font rendering so it doesn't suck).

The thing that suprised me most was how well wheezy works for multimedia. Out of the box it played mp3, aac, and h.264, this is even better multimedia support than ubuntu has out of the box! I wish more distros would follow suit here.

The desktop is very stable and quick, it seems lighter than any other full gnome distros that I've used. The version of gnome it comes with is kind of old already, but I've actually come to really appreciate that it comes with gnome-shell 3.4. IMO gnome 3.4 has been the only gnome 3.x release thats been fully usable and doesn't have a bunch of annoying bugs (for example gnome 3.6 has a lot of weird little issues with network shares, like randomly crashing when mounting/unmounting them or sometimes giving pointless gvfs errors when unmounting shares. ubuntu's patched nautilus 3.6 is even worse, its introduced a bug that upstream nautilus doesn't have where it randomly "loses" my bookmarked shares. And nautilus 3.8 has a bug where it randomly crashes gnome-shell and sometimes even totally crashes gnome). Wheezy's gnome 3.4 desktop has been super solid for me, I've noticed no annoying problems with gnome-shell or nautilus. And honestly after using debian's gnome 3.4 for a week I can't think of a single thing I really miss in 3.6 or 3.8 that really compels me to upgrade from gnome 3.4.

Everything that I use this laptop for is working wonderfully in debian 7, and I've had yet to run into annoying "showtopper" bugs that I've constantly been hitting with all other recent distros. I think I can finally stop distro hopping for now, and I can wait things out in stable debian land until unity-next, gnome-shell, kde etc... become bug free enough for me to use without pulling my hair out :)

The only problem I had with wheezy is that it came with a very old kernel that hates my ivybridge graphics, and the system would randomly lock up. luckily compiling kernel 3.8 sorted that out for me, and now all my hardware (brightness keys, card reader, etc..) works just as well in debian as it does in 13.04, and an official kernel 3.8 backport should be available soon.

I didn't expect debian to be a good "desktop" experience, but was pleasantly surprised. Its been too long since I used a distro where everything actually "works".

After some tweaking I have a very pleasent looking desktop too: [[img]http://en.zimagez.com/avatar/2013-05-19-1848291366x768scrot.png[/img]](http://en.zimagez.com/zimage/2013-05-19-1848291366x768scrot.php)

---

### Post by iamkuriouspurpleoranj on 2013-05-20
Debian is great.

---

### Post by sffvba[e0rt on 2013-05-20
Wheezy looks awesome from install to boot-up... well done to the devs and community!


404

---

### Post by mikodo on 2013-05-20
Funny, I installed Wheezy this week too and I am really liking it also. I use the Xfce environment, so I have Xubuntu 12.04 and have made a very easy transition to Wheezy's Xfce.

A couple of things I found:

1) I know you said that multimedia worked out of the box for you, but here is a link for [deb-multimedia]("http://www.deb-multimedia.org/") which has all the stuff that medibuntu has; be sure to add the signing key first. 

2) [Debian Backports]("http://backports.debian.org/"). I have enabled them for Firefox ( Iceweasel ) and Libreoffice so far, to have the newer versions from Debian Testing. Firefox went from version 10 to 21, with the release version. [Debian Mozilla Team]("http://mozilla.debian.net/"). Libreoffice, went to the version  4.0.3, the same as I got for Xubuntu 12.04 today when I updated. I think I will see about Thunderbird backports to, surprisingly as it is not being developed by Mozilla anymore, I got large updates for it today in Precise. I know they are continuing to provide security updates, so maybe that is all it was.

Just some ideas.

Have fun!

---

### Post by epikvision on 2013-05-21
Does debian now have out-of-the-box wifi support?  Its omission in the previous release was a huge turn-off for me.

---

### Post by mikodo on 2013-05-21
> **epikvision said:**
> Does debian now have out-of-the-box wifi support?  Its omission in the previous release was a huge turn-off for me.
Sorry, I don't use it, so I don't know.

---

### Post by iamkuriouspurpleoranj on 2013-05-21
^For me yes, although somewhat bizarrely I had to configure a file to get it to use the ethernet even though it had installed that way. Maybe something to do with the r2561.bin file it asked for during the installation.

The deb-multimedia drill is:

1. add repo url to /etc/apt/sources.list
2. apt-get update [as root]
3. apt-get install deb-multimedia-keyring [as root]
4. apt-get update [as root]
5. apt-get upgrade [or dist-upgrade]
6. apt-get install frogatto [optional]

---

### Post by monkeybrain2012 on 2013-05-21
> **epikvision said:**
> Does debian now have out-of-the-box wifi support?  Its omission in the previous release was a huge turn-off for me.

Kind of finicky. :)  I don't know why Debian's kernel 3.7.* works in some access point but not others. Same kernel version works in Ubuntu everywhere, on same machine.

Also for one machine with an intel card needed to install iwlwifi whereas Ubuntu and Fedora worked out of the box. That was a problem because I have no wired internet access to install iwlwifi, fortunately there  was a cheap usb wifi adapter lying around and it did work (after editing /etc/networks or something) It is hard to believe that wifi is still relatively painful in Debian.Except for the old broadcom cards which need proprietary drivers I would expect Linux to work out of the box by now (and it does in my experience with Ubuntu and Fedora)

I am by the way using sid, Debian stable and testing are just too stale, I would rather trade off a bit of that much overrated "stability" for something more functional and modern. Sid  is more up to date, but I would not call that bleeding edge either (still on kernel 3.2* and updated to 3.7* which killed the wifi at home, Ubuntu 13.04 is on 3.8*, Fedora 18 on 3.9.2, gnome-shell 3.4.*--updated to 3.8 with experimental but some packages are missing).

---

### Post by benerivo on 2013-05-21
> **monkeybrain2012 said:**
> ...Sid  is more up to date, but I would not call that bleeding edge either (still on kernel 3.2* and updated to 3.7* which killed the wifi at home, Ubuntu 13.04 is on 3.8*, Fedora 18 on 3.9.2, gnome-shell 3.4.*--updated to 3.8 with experimental but some packages are missing).

I use the [Liquorix Kernel]("http://liquorix.net/") repo which has patches for desktop and gaming performance over the stock kernel. It's also a more recent version. A few performance tests against a stock Ubuntu kernel can be seen at [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=liquorix_38_kernel&num=1").

---

### Post by BBQdave on 2013-05-21
> **epikvision said:**
> Does debian now have out-of-the-box wifi support?  Its omission in the previous release was a huge turn-off for me.

[Debian 7 non-free firmware]("http://www.debian.org/releases/stable/debian-installer/")

Check out the message box:

:arrow: If any of the hardware in your system **requires non-free firmware to be loaded** with the device driver...

I downloaded the tarballs of common firmware packages and unpacked them onto a USB stick. Plug in the USB stick - non free firmware packages, and boot up Debian 7 Net-Install CD. Going through the install process, Debian 7 installer will access the USB stick for the missing non free firmware - needed for your hardware.

Was able to easily *wireless* net install Debian 7 on my Toshiba Satellite C655 notebook :)

---

### Post by iamkuriouspurpleoranj on 2013-05-21
^good stuff

---

### Post by mikodo on 2013-05-22
> **BBQdave said:**
> [Debian 7 non-free firmware]("http://www.debian.org/releases/stable/debian-installer/")

Check out the message box:

:arrow: If any of the hardware in your system **requires non-free firmware to be loaded** with the device driver...

I downloaded the tarballs of common firmware packages and unpacked them onto a USB stick. Plug in the USB stick - non free firmware packages, and boot up Debian 7 Net-Install CD. Going through the install process, Debian 7 installer will access the USB stick for the missing non free firmware - needed for your hardware.

Was able to easily *wireless* net install Debian 7 on my Toshiba Satellite C655 notebook :)
Thanks.

From the [Debian GNU/Linux Installation Guide]("http://www.debian.org/releases/stable/i386/index.html.en") in the chapter ["Using the Debian Installer"]("http://www.debian.org/releases/stable/i386/ch06.html.en") is this page ["Loading Missing Mirmware"]("http://www.debian.org/releases/stable/i386/ch06s04.html.en")  suggests what you did.

;p

---

### Post by mips on 2013-05-22
Debian is nice for when you want a solid/stable box and not worried about getting the latest software. If however you wan't newer packages debian is not so accommodating. Great distro though.

---

### Post by BBQdave on 2013-05-22
> **mips said:**
> Debian is nice for when you want a solid/stable box and not worried about getting the latest software. If however you wan't newer packages debian is not so accommodating. Great distro though.

**Backports** help, but your right, Debian Stable is more focused on hardening a system then the latest greatest applications :)

---

### Post by screaminj3sus on 2013-05-24
> **epikvision said:**
> Does debian now have out-of-the-box wifi support?  Its omission in the previous release was a huge turn-off for me.

Yes, and if your wifi needs non-free firmware, you can download the non-free firmware to a USB stick and plug it in during install, and then the debian installer will automatically detect and use the appropriate firmware if needed. [http://wiki.debian.org/Firmware#Firmware_during_the_installation](http://wiki.debian.org/Firmware#Firmware_during_the_installation)

The debian installer had no problem using and connecting with my wifi.

---

### Post by screaminj3sus on 2013-05-24
> **mips said:**
> Debian is nice for when you want a solid/stable box and not worried about getting the latest software. If however you wan't newer packages debian is not so accommodating. Great distro though.

I used to always like the latest software, but with the near-total lack of regression testing in most FOSS software, I now kind of enjoy things being out of date, at least the bugs are predictable and I won't get new ones introduced during updates.

---

### Post by mips on 2013-05-24
> **screaminj3sus said:**
> I used to always like the latest software, but with the near-total lack of regression testing in most FOSS software, I now kind of enjoy things being out of date, at least the bugs are predictable and I won't get new ones introduced during updates.

Agreed. At the end of the day people need to decide which they prefer.

I could probably run wheezy on my laptop as I only have a certain set of apps installed on it and I rarely update it.

---

### Post by mikodo on 2013-05-25
> **mips said:**
> Agreed. At the end of the day people need to decide which they prefer.
I think I am going to start running both Debian "Stable" with some select back-ports apps and Debian "Testing" for a while to decide which is good for me. If for nothing else, to do some testing for Debian.

Choice is good.

;p

---

### Post by Dlambert on 2013-05-25
Just my personal opinion here, but to willingly use outdated software is just something I cannot do. I'm a manjaro/Arch man.

---

### Post by mips on 2013-05-25
> **Dlambert said:**
> Just my personal opinion here, but to willingly use outdated software is just something I cannot do. I'm a manjaro/Arch man.

Yeah, I'm in the same boat as you. I really tried using debian but I always longed for the newer packages. I mean they are still on xfce 4.8. I ran crunchbang xfce for a while and needed a few newer packages and I went the whole apt-pinning route which just ended in disaster.

I'll stick to manjaro/arch for now.

---

### Post by monkeybrain2012 on 2013-05-25
> **mips said:**
> Yeah, I'm in the same boat as you. I really tried using debian but I always longed for the newer packages. I mean they are still on xfce 4.8. I ran crunchbang xfce for a while and needed a few newer packages and I went the whole apt-pinning route which just ended in disaster.

I'll stick to manjaro/arch for now.

Try sid. :)

---

### Post by mips on 2013-05-25
> **monkeybrain2012 said:**
> Try sid. :)

I did try Aptosid once for a while but no, I'll pass thx.

---

### Post by odiseo77 on 2013-05-25
I've been using Debian Sid for about 2 years now and I love it. It's the perfect balance between stable and new -- not thoroughly tested -- software for me. It even has the extra fun of the eventual possibility of some things going wrong when upgrading the system, so you have to be careful when applying upgrades. But generally speaking Sid is stable enough (for me, at least) in spite of being the 'unstable' Debian branch. Also, things in Sid evolve fast and bugs are often fixed quickly.

---

### Post by mikodo on 2013-05-26
> **mips said:**
> I'll stick to manjaro/arch for now.
I want super stable for now. I have to limit the time I have for playing and fixing, to use the time I have for the computer to learning bash. I do hope Manjaro and SolusOS gain traction during my time learning. So, its Xbuntu LTS and Debian Stable Xfde for me. Hell, I still have 10.04 hanging around, that I have to give the boot.

;p

---

### Post by buzzingrobot on 2013-05-26
I've come to think of testing and unstable as two components of what can be seen as a slow rolling release process.  You can jump in because you enjoy that process, or because you want access to newer code. (Unstable, btw, isn't necessarily the newest.) Whether it's Arch or Sid, you're using code only a relatively few people have checked out. 

Many folks seem to jump blindly to new code, thinking it be must better or have wonderful new features. They ought to verify that before they take the risk. 

As to Wheezy:  Very nice Gnome implementation.  3.4 avoids the messaging area annoyances that are in 3.6 and 3.8.  MATE 1.6 is also nice on Wheezy.

---

### Post by sffvba[e0rt on 2013-05-26
Older software as Debian 7 may be, it looks and installs very slick.


404

---

### Post by MeBrains on 2013-06-13
switched over from windows with 9.10 - it has been a very smooth ride with Ubuntu. Each and every update was painless and straigtforward... I did not even do clean install all the time and it was all fine.With 12.04 came the problems - my gut feeling is that it is an error between the graphic driver and the kernel. My once rock-solid Ubuntu distro crashed, hard-freezed within minutes of booting. Tried Nouveau and tried Nvidia - all the same. Went to Fedora and started following launchpad reports about the issue I was experiencing. To my astonishment, the bugs were closed / won't fix. 12.10 did not offer soluce and, eventually, neither did 13.04 - although it initially appeared a lot more stable.Tried installing Mint 15, Fedora, OpenSuse and now Wheezy over the last few days. The latter seems to be brilliant. All the other systems crashes within an hour - the screen all garbled, TTY sometimes worked, sometimes not. Sometimes it worked, but I was typing blind "sudo reboot". Debian now seems to be stable and it still has the packages I wanted to upgrade 11.10 (last stable Ubuntu on my system) for: GIMP 2.8, LibreOffice 4.0. I hope I finally found stability again. I was wondering if indeed Windows was the only way out of instability mess. I'll keep my fingers crossed over the coming days.

---

### Post by TeamRocket1233c on 2013-10-02
Wheezy/Stable and Jessie/Testing are good ways to transition from Ubuntu to Debian, but since I've been at the Linux game for a while now, and have run Ubuntu and Fedora on metal, and CentOS and OpenSUSE Factory in Vbox in the past, and am currently running Archbang on the metal, my current VMs are Debian Sid and Fedora 20 Alpha, I'd say I'm a bigger fan of Archbang and Debian Sid because rolling release and software recency, and because they don't really suffer from bitrot all that much, meanwhile one of my beefs with Ubuntu, as well as Wheezy and CentOS, and OpenSUSE Standard and LTS, is they tend to suffer from a lot of bitrot because they don't move all that much, and I prefer to have a distro that moves a lot, hence Arch/Archbang, Sid, Jessie, Factory, or Fedora.

Also, I'm generally a bigger fan of the rolling release model that Arch/Archbang, Debian Sid, and OpenSUSE Tumbleweed use, and never having to upgrade, than I am of the standard release model that Ubuntu, Jessie, Wheezy, OpenSUSE Standard, OpenSUSE LTS, OpenSUSE Factory, and Fedora use, and having to do frequent system upgrades, as I imagine having to upgrade every few months/years would get pretty annoying longterm.

Now if one was willing to risk their system, and deal with constant breaks, Fedora Rawhide is on a rolling release model, technically, however you gotta have some serious patience to deal with it because it does break like crazy, meanwhile my Debian Sid VM has been pretty stable so far, as well as my Archbang install on the metal.

Ran Fedora 19 for a while with the [FONT=lucida console]updates-testing[/FONT] and the [FONT=lucida console]rpmfusion-nonfree-updates-testing[/FONT] and [FONT=lucida console]rpmfusion-free-updates-testing [FONT=verdana]repos[/FONT][/FONT] for a while, in addition to the [FONT=lucida console]updates[/FONT] and [FONT=lucida console]rpmfusion-free-updates[/FONT] and [FONT=lucida console]rpmfusion-nonfree-updates [FONT=verdana]repos[/FONT][/FONT], finally broke YUM one day, so I quit that during my time with Fedora on the metal, however I'm currently using the [FONT=lucida console]testing[/FONT] and [FONT=lucida console]community-testing [FONT=verdana]repos[/FONT][/FONT] in Archbang, no problems yet.

As for package managers, although I really, really like Fedora's YUM and OpenSUSE's ZYPper, I prefer Arch's Pacman or Debian's APT, and I use the Yaourt wrapper for Pacman, which allows easy AUR access, and the Aptitude front-end for APT, as IMO, it's better than apt-get. Hadn't really messed with Mageia yet.

---

### Post by mamamia88 on 2013-10-03
Damn i only tried the xfce version and now you really make me want to try the gnome-shell version.   But I'm using Ubuntu for the more up to date radeon drivers on my htpc.

---

