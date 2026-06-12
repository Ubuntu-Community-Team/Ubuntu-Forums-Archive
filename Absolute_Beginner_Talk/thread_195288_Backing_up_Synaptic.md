---
title: "Backing up Synaptic"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-06-12
Hi!

I need to reformat my Ubuntu installation. Will backing up /var/cache/apt/archives and restoring it later keep me from having to download all the packages through Synaptic again upon doing a fresh install. I will probably have to tell dapper to install these, but would I have to re-download them? Or is there another directory in which synaptic saves it’s files.

---

### Post by aysiu on 2006-06-12
[This](http://www.ubuntuforums.org/showthread.php?t=42862) may help.

---

### Post by nanotube on 2006-06-12
[QUOTE=RudolfMDLT]Hi!

I need to reformat my Ubuntu installation. Will backing up /var/cache/apt/archives and restoring it later keep me from having to download all the packages through Synaptic again upon doing a fresh install. I will probably have to tell dapper to install these, but would I have to re-download them? Or is there another directory in which synaptic saves it’s files.[/QUOTE]

i am not sure, but why don't you just test it? try uninstalling some package, then check if the .deb is still in the apt cache dir, and then try reinstalling it, and see if it still attempts to download the .deb, or if it skips the download step.

my /guess/ would be that if it sees the right deb in the cache, it won't download it again, but can't be sure, so just run a test. :)

---

### Post by RudolfMDLT on 2006-06-13
Thnx guys, as always, very much appreciated!

---

