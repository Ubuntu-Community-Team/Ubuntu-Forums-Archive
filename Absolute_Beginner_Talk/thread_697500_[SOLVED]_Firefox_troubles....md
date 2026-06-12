---
title: "[SOLVED] Firefox troubles..."
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by timbosity on 2008-02-15
OK

MOre little worries here, nothing major BUT would like to be able to fix them. Probably not related but may be...

There were a couple of reference sites that required me to open pdf in the firefox so I dowloaded and installed the adobe reader plugin yoke and put the *.so file into the .firefox/plugins directory alongside the flashplayer one. That was back in december 07. All was fine and dandy until adobe released reader 8.1.2. At first it asked me for the 8.1.2 when I went to open the files and now it just goes to download which is fine most of the time but not for this particular library site (archive of some description). I looked in the plugins folder see what i could see and no *.so for acroread 8.1.2. Where is that file (cant find it anywhere) and do I need to get it again? I have adobe reader 8.1.2 installed and it works fine out oof the firefox.

This may be related or unrelated (probably nothing to do with it but...)

Basically, some site requires a login which then sends a *.php back at you (???) firefox has decided that I want to either open that *.php file with my editor of choice or save it to disk which I surely dont...

ANY help greatly appreciated

Tim

---

### Post by Discov3ry on 2008-02-15
I don't think it's related to the pdf issue. I believe it's a misconfigured web server you're trying to connect to.

---

### Post by macogw on 2008-02-15
> **Discov3ry said:**
> I don't think it's related to the pdf issue. I believe it's a misconfigured web server you're trying to connect to.

For the second problem, that's right.

For the first... have you tried just having Firefox open it with Evince, the default PDF viewer?

---

### Post by y-lee on 2008-02-15
Install the plugin by following [Adobe Acrobat Reader 8.1 Installation for newbies]("http://ubuntuforums.org/showthread.php?t=604951&highlight=acroread") that way ubuntu will update the plugin whenever an update is added to the medibuntu.repo :)\

Edit: BTW  [acroread-plugins_8.1.2-0medibuntu1_i386.deb]("http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages") is the current package at medibuntu  for Gusty so it is the plugin you are after.

---

### Post by rfrey74 on 2008-02-18
I am having similar troubles on my AMD64 machine.  I took a look at [http://packages.medibuntu.org/dists/gutsy/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/gutsy/non-free/binary-amd64/Packages) and found that there is no mozilla-acroread package available.  Then I looked in [http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages) and found that mozilla-acroread still exists for 32 bit machines.  So for me, the problem is that the firefox plug-in for acroread is not available for my architecture.

[quote=y-lee]Edit: BTW acroread-plugins_8.1.2-0medibuntu1_i386.deb is the current package at medibuntu for Gusty so it is the plugin you are after.[/quote]

acroread-plugins_8.1.2-0medibuntu1_i386.deb contains plug-ins for acroread its self, not the mozilla plug-in we are after.

---

### Post by timbosity on 2008-02-18
Allright,

fixed it up without much trouble, in fact less than I thought from initially setting it up. Just installed acroread-mozilla plugin from synaptic. VERY easy...

Cheers,

tim

---

### Post by y-lee on 2008-02-18
> **rfrey74 said:**
> I am having similar troubles on my AMD64 machine.  I took a look at [http://packages.medibuntu.org/dists/gutsy/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/gutsy/non-free/binary-amd64/Packages) and found that there is no mozilla-acroread package available.  Then I looked in [http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages) and found that mozilla-acroread still exists for 32 bit machines.  So for me, the problem is that the firefox plug-in for acroread is not available for my architecture.

acroread-plugins_8.1.2-0medibuntu1_i386.deb contains plug-ins for acroread its self, not the mozilla plug-in we are after.


you're right, the package you want is the mozilla-acroread package,  I should've looked closer. And I see your problem, there seems to be no [ mozilla-acroread package for amd64]("https://answers.launchpad.net/medibuntu/+question/16387").

It seems you can use the nspluginwrapper and the 32 bit version of the FF plugin:

> I just tried wrapping the acroread 8 plugin (from the 32-bit medibuntu package) using nspluginwrapper (nspluginwrapper -i /path/to/nppdf.so) and it seems to work fine here.

Btw, a 32-bit firefox or xulrunner package (or some other source of 32-bit firefox/mozilla libraries) would be nice in medibuntu, to get rid of the annoying "Could not load gtkembedmoz.so" error when starting up acroread. Maybe i should file a wishlist bug about that...

I don't know much about nspluginwrapper but here's an article with some information and links, see [NSpluginwrapper: A cross-architecture browser plugin tool]("http://www.linux.com/articles/55380")

---

