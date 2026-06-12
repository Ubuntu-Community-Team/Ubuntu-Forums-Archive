---
title: "Problem Upgrading to Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-04-21
Hi:
I get the following trying to upgrade.  Are the servers just busy, or should I do something to fix?


Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)


Thanks,
Ziffnabb

---

### Post by jiminycricket on 2007-04-21
It's busy. try changing to a different Canadian server in Synaptic (Settings->Repositories, the different ones are under "other), then reloading, and then use upgrade-manager again to upgrade.

---

### Post by tbg58 on 2007-04-21
Looks like they're just busy -- I can't do a WGET from the command line either.
It's not your install.  Feisty is quite popular and thousands of folks are downloading. Things will calm down in a few days, I hope.
Good luck!
- Rob

---

