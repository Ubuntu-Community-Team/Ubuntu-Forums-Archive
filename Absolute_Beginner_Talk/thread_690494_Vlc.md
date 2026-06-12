---
title: "Vlc"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by harley87 on 2008-02-07
Trying to install VLC player but keep getting all sorts of errors. Have marked it for installation in the Synaptic Package Manager but i get the following:

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in preferences.

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

I Have the universe repository added and enabled, which is what it says is required. Any ideas?

---

### Post by stchman on 2008-02-07
> **harley87 said:**
> Trying to install VLC player but keep getting all sorts of errors. Have marked it for installation in the Synaptic Package Manager but i get the following:

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in preferences.

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

I Have the universe repository added and enabled, which is what it says is required. Any ideas?

Enable all the repositories.

---

### Post by harley87 on 2008-02-07
All enabled and still have same error message :(

---

### Post by abadtooth on 2008-02-07
Have you tried to install it through the add/remove applications tool?
This worked fine for me on Gutsy.

---

### Post by harley87 on 2008-02-07
through add/remove applications i get:

Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

---

### Post by benfindlay on 2008-02-07
Ok, try a ```
sudo apt-get -f install
``` and a ```
sudo dpkg --pending --configure
``` and a ```
sudo dpkg --configure --a
``` just to make sure nothing is currently stuck in the pipework. Once you've done this, try to install vlc normally

Hope this helps!

---

### Post by harley87 on 2008-02-07
still getting the conflicting with other installed software message....

---

### Post by mc4man on 2008-02-07
go into synaptic,search out the 3 named packages and post the versions that are either installed or available. Would also be useful to know what desktop your using - search in synaptic for ubuntu-desktop and post which one and version. For instance I have ubuntu-desktop - version 1.79. Out of the 3 named packages the one of most concern would be ttf-dejavu, the other 2, if installed can for the moment be removed

---

