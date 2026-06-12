---
title: "looking for help with music production on ubuntu"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by uraliss on 2007-03-30
Hi folks
I am having trouble getting my head around setting up music apps on my laptop running ubuntu
i have no idea what jack, alsa and oss are and seem to be getting confused. Lots of the apps I have installed complain about missing jack files or alsa not configured properly and other similar messages.
Is there an easy but comprehensive guide that shows how this all works together?

---

### Post by teaker1s on 2007-03-30
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

ALSA is sound and we have a choice of 
alsa mixer
or
oss mixer

if we choose for our system alsa mixer,then we must have our app preferences set to the same.

**jackd**
JACK Audio Connection Kit (server and example clients)
Low-latency sound server. JACK allows the connection of multiple applications
to an audio device, as well as allowing them to share audio between
themselves.

**jack**
Rip and encode CDs with one command
Jack has been developed with one main goal: making OGGs (or MP3s)
without having to worry. There is nearly no way that an incomplete rip
goes unnoticed, e.g. jack compares WAV and OGG file sizes when
continuing from a previous run. Jack also checks your HD space before
doing anything (even keeps some MB free).

Jack is different from other such tools in a number of ways:
 - it supports different rippers and encoders
 - it is very configurable
 - it doesn't need X
 - it can "rip" virtual CD images like the ones created by cdrdao
 - when using cdparanoia, cdparanoia's status information is displayed
   and archived for all tracks, so you can see if something went wrong
 - it uses sophisticated disk space management, i.e. it schedules its
   ripping/encoding processes depending on available space.
 - freedb query, file renaming and id3/ogg-tagging
 - it can resume work after it has been interrupted. If all tracks have
   been ripped, it doesn't even need the CD anymore, even if you want
   to do a freedb query.
 - it can do a freedb query based on OGGs alone, like if you don't
   remember from which CD those OGGs came from.
 - freedb submissions

---

### Post by Patrick K on 2007-03-30
Jack Control (qjackctl) is a very handy way to control JACK. Well worth having. Otherwise you have to configure JACK from the command line, and that ain't easy.

---

### Post by cowlip on 2007-03-30
Might take a look at[ ubuntu-studio]("http://ubuntustudio.org/") | [Wiki]("https://wiki.ubuntu.com/UbuntuStudio")
They have metapackages in Ubuntu Feisty Fawn already.

Also, there are some good threads in the Community Cafe about music production, like the guitar thread..

---

