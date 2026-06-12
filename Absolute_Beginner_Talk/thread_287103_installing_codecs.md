---
title: "installing codecs"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-10-28
I have kubuntu 6.06

I was not able to play mp3s
so I downloaded libxine extracodecs from packages.ubuntu.com

now I have a single .deb file

How do I install it.

---

### Post by Perfect Storm on 2006-10-28
```
cd /where/the/file/is
sudo dpkg -i XXXXXXXXX.deb
```

---

### Post by dhawald3 on 2006-10-28
> **Artificial Intelligence said:**
> ```
cd /where/the/file/is
sudo dpkg -i XXXXXXXXX.deb
```

I tried it but it reports some dependancy problem.

on the packages.ubuntu.com I saw some 3-4 dependancies for this codec.

what shuld I do about them,where do i get them??

---

### Post by PriceChild on 2006-10-28
Maybe you could look at the error, see what dependencies are missing and download them as well from packages.ubuntu.com

That or post the error and we'll help you further...

---

### Post by Bachstelze on 2006-10-28
Why didn't you install it *via* APT ? No internet connection ?

---

### Post by dhawald3 on 2006-10-28
> **HymnToLife said:**
> Why didn't you install it *via* APT ? No internet connection ?

how do you do It??

---

### Post by dhawald3 on 2006-10-28
well here's the error message


dpkg: dependency problems prevent configuration of libxine-extracodecs:
 libxine-extracodecs depends on libmad0 (>= 0.15.1b); however:
  Package libmad0 is not installed.
dpkg: error processing libxine-extracodecs (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxine-extracodecs
dhawal@dhawal-desktop:~/net_data/ubuntu$

---

### Post by Bachstelze on 2006-10-28
Because if you have one, it's quite stupid to go through all this hassle instead of just using APT ;)

Well, paste the error and we'll help you find the missing packages.

EDIT : All right, so try installing the libmad0 package before. It's the only one you need in order to play mp3s so if you want just that, you could as well not install libxine-extracodecs.

---

### Post by Brownedwg89 on 2006-10-28
type in a terminal:
```
sudo apt-get install libxine-extracodecs
```

---

### Post by dhawald3 on 2006-10-28
it worked after i loaded libmad0

caffeine now playes mp3

but

amarok does not.

---

### Post by Bachstelze on 2006-10-28
make sure you have amarok-xine installed, not amarok-arts/gstreamer/whatever.

---

