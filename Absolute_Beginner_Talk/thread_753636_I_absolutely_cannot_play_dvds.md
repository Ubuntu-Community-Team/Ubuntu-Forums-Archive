---
title: "I absolutely cannot play dvds"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by ravosava on 2008-04-12
I've read all of these "how tos" to make DVDs work, but for some reason, it wont. Can ANYONE help me? Any help is much appreciated. :)

---

### Post by joshrobinson on 2008-04-12
do the following

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

```
sudo apt-get install libdvdcss2
```

pop in a dvd, and open totem if it doesnt do it itself, then if it asks to install some codecs, install the ones it recommends

---

### Post by crjackson on 2008-04-12
> **ravosava said:**
> I've read all of these "how tos" to make DVDs work, but for some reason, it wont. Can ANYONE help me? Any help is much appreciated. :)


Here, try this...

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

---

### Post by pinoyboyf4i on 2008-04-15
> **crjackson said:**
> Here, try this...

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

I want to cry tears of joy.  I have been searching this forum for nearly one month.  I installed Gutsy over and over.  Every time I installed k9copy I could not play DVDs again AND k9copy never worked.  I installed the latest version of k9copy, I tried other DVD players, nothing worked.  I got the blocking error many users received in dmesg.  Only this worked for me after k9copy was installed.  I am using a Toshiba A135-S4656.  Thank you so very much crjackson!

---

### Post by crjackson on 2008-04-15
> **pinoyboyf4i said:**
> I want to cry tears of joy.  I have been searching this forum for nearly one month.  I installed Gutsy over and over.  Every time I installed k9copy I could not play DVDs again AND k9copy never worked.  I installed the latest version of k9copy, I tried other DVD players, nothing worked.  I got the blocking error many users received in dmesg.  Only this worked for me after k9copy was installed.  I am using a Toshiba A135-S4656.  Thank you so very much crjackson!

You are very welcome.  I'm glad I could help you... :)

---

