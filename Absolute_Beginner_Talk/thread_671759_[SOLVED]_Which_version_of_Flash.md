---
title: "[SOLVED] Which version of Flash?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by MicrosoftlessMesh on 2008-01-18
First post, first question.

Fifteen years of WIndows, pardon me.

I was just beginning to grasp the concepts before I realised that I know absolutely nothing.  I can't say enuff good things about this fine OS.

I got a question for the experienced users out there.  I don't know anything about *nix yet but I had a short class on Red Hat in college.  I'm wondering if I should go the "official" flash player or the alternative that pops up in Firefox.

Which version do you guys suggest?  I thank you all in advance...

Also if I do either of these when promted in Fox do I have the option to uninstall it from the Add/Remove or Synaptic?  I installed something I downloaded from the web before really looking into the concept of repositories and had a heck of a time trying to get the application to go away.

Any help is appreciated.  I hope you all have a good night.

---

### Post by PeterJS on 2008-01-18
If memory serves there should be two options for flash, the official plugin and Gnash. Gnash is nice in that it's open source, but when it comes down to functionailty and rendering flash it really doesn't hold a candle to the actual flash plugin. Maybe someday Gnash will correctly and quickly render flash but it's not there yet. I would recommend the official plugin unless you're intent on keeping a pure free system. An the flash installer from firefox will be installed from the repositories, and as such will be easily removed with the standard package tools.

And welcome to the Ubuntu community, isn't package management cool?

---

### Post by CCNA_student on 2008-01-18
I would suggest getting Adobe Flash Player 9 from adobe.com. The instructions on the website are really easy to follow.

---

### Post by iansane on 2008-01-18
Not an expert, actually still new but I installed the tar.gz from adobe. There is a tar.gz, an rpm, and a yum. The tar.gz is the one for Ubuntu It was easy to install. I think during the install I had to tell it the installation path. Only had to change the path in the example from Mozilla to Firefox and it installed real quick with no problems.

---

### Post by PeterJS on 2008-01-18
Problem with that is that you've got the choices of: tarball, RPM, YUM. The tarball will install correctly but won't have the package manager metadata. Using the rpm would mean using Alien and that's not the most reliable method. And looking at the alien man page, it looks like YUM is a complete no go.

The version in the Gutsy repo's is 9.0.48, is the version from adobe really that much newer and better?

---

### Post by MicrosoftlessMesh on 2008-01-18
> **PeterJS said:**
> isn't package management cool?

Yes my friend it is and thank you so much for your answer for it was exactly what I was looking for. Thank you so much again.

---

### Post by MicrosoftlessMesh on 2008-01-18
Thanks everyone for the reply! I didn't have any idea the community was that strong here. I'm going to have a great time with you wonderful people.  Thanks again.

---

### Post by tgalati4 on 2008-01-18
Try Linux Mint 4, it has all that stuff already loaded and working.  No fuss.  18 minutes from popping in the CD to install to reboot to surf.  Can't beat it.

Linux Mint 4 is based on Gutsy.

---

### Post by r4ik on 2008-01-18
Seems solved still a good read,

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)

from,

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

And last but not least,

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Good Luck !

---

### Post by MicrosoftlessMesh on 2008-01-29
You guys will have to pardon me, I didn't know about the "SOLVED" function of this forum.  What a good feature!  Anyways I ended up finding [the solution on another thread](http://ubuntuforums.org/showpost.php?p=3916182&postcount=9).

Thanks to **daradib** I was enlightened on what the issue was:

> This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pres...moviestar.html](http://www.adobe.com/aboutadobe/pres...moviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See bug 173890. This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/107610...untu2_i386.deb](http://launchpadlibrarian.net/107610...untu2_i386.deb)

---

