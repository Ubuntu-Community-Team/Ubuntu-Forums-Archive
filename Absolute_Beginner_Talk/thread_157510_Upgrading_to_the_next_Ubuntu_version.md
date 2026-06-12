---
title: "Upgrading to the next Ubuntu version"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-04-09
I know that the next expected upgrade is in next June. I am running 5.10 now. When the new version is released, what are the upgrade options? Can I upgrade the OS without having to do a clean install?

---

### Post by Ferri on 2006-04-09
You can, although if you do a clean install is always less likely that you run into trouble.
You just have to edit your sources.list file in /etc/apt/ and change the repositories from "breezy" to "dapper". Afterwards, "sudo apt-get update" and "sudo apt-get dist-upgrade".
Hopefully you'll have your Ubuntu updated (you can go for a couple of drinks in the upgrade process).

---

### Post by aysiu on 2006-04-09
First you should make sure you have *ubuntu-desktop* installed or *kubuntu-desktop*. [QUOTE=Ferri]You just have to edit your sources.list file in /etc/apt/ and change the repositories from "breezy" to "dapper". Afterwards, "sudo apt-get update", "sudo apt-get upgrade" and "sudo apt-get dist-upgrade".[/quote] Actually, after you edit your sources.list, you need only ```
sudo apt-get update
sudo apt-get dist-upgrade
``` The second command you don't need and shouldn't use.

---

### Post by Ferri on 2006-04-11
[QUOTE=aysiu]The second command you don't need and shouldn't use.[/QUOTE]
Sorry for the mistake.
I've edited my previous post, just in case anyone doesn't go on reading.

---

