---
title: "movie --&gt; psp or converter to mp4"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2006-10-31
is there any program on ubuntu that will convert a movie to mp4 format or is there  a program that will put a movie directly on the psp?

or if you could tell me why this wont work, i got QPSPmanager and this is the readme and it wont work:




First, be sure you have the QT3 Development files, then just type

qmake

to build the Makefile, then

make

to build the project, and finally

make install

to install the program (you should execute make install with root permission).

Then you will have the binary "qpspmanager" for your enjoyment.

I strongly recommend changing the default "style" for QT, which is KeramiK, to
another one more better looking such as PlastiK.

---

### Post by Fittersman on 2006-11-01
Any application to convert a movie to mp4 format would work....

---

### Post by %hMa@?b&lt;C on 2006-11-01
you should try ffmpeg, there is definately some script for it around there.

---

### Post by Fittersman on 2006-11-01
whats that and how do i get it

---

### Post by Marsolin on 2006-11-02
You could try [PSPVC]("http://linuxappfinder.com/package/pspvc") or [HandBrake]("http://linuxappfinder.com/package/handbrake") instead.

What isn't working when you install [QPSPManager]("http://linuxappfinder.com/package/qpspmanager")?

---

### Post by Fittersman on 2006-11-02
the command qmake

---

### Post by bboyshane on 2006-11-02
You could use a couple of programs, DVD Rip is included in Edgy, it has excellent conversion tools. You could also use Mplayer, it also converts and encodes video files.

---

### Post by Fittersman on 2006-11-04
i cant find the DVD rip thing, where do i get that?

---

### Post by Marsolin on 2006-11-05
[dvd::rip]("http://linuxappfinder.com/package/dvdrip") is in the Ubuntu multiverse section. You can enable it through [Synaptic]("http://linuxappfinder.com/package/synaptic").

---

