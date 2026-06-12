---
title: "[SOLVED] Flight 7"
date: 2006-05-07
forum: Announcements &amp; News
---

### Post by Tollef Fog Heen on 2006-05-07
Hello world,

Flight 7, the latest alpha of Dapper Drake, is now available. These
releases are tested to be reasonably free of showstopper bugs, but are
still not release quality, so do not use these on your production
systems.  You can download the Flight 7 CD here:

  Europe:
[http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-7/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-7/) (Ubuntu)
[http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/dapper/flight-7/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/dapper/flight-7/) (Kubuntu)
[http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/xubuntu/releases/dapper/flight-7/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/xubuntu/releases/dapper/flight-7/) (Xubuntu)

  United Kingdom, and the rest of the world:
[http://cdimage.ubuntu.com/releases/dapper/flight-7/](http://cdimage.ubuntu.com/releases/dapper/flight-7/) (Ubuntu)
[http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-7/](http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-7/) (Kubuntu)
[http://cdimage.ubuntu.com/xubuntu/releases/dapper/flight-7/](http://cdimage.ubuntu.com/xubuntu/releases/dapper/flight-7/) (Xubuntu)

If possible, please use BitTorrent to download them. Other mirrors are
listed at [http://wiki.ubuntu.com/Archive](http://wiki.ubuntu.com/Archive).

We are currently in deep freeze and mostly bugfixes have been applied.
Notable changes include:

  * Crashes in the Live CD installer have been fixed: after
    the timezone page (#41846, #41921), with non-ASCII user names
    (#42097), in the KDE autopartitioner (#41865, #41893), during manual
    partitioning on systems with Mac OS installed (#41768), when
    partitioning errors occur (#39734), and more.

  * Filesystems are now mounted in the right order, which in particular
    fixes GRUB installation with a separate /boot partition (#40395).

  * Leading and trailing spaces in passwords now work properly
    (#37934).

There is a known problem with the partitioner in the live installer
which can cause installation failures. To work around this problem, if
you see something resembling "partition 1 of /dev/hda as" on the summary
page, without a filesystem type listed at the end (it should be something like
"partition 1 of /dev/hda as ext3"), then press back and then go
forward to the summary page again; it should then list filesystem
types correctly and you can continue with the installation.

For Kubuntu, wlassistant and knetworkmanager are now included on the
CD, for a better wireless network experience.

If you're interested in tracking our changes as we continue developing
Dapper, have a look at the dapper-changes mailing list:

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

