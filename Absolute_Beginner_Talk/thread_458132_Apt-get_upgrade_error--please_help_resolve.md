---
title: "Apt-get upgrade error--please help resolve"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-05-29
This is the error message I get when I sudo apt-get update and then sudo apt-get upgrade

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic
The following packages will be upgraded:
  automatix2 hwdb-client-common hwdb-client-gnome kcontrol kdebase-bin
  kdebase-data kdebase-kio-plugins kdesktop kicker konsole libkonq4 libpulse0
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-common linux-restricted-modules-generic python
  python-gdbm python-minimal python2.5 python2.5-minimal unattended-upgrades
  xorg-driver-fglrx
24 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

Any help will be much appreciated;

swb

---

### Post by taurus on 2007-05-29
Do you have another processor like synaptic running by any chance?

---

### Post by shuttleworthwannabe on 2007-05-30
Strangely not; I checked. I logged out and back in again, then tried installing a package. It seemed to have rectified the problem. Perhaps it may have been internally checking for updates as I logged in and connected to the internet.

Thanks for the help,

swb

---

