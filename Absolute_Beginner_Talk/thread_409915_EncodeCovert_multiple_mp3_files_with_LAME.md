---
title: "Encode/Covert multiple mp3 files with LAME?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-04-15
I'm triying to encode a whole folder of mp3 from a bitrate 128 to 112, but I'm unable to set the path to where they should be outputted.
It should be so, that the various mp3 with their names are outputted to the specified folder with the same names. Thx for any suggestions!

---

### Post by heimo on 2007-04-15
In the directory where mp3s are,  run something like:
```
mkdir subdir
find -maxdepth 1 -type f -name '*.mp3' -exec lame -b112 -q0 '{}' -o 'subdir/{}' \;
```

EDIT: Of course I must add the obvious observation ;) that converting from lossy format to lossy format will always degrade quality and should be avoided when possible.

---

### Post by ltk5 on 2007-04-17
Thank you!
I'll try it as soon as I can.:D

-----------------
that seemed to be working.
I also installed **soundKonverter** and it works fine. I just needed to install lame.

---

