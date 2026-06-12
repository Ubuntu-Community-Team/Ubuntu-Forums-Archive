---
title: "Statistics software"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by padeco on 2006-11-28
hi there,

i would like to know if anyone has successfully installed a maths/statistics software? i have installed octave, however, it does not have a friendly windows to operate. on the other hand, i downloaded through synaptic, the scilab program. it  installed without a hitch, but it does not run. it gives the following missing lib:
/usr/bin/scilab: line 31: /usr/lib/pvm3//lib/pvmgetarch: No such file or directory

the window on scilab that opens does not respond. 

if any one has a link to a stats/maths software and that is "user friendly", please let me know.

thanks to all,
padeco

---

### Post by nanotube on 2006-11-28
well, R is "the" statistics software. it is command-driven, rather than gui, but it is at the forefront of statistical technique. 

for symbolic computer algebra, i have found the best open source alternative is maxima. there's also a gui that goes on top of it, called wxmaxima. 

both R (packages like r-base-core) and [wx]maxima are available for easy installation through apt or synaptic.

for more info, can look here: [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Mathematics](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Mathematics)
or even better, here:
[https://help.ubuntu.com/community/UbuntuScientists](https://help.ubuntu.com/community/UbuntuScientists)

have fun :)

---

### Post by padeco on 2006-11-28
thanks nanotube,
i'll have a look at what you sugested.

---

### Post by Jad on 2007-01-11
Padeco, 
have you tried [ChronoJump]("http://www.gnome.org/projects/chronojump/screenshots.html") ?

---

### Post by ahmatti on 2007-03-21
Koctave is a sort of GUI for octave and there are some GUIs available for R as well, just google it. I prefer octave to scilab personally because it is a lot more matlab compatible.

Anyway after you get used to working from the command line you'll notice that in most cases a GUI will only slow your work :)

---

