---
title: "Installing MuseScore"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Diffusion on 2007-09-11
Bear with me as this is only my second day using Linux. ;)

I'm trying to install mscore 0.6.1 on to UbuntuStudio 7.04. I have so far (after lots of trial and error) managed to compile and install Cmake 2.4.7 and Qt 4.3.1, but when I go to build mscore I get the error:

```
CMake Error: Fatal error: QT (version >= 4.3.0) required.
Cmake tries to detect QT4 by searching for 'qmake' in your PATH
If you have QT4 installed, make sure qmake is found in your PATH.

```

Okay, so I added this to bash.bashrc
```
export PATH=$PATH:/usr/local/Trolltech/Qt-4.3.1/bin
```

This is (I believe) the path to qmake, but I still get the same error when I try to build mscore. What am I missing?

---

### Post by wschweer on 2007-09-11
in your new PATH the trolltech dir should appear _before_ the old PATH, so the new qmake
will be found first:
export PATH=/usr/local/Trolltech/Qt-4.3.1/binr:$PATH

check by calling "qmake --version"

---

