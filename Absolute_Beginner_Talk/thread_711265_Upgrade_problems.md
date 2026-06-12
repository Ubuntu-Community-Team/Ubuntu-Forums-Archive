---
title: "Upgrade problems"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Giddes on 2008-02-29
I'm trying to upgrade from Breezy to Dapper, but I can't figure out how.

When I go to system>administration>update manager, the Software Updates panel says "Your system is up-to-date! There are no updates available. Packages to install: 0(0)". Then it brings up a warning box that says: "Your distribution is no longer supported. Please upgrade to a newer version of Ubuntu Linux. The version you are running will no longer get security fixes or other critical updates. Please see [http://www.ubuntulinux.org](http://www.ubuntulinux.org) for upgrade information."

I'd really appreciate it if someone could help me!
Thanks!

---

### Post by jan quark on 2008-02-29
```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by jan quark on 2008-02-29
also have a look at this site
[https://help.ubuntu.com/community/UpgradeNotes?highlight=%28upgrade%29](https://help.ubuntu.com/community/UpgradeNotes?highlight=%28upgrade%29)

---

### Post by Giddes on 2008-02-29
when I type those in the terminal it brings up three "W: Couldn't start source package..." 1 "W: you may want to run apt-get update to correct these problems" and a "E: Could'n't find package ubuntu-base"

I also tried "sudo apt-get install ubuntu-base ubuntu-desktop" and it brought up the same messages

---

### Post by Giddes on 2008-02-29
Anyone?

---

