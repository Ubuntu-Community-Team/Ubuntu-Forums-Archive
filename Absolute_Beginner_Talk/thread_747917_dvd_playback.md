---
title: "dvd playback"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2008-04-07
I can't get a dvd to play back when I try to play it on ANY of the players I install. Totem...xine...VLC...etc etc. What could be the problem? Maybe missing codecs? How do I install them?

---

### Post by tommcd on 2008-04-07
See this:
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29)
also get the stuff from medibuntu:
[http://www.medibuntu.org/](http://www.medibuntu.org/)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
This should enable you to play just about anything.

---

### Post by wormser on 2008-04-07
You need to install libdvdcss2 and w32 codecs.  Add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").

After the repository is added then:
```
sudo apt-get update
```
```
sudo apt-get install w32codecs libdvdcss2
```

---

### Post by Belak on 2008-04-07
The problem IS missing codecs.

Medibuntu can solve your problem.

Open a terminal and run the following 2 commands:
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then open synaptic and reload the packages.
The search for libdvdcss2
I would also reccomend the package non-free-codecs (really it just installs w32codecs - for most computeres)

Cheers!

-Belak

---

### Post by Michael.Godawski on 2008-04-07
This has always worked for me:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by fela on 2008-04-07
libdvdcss2 from medibuntu repo didn't work for me, i had to compile from source.

---

### Post by stchman on 2008-04-07
I have a section on this.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by B34ST1Y on 2008-04-07
Great! Got it working...sweet! I had to allow that restricted driver / codec thing mentioned to run....and viola! Instant success!

---

