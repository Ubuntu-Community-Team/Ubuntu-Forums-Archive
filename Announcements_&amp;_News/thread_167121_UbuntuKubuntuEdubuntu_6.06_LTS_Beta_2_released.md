---
title: "Ubuntu/Kubuntu/Edubuntu 6.06 LTS Beta 2 released"
date: 2006-04-27
forum: Announcements &amp; News
---

### Post by Colin Watson on 2006-04-27
The Ubuntu, Kubuntu, and Edubuntu teams are proud to present a second
Beta release of Ubuntu/Kubuntu/Edubuntu 6.06 LTS, codenamed "Dapper
Drake". This release corrects some serious flaws in the installer
present on the Desktop CD in the first Beta release. Although the
text-mode install CD also forms part of this release, it has not been
modified since Beta 1.

An updated Xubuntu release is also in preparation and will be announced
shortly.


To Get 6.06 LTS Beta 2
----------------------

Download Ubuntu/Kubuntu/Edubuntu 6.06 LTS Beta 2 here (choose the mirror
closest to you):

  Europe:
    [http://se.releases.ubuntu.com/6.06/](http://se.releases.ubuntu.com/6.06/) (Ubuntu)
    [http://se.releases.ubuntu.com/kubuntu/6.06/](http://se.releases.ubuntu.com/kubuntu/6.06/) (Kubuntu)
    [http://se.releases.ubuntu.com/edubuntu/6.06/](http://se.releases.ubuntu.com/edubuntu/6.06/) (Kubuntu)

  United Kingdom:
    [http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/) (Ubuntu)
    [http://releases.ubuntu.com/kubuntu/6.06/](http://releases.ubuntu.com/kubuntu/6.06/) (Kubuntu)
    [http://releases.ubuntu.com/edubuntu/6.06/](http://releases.ubuntu.com/edubuntu/6.06/) (Edubuntu)

  Rest of the World:
    [http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/) (Ubuntu)
    [http://releases.ubuntu.com/kubuntu/6.06/](http://releases.ubuntu.com/kubuntu/6.06/) (Kubuntu)
    [http://releases.ubuntu.com/edubuntu/6.06/](http://releases.ubuntu.com/edubuntu/6.06/) (Edubuntu)

Please download using Bittorrent if possible.

To upgrade from Ubuntu 5.10 to Ubuntu 6.06 LTS Beta 2, follow these
instructions:

[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

The final version of Ubuntu 6.06 LTS is expected to be released in June. At
that time, we will mail pressed Desktop CDs free of charge.


Changes from 6.06 LTS Beta 1
----------------------------

  * If the Desktop CD installer crashes, a signal handling issue in Beta
    1 meant that it was possible for its subprocesses to run wild, which
    was reported to damage partition tables in some cases (#40464). This
    has been corrected.

  * A number of crashes in the Desktop CD installer have been fixed,
    including a keyboard selector crash when a country without a default
    keyboard was chosen (#40658), a Kubuntu crash on entering a
    non-ASCII name (#40666), a language selector crash when choosing
    certain languages (#41132), and a Kubuntu crash in partitioning for
    certain languages (#41621). If the installer still crashes, it will
    now try to provide useful information that we can use to fix the
    problem, so please use this release in preference to any earlier
    one.

  * Atheros wireless network cards are now usable after installation
    (#40547).

  * Installation to ReiserFS filesystems should now work.

Of course, an extra week's worth of the whole team's development and
stabilisation efforts is also included.


Feedback and Helping
--------------------

If you would like to help shape Ubuntu, take a look at the list of 
ways you can participate at

  [http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/)

Your comments, bug reports, patches and suggestions will help turn 
this Beta into the best release of Ubuntu ever.  Please report 
bugs through the Launchpad bug tracker:

  [http://launchpad.net/distros/ubuntu/+bugs](http://launchpad.net/distros/ubuntu/+bugs)

If you have a question, or if you think you may have found a bug but 
aren't sure, first try asking on the #ubuntu IRC channel on FreeNode, 
on the Ubuntu Users mailing list, or on the Ubuntu forums:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-users](http://lists.ubuntu.com/mailman/listinfo/ubuntu-users)
  [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)


More Information
----------------

You can find out more about Ubuntu and about this preview release on 
our website, IRC channel and wiki. If you're new to Ubuntu, please
visit:

  [http://www.ubuntu.com/](http://www.ubuntu.com/)


To sign up for future Ubuntu announcements, please subscribe to Ubuntu's 
very low volume announcement list at:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)


Regards,

-- 
Colin Watson                                       [cjwatson (AT) ubuntu (DOT) com]

-- 
ubuntu-announce mailing list
[email]ubuntu-announce (AT) lists (DOT) ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)
Comment: Colin Watson <cjwatson (AT) debian (DOT) org> -- Debian developer

iD8DBQFEUU7Y9t0zAhD6TNERAvN0AKCEjqrTKE+tJApik4zCHNr0vJDE5gCeMpeH
7uf8ZN5UPD/UdiMXyAT1HHk=
=BZNJ
-----END PGP SIGNATURE-----

---

