---
title: "Clueless about installing new Software"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by HappyPaul on 2005-07-23
Hello:

I've recently installed Kubuntu 5.04 on my Laptop and am quite enjoying it.  I really don't understand however, how to install new applications, having come from the double-click-and-go Windows world.  For example, I'd like to install the Firefox browser.  I've downloaded a .tar.gz file from Mozilla and really don't know what to do with it. Could anybody point me in the right direction?

Thanks,

Paul

---

### Post by jasmuz on 2005-07-23
You dont need to install FF from a tar.gz if you can install it via Kynaptic

---

### Post by maruchan on 2005-07-23
The first thing I'd use Kynaptic for is to download Synaptic. Then use that to download all the cool software out there.

As for stuff that you can't find in Synaptic, usually you can find a .deb which can be installed with dpkg, an .rpm that can be converted to .deb with alien, and sometimes an autopackage - see [http://www.autopackage.org](http://www.autopackage.org) for a lot of cool packages.

Autopackage is about as close as you'll get to windows-style application setup.

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=maruchan]The first thing I'd use Kynaptic for is to download Synaptic. Then use that to download all the cool software out there.

As for stuff that you can't find in Synaptic, usually you can find a .deb which can be installed with dpkg, an .rpm that can be converted to .deb with alien, and sometimes an autopackage - see [http://www.autopackage.org](http://www.autopackage.org) for a lot of cool packages.

Autopackage is about as close as you'll get to windows-style application setup.[/QUOTE]

Agreed. 

Here is a how to for synaptic:

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

---

### Post by aysiu on 2005-07-23
Synaptic Package Manager is one of the easiest ways to install software, and I use it for almost everything (Reload, Search, Check, Apply--can't get easier than that), but for Firefox, I actually do use the Mozilla .tar.gz, for a few reasons:

1. The Ubuntu/Debian version of Firefox always has an ugly blue icon without the flaming fox around it. I happen to like the fox logo. I know it sounds stupid, but I do.

2. For a while (I don't know if this is still true), the Ubuntu Firefox 1.0.4 was identifying as a previous version of Firefox and so could not install extensions.

3. It's actually one of the easier .tar.gzs to install. I just double-clicked it. Clicked "extract to here." Then I double-clicked the firefox-installer icon and it walked me through a "wizard" (just like in Windows). All I had to do was copy that folder to somewhere I wanted (I put it in /home).

---

