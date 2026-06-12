---
title: "how do I use wget in ubuntu to download personal images to directory?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by superpenguin79 on 2007-10-28
Hi, I have a site that I upload all my personal photos to. I want to be able to batch download them to an external drive on another machine for backup purposes and don't want the hassel of having to manually cart a drive back and forth all the time at my office to back them up as I have a lot of family photos I don't want to loose. 

I am semi-familiar with wget enough to get a software install to go through, but is there a line I could use in wget to download all new jpg's from my domain to my other system and save them to a specific directory?   

any help is appreciated. Thanks

---

### Post by llamakc on 2007-10-28
wget -r -A.jpg [http://foo.bar.com](http://foo.bar.com)

Be in the directory where you want to place them.

---

### Post by superpenguin79 on 2007-10-28
Thanks, works nicely.

---

