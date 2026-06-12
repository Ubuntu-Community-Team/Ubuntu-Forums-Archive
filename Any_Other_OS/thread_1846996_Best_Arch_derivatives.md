---
title: "Best Arch derivatives?"
date: 2011-09-20
forum: Any Other OS
---

### Post by Starks on 2011-09-20
Any good ones that deliver a better out-of-box experience?

---

### Post by valytzu01 on 2011-09-20
Read this:
[https://wiki.archlinux.org/index.php/Arch_Based_Distributions_(Active](https://wiki.archlinux.org/index.php/Arch_Based_Distributions_(Active))

---

### Post by kazuya on 2011-09-20
(1) For a very good user-friendly but Kde-based distro => Chakra Linux
Note that: chakra does not support gnome or other Desktop environments; And it is a little deviated from archlinux. Big plus is availability of a gui package manager like synaptic for debian-based distros.
 
(2) Archbang really the best in my opinion or preference to archlinux derivatives. It is pretty much archlinux, with the essential apps and interface you need to be fully functional. Cannot say enough good things about this distro. Like archlinux, no graphical package manager. But the cli pacman front-ends is very good and fast.
 
(3) Ctkarch - never used it, but heard about it as well. Minimalistic like archbang.
 
These are the three I know. Coming from kUbuntu or Mint, Chakra Linux might be the easiest bet. For someone seeking power to alter their install to nth degree, archbang or ctk-arch.

---

### Post by drawkcab on 2011-09-20
Not to hijack, but what are the options in terms of gui package management in arch?

---

### Post by sisco311 on 2011-09-20
> **drawkcab said:**
> Not to hijack, but what are the options in terms of gui package management in arch?

If you are considering to use Arch, then the Arch Wiki is your friend: [https://wiki.archlinux.org/index.php/Pacman_GUI_Frontends](https://wiki.archlinux.org/index.php/Pacman_GUI_Frontends)

---

### Post by Starks on 2011-09-20
Which front-ends are best for AUR usage?

I like Chakra as a base, but I want a firm gnome-friendly foundation for gnome-panel+docky+synapse.

---

### Post by mips on 2011-09-21
> **Starks said:**
> Which front-ends are best for AUR usage?


Packer

[https://wiki.archlinux.org/index.php/AUR_Helpers#packer](https://wiki.archlinux.org/index.php/AUR_Helpers#packer)
> Packer is a wrapper for pacman and the AUR. It was designed to be a simple and very fast replacement for the basic functionality of Yaourt. It has commands to install, update, search, and show information for any package in the main repositories and in the AUR. Use pacman for other commands, such as removing a package.
Website: [http://github.com/bruenig/packer](http://github.com/bruenig/packer)
Forum: [http://bbs.archlinux.org/viewtopic.php?id=88115](http://bbs.archlinux.org/viewtopic.php?id=88115)
Package: [https://aur.archlinux.org/packages.php?ID=33378](https://aur.archlinux.org/packages.php?ID=33378)
Wiki: [https://github.com/bruenig/packer/wiki](https://github.com/bruenig/packer/wiki)

[https://bbs.archlinux.org/viewtopic.php?id=88115&p=1](https://bbs.archlinux.org/viewtopic.php?id=88115&p=1)



.

---

### Post by el_koraco on 2011-09-21
> **Starks said:**
> 
I like Chakra as a base, but I want a firm gnome-friendly foundation for gnome-panel+docky+synapse.

Forget it, you'd have to pin a whole host of stuff to GTK2, and hack your way into keeping gnome-panel alive, since pretty much everything having to do with Gnome 2 is being dropped. You can't keep it bleeding edge and stick to gnome-panel. Consider XFCE as an alternative if that's up your alley, in which case Archbang will suit you just fine, but you'll have to migrate from Openbox to XFCE.

---

### Post by Starks on 2011-09-21
could i do gnome3 fallback with synapse and docky?

i'd lose applets, but i'd have some semblance of a panel, right?

---

### Post by el_koraco on 2011-09-21
You could, you just need to enable Metacity compositing for Docky (some obscure command in Gsettings, no doubt). But it's not even close to Gnome 2 plus Compiz. If I remember correctly, you're on Mint 11. Honestly, until the whole mess gets sorted out, why not just stay with that and carve up a Chakra/Arch(bang) partition and mess around with XFCE, or even Openbox or Compiz standalone? With some config file editing, and with using tint2/xfce4-panel + xcompmgr, xcompmgr-dana or cairo-compmgr if on Openbox, you can have a Gnome independent setup like you describe. 

Of course, the proper thing to do would be to use a tiler...

---

### Post by Starks on 2011-09-21
What about Compiz with GNOME 3 Fallback?

---

### Post by el_koraco on 2011-09-22
> **Starks said:**
> What about Compiz with GNOME 3 Fallback?

AFAIK, the fallback thingy only works with Metacity. I'm not a 100% on that, better to solicit advice from Gnome 3 users.

---

### Post by NightwishFan on 2011-09-22
> **el_koraco said:**
> AFAIK, the fallback thingy only works with Metacity. I'm not a 100% on that, better to solicit advice from Gnome 3 users.

It would be nice if it worked with compiz, this was the one thing I forgot to test! >_<

---

### Post by Starks on 2011-09-23
So, will the Gnome debacle be dealt with in time for the Fall distros or is Spring looking more likely if at all?

---

### Post by el_koraco on 2011-09-23
> **Starks said:**
> So, will the Gnome debacle be dealt with in time for the Fall distros or is Spring looking more likely if at all?

Give it a year at least.

---

### Post by screaminj3sus on 2011-09-23
> **el_koraco said:**
> You could, you just need to enable Metacity compositing for Docky (some obscure command in Gsettings, no doubt). But it's not even close to Gnome 2 plus Compiz. If I remember correctly, you're on Mint 11. Honestly, until the whole mess gets sorted out, why not just stay with that and carve up a Chakra/Arch(bang) partition and mess around with XFCE, or even Openbox or Compiz standalone? With some config file editing, and with using tint2/xfce4-panel + xcompmgr, xcompmgr-dana or cairo-compmgr if on Openbox, you can have a Gnome independent setup like you describe. 

Of course, the proper thing to do would be to use a tiler...

You can use gnome 3 fallback with compiz...

And docky/awn have plenty of their own applets to replace any missing gnome ones.


> **NightwishFan said:**
> It would be nice if it worked with compiz, this was the one thing I forgot to test! >_<

It does work with compiz guys...

---

### Post by Starks on 2011-10-09
I might try out Archbang.

---

### Post by chazinams on 2011-10-09
does archbang have a LIVEcd users can test it out with without installing?

---

### Post by mips on 2011-10-10
> **chazinams said:**
> does archbang have a LIVEcd users can test it out with without installing?

The Archbang CD is a LiveCD and you can install from within the live environment.

[http://archbang.org/](http://archbang.org/)
> The download page has links to both 32 & 64 bit versions, **[COLOR="Red"]bootable as a live CD / USB[/COLOR]** – allowing you to easily test it out before doing a full install.

Here is installation guide with screenshots [http://archvortex.blogspot.com/2011/09/simple-archbang-installation-guide.html](http://archvortex.blogspot.com/2011/09/simple-archbang-installation-guide.html)

---

### Post by jemadux on 2011-10-11
if you want try archbang is easy ..... has packer for aur / grabbder

---

