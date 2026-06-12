---
title: "libc6-dev"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by n3ldan on 2006-12-05
So I've been fighting tooth and nail to get gapless playback of mp3s.  I got MPD installed(0.12.1), but it didn't play back gapless :/

So I found aqualung, tried the .deb package, which installed, but wouldn't start.  I would run aqualung -o alsa, it would just sit there, without anything happening.

So I figured I would compile it.  ./configure dies with a gcc error, cannot find crt1.o, which I found means I need to install libc development packages.  I find libc6-dev in the repositories, try to install it, and get:

"libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu10 is to be installed".

So after ~3 days of trying to get gapless playback, I have nothing.

Help is appreciated :D

---

### Post by hod139 on 2006-12-05
For the build tools, install the package build-essential

---

### Post by n3ldan on 2006-12-05
> **hod139 said:**
> For the build tools, install the package build-essential

"
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
"

:/

---

### Post by hod139 on 2006-12-05
What if you use aptitude to try the install
```
sudo aptitude install build-essential 
```

---

### Post by n3ldan on 2006-12-05
Hmm, that seemed to work.  MPD, libasound2, and libc6 are being downgraded (I forgot, I had installed newer versions so I could install MPD 0.12.1, the version in the repositories doesn't have gapless playback support).

So you solved problem 1, now I have another problem :/

"
checking whether GTK+ version >= 2.6... no
configure: error: GTK+ not found or too old (version < 2.6)
"

So I guess I'll either have to live without aqualung, or install 6.10?

---

### Post by hod139 on 2006-12-05
You need to install libgtk2.0-dev.  Any package-**dev** installs the development files, which is usually headers and libraries.

---

### Post by n3ldan on 2006-12-05
That makes sense, so I installed that, then it complained about libxml2, so I installed libxml2-dev (figured that out all by myself:D ), and now ./configure finishes.  However, I need something for ALSA support:

"
checking for ALSA support... checking for snd_pcm_open in -lasound... no
"

Is there a dev package I need to install for that?

EDIT: figured it out, libasound2-dev

thanks for all the help!

---

### Post by hod139 on 2006-12-05
Glad to help.  And people say building from source is tough...

---

### Post by twinszg on 2007-01-06
Thanks! That works for me

---

