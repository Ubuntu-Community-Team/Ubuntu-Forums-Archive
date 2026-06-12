---
title: "Missing architecture error in update."
date: 2012-02-11
forum: Any Other OS
---

### Post by r3bol on 2012-02-11
Hey folks, I'm not sure what to do with this...
(I'm using Linux Mint9 = Ubuntu 10.04)

[IMG]http://i.imgur.com/0MwCJ.png[/IMG]

How do I fix this? Thanks in advance.

---

### Post by lechien73 on 2012-02-11
Hi,

Could you try opening a terminal window and running:

```
sudo dpkg --clear-avail
sudo apt-get update
```

That should at least clear the /var/lib/dpkg/available error.

If the /var/lib/dpkg/status error persists, could you please do the following:

```
gksu gedit /var/lib/dpkg/status
```

Locate the entries for the problem packages (mirthkit and fing). Copy and paste them here between CODE tags (the **#** button on the post toolbar).

An entry in the status file looks like this:

```
Package: libbamf-dev
Status: install ok installed
Priority: optional
Section: libdevel
Installed-Size: 112
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bamf
Version: 0.2.104-0ubuntu1
Depends: libbamf0 (= 0.2.104-0ubuntu1), libwnck-dev, libglib2.0-dev (>= 2.23.0-1ubuntu3~)
Suggests: libbamf-doc
Description: Window matching library - development files
 bamf matches application windows to desktop files
 .
 This package contains files that are needed to build applications.
Homepage: https://launchpad.net/bamf

```

---

### Post by r3bol on 2012-02-11
Hi, thanks for the reply. 

> That should at least clear the /var/lib/dpkg/available error.
After doing that I get this error after trying to update:
```
W:GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC7B7B7D4439DBD6, W:Failed to fetch http://debian.wgdd.de/ubuntu/dists/jaunty/main/binary-i386/Packages.gz  410  Gone
, W:Failed to fetch http://debian.wgdd.de/ubuntu/dists/jaunty/restricted/binary-i386/Packages.gz  410  Gone
, W:Failed to fetch http://debian.wgdd.de/ubuntu/dists/jaunty/universe/binary-i386/Packages.gz  410  Gone
, W:Failed to fetch http://debian.wgdd.de/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.gz  410  Gone
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```
> Locate the entries for the problem packages (mirthkit and fing). Copy and paste them here between CODE tags.
Couldn't find mirthkit in that file, but I found fing...
```
Package: fing
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 9884085
Maintainer: fing@over-look.com
Version: 1.4
Description: Overlook Fing

Package: libept0
Status: install ok installed
Priority: important
Section: libs
Installed-Size: 516
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libept
Version: 0.5.30
Depends: libapt-pkg-libc6.10-6-4.8, libc6 (>= 2.8), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.4.0), libxapian15, zlib1g (>= 1:1.1.4)
Description: High-level library for managing Debian package information
 The library defines a very minimal framework in which many sources of data
 about Debian packages can be implemented and queried together.
 .
 The library includes four data sources:
 .
  * APT: access the APT database
  * Debtags: access the Debtags tag information
  * Popcon: access Popcon package scores
  * The Xapian index built by apt-xapian-index
 .
 This is the shared library.
Original-Maintainer: Enrico Zini <enrico@debian.org>

```

---

### Post by lechien73 on 2012-02-11
These repositories are no longer available, so they can be removed.

I'm not familiar with how Mint manages repositories, but my guess is that you could remove them through the **Software Manager**.

Alternatively, you could open a terminal window and type:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.old
gksu gedit /etc/apt/sources.list
```

This makes a backup of the existing file - in case anything goes wrong, and then opens it in a text editor.

Find the offending repositories, which are:

```
deb-src [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty restricted
deb-src [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty universe
deb-src [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty multiverse
```

Place a # at the beginning of each line to comment it out.

Save the file, close the text editor and run:

```
sudo apt-get update
```

---

### Post by Perfect Storm on 2012-02-11
Moved to Other OS/Distro Talk.

---

### Post by r3bol on 2012-02-11
Thanks :) It looks ok now. 
I did get 
```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC7B7B7D4439DBD6
```
after the update, but I googled it and found I needed to do this...
```

asdf@asdf-laptop ~ $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EC7B7B7D4439DBD6

```
and it disappeared :P

---

