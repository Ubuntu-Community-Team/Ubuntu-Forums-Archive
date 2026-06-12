---
title: "where is w32codecs?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-09-06
```
antsvr@antubuntu:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
antsvr@antubuntu:~$ 

```[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

---

### Post by Gremlinzzz on 2007-09-06
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by TheOtherShoe on 2007-09-06
w32codecs is also available in the Medibuntu repository. You can get it by adding these lines to /etc/apt/sources.list
```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

---

### Post by rsambuca on 2007-09-06
> **TheOtherShoe said:**
> w32codecs is also available in the Medibuntu repository. You can get it by adding these lines to /etc/apt/sources.list
```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

You should add the key as well.

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by ant2ne on 2007-09-06
*smacks forehead* 64bit AMD don't work with 32bit codecs, huh?

---

### Post by yabbadabbadont on 2007-09-06
Nope.  The last time I reinstalled Ubuntu, I didn't bother to install w32codecs.  So far, I haven't run into anything that can't be played by ffmpeg/xine/mplayer/vlc.

---

### Post by rsambuca on 2007-09-06
Oh, yeah, but there are w64codecs.

---

### Post by ant2ne on 2007-09-06
*thumbs up* I got it working. Thanks for the linky!

---

