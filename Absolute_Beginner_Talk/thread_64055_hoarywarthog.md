---
title: "hoary/warthog"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by war-totem on 2005-09-09
what is the difference between the two of them? is one just the upgrade of the other?

---

### Post by manicka on 2005-09-09
[QUOTE=war-totem]what is the difference between the two of them? is one just the upgrade of the other?[/QUOTE]
 basically...yes. Hoary being the most recent and soon to be replaced by breezy

---

### Post by war-totem on 2005-09-09
so to update to hoary or breezy you just change warthog to breezy and run apt-get dist-upgrade?

---

### Post by matthew on 2005-09-09
From a command line: "sudo gedit /etc/apt/sources.list"

Change all instances of "hoary" or "warty" to "breezy" and save

Back at commandline:
sudo apt-get update
sudo apt-get dist-upgrade

In other words, "yep."

---

### Post by TristanMike on 2005-09-10
I would think that if you're upgrading from Warty to Breezy, it should be a fresh install. I may be incorrect, but there may be too many incompatability issues when you do a dist. upgrade from Warty to Breezy. I'd think to do an upgrade from Warty to Hoary then to Breezy *_IF_* reinstalling Breezy is not an option.

---

