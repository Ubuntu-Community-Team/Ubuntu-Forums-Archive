---
title: "No mplayer binary in mplayer-powerpc?"
date: 2005-06-05
forum: Apple PPC Users
---

### Post by hensan on 2005-06-05
Since Totem refuses to play mpeg movies (I tried installing gstreamer8.0-ffmpeg, but now it just crashes), I decided to install mplayer (mplayer-powerpc 1.0-pre6-0.3ubuntu5 (hoary)). But the package doesn't seem to include a mplayer binary, just a dead link to it called gmplayer. Where's the binary?

---

### Post by pvz on 2005-06-05
I think it's not included due to licence issues of some codecs or something, at least that's why Debian doesn't include it. Although I seem to remember that a working mplayer was included in Warty. You can compile your own, or use the exellent vlc-player. apt-get install vlc and you're ready to go.

---

### Post by hensan on 2005-06-06
Seems to be a bug in the powerpc and G4 builds, and it has been around for at least 3 months but nobody seems interested in fixing it.

It has been reported in Malone:

[https://launchpad.ubuntu.com/malone/bugs/402](https://launchpad.ubuntu.com/malone/bugs/402)

And Ubuntu Bugzilla:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=7586](https://bugzilla.ubuntu.com/show_bug.cgi?id=7586)

---

