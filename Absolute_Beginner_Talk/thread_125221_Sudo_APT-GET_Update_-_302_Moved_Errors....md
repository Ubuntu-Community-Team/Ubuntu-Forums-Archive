---
title: "Sudo APT-GET Update - 302 Moved Errors..."
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by kleptos on 2006-02-03
I have been using Ubuntu for a few months now and decided to install the server version (from the normal install cd using the server option). I uncommented the security lines in the sources.list and ran the update command. I get a bunch of '302 Moved' messages. Have these things changed since the 5.10 release cd? I wanted to install some new things and they cant be found anymore. (Like mono and lynx and such...)

```

sudo apt-get update
Ign http://security.ubuntu.com breezy-security Release.gpg
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Err http://security.ubuntu.com breezy-security/main Packages
  302 Moved
Err http://security.ubuntu.com breezy-security/restricted Packages
  302 Moved
Err http://security.ubuntu.com breezy-security/main Sources
  302 Moved
Ign http://us.archive.ubuntu.com breezy Release.gpg
Ign http://us.archive.ubuntu.com breezy-updates Release.gpg
Ign http://us.archive.ubuntu.com breezy-backports Release.gpg
Ign http://us.archive.ubuntu.com breezy Release
Ign http://us.archive.ubuntu.com breezy-updates Release
Ign http://us.archive.ubuntu.com breezy-backports Release
Ign http://us.archive.ubuntu.com breezy/main Packages
Ign http://us.archive.ubuntu.com breezy/restricted Packages
Ign http://us.archive.ubuntu.com breezy/main Sources
Ign http://us.archive.ubuntu.com breezy/restricted Sources
Ign http://us.archive.ubuntu.com breezy/universe Packages
Ign http://us.archive.ubuntu.com breezy/universe Sources
Ign http://us.archive.ubuntu.com breezy-updates/main Packages
Ign http://us.archive.ubuntu.com breezy-updates/restricted Packages
Err http://security.ubuntu.com breezy-security/restricted Sources
  302 Moved
Ign http://us.archive.ubuntu.com breezy-updates/main Sources
Err http://security.ubuntu.com breezy-security/universe Packages
  302 Moved
Ign http://us.archive.ubuntu.com breezy-updates/restricted Sources
Err http://security.ubuntu.com breezy-security/universe Sources
  302 Moved
Ign http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://us.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-backports/main Sources
Ign http://us.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://us.archive.ubuntu.com breezy/main Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy/restricted Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy/main Sources
  302 Moved
Err http://us.archive.ubuntu.com breezy/restricted Sources
  302 Moved
Err http://us.archive.ubuntu.com breezy/universe Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy/universe Sources
  302 Moved
Err http://us.archive.ubuntu.com breezy-updates/main Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy-updates/restricted Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy-updates/main Sources
  302 Moved
Err http://us.archive.ubuntu.com breezy-updates/restricted Sources
  302 Moved
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  302 Moved
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  302 Moved
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  302 Moved
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  302 Moved
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  302 Moved
Reading package lists... Done
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

