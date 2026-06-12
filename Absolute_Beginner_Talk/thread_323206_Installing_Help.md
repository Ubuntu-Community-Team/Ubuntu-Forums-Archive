---
title: "Installing Help"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Ronfar on 2006-12-21
I recently just got a new laptop and decided to try out Ubuntu edgy. My problem is that Anjuta is already in the package manager but it's a version I don't want. Every time I use apt-get install anjuta obviously it installs the one from the package manager. So if anyone can offer me some advice on how to get the installation of the version I want that I downloaded, I would greatly appreciate it. Thanks  for any help given!

---

### Post by meng on 2006-12-21
What version do you want? What version is in the repositories (package manager)?
If you can find a .deb file for the version you want, then download the deb file and enter this command:
sudo dpkg -i anjuta---.deb
You will have to resolve dependencies manually.

---

### Post by riven0 on 2006-12-21
[Debian]("http://www.us.debian.org/distrib/packages") is a wonderful place to get newer versions of software. Check there first, it usually lists the dependencies for you, too.

---

