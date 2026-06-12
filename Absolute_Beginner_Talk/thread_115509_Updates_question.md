---
title: "Updates question"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by HyperX on 2006-01-10
If a new version of Ubuntu comes out (lets say its a whole version up - or however Ubuntu does it) do I just download the updates and it will take me to that level? Or do I need to burn a cd and do another install. Just curious how the process works. Sorry for the newbie questions.

---

### Post by ape on 2006-01-10
The preferred way would be to modify your /etc/apt/sources.list to point to the new versions repositories, then perform `sudo apt-get update; sudo apt-get dist-upgrade` to update the machine.

---

### Post by dueY on 2006-01-10
[QUOTE=HyperX]If a new version of Ubuntu comes out (lets say its a whole version up - or however Ubuntu does it) do I just download the updates and it will take me to that level? Or do I need to burn a cd and do another install. Just curious how the process works. Sorry for the newbie questions.[/QUOTE]

You can do either.

---

### Post by blair on 2006-01-10
The most recent issue of Tux Magazine (([www.tuxmagazine.com](www.tuxmagazine.com), issue #9, see the Q&A w/ Mango Parfait column) has an excellent article on how to configure your Synaptic repositories to update yourself. I had 5.04 installed, changed my repositories to point to the 5.10 files, updated the database, selected auto-apply all updates, downloaded over a 1,000 files !!!! and it worked like a champ. I had 1-2 small hiccups during the install process I was able to work around, but generally it automatically brought me up to the newer version far easier than you would ever expect for an OS out of Redmond. I was very, very impressed.

---

### Post by blair on 2006-01-10
1

---

