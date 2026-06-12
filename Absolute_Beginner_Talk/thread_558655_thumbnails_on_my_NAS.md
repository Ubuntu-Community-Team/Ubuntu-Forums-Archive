---
title: "thumbnails on my NAS?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by alongenemylines on 2007-09-24
I've done a lot of searching before i joined up here, so hopefully someone can help a bit.

i want to be able to view pictures stored on my nas, as thumbnails, in nautilus.  if there's another file manager that will allow for it, i'll gladly use that too.  i keep a few thousand images on my nas, and it's much nicer to be able to see what i'm opening instead of playing hide and seek.

please, someone help.

---

### Post by amauk on 2007-09-24
Exif

Exif is a standard set of headers contained within Jpegs (a thumbnail image being one of the headers, although there's lots of other info as well)
Most digital cameras write the Exif headers to the file, but it sounds like you don't have the headers on your files

Nautilus, I believe, can use the Exif information from Jpeg's to provide image thumbnails.

Try to find a program that can scan the images, and generate the Exif thumbnails

Never used it, but a google brought this up
[http://www.sentex.net/~mwandel/jhead/](http://www.sentex.net/~mwandel/jhead/)

Looking over the online manual,
option -mkexif creates an Exif header for a Jpeg
and
option -rgt creates (regenerates) image thumbnail information and writes it to the Jpeg header

---

