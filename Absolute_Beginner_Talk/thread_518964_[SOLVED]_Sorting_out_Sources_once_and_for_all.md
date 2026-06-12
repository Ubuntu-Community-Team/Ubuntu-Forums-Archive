---
title: "[SOLVED] Sorting out Sources once and for all"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by staib on 2007-08-06
Hi all,

I am looking for a little help.

Whenever I go to download updates I get the following 'error' message - suggesting that I have duplicate sources - I'm sure that I do, it's just that I'm not sure from this list which ARE duplicates and how to remove them....

Any help - as ever - appreciated!

Nick

----------------------

W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_i18n_Translation-en%5fGB)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-backports_multiverse_binary-i386_Packages)

---

### Post by jasonlfunk on 2007-08-06
Look in your /etc/apt/sources.lst file for all of the repositories that your system uses, if you notice duplicates, remove one.

---

### Post by aysiu on 2007-08-06
Best way to do it is to just get a clean list. Delete your old list and add a new one.

Follow these instructions:
[http://psychocats.net/ubuntu/sources#key](http://psychocats.net/ubuntu/sources#key)

---

### Post by staib on 2007-08-06
Thanks for the help Jason and Aysiu - I used that very clear psychocats guide and just replaced the sources as advised.

Cool beans - another thing learned - now I just gotta remember it all!

Nick

---

