---
title: "Compressing folders"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by kwgarner on 2007-07-31
I have a folder containing several jpeg photos (50 mb in total) which I want to compress further so I can email them. Is there an easy way to do this? Many thanks.

---

### Post by Rocket2DMn on 2007-07-31
JPEGs are already a compressed format, but you may be able to squeeze a little more by putting them in a tar.gz file, though Windows users might have trouble reading it without WinRAR.  tar.gz is a compressed tarball
```
tar -cvf tarname directory/
gzip tarname.tar
```this gives you a file called tarname.tar.gz

There is also a GUI way to compress the folder into a .zip file which Windows users can read more easily.  It should be as simple as a right click, but I'm not in front of my linux laptop to check that.

PS: to uncompress that type of file in linux
```
tar -xzvf tarname.tar.gz
```

---

### Post by Pragmatist on 2007-07-31
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by jnorthr on 2007-07-31
It will depend on your target systems, that is, if the people receiving your email do not have the same unzip facility they may not be able to extract the photos. Only those people with a similar hardware and  ubuntu software might be able to view them . Consider using a utility to resize your photos and thus reduce their size, then send as .jpg's or .gifs if possible as these photo formats are standard and most machines can view pix using these formats.

---

### Post by mcduck on 2007-07-31
If you use Gnome just right-click on the directory, select "Create Archive" and then set the archive type to whatever you want. (I recommend .zip if you send them to Windows users and tar.gz or tar.bz2 for Linux)

However as the images are already in compressed format you probably won't get much more compression. But at least you get a single file instead of many..

---

