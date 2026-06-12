---
title: "Play wmv files on the internet"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by bluescreenofdeath on 2008-03-08
I would like to to be able to play wmv files. For example if I click on a song preview on a website.

---

### Post by crjackson on 2008-03-08
> **bluescreenofdeath said:**
> I would like to to be able to play wmv files. For example if I click on a song preview on a website.

Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

### Post by herbster on 2008-03-08
If you mean from a browser, you can use [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

