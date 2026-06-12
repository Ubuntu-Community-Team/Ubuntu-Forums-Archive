---
title: "[HELP] updating/installing packages"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by czhou on 2007-06-16
I am running Edgy 6.10, and I tried to install the latest version of Skype, but I get the error message saying that I have unment dependencies. Turns out that Skype requires newer version of some of the packages I have. Here are the details:


The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is installed.
         Depends: libqt4-core (>= 4.2.1) but 4.2.0-1ubuntu6 is installed.
         Depends: libqt4-gui (>= 4.2.1) but it is not installable
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

I tried running update manager update these packages. I tried updating everything manually:

sudo apt-get update
sudo apt-get upgrade

but it still doesn't work.

How do I update/install those dependencies? (without upgrade system to 7.04)

Thanks in advance.

---

### Post by skymera on 2007-06-16
im not sure.

i would reccomend upgrading to 7.04 since 7.10 is out soon.
i have 7.04 and runs smooth.

but sorry i cant help

---

### Post by ingvald on 2007-06-20
Hey,
I have got the same problem. Runnign ubuntu 6.10 and get the same message dependency ..........I actually had feisty first, but could not get my wireless usb adapter to work so installed 6.10 instead where it was detected automatically, and working ever since....I was hoping to get Skype to work on 6.10.

Anyone that have found out how to do that?????

---

