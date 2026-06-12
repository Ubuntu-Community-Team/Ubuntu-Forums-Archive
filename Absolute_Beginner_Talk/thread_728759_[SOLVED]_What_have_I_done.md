---
title: "[SOLVED] What have I done??"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-19
I downloaded and installed Gimp from getdeb.net without removing the previous version. But on my attempt to do so, I have gimp as a broken package as well as ubuntu-desktop is a broken package. I cannot reinstall either of these packages. What do I do now?

---

### Post by (((X))) on 2008-03-19
Do what output of apt-get install *broken package says

---

### Post by kellemes on 2008-03-19
```
sudo apt-get -f install
```

---

### Post by sayakb on 2008-03-19
> **(((X))) said:**
> Do what output of apt-get install *broken package says

I dont seem to be able to post the output.. It freezes as I press Submit..

---

### Post by sayakb on 2008-03-19
Looks like it is fixed. I fixed the broken packages by:
sudo apt-get -f install

As indicated by kellemes
Then I removed every Gimp package and downloaded them again (I think gimp-data was corrupted)
So its working again now
Thanks for your time :)

---

