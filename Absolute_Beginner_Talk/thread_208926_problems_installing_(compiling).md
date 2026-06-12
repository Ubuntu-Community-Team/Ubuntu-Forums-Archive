---
title: "problems installing (compiling)"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-04
Well... Everything started 2 weeks ago, when i decided to try Linux. Well, i think that everything runs well, but (why does there always have to be a but?) I hate installing programs. For Example: to install one game called Flight Gear, I have to install other programs : SDL mixer, SDL image, Simgear, plib. Well, i install all except Simgear. I install the version from Synaptic - 0.3.9 I guess and it says no, I need version 0.3.10 . I download it. This one requires Openal 1.1. I download and install this one. Now, when ./configure works well, but at make, nearly at the end, BANG! error ```
../../simgear/sound/sample_openal.hxx:52:22: error: AL/alut.h: No such file or directory
make[2]: *** [visual_enviro.o] Error 1
make[2]: Leaving directory `/home/fuzzy/Desktop/SimGear-0.3.10/simgear/environment'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/fuzzy/Desktop/SimGear-0.3.10/simgear'
make: *** [install-recursive] Error 1:

``` :confused: This is not the first time when it happens. I tried another game OpenMortal --- the same, a similar error at the end. I tried to install a text editor (Yzis) that required Lua 5.1. I installed Lua 5.1 but the configure didn't recognise him:confused: . What's happening. Am I blind? Am I stupid? I followed all the instructions. What's happening with me? Pls help. If I'll solve this problem I guess I'll totally move from Win to Linux, cos, sincerelly, I started to hate Windows. Hope I'll not give you head aches with so much writing. Thx:KS I hope that this post doesn't make me a troll cos this is the last thing I'd like to be. \\:D/

---

### Post by FuzZy2006 on 2006-07-04
pls heeeelp, i need your help, anybody, pls tell me what's happening.

---

### Post by Jagot on 2006-07-04
Have you followed all the stages outlined in this tutorial about installing from source:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

