---
title: "Supposed bug in Synaptic and unavailible updates"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by perixx on 2007-10-10
Generally, if I use Synaptic packet-manager,click 'Reload' and click the arrow for 'file progress', updating freezes at the current file. Updating won't proceed even if I close the 'file progress' overview and an error message like this is produced:


[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)
[http://de.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2](http://de.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2)
[http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2](http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2)
[http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.bz2](http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.bz2)
[http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.bz2](http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.bz2)
[http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.bz2](http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.bz2)




Additionally, after 2 or 3 tries (letting it finish without 'file progress' the third time) I get the following message:

W: Duplicate sources.list entry [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) feisty/main Translation-de (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_feisty_main_i18n_Translation-de)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)


I suppose that the 'file progress' freezing is a bug, but what can I do about the unavailible updates? And what about those 'duplicate' errors?

Thanks for hints on this matter... :)


perixx

---

### Post by ravenwere on 2007-10-10
Follow the suggestion of the error message and check the contents of your /etc/apt/sources.list file. Are you checking repositories on the german mirror and also on the main server??

---

### Post by perixx on 2007-10-10
Well,

seems like the second problem with the error messages solved itself... no more after rebooting!
Although I don't know why there was a problem with the German repositories.

The bug with freezing update procedure due to clicking 'File progress' remains, however.

perixx

---

### Post by perixx on 2007-10-11
I wonder if I should report this... can anybody else confirm this effect?

perixx

---

