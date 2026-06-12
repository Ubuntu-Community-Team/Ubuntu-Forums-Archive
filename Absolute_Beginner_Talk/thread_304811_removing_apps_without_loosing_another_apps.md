---
title: "removing apps without loosing another apps"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by vladb on 2006-11-22
Ubuntu 6.10, installed from live cd
I am trying some customize, unistalling Rhythmbox, Totem (gstreamer), games using Synaptics and apt-get.
In present time impossible for me get rid of that apps , everytime Synaptic asking remove with them ubuntu-desktop and some other apps, but I like to keep them. 
How can I remove only Rhythmbox, totem, games and keep the ubuntu-desktop?
When I was installing Ubuntu 6.10 I didnt find customizing package option like Fedora Core 6 has, how can I choose the packaging in time of installation.
Please help. I am downloading Ubuntu 6.10 DVD and I will try install again in one hour
Thanx

---

### Post by Delkster on 2006-11-22
> **vladb said:**
> How can I remove only Rhythmbox, totem, games and keep the ubuntu-desktop?

Removing the ubuntu-desktop package doesn't really remove anything from your desktop directly. It's a so-called metapackage. It doesn't contain any software itself but it's been purposefully set to "depend" on all the applications included in the default Ubuntu desktop so that it kind of binds it all together: by having ubuntu-desktop installed you can make sure that you have everything the default desktop has.

Thus, if you remove something that's in the default desktop system, you'll necessarily also get ubuntu-desktop removed. If at some later point you want to have all the default applications back again, you can just install ubuntu-desktop and it'll bring them all.

It's advisable to have the ubuntu-desktop package installed when doing a distribution upgrade from one release of Ubuntu to another but other than that you aren't losing anything by letting it go.

---

### Post by turbojugend_gr on 2006-11-22
I don't see any point in removing those apps, as you can see in the bottom of Synaptic you wont gain more than 30-50 mbs tops, so there's actually no need of removing 'em, I would suggest you to delete their menu entries and also make your desired applications the ubuntu defaults (System->Preferences-> Prefered applications or sth like that), so it would be like not having these appsm without having the issues that removing 'em might mean.

It is not only the upgrades issue, many deb's (like fedora's rpms) designed for ubuntu assume you have the default apps-desktop-libs, so removing 'em is not a wise choice.

Cheers, TJ.

---

### Post by Delkster on 2006-11-23
> **turbojugend_gr said:**
> It is not only the upgrades issue, many deb's (like fedora's rpms) designed for ubuntu assume you have the default apps-desktop-libs, so removing 'em is not a wise choice.

Many debs such as? I'm just curious.

If they need a specific package, they should depend on it.

If you mean packages created with checkinstall, they aren't really meant for distribution anyway since they lack all dependency information.

---

### Post by turbojugend_gr on 2006-11-23
You should know not everything is as it should be, many debs, especially if described as edgy package, breezy package etc, they tend to lack proper dep tree, they assume defaylt installation is there.

I didn't mean to provoke you in any way, it's just what my experience suggests.

Best Regads, TJ.

---

