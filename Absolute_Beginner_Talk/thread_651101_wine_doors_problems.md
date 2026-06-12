---
title: "wine doors problems"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Bart Ellebaut on 2007-12-27
I have installed wine doors, but when I want it to start, it starts loading, but it never starts. 
What am I doing wrong?

thx
Bart

---

### Post by staticvoid on 2007-12-27
why use wine doors...?

what do you need to install? I think there are better ways...

where did you download wine doors from? the official site?

---

### Post by Bart Ellebaut on 2007-12-27
I need to have Acces but I don't have office, so I can't install it under wine myself.

Yes, I have downloaded it from the official website (I think)

---

### Post by Bart Ellebaut on 2007-12-27
bart@bart-laptop:~$ wine-doors
Started logging session
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 92, in <module>
    import gtk, ui
  File "/usr/share/wine-doors/src/ui.py", line 7, in <module>
    from ctile import Tile
  File "/usr/share/wine-doors/src/ctile.py", line 1, in <module>
    import cairo, rsvg, math
ImportError: No module named rsvg


maybe this can be of any use.
should I install all them things he says to import?

---

### Post by Dark Hornet on 2007-12-27
I tried WINE DOORS a while ago, and found it to be WAY to buggy.  Personally, I wouldn't mess with it right now....maybe later on when the program has had time to develop.

---

### Post by abaete on 2008-02-21
I Need Help With Wine-doors. After Installation, I Choose Internet Explorer And Some Others, It Begins To Download Apps, Fonts And Dependencies, And The Download Freezes On Microsoft Windows Scripting Host 5. 

Help?

---

### Post by bodhi.zazen on 2008-02-21
I have to agree with previous comments, wine-doors looks nice, but remains buggy. As wine-doors is not in the repos, I suggest you file a bug report with wine-doors.

---

