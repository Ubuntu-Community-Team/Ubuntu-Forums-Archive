---
title: "Fonts look weird on the forums"
date: 2008-04-15
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2008-04-15
Take a look at the pictures and you'll see what I mean.  The top picture is how the fonts should look (and how they've always looked in Mint/Ubuntu).  The picture is Konqueror; in the other distros I used, I used Firefox and the fonts were similar.  

The second picture is how they look in Firefox currently.  It isn't pretty.  I'm not really sure why there is a difference, but could someone try to help me fix them?

[IMG]http://img.photobucket.com/albums/v258/TheOrangePeanut/ubuforumskonq.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v258/TheOrangePeanut/ubforumsfirefox.jpg[/IMG]

---

### Post by kerry_s on 2008-04-15
hard to tell from your pic's just looks like 2 different sizes of fonts,
so first go to edit> preferences and adjust the font size to match what you use in other distro's.
the other thing looks like hinting on the bold fonts, but that could be because of the size.

---

### Post by ynnhoj on 2008-04-15
are you sure you have the display size & dpi set properly in your /etc/X11/xorg.conf?  [here's the appropriate section in the wiki](http://wiki.archlinux.org/index.php/Xorg#Display_Size.2FDPI).  alternatively: are you sure you've got all the necessary fonts installed?  maybe a bit of searching through the repositories would turn something up.

---

### Post by ch_123 on 2008-04-15
Search "Firefox" in the ArchWiki, tells you all you need to solve this issue.

---

### Post by cannonfodder on 2008-04-16
I experienced a similar, if not identical, problem with Arch and Linux Mint.

In both cases I was using OpenBox as the sole WM/DE and had MS Core Fonts installed.

After some deduction and by a process of elimination I narrowed the problem down to two culprits.

First, the worst-looking fonts were html headers (h1, h2, h3, etc.) that called for Tahoma, which is an MS Core Fonts.

Second, I was relying exclusively on OpenBox and / or gtkrc-type config files to control antialiasing and hinting for my HP vs17 LCD flat screen monitor and not GNOME or KDE.

The solution? Setting Firefox to force web pages to use the default fonts I had selected worked but felt like just a work around. Uninstalling the MS Core Fonts would have accomplished the same and I could live without them but I wanted a better solution and not just a work around.

Maybe there was an easier way but I just ended up following the Arch Wiki's guidelines for improving font display. I also read whatever I could google on the subject -- I believe I consulted the Gentoo Wiki and a Slackware forum.

I regret to say that although I managed to get my fonts to look acceptable in Arch, I never mastered this particular aspect of Linux.

Good Luck!

---

### Post by TheOrangePeanut on 2008-04-18
I searched the Arch, Gentoo and Slackware wiki for the hell of it and couldn't find an answer.  I changed the DPI settings in about:config but that didn't do any good.  I'm fairly certain it isn't a problem with my fonts in general, but instead a setting with Firefox.  I believe this, of course, because the fonts look okay in Konqueror.

Anyone have any other ideas?

---

