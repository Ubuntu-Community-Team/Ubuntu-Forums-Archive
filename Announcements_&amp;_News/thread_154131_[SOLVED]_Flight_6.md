---
title: "[SOLVED] Flight 6"
date: 2006-04-02
forum: Announcements &amp; News
---

### Post by Tollef Fog Heen on 2006-04-02
Hello world,

Flight 6, the latest alpha of Dapper Drake, is available. These
releases are tested to be reasonably free of show stopper bugs, but
are obviously still alpha quality, so do not use these on your
production systems.  You can download the Flight 6 cd here:

  Europe:
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-6/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-6/) (Ubuntu)
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/edubuntu/releases/dapper/flight-6/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/edubuntu/releases/dapper/flight-6/) (Edubuntu)
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/) (Kubuntu)

  United Kingdom, and the rest of the world:
    [http://cdimage.ubuntu.com/releases/dapper/flight-6/](http://cdimage.ubuntu.com/releases/dapper/flight-6/) (Ubuntu)
    [http://cdimage.ubuntu.com/edubuntu/releases/dapper/flight-6/](http://cdimage.ubuntu.com/edubuntu/releases/dapper/flight-6/) (Edubuntu)
    [http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/](http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/) (Kubuntu)

Please download using BitTorrent if possible, and see
[http://wiki.ubuntu.com/Archive](http://wiki.ubuntu.com/Archive) for other mirrors.

A list of notable changes in this release across the whole distribution
is available here, thanks to Matt Galvin:

  [http://www.ubuntu.com/testing/flight6](http://www.ubuntu.com/testing/flight6)

Significant changes affecting the installer and live CD include:

  * Espresso has been further improved and should now work on PowerPC.
    It now correctly estimates time needed for installation.  The UI
    has been polished and translation efforts have been made possible
    and started.

    Espresso still has bugs, but we encourage everybody to test it and
    file bugs about any bugs you find.

  * The default theme has been tweaked slightly.

  * New versions of GNOME and KDE are included.

Some known bugs:

  * The keyboard selector in the espresso doesn't set the keyboard in
    the installed system.  It should change the keyboard in the
    running system, however.

  * The live bootup falls back into text-only mode after a short
    amount of inactivity.

  * The edubuntu live cd doesn't log in automatically.  Entering
    "ubuntu" as the user name and a blank password lets you in.

  * Espresso's manual partitioner assumes ext3 so trying to
    use another file system will fail.

  * When rebooting after installing using espresso, the GUI fails to
    shut down properly and you need to press enter to continue.

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

