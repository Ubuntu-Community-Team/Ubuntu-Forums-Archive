---
title: "Playing dvd's"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Kreat on 2005-12-13
I posted this in another forum and i definetly think it was in the wrong spot so i figured i'd post it again in the right area (mod please delete the other one)

Hey all Noob here, not a big surprise. just started playing with Ubuntu today so i'm very very new.. I would like to try and get my dvd's to play. I've gone to [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) but still cant get totem to work, I also tried downloading ogle and when it goes to play the dvd it just closes with no type of error message.

Totem gives me this Totem could not play 'dvd://'.
Could not determind type of stream.

I downloaded everything form that site so im nto sure where im going wrong. Thanks all.

---

### Post by Zelut on 2005-12-13
take a look at the [www.ubuntuguide.org](www.ubuntuguide.org).  There are some things you can install to help with playing back DVDs & also some multimedia codecs you might need.  Let me know if you still need help..

---

### Post by Kreat on 2005-12-13
I tried installing xine and this is the error message i get:

xine: found demuxer plugin: elementary mpeg stream demux plugin
xine: found input plugin : file input plugin
xine: found demuxer plugin: DVD/VOb demux plugin
xine: found input plugin :DVD Navigator

So im obviously missing some files,  but i could ahve sworn i installed everything

---

### Post by Zelut on 2005-12-13
did you install xine per the instructions on that page or manually?  here are a few suggestions:

1) sudo apt-get remove xine-ui
2) make sure you've got the full sources.list (see [http://wiki.ubuntu.com/SourcesList](http://wiki.ubuntu.com/SourcesList))
3) sudo apt-get update && apt-get upgrade
4) sudo apt-get install xine-ui
5) also make sure you've got these: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
6) also this: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by Kreat on 2005-12-13
I changed my sources to the one on that page,  Im pretty sure it was the same i had before, but just so nothing could be said or done,  the only codec i coudlnt install was this:
*******:~$ sudo apt-get install libdivx4linux
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libdivx4linux

Any idea?

---

### Post by Kreat on 2005-12-14
bump,  wonder if anyone knows how to fix thix =/

---

### Post by Perfect Storm on 2005-12-14
You  need avifile-divx-plugin instead.

```

sudo apt-get install avifile-divx-plugin

```

Some of the stuff on ubuntuguide.org don't work. It's for the earlier version of ubuntu.

---

### Post by Kreat on 2005-12-14
says my disc is still encrypted even though i stalled all the right packages.  And its a copy where the encryotion was removed

---

### Post by Griff on 2005-12-14
Automatix fixed all my problems with DVDs.  Check out #23 on the list.
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)
edit: you can download the file at the bottom left of the page

---

