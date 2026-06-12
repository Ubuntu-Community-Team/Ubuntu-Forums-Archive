---
title: "Apt Dependency Problem"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-01-09
I'm trying to download a package (ia32-libs). When I check it in Synaptic (or apt-get from command line), I get the error:

> ia32-libs:
 Depends: lib32stdc++6 but it is not going to be installed
 Depends: lib32gcc1 but it is not going to be installed

If I check lib32stdc++6, I get the error:

> lib32stdc++6:
  Depends: gcc-4.1-base (=4.1.1-13ubuntu5) but 4.1.1-21 is to be installed
 Depends: lib32gcc1 but it is not going to be installed

I have gcc-4.1-base installed, but it's version 4.1.1-21 (like the error says). What's weird (to me, anyways) is that gcc-4.1-doc, -locales, and -source are all 4.1.1-13ubuntu5.

Is there anyway I can downgrade 4.1.1-21 to 4.1.1-13ubuntu5, or ignore the dependency problem?

---

### Post by Bachstelze on 2007-01-09
Please tell us which Ubuntu version you are using and pastebin your /etc/apt/sources.list

---

### Post by tonyr1988 on 2007-01-09
Ubuntu Edgy AMD64

sources.list:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## Beryl
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

I uncommented all the universe / restricted / etc repos for the sake of convenience. :) Should I comment back one of them?

---

### Post by Bachstelze on 2007-01-09
Have you tried doing a *sudo apt-get update* before installing the packages ? What annoys me is that your Apt is trying to install a Feisty gcc, which is obviously not compatible with Edgy libs...

---

### Post by tonyr1988 on 2007-01-09
I just updated and tried again - no luck.

I thought I'd uninstall the gcc-4.1-base, update, and re-install, but it would have to take TONS of other packages with it, so I figured that would be a bad move. Is there any way to downgrade it safely?

PS Wait...What Debian versions correspond to Ubuntu versions? (such as Sarge?)

---

### Post by tonyr1988 on 2007-01-09
Also, I noticed you can force the version to downgrade, but it would remove all the things dependent on it (instead of leaving them and seeing if it works with the lower version).

I looked deeper and saw that it would remove apt, synaptic, etc....so I chose not to do it. :)

---

### Post by tonyr1988 on 2007-01-09
I found out the problem.

The first thing I did after installing Ubuntu was get the drivers for my wireless card (MadWifi) per [this]("http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi") tutorial.

I didn't use the sarge-backports because it didn't have madwifi-tools, only madwifi-source, so m-a wouldn't work. I used the unstable repo, and it worked beautifully. I then removed the repo from sources.list, since I wasn't sure what else was on the repo that would conflict with Ubuntu repos (it was for Debian). Apparently that didn't work too well - it already conflicted with gcc. :)

I did a fresh install of Ubuntu (I wasn't very far in it anyway :D) and am now trying to figure out a way to get MadWifi working.

---

