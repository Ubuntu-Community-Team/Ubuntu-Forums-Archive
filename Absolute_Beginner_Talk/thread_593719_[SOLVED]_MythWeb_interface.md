---
title: "[SOLVED] MythWeb interface"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by dysphasi on 2007-10-27
Ok, I finally got through to [http://localhost/mythweb/](http://localhost/mythweb/) but all I get is a page called "Index of /mythweb" and a list of folders and files (data, includes, js, modules, mythweb.php, mythweb.pl and a skins folder).

What's gone wrong? Aren't I meant to have a proper gui? :(

---

### Post by dysphasi on 2007-10-28
Solved :D All that I needed to do was remove apache (easiest way was to rid all related entries in Synaptic Package Manager) then run:
```

sudo dpkg --purge mythweb

```
The slate well and truly wiped clean, I then went on to reinstalling the bits I needed:
(1) ```
 sudo apt-get install libapache2-mod-php5 
```
(2) ```
 sudo apt-get install mythweb 
```
All worked A-OK. For securing I just used the Mythbuntu Control Center et voila I had a password setup. If there are any problems with securing this way, would appreciate some pointers at a better manual way, but for now I'm content :D

---

