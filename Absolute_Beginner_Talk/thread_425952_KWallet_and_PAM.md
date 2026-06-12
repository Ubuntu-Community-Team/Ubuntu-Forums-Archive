---
title: "KWallet and PAM"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2007-04-28
In Gnome I use libpam_keyring so I dont have to authenticate to type my password twice in a row. I just type it once to log in, and then pam does the keyring authentication to connect to my WPA network.

Is there something similar for KDE and KWallet?

---

### Post by ukio on 2007-07-13
just found [this kwallet pam module]("http://repos.opensuse.org/home:/dirkmueller/gcc43_Factory/repodata/repoview/pam_kwallet-0-0.1-2.2.html"), however, it is an opensuse rpm package. I will give it a try...

**EDIT: **
successfully converted the pam_kwallet .rpm package to .deb, but could not build from the sources. I guess this is because the pam_kwallet.rpm depends on the libpam-devel .rpm, but the libpam0g-dev .deb for ubuntu seems to be too much different. 

for a more detailed explanation see my [ubuntu blog]("http://ubuntu.tknerr.de/2007/07/13/kwallet-pam-module-for-kubuntu-anyone/").

---

