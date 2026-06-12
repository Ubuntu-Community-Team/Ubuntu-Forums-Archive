---
title: "Adept-Manager dependencies corrupt"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by FreakerBeaker on 2008-04-05
I have been using Ubuntu 7.10 for a few weeks now and am loving it.  Last week, I upgraded to Kubuntu and seems to have been working perfectly fine.  The other day, I decided to install VMware Server and though it seems to be running fine, adept-manager may have been corrupted along the way.  So here are a few things I tried after looking through the forums and searching through Google:

1.) I ran the sudo apt-get update and seems to have loaded fine.  When I enter in sudo apt-get upgrade, I receive the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  adept-manager: Depends: {delibs4c2a (>= 4:3.5.7-1) but it is not installable
E: Unmet dependencies. Try using -f.


2.) Tryed using Synaptic to fix the dependencies but when clicking on fix and apply, it highlights adept-manager in yellow.

I noticed that there was an update for adept-manager, but the current and update seem to match the following "2.1.3ubuntu17.1".  I tried to update this but receive the error "There was an error commiting changes.  Possibly there was a problem downloading some packages or the commit would break packages"

I thought maybe one way to go about this would be uninstalling and reinstalling, but I would like to dodge that route cause my curiosity is struck.  Any help would be appreciated.

---

### Post by joshrobinson on 2008-04-05
did you run the command it said to run?

```
sudo apt-get -f install
```

---

### Post by FreakerBeaker on 2008-04-05
I forgot to mention I did run the sudo apt-get -f install and received the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  adept-manager
The following packages will be upgraded:
  adept-manager
1 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
3 not fully installed or removed.
Need to get 0B/618kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? yes
dpkg: parse error, in file `/var/lib/dpkg/status' near line 25524 package `adept-manager':
 `Depends' field, invalid package name `{delibs4c2a': must start with an alphanumeric
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by FreakerBeaker on 2008-04-05
Another idea was to revert back to an earlier version of adept-manager but beleive the depends' field, invalid package name `{delibs4c2a': must start with an alphanumeric message may stop me from doing this.   I still think VMware is the one to blame for this, but is it possible that this should be named deblibs4c2a and somehow got renamed to {delibs4c2a?

---

### Post by FreakerBeaker on 2008-04-05
Interesting!  I went into the status file and found that the old has this:

adept-common, kdelibs4c2a (>= 4:3.5.7-1)

while mine has this
adept-common, {delibs4c2a (>= 4:3.5.7-1)

Wonder how that got created.  Will now attempt to change this back and see where it goes from here.

---

