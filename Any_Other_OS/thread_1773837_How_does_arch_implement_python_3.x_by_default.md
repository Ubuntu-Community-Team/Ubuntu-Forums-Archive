---
title: "How does arch implement python 3.x by default?"
date: 2011-06-02
forum: Any Other OS
---

### Post by user1397 on 2011-06-02
How does arch do have python 3.x as the default python version currently?  Does that not break anything?  If not, why aren't other distributions doing it?

---

### Post by snowpine on 2011-06-02
Arch is a "rolling release" distribution that provides the latest software, and for most Arch users, it is second nature to read the [news]("http://www.archlinux.org/news/python-is-now-python-3/"), [wiki]("https://wiki.archlinux.org/index.php/Python"), and [forum]("http://bbs.archlinux.org/") before a major upgrade.

---

### Post by jeffathehutt on 2011-06-02
Arch actually has both versions.  python refers to Python 3, and python2 is Python 2.  So, you can use python2 if you still need the old version.  All of the programs in the official repos were modified to represent the change.;)

---

### Post by user1397 on 2011-06-03
Ah, I see. So you pretty much have to install both currently?

---

### Post by handy on 2011-06-03
I don't believe that you "have to" install both. But if you go with only 3, you will have problems, until all of the packages that rely on python2 have been made python3 compatible.

It is one of those problems that gets better everyday.

I've been running both versions for quite some time & there has been no problems whatsoever.

---

### Post by del_diablo on 2011-06-03
Define "install" please :P

---

### Post by user1397 on 2011-06-03
Ah, got it.  Weird that arch is always so up to date with its packages and yet it still uses grub 1..

---

### Post by handy on 2011-06-04
> **ubuntuman001 said:**
> Ah, got it.  Weird that arch is always so up to date with its packages and yet it still uses grub 1..

At this stage GRUB2 is offered as a choice rather than the default:

[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by user1397 on 2011-06-06
> **handy said:**
> At this stage GRUB2 is offered as a choice rather than the default:

[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)The one thing I can't find in that wiki page is why they still keep version 1 as the default, that's what I'm curious about.

---

### Post by snowpine on 2011-06-06
> **ubuntuman001 said:**
> The one thing I can't find in that wiki page is why they still keep version 1 as the default, that's what I'm curious about.

Probably because the most recent installation media is over a year old: [http://www.archlinux.org/news/201005-snapshots-less-is-more/](http://www.archlinux.org/news/201005-snapshots-less-is-more/)

---

### Post by mips on 2011-06-07
> **snowpine said:**
> Probably because the most recent installation media is over a year old: [http://www.archlinux.org/news/201005-snapshots-less-is-more/](http://www.archlinux.org/news/201005-snapshots-less-is-more/)

A new 'release' is hopefully around the corner. I see the latest testing iso was released just yesterday so they are busy with it.
[http://releng.archlinux.org/isos/](http://releng.archlinux.org/isos/)




.

---

### Post by handy on 2011-06-08
My Arch install is now over 3 years old. When the Arch install .iso does come with GRUB2, it certainly won't be any incentive for me to convert my 2 Arch systems. 

I have no need of the GRUB2 enhancements. 

Deprecation is fine by me, it is probably something that you learn to live with as you get older. ;)

---

### Post by mips on 2011-06-09
> **handy said:**
> My Arch install is now over 3 years old. When the Arch install .iso does come with GRUB2, it certainly won't be any incentive for me to convert my 2 Arch systems. 


I just want a new .iso so I can go back to Arch ;)

---

### Post by handy on 2011-06-09
> **mips said:**
> I just want a new .iso so I can go back to Arch ;)

Can't you use your old .iso & do a net install?

---

### Post by mips on 2011-06-09
> **handy said:**
> Can't you use your old .iso & do a net install?

Yes but I'm being weird, I want the new one. Apparently you also have to go through a couple of pacman updates/tweaks to get to current. Not that I have any experience of that, just heard something along those lines and it won't be a problem. Maybe I should look at the latest releng iso...

Nice think is they now have dual 32/64-bit iso images so I only have to download one for my both my 32 & 64 bit machines.

I just want a new shiny precious :evil: :biggrin:

---

### Post by screaminj3sus on 2011-06-09
> **mips said:**
> I just want a new .iso so I can go back to Arch ;)

Just download the net iso. That's what I did. Just make sure you choose a mirror thats up to date and you will have all the very latest packages during the install :)

Regarding pacman "updates/tweaks" all I had to do was run pacman-db-upgrade after pacman was updated. Very easy. (besides all the normal pacman configuration you do during install, setting up mirrors and such)

---

### Post by mips on 2011-06-09
> **screaminj3sus said:**
> Just download the net iso. 

I already have it.

---

### Post by sisco311 on 2011-06-09
I usually (re-)install Arch from Ubuntu:
```
pacman -S base -r /newarch
```

---

### Post by manzdagratiano on 2011-06-10
> **handy said:**
> My Arch install is now over 3 years old. When the Arch install .iso does come with GRUB2, it certainly won't be any incentive for me to convert my 2 Arch systems. 

I have no need of the GRUB2 enhancements. 

Deprecation is fine by me, it is probably something that you learn to live with as you get older. ;)

Actually the single-most thing I like about grub2 compared to grub-legacy is that combined with os-prober, it autodetects all OSes on the machine and therefore eliminates the need for doctoring a menu.lst.

---

### Post by handy on 2011-06-11
> **manzdagratiano said:**
> Actually the single-most thing I like about grub2 compared to grub-legacy is that combined with os-prober, it autodetects all OSes on the machine and therefore eliminates the need for doctoring a menu.lst.

I'm sure that GRUB2 has many advantages over GRUB, it is just that I don't have the need for any of them. :)

---

