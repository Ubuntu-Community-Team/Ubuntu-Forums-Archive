---
title: "[SOLVED] Flight CD 4"
date: 2006-02-19
forum: Announcements &amp; News
---

### Post by Colin Watson on 2006-02-19
Hello world,

Flight CD 4 is ready. This is the fourth in a series of milestone CD
images that will be released throughout the Dapper development cycle, as
images that are known to be reasonably free of showstopper CD-build or
installer bugs, while representing very current snapshots of Dapper. You
can download it here:

  Europe:
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-4/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-4/) (Ubuntu)
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/dapper/flight-4/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/dapper/flight-4/) (Kubuntu)
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/edubuntu/releases/dapper/flight-4/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/edubuntu/releases/dapper/flight-4/) (Edubuntu)

  United Kingdom, and the rest of the world:
    [http://cdimage.ubuntu.com/releases/dapper/flight-4/](http://cdimage.ubuntu.com/releases/dapper/flight-4/) (Ubuntu)
    [http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-4/](http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-4/) (Kubuntu)
    [http://cdimage.ubuntu.com/edubuntu/releases/dapper/flight-4/](http://cdimage.ubuntu.com/edubuntu/releases/dapper/flight-4/) (Edubuntu)

Please download using BitTorrent if possible, and see
[http://wiki.ubuntu.com/Archive](http://wiki.ubuntu.com/Archive) for other mirrors.

A list of notable changes in this release across the whole distribution
is available here, thanks to Matt Galvin:

  [http://wiki.ubuntu.com/DapperFlight4](http://wiki.ubuntu.com/DapperFlight4)


Significant changes affecting the installer and live CD include:

  * A preliminary version of the long-awaited live CD installer
    ("Espresso", formerly known as "Ubuntu Express", based on though
    substantially changed from work done by Guadalinex), is now
    available: there's an "Install System Permanently" icon on the live
    CD's desktop.

    I should stress that this is an early release, and omissions or user
    interface issues here don't necessarily reflect what you'll see in
    the final product. However, we feel it's important to get this out
    now in order to encourage as much testing as possible.

  * The powerpc live CD is much more stable now.

  * The network configurator no longer creates /etc/dhcp3/dhclient.conf
    with syntax errors (#27141). If you're seeing errors from
    ifup/ifdown, just delete the line containing "NetcfgDHClient" from
    that file.

  * Progress bars for DHCP and wireless access point search now have a
    cancel button.

  * Installation on systems with 32MB of memory should now be possible.

  * The live CD now configures networking properly again, and sets up a
    keymap based on that selected in the graphical boot loader.

  * The installer's rescue mode now has a simple way to reinstall GRUB
    without having to use the shell.

  * Fixed time zone configuration crash for a number of language/country
    combinations (#28722).

  * The installer no longer asks for a proxy or whether to download
    language support if networking is disabled.

  * Support for installing with / on a removable device has been
    improved.

  * The graphical boot loader now has help text, which is localisable.
    Translations welcome!

  * We no longer copy remaining packages from the CD to the hard disk,
    since with the new single-stage installer its usefulness is
    outweighed by the extra installation time and use of disk space.

  * Custom install CDs made without the restricted component should now
    work more smoothly.

  * Monitor resolution is now detected automatically on amd64 systems.

  * Fixed installations on machines with badly-skewed system clocks
    (again).


Known bugs in the new live CD installer:

  * It's available only for Ubuntu and Edubuntu at present. A Kubuntu
    version is under development.

  * It probably won't install a working system on powerpc, as the
    appropriate boot loader magic isn't there yet.

  * As yet, there is no language, location, or keymap configuration
    support. Obviously these are high on the list of things to sort out.

  * It doesn't deal with installing language packs.

  * It wrongly installs the ubuntu-live metapackage, so the live CD
    installer itself will end up installed on the target system
    (although you probably won't notice it, since it's hidden from the
    menus).

  * The advanced partitioner is excessively painful to use at present,
    particularly the mountpoint selector, and it can sometimes take a
    few attempts to persuade it to accept a valid partition layout.


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
Colin Watson                                       [cjwatson (AT) ubuntu (DOT) com]

-- 
ubuntu-announce mailing list
[email]ubuntu-announce (AT) lists (DOT) ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)
Comment: Colin Watson <cjwatson (AT) debian (DOT) org> -- Debian developer

iD8DBQFD+DoA9t0zAhD6TNERAvr4AKCHJt54Xg9+hREv3m6tgGPU6l0hyACffAXN
9Lo3ViC1MeZFVemZa/mWPzo=
=ozUU
-----END PGP SIGNATURE-----

---

