---
title: "question about upgrading (breezy etc)"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by glandula on 2005-07-11
i just want some clarification about how upgradnig and updating ubuntu works
when breezy and other future builds are released, what do i need to to ?

1) download, burn, total reinstall, losing settings ?
2) download, burn, upgrade via some upgrade thingy on the cd, keeping all my files and settings?
3) will the update manager keep me up2date so that when breezy is released it will prompt me to download a bunch of files and voila im running breezy?
4) seomthing else?

---

### Post by Leif on 2005-07-11
You change references of hoary to breezy in the /etc/apt/sources.list file. the you do a "sudo apt-get update" and a "sudo apt-get dist-upgrade", and you will have everything upgraded. Nothing lost, not even the need to burn a CD, and no need to ever reinstall again.

---

### Post by glandula on 2005-07-11
[QUOTE=][/QUOTE]
 thank you, sounds very nice

---

