---
title: "tring to play a DVD"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-17
when i put in  DVD the TOTem automatically pops up and says 

an error occurred
could not open location; you might not have permission to open the file

how do i fix it and is there any better dvd players?

---

### Post by ctswhole on 2008-02-17
I prefer xine myself.  You can install it through synaptic, or just enter
```
sudo apt-get install xine-ui
```
And if you don't already have the proper codecs to watch a DVD, enter this as well:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by wolfen69 on 2008-02-17
installing ubuntu restricted extras is good, but ive never gotten a dvd(store bought) to play with that. do the following for dvd playback.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2
```

also, i prefer VLC for watching dvd's.

---

