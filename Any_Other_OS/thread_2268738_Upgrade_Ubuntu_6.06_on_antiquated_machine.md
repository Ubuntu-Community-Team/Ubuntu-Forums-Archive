---
title: "Upgrade Ubuntu 6.06 on antiquated machine?"
date: 2015-03-11
forum: Any Other OS
---

### Post by Cubytus on 2015-03-11
Hello there, 

this post os to ask for a simple way to give my father a way to upgrade his antiquated 6.04 Ubuntu installation running on a 2001-era computer. It's so old that repositories have been pulled offline, and he probably doesn't receive security nor software upgrades anymore, maybe contributing to increasing bugs in the way his email is displayed.

I'd like to know:
[LIST=1]
[*]Which release of Ubuntu would still be able to run on this never-upgraded machine (Please, nothing that would remove the classical three-button top bar. He's very GUI-oriented and wouldn't find its way.) 
[*]If its matching repositories are still online at a speed sufficient for frustration-free updates
[*]And how to upgrade to that specific release through the Internet. Of course a **dist-upgrade** can't work with that requirement.
[/LIST]

Any idea, save of buying a new computer?

---

### Post by mörgæs on 2015-03-11
Don't upgrade, but a fresh install of Ubuntu Mate is a good option.

Before erasing 6.04 please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

More info in the link in my signature.

---

### Post by The Cog on 2015-03-11
I agree.
Copy his data files off onto a USB stick or disk so you can copy them back later - to keep the permissions you could perhaps tar them up or use a linux filesystem on the usb drive.
It would help if you can find the firefox config folder to retain the bookmarks etc. (~/.firefox or ~/.config/firefox perhaps). 

Ubuntu looks very different now and he probably won't like the change. So mate, which is a continuation of Gnome2 that Ubuntu used, is a good choice.

---

### Post by sudodus on 2015-03-11
I'm afraid that a computer from 2001 needs something ultra-light, lighter than any current Ubuntu family operating system (even lighter than Lubuntu).

I suggest that you download and try (without installing), booting from CD the following linux distros:

***Wary Puppy***, ***TahrPup*** and ***Tiny Core***. At least one of these would probably work, but looks different.

If your father really needs the old style (like Ubuntu 6.04) and a current, supported, operating system, I'm afraid that he would need a newer computer, not more than 10 years old, with at least Pentium 4 and 512 MB RAM (better with 1 MB RAM). Then the ***Mate*** desktop environment would suit well as suggested by *mörgæs* in post #2.

See this link: 'Bringing [old hardware]("http://ubuntuforums.org/showthread.php?t=2130640") back to life'.

---

### Post by yancek on 2015-03-11
Posting some details on the old hardware (CPU, graphics, RAM) would help someone make suggestions.  A couple of other systems which might run on older hardware are AntiX and Slitaz but they will be very different from Ubuntu.

---

### Post by grahammechanical on 2015-03-11
apt-get dist-upgrade does not upgrade one release of Ubuntu to the next release. And there is not a simple way to upgrade to 6.10 because the repositories are closed. The next supported version of Ubuntu is 12.04 and that reaches end of life in two years time. So, your father will have to upgrade through several unsupported versions to get to a supported version of Ubuntu and each upgrade will bring with it the risk of everything being messed up. I know I tried it. As an experiment I installed 9.04 and tried upgrading to 12.04. I got as far as 11.04 when everything became so messed up as to make the OS unusable.

Ubuntu has moved with the times and there comes a time when some hardware becomes obsolete in regards to modern Linux operating systems. That video adapter is most likely no longer supported by a proprieatary video driver. Does that motherboard allow booting from a CD drive or a USB port? Maybe not. The Ubuntu install image is now too large to fit onto a CD disc. We have to use a DVD disc.

There are options but they start with backing up the data and doing a new installation with a Linux distribution more suited to that hardware. There is a saying - you cannot teach an old dog new tricks. But we are people not dogs. We can learn new things and continual learning helps keep the mind active in old age. I do not have children but I would be very upset if a child of mine thought that at the age of 67 I was past learning anything new.

Regards.

---

### Post by Impavidus on 2015-03-12
It's 6.0**6**. Dapper Drake was the only Ubuntu release ever to be delayed by two months, and it has been unsupported (no security updates) for 6 years.

My father has a computer stil happily running Xubuntu 14.04 on which I originally installed Ubuntu 6.06, but it's a bit younger than your father's computer (2005 or thereabouts) and was quite powerful for that time (powerful ATI graphics, has always been running on open source drivers). Depending on the exact specs, your father's computer might still be (just) able to run a supported Lubuntu, or else a lighter distro.

In any case, upgrading is not an option. Upgrading 6.06&#8594;8.04&#8594;10.04&#8594;12.04&#8594;14.04 (the light 12.04 flavours are no longer supported, or nearly so) could take days and because so many things have changed it would take a long time to reconfigure everything. A fresh install is faster and more likely to succeed.

There are destop environment looking similar to the one of 6.06, but most other programs will also have changed their GUIs.

There is a time when computers get really obsolete and you have to ask yourself whether it's worth the effort to squeeze another two years out of the old hardware.

---

### Post by Cubytus on 2015-03-25
First, thanks to all for your answers. From the first tests, it seems that MATE is still too resource-heavy on this machine. I temporarily put back the old hard drive. ***Tiny Core*** seems too radical of a change. I will ***try Slitaz***, but ***TahrPup*** seems interesting because of its full compatibility with Ubuntu.

I am longing for an OS that would be as light as Windows XP and as secure as modern Linux distros. It seems applications and OSes get heavier and heavier as years pass by, without really doing much more than their older siblings.

---

### Post by sudodus on 2015-03-25
Maybe the heavier OSes do more, have to do more, because the computers and the web-sites get more complicated. A lot of today's computing power is used for eye candy :-)

***ToriOS*** might be what you are looking for. It is not released yet, but beta tested right now, [http://torios.net/](http://torios.net/)

But ***TahrPup*** is released, and really worth trying.

---

### Post by egalvan on 2015-03-25
> **Cubytus said:**
> Hello there, 

Any idea, save of buying a **_new_** computer?

If by "new" you will accept "refurbished" or "used", then you have many more options.

I have purchased a "store-bought" new computer just once in the past 35+ years...
(it was a Radio Shack TRS-80)

Other than that, I have always bought refurbished, used, even fished out of trashcans...
(a laptop that had a dead battery and a ton of dust)

My main machines right now are:
Dell 745 (8gb RAM, Core 2 Duo @2.8gHz, 160GB drive)
Dell 780 (8gb RAM, Core 2 Duo @3gHz, 120gb SSB boot, and 1TB spinner for data)
Both run Win7 Pro 64bit, and the 780 dual-boots Ubuntu 12.04..
neither is "new"...

Dell has this for sale right now...(25-March-2015)

"Refurbished: Dell off-lease OptiPlex 745 Small Form Factor Desktop PC
 [Microsoft Authorized Recertified-One year Warranty]

    Core 2 Duo 1.8GHz
    2GB 80GB HDD
    Windows 7 Home Premium
    No Screen
    Intel GMA 3000

$84.99 Free Shipping"


A basic machine to be sure, but fully capable of running Win7 or Ubuntu.

Mom&Pop computer stores and computer clubs are another source of low-cost used stuff....

---

### Post by Cubytus on 2015-03-25
I second that on web-sites becoming steadily heavier. But I don't think modern OS do more than older ones.

But the "used" computer option is a big no-no. Too many of them came through this house, only to fail within weeks, but more often requiring constant maintenance, fiddling with settings, an hour at a time whenever the wifi went down just because they couldn't power the USB dongle properly. But I'll remind him of factory-refurbished machines, which I perceive as more likely to work than those from dusty shops.

I don't know where you go fishing to find Core2Duo in the trashcans, but what I find here are, at most, old Semprons and first-generation P4. And there are no "Corner Chinese" computer stores in my city anymore, nor any computer club that I know of. I guess it's pretty much different from what can be found in the US. But thanks for the suggestions.

---

### Post by Cubytus on 2015-03-26
There's no locale setting on ToriOS? Or am I mistaken?

---

### Post by Topsiho on 2015-03-26
You might try live-DVD's with lighter versions of Ubuntu, such as Lubuntu or Xubuntu, or of Mint, or so. Download their ISO's and burn them on a USB-stick or on a DVD. Keep in mind that on a liveDVD or USB the speed is always slower than after an install on the hard disk.
The latest .ubuntu LTS versions are 14.04.

I DO think it's fun to keep such an old computer alive as long as possible :)

You may run into pae-problems (physical address extension), if you want to know more about these, try google, or someone on this forum may comment on this ...  :). (Some) later Ubuntu versions do not support non-pae processors.

Topsiho

---

### Post by sudodus on 2015-03-26
> **Cubytus said:**
> There's no locale setting on ToriOS? Or am I mistaken?

The live session is very limited concerning locale, but you can select keyboard in a terminal window (and it will be set globally), for example

```
setxkbmap se
```

During installation, you are offered to select continent and language, but it is still very simple.

---

### Post by Elfy on 2015-03-26
Given that this has moved on to installing anything at all - none of which are Ubuntu Official flavours

*Thread moved to **Any Other OS**.*

---

### Post by Cubytus on 2015-03-26
> **sudodus said:**
> The live session is very limited concerning locale, but you can select keyboard in a terminal window (and it will be set globally), for example

```
setxkbmap se
```

During installation, you are offered to select continent and language, but it is still very simple.Locale goes beyond keyboard map. At installation time, I think it did ask me for the locale, but left it at English US anyways. It is a beta after all, but…

---

