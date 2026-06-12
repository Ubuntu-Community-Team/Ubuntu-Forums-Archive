---
title: "Mame roms"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by crazysexycool on 2007-12-03
Hello people i have these mame roms and a mame emulator i am going to try and use the emulator you get on ubuntu but first i want to try and convert the roms which are in a zip status there is a linux pgm which is the same as zip and even better but i cant get the name can anyone help or has anyone had the same experience??

---

### Post by disturbedite on 2007-12-03
locky locky time.

oh, and mame won't recognize roms you convert to other archive formats anyway.

---

### Post by crazysexycool on 2007-12-03
Will the roms work in xmame?

---

### Post by disturbedite on 2007-12-03
you're not really supposed to ask about mame roms here...

don't use xmame.  its dead and super outdated.  use [sdlmame]("http://wallyweek.altervista.org/index.php").  if you need a frontend/gui use sdlmame w/ [kxmame]("http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402").  (<-- use that build specifically, not any other or the version available in the official ubuntu repos, its too old & doesn't support sdlmame).

you have to compile kxmame tho.  if you can't get it to compile try this:
```
./configure --disable-joystick
```
(of course that will disable joystick/joypad support, but some ppl have reported that is what is needed to get it compile).

---

