---
title: "Weird DVD playback problems"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by budroboy on 2006-09-07
hey guys, i had back | track on my computer and my friend gave me the ubuntu-live cd. I loved it, partitioned for it and installed it :D . So one day i wanted to watch a DVD. Well, i got the no codecs/install necessary plugins message for all the players. SO i used synaptic to install virtually every codec/plugin i could find, including libdvd stuff and divx. now, i can listen to mp3s and wma, but when i play a DVD, the only video that plays is (what i would call the first track) the FBI/expessed commentary explanation video which lasts only 8 seconds tops. after that, the video stops playing and thats that. ive tried kaffeine, kmplayer, xine, vlc nothing works.
i know its not the DVD player because it worked with windows.
help greatly appreciated

---

### Post by orb9220 on 2006-09-07
libdvdcss2 ?

Simple foundation for reading DVDs - runtime libraries
To allow applications to access some of the more advanced features
of the DVD format.

libdvdnav4 ?

The DVD navigation library
This is the DVD navigation library, which provides an interface
to the advanced features of DVDs, like menus, navigation, etc.

This package contains the libdvdnav runtime library.

libdvdplay0 ?

portable abstraction library for DVD menus support
libdvdplay is a portable abstraction library for DVD menus navigation
support.  It provides low-level functions for DVD reading and seeking, as
well as access to the DVD data (subtitles, languages, chapters). It also
provides the virtual machine required for DVD navigation to the client
application.

This package contains the libdvdplay0 runtime library.

libdvdread3 ?

Simple foundation for reading DVDs
To allow applications to access some of the more advanced features
of the DVD format, libdvdread offers:

1. A simple abstraction for reading the files on a DVD image
  (dvd_reader.h).
2. A simple library for parsing the information (IFO) files
  (ifo_read.h/ifo_types.h).
3. A simple library for parsing the navigation (NAV) packets
  (nav_read.h/nav_types.h).

libdvdread currently uses libdl to dynamically probe for libdvdcss at
runtime, if found, libdvdcss will be used to decrypt sections of the
DVD as necessary.

Just search in synaptic on term dvd.

---

### Post by budroboy on 2006-09-07
i checked and i have all of those installed except for libdvdcss2 (search for dvd). so i searched for it and cant find in synaptic, so i tried the commandline version, which didnt find anything.
is libdvdcss2 known by another name?

---

### Post by orb9220 on 2006-09-07
You need to enable aditional repos in synaptic. In synaptic go to settings>repostories and enable any with the word binary at the end. then click on reload button and then try search again.

---

### Post by budroboy on 2006-09-07
thx for all your help. by the time i read your post, i had already     fixed the repo and had watched a test movie. sorry i beat you to the punch. anyways, if anyone ever comes here with the same problem, make sure you install the libdvdread3 in root.
and make use of google, there's a reason its there

---

