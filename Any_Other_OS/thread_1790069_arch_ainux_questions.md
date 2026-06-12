---
title: "arch ainux questions"
date: 2011-06-24
forum: Any Other OS
---

### Post by Starks on 2011-06-24
so, how is arch?

i have few questions

1. is it pure rolling or an afterthought like fedora rawhide, opensuse tumbleweed/factory, and debian sid/experimental?

2. how does the AUR compare to PPAs and YUM repos?

3. will i be able to reuse my /home and will permissions/ownerships be updated?

4. will everything just work if i have no hardware requiring binary drivers?

---

### Post by uRock on 2011-06-24
Moved to *Other OS/Distro Talk*.

---

### Post by mips on 2011-06-24
1. Pure rolling
2. AUR is great but I have no experience with the others.

No experience with the rest so can't answer them.

My suggestion is to try it, like many you might just stick with it after that.

---

### Post by silex89 on 2011-06-24
I used Arch for two months:


[LIST=1]
[*]Yes, Arch is pure rolling, you can install the first release and after doing update, you'll be at the latest version no matter what.
[*]AUR... hmmm, I don't know how to compare them because I've never used YUM or PPA lol, but I can give you a brief description: AUR is the repository that the users put out, when you use AUR, the package is downloaded from the place that was created (let's say that we wanna install LibreOffice through AUR, the script begins to download it from [www.libreoffice.org]("http://www.libreoffice.org")) and it compiles it for you on the fly, resolving dependencies as soon as they appear, everything custom compiled for your kernel, of course.
[*]Yes, when you install Arch, by default, your home folder is landed in it's own partition.
[*]If the kernel modules for your hardware are there, you should have no problems....
[/LIST]
If you have more questions, I would highly recommend you to check out the [Beginners' Guide]("https://wiki.archlinux.org/index.php/Beginners%27_Guide") (Arch has a wonderful documentation :D)


Best Luck :)

---

### Post by Starks on 2011-06-24
so anyway, i'm looking for a bleeding edge linux desktop.

how is arch in that regard? if i want to use wayland, can i use wayland?

what about gentoo? a lack of binaries sounds maddening.

---

### Post by snowpine on 2011-06-24
> **Starks said:**
> so anyway, i'm looking for a bleeding edge linux desktop.

how is arch in that regard? if i want to use wayland, can i use wayland?

what about gentoo? a lack of binaries sounds maddening.

Arch is not "bleeding edge" in the sense that every package in Arch is a stable release. Arch also has a "testing" repo that is comparable to rawhide, tumbleweed, etc.

Wayland is still under development as far as I know. It is not going to be the default for Arch any time soon. However you can install it if you choose (Linux is all about choice). You can find more info in the Arch forums, for example: [https://bbs.archlinux.org/viewtopic.php?id=107499](https://bbs.archlinux.org/viewtopic.php?id=107499)

ps Have you ever checked out Sabayon? It is based on Gentoo but uses pre-compiled binaries.

---

### Post by mips on 2011-06-24
> **Starks said:**
> if i want to use wayland, can i use wayland?

[http://aur.archlinux.org/packages.php?O=0&K=wayland&do_Search=Go](http://aur.archlinux.org/packages.php?O=0&K=wayland&do_Search=Go)

---

### Post by doorknob60 on 2011-06-24
1. Pure rolling
2. I like AUR a lot better than PPAs, more organized and easier to find what you want
3. You should be able to, I've done it between Arch installs. When you create your new user, just set it to the right home folder and it will make sure it has the correct permissions as well.
4. Most likely, assuming the hardware works in other distros too

---

### Post by handy on 2011-06-24
Gentoo requires you to compile everything, the average time for a first install is about 3 days.

Old hands will manage to do it quicker than that.

Arch is a binary distro, though all of the packages in AUR have to be compiled.

As far as closed source binary blobs are concerned, the nVidia & AMD/ATi GPU drivers are of course available.

Everything you need to know is in the Arch Wiki, which basically sets the standard for others to follow. (Though the Gentoo Wiki is also very good.)

---

### Post by screaminj3sus on 2011-06-25
> **Starks said:**
> so, how is arch?

i have few questions

1. is it pure rolling or an afterthought like fedora rawhide, opensuse tumbleweed/factory, and debian sid/experimental?

2. how does the AUR compare to PPAs and YUM repos?

3. will i be able to reuse my /home and will permissions/ownerships be updated?

4. will everything just work if i have no hardware requiring binary drivers?
1. Arch is as pure rolling as you can get.
2. The AUR is great, I don't find it quite as nice as PPA's, but it works great, especially if you use something like yaourt or packer to make installing and updating aur packages pretty seemless. You can find pretty much any app in the aur.
3. Not Sure.
4. Should work fine if the hardware works in other distros. On my laptop the only driver I needed to install was xf86-intel-video.

---

### Post by NightwishFan on 2011-06-25
edit nvm

---

### Post by Starks on 2011-06-25
gave arch a try.

it's really more trouble than it's worth to get a stable, usable desktop.

took me over an hour to set up when your average distro takes me 15 minutes.

---

### Post by handy on 2011-06-25
> **Starks said:**
> gave arch a try.

it's really more trouble than it's worth to get a stable, usable desktop.

took me over an hour to set up when your average distro takes me 15 minutes.

I don't think that you know what you are talking about.

You can't possibly make such a statement after spending such a small amount of time with a system that functions so differently to what you are used to.

You don't really know how Arch works yet. Even though you have installed it. You have to live with Arch for a while to learn its ways, strengths & weaknesses.

What happens with Arch, is you spend the time to install it, then as the months go by you become more familiar with the way Arch works. As you learn more you are optimising & customising the system to suit you. 

In a year or two, or three, you find that you are so comfortable with the system which due to the rolling release upgrades you are in the position where you haven't had to scrap your system & do a reinstall from scratch, setting everything up again to how you like it. Many of the little tweaks that you have made get forgotten about because they can have been done years ago. :)

There are no sudden changes made to the most resent release (like Unity for instance) that you can't (at least easily) escape from. Your system is just how you want it to be.

This is the reason why I use Arch. I don't have any other crap on my system than what I put there. I can go straight to a config file & change it if need be. Which may sound like a pain to the mouse prone user, but in reality, there are only a few config files that you need to use to do most everything you will ever need to do on Arch. That in combination with the absolutely brilliant Arch wiki makes it all so easy.

In over 3 years of use, I have found Arch to be more stable than any other system I have used in over 26 years or computing.

I've found that what some may consider a loss, due to the time spent in what has to be, due to the nature of Arch, your setting up & acclimatisation to your new custom Arch system, you most certainly pick up with the rolling release upgrade system in combination with the simplicity of maintenance.

Many don't like the Arch way of computing, many prefer OSX. That's fine by me, whichever way we chose is valid, I'm grateful that we have so many choices. :)

---

### Post by screaminj3sus on 2011-06-26
> **Starks said:**
> gave arch a try.

it's really more trouble than it's worth to get a stable, usable desktop.

took me over an hour to set up when your average distro takes me 15 minutes.
You should have known how different arch is from ubuntu by just looking at the wiki, before you even got to the install stage lol.

The whole point of arch is you start with a totally minimal system and ONLY install what you want/need.

---

### Post by NightwishFan on 2011-06-26
I have nothing against arch but I feel the same way as starks.

---

### Post by handy on 2011-06-26
> **NightwishFan said:**
> I have nothing against arch but I feel the same way as starks.

Arch is pretty much the opposite to what Ubuntu is. So the Ubuntu forum is never going to be the place where the Arch way finds a great deal of acceptance.

There are very good reasons why we have so many different distros, let alone the other systems that exist. What one person thinks is the ducks guts, another considers to be poison... :popcorn:

***[edit:]** That wasn't me slipping in a jab at Ubuntu by the way. I think Ubuntu is great for many reasons. :)*

---

### Post by NightwishFan on 2011-06-26
I certainly agree.

---

