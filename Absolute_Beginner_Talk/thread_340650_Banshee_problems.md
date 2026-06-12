---
title: "Banshee problems"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-01-17
I really want to try out the latest Banshee 11.4, but I can't get the repository to work. I open synaptec and added it to "Third Party" and reloaded my packages. It shows up with an error every time. These are the instructions on banshee-project.org:
> Currently, to run Banshee under Ubuntu Dapper ([http://ubuntulinux.org/)](http://ubuntulinux.org/)), it can be installed from APT.

The version in the Dapper repository is outdated (0.10.10). There are some unofficial backports availible.

A Dapper repository of many thing mono including banshee and dependencies are available by adding this line to /etc/apt/sources.list:
```

deb http://apebox.org/badgerexplosion ./
```

The above repository will upgrade about anything related to mono that ships with Ubuntu. This also will expect you to ignore that these packages are not authenticated. Use your own head to make this decision please. :-)

You will need to run sudo apt-get update and sudo apt-get dist-upgrade when finished to add the upgraded versions of the software.


Any ideas?

---

### Post by tbroderick on 2007-01-17
Go to [http://directhex.mfgames.com/](http://directhex.mfgames.com/). Follow the instructions there. You need to add the GPG key.

---

### Post by tdrusk on 2007-01-18
When I tried to install it I got this:
> banshee:
 Depends: libdbus-1-2 (>=0.60) but it is not installable
 Depends: libnautilus-burn3  but it is not installable
 Depends: libipoddevice0 but it is not going to be installed
  Depends: libmono1.0-cil (>=1.2.2) but 1.1.17.1-1ubuntu7.1 is to be installed
 Depends: libnautilus-burn3  but it is not installable
Now what?

---

### Post by tdrusk on 2007-01-18
[http://ubuntuforums.org/showthread.php?t=329260](http://ubuntuforums.org/showthread.php?t=329260)
thank god.

---

