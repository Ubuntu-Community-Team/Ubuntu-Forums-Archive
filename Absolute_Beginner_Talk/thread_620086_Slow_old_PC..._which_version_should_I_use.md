---
title: "Slow old PC... which version should I use?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by brielp on 2007-11-22
Hi, I installed Ubuntu 7.10 on an HP Satellite Pro 4600 with 128MB memory, and it is SLOW. I believe that it continuously swaps to disk, so I shoud probably 'downgrade' some features.

My questions... should I:
- keep Gome and unselect some new features that take up resources?
- keep Ubuntu and switch to Xfce
- reinstall my PC with Xubuntu?

What is the difference between Xubuntu and Ubuntu with Xfce?

As you can see, I'm a novice :)

Thanks to anyone who can answer these questions!

---

### Post by philinux on 2007-11-22
Ubuntu needs minimum 256m of ram, this is why its slow.

Either fit more ram or use xubuntu I would think.

---

### Post by zvacet on 2007-11-22
> What is the difference between Xubuntu and Ubuntu with Xfce?

There is no difference.Xubuntu is Ubuntu with  Xfce.Read [this](http://www.psychocats.net/ubuntu/xubuntu).After installing of Xfce remove Gnome with this command

```
sudo aptitude remove ubuntu-desktop
```

---

### Post by kleo skywalker on 2007-11-22
Maybe you could try Xubuntu or Fluxbuntu or some other lighter distro?
There are lots of threads about this and related topics on this forum, such as [this one]("http://ubuntuforums.org/showthread.php?t=617666").

---

### Post by exploder on 2007-11-22
I am surprised that you were able to install Ubuntu 7.10 with only 128 mb of RAM! 

I would suggest fluxbuntu but the final has not been released yet. Fluxbox uses very little resources and would make your machine run fast. The beta may interest you, they have done an excellent job refining the look. The beta is only available as an install CD. 

Mepis AntiX would be worth a try.. AntiX gives you a choice of Fluxbox and IceVM. AntiX only used 40 mb of RAM on my test system!

Unfortunately Xubuntu uses quite a bit of memory because although Xfce is the desktop environment it uses many Gnome packages for functionality. 

There is also a PCLinux edition that uses Fluxbox, I think it is TinyME. TinyME has a very refined look and lean applications. I tested TinyME a while back and I must say that they have paid great attention to detail for the release.

Have a look at some of these and see what you think. Fluxbot is very light and customizable and would give your system the speed you are after.

---

### Post by xpod on 2007-11-22
You could always have a go at a minimal installation.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

You could always try some of the many lightweight distros out there, that would run just fine on that spec i think.I know Puppy LInux runs just fine with 128Mb.
Hell, Puppy runs fine *from* that amount of memory never mind with it:)

We have an old DellC600 that i have either 256Mb or 128Mb for and even that thing has run normal Ubuntu with just the 128Mb ......painfully slow of course.
Plus i created the swap prior to installing with an alternate cd.

It currently has a minimal XFCE installation on it.......as per the link above but i find Puppy still  boots & runs a lot faster.In fact i`m wrong,it currently has Freenas on it still.

In fact i cant remember what the hell`s on the thing just now:-k

---

### Post by brielp on 2007-11-22
Okay... just one question: say that I install Xubuntu, does the version matter? I mean, is 7.10 slower than 7.4 and so on?

(Like Microsoft :)   - sorry)

---

### Post by philinux on 2007-11-22
Back up any important stuff. Move your home to a separate partition and try out xubuntu.

7.1 is better at hardware detection and configuring display drivers.

---

### Post by brielp on 2007-11-22
Again... is installing XUBUNTU from scratch any different from doing what I just did - meanwhile :) which is installing XUBUNTU desktop on Ubuntu, and switching to that interface?

In other words, is the selection of applications any different? (e.g. less memory demanding, or anything)

---

### Post by overdrank on 2007-11-22
> **brielp said:**
> Again... is installing XUBUNTU from scratch any different from doing what I just did - meanwhile :) which is installing XUBUNTU desktop on Ubuntu, and switching to that interface?

In other words, is the selection of applications any different? (e.g. less memory demanding, or anything)

HI and maybe this link will help
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by tdrusk on 2007-11-22
If you want a fast os run puppy linux

---

