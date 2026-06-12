---
title: "Bugzilla or Launchpad for Ubuntu desktop?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by persofi on 2008-04-15
Hey folks,
Is it possible to run Bugzilla/Launchpad or a program with similiar functionality not on a server but on a simple Ubuntu desktop?

---

### Post by PeterJS on 2008-04-15
The difference between desktop and server is whats installed by default, you could install from an ubuntu server disk and then install gnome on top of that and call it a desktop. Or you could take a working desktop, install say apache on it and call it a server, or you could even keep calling it a desktop.

So you could certainly install the apache, etc, and then bugzilla or launchpad on top of that.

---

### Post by persofi on 2008-04-15
Thx that is interesting. Do you happen to know any guides/tutorials on how to install apache-->bugzille ? I'm not really that linux savvy at the moment, so anything would be appreciated.

---

### Post by PeterJS on 2008-04-15
Apache is easy:
Open Synaptic > Edit > Mark packages by task > LAMP (Linux Apache MySQL PHP (Can also be perl or python)) Server
and that much will take care of itself. As for bugzilla, no idea never tried.

---

