---
title: "Watching a DVD Movie Problem"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Taras on 2008-02-25
I am trying to watch a dvd, and it tells me that it cannot read from the source. Doesn anybody know what i can do to watch dvd

---

### Post by Sordelka on 2008-02-25
Did you install dvd support?

---

### Post by wolfen69 on 2008-02-25
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```

---

### Post by mkoehler on 2008-02-25
Most distros of linux do not include support for various media types, so you have to install the libcssdvd2 codec as stated by wolfen.

---

### Post by halitech on 2008-02-25
when you put the DVD in the drive, does it mount and show on your desktop? Also, is this a commercial dvd or a burned dvd? what program are you trying to watch it in?

---

### Post by Afkpuz on 2008-02-25
Do the above, but also do this.

```

sudo apt-get install ubuntu-restricted-extras totem-gstreamer

```

Also, goto Application>Add/Remove Programs

Search for "gstreamer" and add every single package with the word "gstreamer" in it.  Those gstreamer libraries were crucial to get my system reading dvds.  Hope that helps

---

### Post by wolfen69 on 2008-02-25
> **Afkpuz said:**
> Do the above, but also do this.

```

sudo apt-get install ubuntu-restricted-extras totem-gstreamer

```

Also, goto Application>Add/Remove Programs

Search for "gstreamer" and ***add every single package with the word "gstreamer" in it***.  Those gstreamer libraries were crucial to get my system reading dvds.  Hope that helps

NO. it is **not** needed. you only need gstreamer-good/bad/and maybe ugly. no need to download all that. please do not give bad advice. he does not need gstreamer editing modules and development files. the basic codecs will do.

---

### Post by Afkpuz on 2008-02-26
I wouldn't call that bad advice.  I spent a long time messing with codecs and getting the right gstreamer package installed.  I could have sworn I had the right ones I needed installed, so installing all of them at once is simple and covers all your bases.  All I've done is save him time later on looking for codecs.

---

