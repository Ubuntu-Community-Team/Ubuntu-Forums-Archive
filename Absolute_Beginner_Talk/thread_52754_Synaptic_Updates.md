---
title: "Synaptic Updates"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by KonigWalker on 2005-07-28
Ok guys, I've run into a problem. For some reason the Synaptic Package Manager won't update it's list. It says that it does but it actually doesn't. Some of my programs are outdated like firefox and gaim and I can't update them cause the newer version isn't on the list! How the heck can I fix this? I don't even know where to begin?

---

### Post by bored2k on 2005-07-28
[QUOTE=KonigWalker]Ok guys, I've run into a problem. For some reason the Synaptic Package Manager won't update it's list. It says that it does but it actually doesn't. Some of my programs are outdated like firefox and gaim and I can't update them cause the newer version isn't on the list! How the heck can I fix this? I don't even know where to begin?[/QUOTE]
 Have you updated your package repository ? [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Open up a terminal (after doing those steps)
1. sudo apt-get update
2. sudo apt-cache search smeg

If you find a file, it's updated. To upgrade/update your system:
1. sudo apt-get dist-upgrade

---

### Post by KonigWalker on 2005-07-28
Thanks alot, problem solved.  :)

---

