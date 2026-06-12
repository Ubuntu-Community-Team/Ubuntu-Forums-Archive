---
title: "Flight 5"
date: 2006-03-11
forum: Announcements &amp; News
---

### Post by Tollef Fog Heen on 2006-03-11
Hello world,

Flight 5, the latest alpha of Dapper Drake, is available. These
releases are tested to be reasonably free of show stopper bugs, but
are obiviously still alpha quality, so do not use these on your
production systems.  You can download the Flight 5 cd here:

  Europe:
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-5/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-5/) (Ubuntu)
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/edubuntu/releases/dapper/flight-5/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/edubuntu/releases/dapper/flight-5/) (Edubuntu)

  United Kingdom, and the rest of the world:
    [http://cdimage.ubuntu.com/releases/dapper/flight-5/](http://cdimage.ubuntu.com/releases/dapper/flight-5/) (Ubuntu)
    [http://cdimage.ubuntu.com/edubuntu/releases/dapper/flight-5/](http://cdimage.ubuntu.com/edubuntu/releases/dapper/flight-5/) (Edubuntu)

The Kubuntu images were not ready at the time of this announcement,
but they will be in the near future and will be announced then.

Please download using BitTorrent if possible, and see
[http://wiki.ubuntu.com/Archive](http://wiki.ubuntu.com/Archive) for other mirrors.

A list of notable changes in this release across the whole distribution
is available here, thanks to Matt Galvin:

  [http://www.ubuntu.com/testing/flight5](http://www.ubuntu.com/testing/flight5)

Significant changes affecting the installer and live CD include:

  * A much improved version of Espresso, the live CD based installer
    is included.  It still has bugs, but we encourage everybody to
    test it and file bugs about any bugs you find.

    Unfortunately, due to a programming error, it will in many cases
    not work correctly on PowerPC.  We are sorry for this and will
    correct this before the next Flight.

  * A new default theme has been included.

  * NetworkManager has received a lot of attention and bugfixes and
    should work much better with the rest of the system now.

  * A range of ATI cards which were previously unsupported (some of
    the high-end X850 cards) are now supported.

  * The X autoconfiguration on AMD64 has been improved to use
    information from the screen, not just the graphics card.

  * New development version of GNOME is included.

Some known bugs:

  * PowerPC has problems with the keymap selector which will make the
    installer fail completely.  The keyboard selection is also a
    complete dummy and won't actually set up your keyboard.

  * Both the NetworkManager applet and the GNOME wireless applet is
    included in the taskbar.

  * The OpenOffice.org menus and the new theme interacts in an
    unfortunate way which ends up with the menus being transparent.
    This has already been fixed, but the fix wasn't ready when the
    installation CDs were made.

  * The new theme is very orange.  A less orange version has already
    been uploaded after user feedback told use the theme was too
    bright.

If you're interested in following changes as we further develop Dapper,
have a look at the dapper-changes list:

  [http://lists.ubuntu.com/mailman/listinfo/dapper-changes](http://lists.ubuntu.com/mailman/listinfo/dapper-changes)

We also suggest that you subscribe to the ubuntu-devel-announce list if
you're interested in following Ubuntu development. This is a low-traffic
list (a few posts a week) carrying announcements of approved
specifications, policy changes, alpha releases, and other interesting
events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

The Testing area of the wiki suggests various tests that can be
performed on Flight CD releases to try to catch bugs far enough before
the final release that they can be fixed:

  [http://wiki.ubuntu.com/Testing](http://wiki.ubuntu.com/Testing)

Bug reports should go here:

  [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

Enjoy,

-- 
Tollef Fog Heen
UNIX is user friendly, it's just picky about who its friends are

-- 
ubuntu-announce mailing list
[email]ubuntu-announce (AT) lists (DOT) ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)

---

