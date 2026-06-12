---
title: "Flight CD 3"
date: 2006-01-16
forum: Announcements &amp; News
---

### Post by Colin Watson on 2006-01-16
Hello world,

Flight CD 3 is ready. This is the third in a series of milestone CD
images that will be released throughout the Dapper development cycle, as
images that are known to be reasonably free of showstopper CD-build or
installer bugs, while representing very current snapshots of Dapper. You
can download it here:

  Europe:
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-3/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-3/) (Ubuntu)
    [http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/dapper/flight-3/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/dapper/flight-3/) (Kubuntu)

  United Kingdom, and the rest of the world:
    [http://cdimage.ubuntu.com/releases/dapper/flight-3/](http://cdimage.ubuntu.com/releases/dapper/flight-3/) (Ubuntu)
    [http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-3/](http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-3/) (Kubuntu)

An Edubuntu release should follow soon. Please download using BitTorrent
if possible, and see [http://wiki.ubuntu.com/Archive](http://wiki.ubuntu.com/Archive) for other mirrors.

A list of notable changes in this release across the whole distribution
is available here, thanks to Matt Galvin:

  [http://wiki.ubuntu.com/DapperFlight3](http://wiki.ubuntu.com/DapperFlight3)


Significant changes affecting the installer and live CD include:

  * Improved the x86 CD graphical bootloader screen by adding a
    normal/expert mode switch to reduce the number of menu items,
    offering more video modes, disabling the timeout on install CDs,
    removing the scary countdown-to-doomsday timeout clock, and making
    the "boot from first hard disk" option clear the screen properly.

  * The installer now runs in a single stage. This has lots of
    advantages in terms of speed, comprehensibility, reducing code
    duplication, and bug fixes.

  * The live CD now uses squashfs and unionfs, which makes it faster and
    smaller.

  * Live CD keyboard setup has been improved.

  * An integrity check boot option has been added to both install and
    live CDs.

  * Users of powerpc CD images on 64-bit hardware no longer need to type
    'install-powerpc64' or 'live-powerpc64' by hand; the bootloader will
    figure that out automatically.

  * Configuration of network cards on first boot has mostly been fixed.

  * Network cards that require firmware will once more work in the
    installer.

  * Many hardware detection/activation fixes.

  * Fixed path display errors in the automatic partitioner.

  * Installs to USB sticks should now get correct GRUB bootloader
    configuration.

  * The live CD will now look for a device labelled "casper-cow" (the
    label may change) and automatically save its state to that, so that
    you can carry around a USB stick with all your documents and
    settings saved from the live CD.

  * The live CD boot process now uses usplash, making it much more
    aesthetically pleasing.

  * The system now displays a better "restart required" notification
    when complex system upgrades require a reboot.

  * Installation on non-networked machines now works properly again
    (broken in Flight CD 2).

  * Kickstart support has been fixed to cope with some installer
    changes from earlier in the Dapper release cycle.


Known bugs:

  * Restoration of sound card mixer settings is erratic.

  * Bad shutdowns can result in network cards not getting activated on
    subsequent boots.

  * The powerpc live CD is still pretty broken, due (I think) to unionfs
    bugs.

  * OEM installation is broken, since it hasn't been fixed up to cope
    with the single-stage installer yet.

  * Many of the CD images are oversized for 650MB media.


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

We have switched to Launchpad for bug tracking. All bug reports on
Ubuntu, no matter which component is affected, should go here:

  [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

Enjoy,

-- 
Colin Watson                                       [cjwatson (AT) ubuntu (DOT) com]

-- 
ubuntu-announce mailing list
[email]ubuntu-announce (AT) lists (DOT) ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)
Comment: Colin Watson <cjwatson (AT) debian (DOT) org> -- Debian developer

iD8DBQFDy8Oj9t0zAhD6TNERAjDhAJ9502mEPyGlrlLNZ11fvbrltbklQwCfcmbw
kv0agZFxuVGQkXROZPT3Yh0=
=cqUC
-----END PGP SIGNATURE-----

---

