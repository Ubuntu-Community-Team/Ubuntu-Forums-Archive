---
title: "apt-get update problem"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by NiTsi on 2006-05-18
I have breezy 5.10.it seems that even though i do "sudo apt-get update" the next time i login it is not kept in memory and when i do it again it begins almost from the start as if it doesn't remember it. Not from the start but I think in particular that it re-updates the repositories from security and maybe from grarchive.
Does anybody know why this happens?
I also think that i have noticed it in two different pc's.
While in my old pc which is with 5.04 hoary it hasn never happened ](*,)

---

### Post by xtacocorex on 2006-05-18
apt-get update only updates the package list in the repositories on your computer. If you want to install the updates, you need to do apt-get upgrade or apt-get dist-upgrade.

Hopefully I understood your question.

---

