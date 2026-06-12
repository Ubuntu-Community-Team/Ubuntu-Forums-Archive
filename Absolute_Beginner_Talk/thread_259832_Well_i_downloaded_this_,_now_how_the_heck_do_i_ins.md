---
title: "Well i downloaded this , now how the heck do i install it.."
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-09-17
here ==>  [http://beagle-project.org/Main_Page]("http://beagle-project.org/Main_Page")

Or should i not bother..?

---

### Post by bodhi.zazen on 2006-09-17
See here:
[How to install Beagle](http://beagle-project.org/Ubuntu_Installation)

---

### Post by qamelian on 2006-09-17
Beagle is available in the Ubuntu repositories, so you can easily install it using aptitude, apt-get or Synaptic. Just make sure you've uncommented the various extra repositories in /etc/apt/sources.list, then do a ```
sudo aptitude update
``` followed by a ```
sudo aptitude install beagle
``` and you're all set.

---

### Post by Najand on 2006-09-17
No need to download; just enable universe /multiverse if haven't done it yet:
```

sudo aptitude install beagle

```
then in order to make Beagle start indexing your home directory, you need to disable then re-enable indexing in the Beagle preferences dialog (System->Preferences->Search & Indexing->Indexing tab->Uncheck then re-check the box next to Index my home directory.

---

