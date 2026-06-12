---
title: "A day 1 question"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by dixonpete on 2008-02-02
Just installed Kubuntu, got the Net working.

I'm trying to add Firefox thru add programs and it's greyed out as is The Gimp when I try to add it. I appear to be in read only mode. Not helpful for an add program program.

I'm the only person/ID for this machine.

What's up?

Pete

---

### Post by wolfen69 on 2008-02-02
in Konsole:
```
cat /etc/apt/sources.list
```
post the output here.

---

### Post by dixonpete on 2008-02-02
Tx. Here u go. I don't think I changed any setting that would have contributed to this problem

## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by bruce89 on 2008-02-02
What happens if you do this?

```
sudo aptitude install firefox gimp
```

---

### Post by Bodsda on 2008-02-02
Uncomment all lines that begin with deb

This list is a list of 'Respositories'   basically its a list of where things are, if you have commented out lists, that means they wont be read by a program, when you add these lists new things become available in synaptic.

To see the new choices, you can click the reload button in Synaptic or type sudo apt-get update && sudo apt-get upgrade

Have fun  :):KS:)

oh, FireFox and Gimp are probably already installed

---

### Post by dixonpete on 2008-02-02
I get this..

Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
No candidate version found for firefox
No candidate version found for gimp
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

---

### Post by Bodsda on 2008-02-02
Enable your repositories by uncommenting all files that begin with deb in that list

---

