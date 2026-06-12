---
title: "image files"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by ponchuk on 2007-09-12
I have a bunch of window based rar files.  when i unrar them the first file produced a .img which i think is an image file.I s this image a an image of all the rar files?  Can I burn the window made images in ubuntu using gnome baker?  If so, I tied and "baker" can't see the file. What am I doing wrong.

---

### Post by hyper_ch on 2007-09-12
That's going to be difficult (it seems).

I found this here: [http://www.samuel-greef.de/?p=133](http://www.samuel-greef.de/?p=133) (german)

(1) rename the .img file to *.bin

(2) because we don't have a .cue file for it we need to create one. Get this file here:

[http://www.samuel-greef.de/wp-content/uploads/2007/05/bin2iso19b.c](http://www.samuel-greef.de/wp-content/uploads/2007/05/bin2iso19b.c)

(3) compile it:

In case you have not yet build-essential installed you need to do so:
```

sudo apt-get install build-essential

```

now compile it:

```

gcc -o bin2iso bin2iso19b.c

```

(4) Move the files to /usr/local/bin

(5) Create the .cue file:

```

bin2iso DATEI.cue -c DATEI.bin

```

(6) Convert it to an .iso

Frist get bchunk (dunno if it's installed by default):
```

sudo apt-get install bchunk

```

Convert it:
```

bchunk FILE.bin FILE.cue FILE.iso

```

(7) Mount it:

```

sudo mount -o loop FILE.iso /path/to/folder

```

---

### Post by bone2006 on 2007-09-12
almost all img files I've just renamed ISO and burn them.  Been doing this for years.  If it's a movie that's an img file, just rename it iso, then use VLC and see if you can open and play it.  Everything ok.........
right click on it and click write to disc.

---

### Post by hyper_ch on 2007-09-12
ok, if that works it's a lot simpler ;)

---

