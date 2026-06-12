---
title: "Video Codecs"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by 7raTEYdCql on 2007-11-15
I am presently using Fiesty, and having problems during the installing of the Video codecs.
The operation times out, this is the message i get when part of my download is complete.

To add to all the trouble my Internet speed sucks. Any help (note i am a first time user of ubuntu).

---

### Post by bswilson on 2007-11-15
Considering you state you have a slow Internet connection, I don't think that there is anything to `fix` here.  Ubuntu simply cannot get the video codecs to download due to your slow link, probably.

---

### Post by Hospadar on 2007-11-15
if you are having trouble with a very specific package, you might try writing down the name and manually downloading it from the package site, and then installing it with dpkg (you can just double-click it)

[http://packages.ubuntu.com/gutsy/allpackages](http://packages.ubuntu.com/gutsy/allpackages)
be careful, the above link is the full package list, so it's a big page.

if you wanted to be really slick, you could copy it to the package cache at /var/cache/apt/archives```
sudo cp ~/Desktop/<name of package file> /var/cache/apt/archives
``` (assuming it's on your desktop) and then just install it through synaptic, and synaptic will behave as if the package was already downloaded.

---

