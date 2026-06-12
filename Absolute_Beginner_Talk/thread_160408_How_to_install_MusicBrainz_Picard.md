---
title: "How to install MusicBrainz Picard"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Jordan Meeter on 2006-04-14
Hello,

I downloaded [FONT="Courier New"]picard-0.7.0-beta2.tar.gz [/FONT] and I was wondering, how exactly do I install it?:p

Ok, I got this from INSTALLER.ubuntu:

> Installing picard-0.7.0 on Ubuntu 5.10 ("Breezy Badger")
--------------------------------------------------------

You have to install the following packages from Ubuntu's repository:

  libmusicbrainz:   libmusicbrainz4c2-dev
  expat:            libexpat1-dev 
  curl:             libcurl3-dev
  libfftw3:         fftw3-dev
  ctypes:           python2.4-ctypes
  wxpython:         python-wxgtk2.6

Note that Ubuntu's libmusicbrainz *should* work but isn't up to date.
You might want to install version 2.1.2 from source.

These packages are optional but are needed for libtunepimp's input
plugins:

  MP3:              libmad0-dev
  ogg/vorbis:       libogg-dev, libvorbis-dev
  Flac:             libflac-dev
  MP4:              libmp4v2-dev

For WMA and Musepack you have to install TagLib 1.4 from source, Ubuntu's
package is too old.

To install all available binary packages:

  sudo apt-get install libmusicbrainz4c2-dev libexpat1-dev libcurl3-dev    \
		       fftw3-dev python2.4-ctypes python-wxgtk2.6          \
		       libmad0-dev libogg-dev libvorbis-dev libflac-dev    \
		       libmp4v2-dev


Before installing source packages, make sure /etc/ld.so.conf contains
the following line:

  /usr/local/lib

If you don't have that file, please create it. You'll avoid lots of trouble.


The following packages have to be installed from source:

  1. libofa: Open Fingerprint Architecture Library (0.9.1 or later)
     [http://www.musicdns.org/downloads](http://www.musicdns.org/downloads)
     NOTE: Don't forget to run 'ldconfig' as root after installing this!

  2. TagLib (1.4 or later)
     [http://developer.kde.org/~wheeler/taglib.html](http://developer.kde.org/~wheeler/taglib.html)
     NOTE: This is only required for WMA and Musepack support!
           Don't forget to run 'ldconfig' as root after installing this!

  3. libtunepimp (0.5.0-alpha1 or later)
     [http://ftp.musicbrainz.org/pub/musicbrainz/libtunepimp-0.5.0-alpha1.tar.gz](http://ftp.musicbrainz.org/pub/musicbrainz/libtunepimp-0.5.0-alpha1.tar.gz)
     NOTE: Don't forget to run 'ldconfig' as root after installing this!

  4. libtunepimp's python bindings
     They can be found in libtunepimp's source package (directory "python").

  5. python-musicbrainz2 (version 0.2.2)
     [http://wiki.musicbrainz.org/PythonMusicBrainz2](http://wiki.musicbrainz.org/PythonMusicBrainz2)

  6. Picard (0.7.0-beta or later)
     [http://wiki.musicbrainz.org/PicardWithAcousticFingerprinting](http://wiki.musicbrainz.org/PicardWithAcousticFingerprinting)


Good Luck :-)


Can someone help me... I have no idea what to do!

---

### Post by croak77 on 2006-04-15
Is this the same program?

[http://wiki.musicbrainz.org/PicardLinuxInstall](http://wiki.musicbrainz.org/PicardLinuxInstall)

1.  Add the line deb [http://zim.musicbrainz.org/~luks/ubuntu](http://zim.musicbrainz.org/~luks/ubuntu) / to /etc/apt/sources.list.
2.  sudo apt-get install picard

This is for Breezy.

---

### Post by Jordan Meeter on 2006-04-15
Ahh, so close... I'm using Dapper.

---

### Post by croak77 on 2006-04-15
Well you can try compiling everything you need thats not is the repo's. Shouldn't be to hard or try kid3 and easytag if you haven't allready. Kid3 has MusicBrainz and freedb.org lookup. Easytag just has freedb.org.

---

