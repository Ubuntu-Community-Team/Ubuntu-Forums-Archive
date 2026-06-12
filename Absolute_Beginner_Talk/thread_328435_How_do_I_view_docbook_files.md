---
title: "How do I view docbook files?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by rhb on 2006-12-30
I have documentation on my ubuntu CE system for Kstars in docbook format, but don't know how to view the files.  Opera displays them as text, and Epiphany says they are a security risk, so is willing to download but not display, even when I used the "open" command on the menu.

I know I have a lot of other kde programs which don't display help at all because the KDE help interface is not available.  Can I get a KDE-help package which handles all the help files?  Does that handle docbook format?  I was reluctant to download kde help because I thought I would have to download the whole KDE system.  KDE help files do need to be readable on all gnome systems, preferably without all of KDE installed.

What is the best way for me to view the docbook files?  Does anyone know of Kstars documentation in another format?

Edit:

I found the docbook-utils package which seems to give me low-level tools to convert docbook files.  I found out you apparently don't just read them, they must be built.  The jw command converted one file for me.  The conversion wasn't clean, but it was readable.  I then googled for a sentence on the page and found the book at:

[http://docs.kde.org/development/en/kdeedu/kstars/using-kstars.html](http://docs.kde.org/development/en/kdeedu/kstars/using-kstars.html)

So now my main problem is solved.  I still wonder about KDE documentation.  Is it written in docbook, and built on first reference?  Do I need to get a complete KDE environment to get the help viewer?  I did find a thread that described the different KDE packages, with some not having a large number of apps included.  I may load the smallest package in the future.

Edit:

OK, I found the Khelpcenter package.  With it installed, the helps in the KDE apps I have work, and that includes KDE.  Apparently all or most of the KDE documentation is in docbook, so now I should be able to see all of it.  The docbook files are read directly by Khelpcenter; intermediate files (if any) are not saved.  I also considered installing Konqueror, but it requires a lot of packages to support it.  My question is now fully resolved.

---

