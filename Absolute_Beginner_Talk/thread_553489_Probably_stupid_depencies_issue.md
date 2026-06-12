---
title: "Probably stupid depencies issue"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by PurposeOfReason on 2007-09-17
Today I went to upgrade gimp to 2.4 because who doesn't love the newest toys. Anyways, before I found a simple .deb to install without trouble, I found a different one. It had me install a different gimp-data, which led to a newer version of this, which etc etc. Before I knew it, I had to 'sudo apt-get install -f" and watched quite a few libs get removed. Probably not good. While everything still works, swiftweasel freezes often on myspace/weather.com and conky won't show weather now. I think it may be related so is there a way to either restore to what I had before (doubtful) or to install original dependencies or ones Ubuntu thinks I need?

---

### Post by ddrichardson on 2007-09-18
Start with```
apt-get check
```That'll show if anything is broke.

---

### Post by PurposeOfReason on 2007-09-18
Thanks, instead I just looked for what sounded important (I'm typically good a recognizing what I lost) and one of the ones I choose was it.

---

