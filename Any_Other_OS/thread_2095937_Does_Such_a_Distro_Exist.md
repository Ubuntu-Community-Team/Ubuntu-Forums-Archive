---
title: "Does Such a Distro Exist?"
date: 2012-12-18
forum: Any Other OS
---

### Post by mamamia88 on 2012-12-18
I'm looking for something super stable like Debian Stable but require the latest version of google chrome and Xfce.  Everything else can be super old as long as it works.  Does something like this exist?

---

### Post by haqking on 2012-12-18
> **mamamia88 said:**
> I'm looking for something super stable like Debian Stable but require the latest version of google chrome and Xfce.  Everything else can be super old as long as it works.  Does something like this exist?


Every distro I have ever run, you can install Google chrome and xfce into all of them ;-)

---

### Post by dannyboy79 on 2012-12-18
why don't you just run debian stable and then install xfce dekstop. then the latest google chrome from their website?

---

### Post by mamamia88 on 2012-12-18
> **dannyboy79 said:**
> why don't you just run debian stable and then install xfce dekstop. then the latest google chrome from their website?

Cause when I checked packages debian stable was at 4.6 and I've become too used to the tiling in 4.10 and don't want to give it up?   Wouldn't pulling 4.10 in from sid cause potential breakage?

---

### Post by snowpine on 2012-12-18
Actually Debian still considers Xfce 4.10 to be "experimental" so correct, it is not recommended to mix stable and experimental software in a Debian system.

Give Arch a try; then you will get the latest stable versions of all applications with no hassle. Or Xubuntu 12.10, which has Xfce 4.10 and is Debian-based.

---

### Post by dannyboy79 on 2012-12-18
you could use a PPA so it only has stuff related to XFCE 4.10 in it and not screw up base debian stable packages.

sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
sudo apt-get update && sudo apt-get install xubuntu-desktop

I am using Xubuntu 12.04, not sure which Xfce is in there but I believe 12.10 Xubuntu uses Xfce 4.10

---

### Post by snowpine on 2012-12-18
^--- That is a great suggestion DannyBoy. Xubuntu 12.04 with Xfce PPA will give the OP Xfce 4.10 and years of long term support, an experience roughly comparable to Debian Wheezy.

---

### Post by Rangir on 2012-12-18
> **mamamia88 said:**
> I'm looking for something super stable like Debian Stable but require the latest version of google chrome and Xfce.  Everything else can be super old as long as it works.  Does something like this exist?

**#!**
the nimble desktop!
[http://crunchbang.org/](http://crunchbang.org/)
You can install Xfce very easily.
A very nice forum too!:p

---

### Post by mamamia88 on 2012-12-18
> **snowpine said:**
> Actually Debian still considers Xfce 4.10 to be "experimental" so correct, it is not recommended to mix stable and experimental software in a Debian system.

Give Arch a try; then you will get the latest stable versions of all applications with no hassle. Or Xubuntu 12.10, which has Xfce 4.10 and is Debian-based.

I'm on arch actually.  Had a kernel panic yesterday but i think i solved it.  Still considering my options though can't hurt.

---

### Post by snowpine on 2012-12-18
> **Rangir said:**
> **#!**
the nimble desktop!
[http://crunchbang.org/](http://crunchbang.org/)
You can install Xfce very easily.
A very nice forum too!:p

LOL, #! has terrible support for upgraded versions of anything. The lone developer is semi-notorious for not providing stability/security updates on a timely basis (for example, according to packages.crunchbang.org, there hasn't been a security update to the browser since March). Most of the core long-time users have switched to Debian or Arch. ;)

---

### Post by snowpine on 2012-12-18
> **mamamia88 said:**
> I'm on arch actually.  Had a kernel panic yesterday but i think i solved it.  Still considering my options though can't hurt.

99.9% of Arch users who switch to Debian find that the packages seem very outdated after their Arch experience.

---

### Post by LiamOS on 2012-12-18
I think Gentoo might be just what you're looking for, if you don't mind the effort of the install.
Gentoo defaults to 'stable'(Which is bloody stable), but you can easily install 'unstable' packages; the package manager will handle this gracefully, and let you know what other(if any) unstable dependencies you'll need.

---

### Post by mamamia88 on 2012-12-18
> **LiamOS said:**
> I think Gentoo might be just what you're looking for, if you don't mind the effort of the install.
Gentoo defaults to 'stable'(Which is bloody stable), but you can easily install 'unstable' packages; the package manager will handle this gracefully, and let you know what other(if any) unstable dependencies you'll need.

i'm on a netbook.  would take way too long to compile everything on the cpu

---

### Post by Rangir on 2012-12-18
> **snowpine said:**
> LOL, #! has terrible support for upgraded versions of anything. The lone developer is semi-notorious for not providing stability/security updates on a timely basis (for example, according to packages.crunchbang.org, there hasn't been a security update to the browser since March). Most of the core long-time users have switched to Debian or Arch. ;)

The lone developer is amply helped by a vibrant forum. #! is rock solid!
It never breaks. The long time users play with Arch, but are with #!. 
Arch forum? If you have steel nerves, you can ask a question there. Its full of we-know-all guys, who look down at others. Arch is not that good as you think. You update and you get into trouble. You upgrade, its even worse, you get a kernel panic and your installation is gone. 

Archbang came because of #!, but the original developer Will had left it. Anyway, nothing to beat #!, if it has to be a Debian, maybe SolusOS 2 A5. 

For a nimble distro, it has 214 guests online right now in the forums!

---

### Post by LiamOS on 2012-12-18
You'd probably be looking at about ~30 hours of compile time.

Alternatively you could compile on a faster machine for the netbook and then install on your netbook.

---

### Post by mamamia88 on 2012-12-18
> **LiamOS said:**
> You'd probably be looking at about ~30 hours of compile time.

Alternatively you could compile on a faster machine for the netbook and then install on your netbook.

don't have a faster machine and 30 hours is more than i'm willing to spend installing an os.  even arch took me an hour

---

### Post by snowpine on 2012-12-18
> **Rangir said:**
> The lone developer is amply helped by a vibrant forum. #! is rock solid!
It never breaks. 

Don't take my word for it, see for yourself:

[http://packages.crunchbang.org/statler/pool/main/](http://packages.crunchbang.org/statler/pool/main/)

No updates since April. Maybe #! is so "rock solid" it doesn't need security/stability patches like other distros? :) Furthermore, I have heard several incidents on #! forums of users mysteriously losing many GB's of data, enough to give me pause.

---

### Post by nothingspecial on 2012-12-18
This isn't a thread about whether or not the #! dev provides updates for the browser or not.

If you want to talk about that make another one.

---

### Post by snowpine on 2012-12-18
The OP's question was "I'm looking for a Debian Stable derivative that provides the latest Xfce and browser" (thus disqualifying #! in my opinion for the reasons I have explained), but please feel free to move my contributions into a separate thread if you feel the information I provided was off-topic.

---

### Post by claudecat on 2012-12-18
I'd check out Manjaro - it's Arch based but with its own repos for stability and comes with a very polished Xfce 4.10 in its most popular form (other DE ISOs are available too). Browsers (in truth all packages) stay up to date too and it's much easier to install than Arch.

---

### Post by mips on 2012-12-19
> **claudecat said:**
> I'd check out Manjaro - it's Arch based but with its own repos for stability and comes with a very polished Xfce 4.10 in its most popular form (other DE ISOs are available too). Browsers (in truth all packages) stay up to date too and it's much easier to install than Arch.

The 0.8.3 iso images will be release in 2 days or so if the OP is interested.

---

### Post by mamamia88 on 2012-12-19
> **claudecat said:**
> I'd check out Manjaro - it's Arch based but with its own repos for stability and comes with a very polished Xfce 4.10 in its most popular form (other DE ISOs are available too). Browsers (in truth all packages) stay up to date too and it's much easier to install than Arch.

not particularly interested in switching from arch to an arch based distro

---

### Post by jefsview on 2012-12-19
You can just use plain Debian and then add the Siduction XFCEnext repo to pull in Xfce 4.10 and the latest Thunar, and then uncomment the source out.

Google Chrome is easy; just download the .deb and use gdebi to install it; it adds the repo to the sources list automatically to stay updated.

Or you can just run Debian Sid, like Siduction or LinuxBBQ; being a current Arch user, you'll think Sid is a bit old.

I'm currently dual-booting Xubuntu 12.04 and a Debian sid with added Siduction repos.

---

