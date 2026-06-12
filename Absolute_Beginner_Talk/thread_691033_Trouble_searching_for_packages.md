---
title: "Trouble searching for packages"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by marenum on 2008-02-08
I'm trying to search for packages like VLC and Azureus in synaptic package manager but I can't seem to get any results. I have the universal repositories box checked. I'm a little stumped here because I can find them on my other pc with the same settings.

---

### Post by hyper_ch on 2008-02-08
did you also enable the multiverse repos?

```

apt-cache search vlc

```

---

### Post by oedha on 2008-02-08
mm...vlc is on universe......
but the dependent packages maybe not in the universe......
i usually checked all 4 boxes on system - adminstration - software source - ubuntu software
then sudo apt-get update
then sudo apt-get install vlc

---

### Post by marenum on 2008-02-08
Thanks a lot, everything seems to be there now!

---

