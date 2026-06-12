---
title: "[SOLVED] Help .. Font problem"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by nge on 2008-04-18
Can anyone help me with this ?
Note:
Red is the problem.
Blue is to notice that the ' character actually could appear.
Green is to notice that when I tried typing ' and ` in GEdit they also could appear. 

Screenshot attached.

---

### Post by nge on 2008-04-18
bump

---

### Post by Bloch on 2008-04-18
This seems to be the unicode character U+0092

see [http://www.fileformat.info/info/unicode/char/0092/index.htm](http://www.fileformat.info/info/unicode/char/0092/index.htm)

The character is called "Private Use Two" and is a non-standard character - not used in any language. On some systems/fonts however it seems it is shown onscreen as a '   and on others like yours with the square and 0092 inside.

Who wrote this text? They may have a problem with their keyboard settings.

If it was not written on your system, then there's nothing you can do except re-write those particular file names.

---

### Post by nge on 2008-04-21
Thanks for the info. I guess it can't be helped.

That character comes from CD-Texts in an album (Coco D'or Parfait) and in the package libgnome-compiz-manager0

---

