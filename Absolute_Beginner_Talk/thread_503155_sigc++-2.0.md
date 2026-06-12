---
title: "sigc++-2.0"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by rutherford on 2007-07-17
I am very new to Ubuntu.
I have installed Feisty. Then I installed build-essentials from Synaptic package manager.
I tried installing ktorrent, I downloaded the .tar.gz files from here [http://libtorrent.rakshasa.no/downloads/](http://libtorrent.rakshasa.no/downloads/)
and extracted it. I cd'ed to the directory and typed ./configure in the terminal, but I get this error.

checking for sigc++-2.0... Package sigc++-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `sigc++-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'sigc++-2.0' found
configure: error: Library requirements (sigc++-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Please help me with what should I do.

---

### Post by lamalex on 2007-07-17
why didn't just also use ktorrent from synaptic?

---

### Post by rutherford on 2007-07-17
I tried it, but whatever I tend to download, it says 'Stalled'.

Besides I really want to rectify this error, so any help for this sigc++ error would be appreciated.

Regards.

---

### Post by rutherford on 2007-07-17
Please Help someone.

---

### Post by Tommy on 2007-07-17
> **rutherford said:**
> I tried it, but whatever I tend to download, it says 'Stalled'.

Just to be clear -- are you saying that you successfully installed the build-essential package using synaptic, but after that, nothing else will install?

> Besides I really want to rectify this error, so any help for this sigc++ error would be appreciated.well, if you're new to Ubuntu you might find a Ubuntu or Debian source package easier to get started with rather than a tar.gz -- because a properly packaged .deb file can satisfy the dependencies when you are downloading AND you will know that the paths and variables are set in a standard way.

On my system, the libsigc libraries are in the /usr/lib directory, so to continue with what you have, you might check to make sure the .config script is looking there AND you have the libraries properly installed (using synaptic).

P.S.: By the way, synaptic doesn't install Ubuntu/Debian packaged source files -- you have to use the command line or another package manager for that.

P.P.S.: Ubuntu includes a torrent client (and at least two front ends) by default. From a terminal window, for example you can use btdownloadcurses [url]

---

### Post by rutherford on 2007-07-19
I mean, I installed ktorrent fine, but whenever I open a torrent in it, the status is 'Stalled'.

> 
On my system, the libsigc libraries are in the /usr/lib directory, so to continue with what you have, you might check to make sure the .config script is looking there AND you have the libraries properly installed (using synaptic).


How to do that, please help.

---

### Post by Tommy on 2007-08-02
> **rutherford said:**
> I mean, I installed ktorrent fine, but whenever I open a torrent in it, the status is 'Stalled'.


For some reason, it sounds like the network connection isn't working for you... 

Try the same torrent using the command (in a terminal)

btdownloadcurses 

(paste the torrent URL after that command)

If that doesn't work maybe your network connection is not working consistently.

Sorry I can't really help on getting compiling set up -- if you can't apt-get install build-essential, then there's something more basic wrong and I would recommend trying a fresh install and making sure the repositories are correct, and the automatic updates work.

---

