---
title: "Realtek Soundman Install"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by oldstumpy on 2007-01-08
HI:oldstumpy here, trying to install sound player  and cant seem to get it,here are the instructions.SoundMan v0.1 - Realtime Frequency analyzator
Copyright (C) 1999 Gabor Kerenyi (wom@fireball.kalmar.hu)

SoundMan is a frequency analyzator with some additional feature, such
as noise filter, and frequency filter. But these features are under
developping, so it's slow, and may not work well.

It is developed under Qt library (1.4), with Qt-Architect.
The files for Qt-Architect can be found in the Dlg directory.
When you regenerate the files don't forget to copy to the directory,
which contais the sources.

The Src directory contains all the source which are needed to compile
it. The Makefile is generated with Tmake. The pro file for tmake is
named soundman.pro.

In the main directory you can find a soundman.conf file. It's an
example config file for colors. After the first run, copy it
to .SoundMan/ in your HOME directory.

The program needs OSS driver. You have to use a mixer program
(for example kmix) to adjust recording sources.Can anybody please help.Real Linux dummy](*,)Thanks oldstumpy

---

