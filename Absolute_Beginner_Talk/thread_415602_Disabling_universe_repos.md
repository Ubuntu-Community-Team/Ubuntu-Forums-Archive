---
title: "Disabling universe repos?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Seriphyn on 2007-04-20
> Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close. If you have the universe repository enabled we need to disable it. The beryl that is in the universe does not work with xgl.
Code:

System >> Administration >> Software sources

now disable the universe repo and reload.
Now we need to add the beryl repo.
Code:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -



Sorry, where are universe repos? How can I turn them off? I tried just skipping that bit and going to the next stage (installing Beryl that is) but it didn't work, unsurprisingly.

I go into Software Sources, but huh? Help please? thanks.

---

### Post by markl187ld on 2007-04-20
System - Admin - Software Sources - Untick "community maintained open source software (universe)"

---

### Post by Seriphyn on 2007-04-20
Hahahahaha. I guess I should be more observant Thanks man.

---

