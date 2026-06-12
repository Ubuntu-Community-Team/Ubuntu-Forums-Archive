---
title: "debian 6.0 xfce ---&gt; very fast"
date: 2012-03-22
forum: Any Other OS
---

### Post by husnos on 2012-03-22
I've recently installed debian 6 - xfce edition next to my ubuntu installation. The speed and response is amazing. Memory usage upon logging in is only 93MB.

The only problem was installing non-free wireless driver, which was straightforward since the drivers are packaged as .deb on the distro's website. Everything else worked out of the box. I have compiz enabled and gdesklet for weather.

The only downside, you lose the convenience of unity. However, awn can be used instead.

And the "200-lines" patch is not in debian 6 kernel. But I have not noticed real difference in speed and responsiveness.

Give it a try.

---

### Post by Gremlinzzz on 2012-03-22
what the System requirements :popcorn:
you know like 
processor
MB RAM
disk space
Graphics card :popcorn:

---

### Post by Warpnow on 2012-03-22
Debian Xfce is *very* lightweight compared to Xubuntu.

---

### Post by Roasted on 2012-03-22
This makes me wonder if I should revert my file server to it, mostly because, why not?

Does Debian have an LXDE variant? I bet that's be crazy fast too.

---

### Post by Paqman on 2012-03-22
> **husnos said:**
> 
And the "200-lines" patch is not in debian 6 kernel. But I have not noticed real difference in speed and responsiveness.


That's because that patch only made a difference under certain specific (and fairly unusual) workloads anyway.

---

### Post by Sector11 on 2012-03-22
> **Roasted said:**
> This makes me wonder if I should revert my file server to it, mostly because, why not?

Does Debian have an LXDE variant? I bet that's be crazy fast too.

No, Debian doesn't but LXDE is in the Debian repos so it can be installed.

Want something even lighter:  [#! CrunchBang v10]("http://crunchbanglinux.org/") based on Debian Stable & OpenBox.  NO desktop just OpenBox. Less bling, less eyecandy, more speed and power for you to use.

---

### Post by husnos on 2012-03-23
> **Roasted said:**
> This makes me wonder if I should revert my file server to it, mostly because, why not?

Does Debian have an LXDE variant? I bet that's be crazy fast too.

yes. the xfce cd is actually for both xfce and lxde install. while installing, it will ask you to choose between xfce and lxde. you can find this special cd in the download mirrors if you scroll down.

i have also downloaded .deb package of latest libreoffice and it installed with no problems. also, chrome .deb from google.

flash palying is working very good. i think better than ubuntu because my laptop is from 2006.

---

### Post by husnos on 2012-03-23
> **Gremlinzzz said:**
> what the System requirements :popcorn:
you know like 
processor
MB RAM
disk space
Graphics card :popcorn:

i dont know exactly but should be low. i am using toshiba m400 released around 2006.

---

### Post by husnos on 2012-03-23
> **Sector11 said:**
> No, Debian doesn't but LXDE is in the Debian repos so it can be installed.

Want something even lighter:  [#! CrunchBang v10]("http://crunchbanglinux.org/") based on Debian Stable & OpenBox.  NO desktop just OpenBox. Less bling, less eyecandy, more speed and power for you to use.

actually, main reason i install major distros is because i dont know how to trust distros made by unknown people or group of people. at least debian or ubuntu organization seem to be legit. i dont have to worry about backports and spyware.

i dont mean to flame those sping off distros and discredit their developers. i am trying to figure out how to properly trust such distros especially when i am typing my social security and credit card info. very serious business.

---

### Post by BrokenKingpin on 2012-03-23
> **Roasted said:**
> 
Does Debian have an LXDE variant? I bet that's be crazy fast too.
Just use the netinstall and then manually install it afterwards. That being said, with how fast Xfce is under Debian, I am sure LXDE would not seem all that much faster.

---

### Post by Roasted on 2012-03-23
> **BrokenKingpin said:**
> Just use the netinstall and then manually install it afterwards. That being said, with how fast Xfce is under Debian, I am sure LXDE would not seem all that much faster.

A few searches on Debian forums reveals that their overall opinion is XFCE is a nicer experience. They say that LXDE is nice too, but it only shaves off about 10 MB of RAM max versus XFCE, and that XFCE is a bit more integrated to the overall experience, hence why they lean that way.

It sounds like XFCE would be the way to go.

The one thing that I never understood is Debian's download site. I mean, what is this?

[http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/](http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/)

What are the differences? Where is the XFCE variant? Am I having a durp durp moment or is this kind of disorganized?

---

### Post by blueturtl on 2012-03-23
> **Roasted said:**
> ...The one thing that I never understood is Debian's download site. I mean, what is this?

[http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/](http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/)

What are the differences? Where is the XFCE variant? Am I having a durp durp moment or is this kind of disorganized?

> **BrokenKingpin said:**
> Just use the netinstall and then manually install it afterwards. That being said, with how fast Xfce is under Debian, I am sure LXDE would not seem all that much faster.

Actually the Debian installer let's you choose the default desktop environment. Just select the 'Advanced option' from the install boot menu and pick KDE, Xfce, or LXDE.

edit:

CD1 ISO = base install CD that copies the default install files off the CD.
netinst ISO = minimal system files on disk, rest retrieved from the web
businesscard ISO = pretty much only houses the installer, all packages are retrieved from the repositories during install

the business card iso is my favorite, because it automatically downloads the most up-to-date packages, so no need to start downloading updates the first thing after installing.

---

### Post by husnos on 2012-03-23
> **BrokenKingpin said:**
> Just use the netinstall and then manually install it afterwards. That being said, with how fast Xfce is under Debian, I am sure LXDE would not seem all that much faster.

debian already provides a xfce-lxde CD

specifically,

debian-6.0.4-i386-xfce+lxde-CD-1.iso

---

### Post by husnos on 2012-03-23
> **blueturtl said:**
> Actually the Debian installer let's you choose the default desktop environment. Just select the 'Advanced option' from the install boot menu and pick KDE, Xfce, or LXDE.

edit:

CD1 ISO = base install CD that copies the default install files off the CD.
netinst ISO = minimal system files on disk, rest retrieved from the web
businesscard ISO = pretty much only houses the installer, all packages are retrieved from the repositories during install

the business card iso is my favorite, because it automatically downloads the most up-to-date packages, so no need to start downloading updates the first thing after installing.

yes

additionally, CD2 and onwards are for packages. so, the only difference is in CD1 because it provides the base system with different desktop environments

---

### Post by Warpnow on 2012-03-24
> **Sector11 said:**
> No, Debian doesn't but LXDE is in the Debian repos so it can be installed.

Want something even lighter:  [#! CrunchBang v10]("http://crunchbanglinux.org/") based on Debian Stable & OpenBox.  NO desktop just OpenBox. Less bling, less eyecandy, more speed and power for you to use.

I had crunchbang and debian xfce installed side by side and debian xfce used less ram and cpu power consistently. It may not be a fair comparison though because crunchbang is much more polished and modified after the fact, whereas debian xfce is literally just normal xfce no changes. Still, though, for out of the box resources debian xfce was more lightweight for me.

That said, crunchbang is still an excellent distribution. People just don't realize how lightweight xfce is because their experience is xubuntu.

---

### Post by BrokenKingpin on 2012-03-24
> **Warpnow said:**
> I had crunchbang and debian xfce installed side by side and debian xfce used less ram and cpu power consistently.

I really find this hard to believe, especially for ram usage. Don't get me wrong, I am an Xfce user and I know it can be very good on resources, but not as good as openbox (at the cost of functionality). And what crunchbag adds over debian I don't think would bloat it that much.

---

### Post by Warpnow on 2012-03-24
> **BrokenKingpin said:**
> I really find this hard to believe, especially for ram usage. Don't get me wrong, I am an Xfce user and I know it can be very good on resources, but not as good as openbox (at the cost of functionality). And what crunchbag adds over debian I don't think would bloat it that much.

[http://img203.imageshack.us/img203/4032/20091014004137800x600sc.png](http://img203.imageshack.us/img203/4032/20091014004137800x600sc.png)

And crunchbang brings in alot of dependencies for the applications it ships with. You may end up installing those anyway in a raw debian install, or you may not. The apps you install really going to have more of an affect on the usage than the WM/DE in my opinion.

---

### Post by BrokenKingpin on 2012-03-24
> **Warpnow said:**
> [http://img203.imageshack.us/img203/4032/20091014004137800x600sc.png](http://img203.imageshack.us/img203/4032/20091014004137800x600sc.png)

Seeing that icon theme brings me back about a more simple time :P... awesome.

---

### Post by Warpnow on 2012-03-25
> **BrokenKingpin said:**
> Seeing that icon theme brings me back about a more simple time :P... awesome.

The sad thing is that is the default for Xfce 4.6, which is only 1 release ago...hehe...

Yeah, the default xfce stuff is all pretty bad. You've gotta change the theme/icon set once you install it.

---

### Post by Rodney9 on 2012-03-25
On my Laptop with Pentium Dual Core CPU and 1GB Ram I have Xubuntu 11.10 64bit, can't see much difference - mem 16% cpu 1%

Rodney

---

### Post by keithpeter on 2012-03-25
> **Warpnow said:**
> Yeah, the default xfce stuff is all pretty bad. You've gotta change the theme/icon set once you install it.

Hello Warpnow and all

Looks way better than the Citrix thin client version of Windows I have just been logged into for a bit of work :twisted:

Any suggestions on how to jazz XFCE up so it looks nice for younger people (blackberry weilding teenagers)?

Is it possible to use compositing with XCFE? Any pointers? I find Compiz results in smoother windows movement with nvidia proprietary drivers than does 'no effects' in the old Gnome.

---

### Post by husnos on 2012-03-25
> **keithpeter said:**
> Hello Warpnow and all

Looks way better than the Citrix thin client version of Windows I have just been logged into for a bit of work :twisted:

Any suggestions on how to jazz XFCE up so it looks nice for younger people (blackberry weilding teenagers)?

Is it possible to use compositing with XCFE? Any pointers? I find Compiz results in smoother windows movement with nvidia proprietary drivers than does 'no effects' in the old Gnome.

i have compiz enabled with default xfce 4.6 that comes with debian 6. seems to work fine. very responsive.

---

### Post by philinux on 2012-03-25
Moved to Other OS/ Distro talk.

---

### Post by keithpeter on 2012-03-25
> **husnos said:**
> i have compiz enabled with default xfce 4.6 that comes with debian 6. seems to work fine. very responsive.

Hello husnos

Yes, works fine on nvidia proprietary drivers with Ubuntu 12.04 and just the xfce4 desktop metapackage installed, not the full xubuntu (although I'm sure it would work with that as well).

I've found that XFCE's own compositor makes window moving smooth, and so I'm using that.

Thanks

PS: I'm discussing XFCE on *Ubuntu*.

---

### Post by husnos on 2012-03-25
> **keithpeter said:**
> Hello husnos

Yes, works fine on nvidia proprietary drivers with Ubuntu 12.04 and just the xfce4 desktop metapackage installed, not the full xubuntu (although I'm sure it would work with that as well).

I've found that XFCE's own compositor makes window moving smooth, and so I'm using that.

Thanks

PS: I'm discussing XFCE on *Ubuntu*.

you are welcome

i think you would be using 4.8 on ubuntu. it is better than xfce 4.6. 

> 
Xfce 4.8 is our attempt to update the Xfce code base
[http://www.xfce.org/about/news/?post=1295136000](http://www.xfce.org/about/news/?post=1295136000)


xfce 4.8 has been backported  officially and unofficially to debian 6, but it will make the system less stable. so i will stick with 4.6 until next debian release. i still have ubuntu for a more up to date experience.

---

### Post by collisionystm on 2012-03-25
> **husnos said:**
> I've recently installed debian 6 - xfce edition next to my ubuntu installation. The speed and response is amazing. Memory usage upon logging in is only 93MB.

The only problem was installing non-free wireless driver, which was straightforward since the drivers are packaged as .deb on the distro's website. Everything else worked out of the box. I have compiz enabled and gdesklet for weather.

The only downside, you lose the convenience of unity. However, awn can be used instead.

And the "200-lines" patch is not in debian 6 kernel. But I have not noticed real difference in speed and responsiveness.

Give it a try.


This is why God invented CrunchBang

---

