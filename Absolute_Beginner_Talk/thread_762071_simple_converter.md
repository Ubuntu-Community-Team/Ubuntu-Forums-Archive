---
title: "simple converter"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by lunaluna on 2008-04-21
i want a simple converter for exchange,length,weight....etc all kind of things
so i could calculate quickly nice and easily...
so?

---

### Post by PeterJS on 2008-04-21
The google calculator maybe?

Just google:
Value unit X in unit Y

---

### Post by slibuntu on 2008-04-21
[http://prdownload.berlios.de/convertall/convertall-0.4.1.tar.gz]("http://prdownload.berlios.de/convertall/convertall-0.4.1.tar.gz")

should do the job I think   :)

---

### Post by LeoSolaris on 2008-04-21
convertall is in the repos. I just installed it from Synaptic.

Just search for "convertall" in Syn or Aptitude to save yourself the trouble of installing it from an unknown source.

Leo

---

### Post by nhandler on 2008-04-21
You can do some types of conversions using an applications called "units". It is a terminal application. Just type "units" in a terminal to launch it. After that, you enter what you have, and what you want it converted into.

---

### Post by Endolith on 2008-05-03
Does anyone know of a program that provides the same functionality as Google Calculator?  I've talked to the guy who wrote it and he says it was custom-written by them.  Has anyone tried to reproduce the functionality in an open-source program?

I know Deskbar applet has a calculator handler and a converter handler [that can be used together]("http://twoday.tuwien.ac.at/jo/stories/311493/"), but that only lets you do things like "100 + 5 + 3 feet in miles".  It doesn't let you do things like "100 feet + 5 inches + 3 km in yards" or "100 V / 5 ohms".  I want a program that I can just type equations like these into and it will give me both a mathematical formula equivalent to show me it's calculating the right way and the answer I'm looking for.  Like Google Calculator, but with more functionality.  GNU Units could be part of the backend, most likely.

Looks like someone is paying for a library to be written: [http://www.getacoder.com/projects/google_calculator_library_52708.html](http://www.getacoder.com/projects/google_calculator_library_52708.html)

---

### Post by Endolith on 2008-05-04
I just realized Maxima has units, too, if you type ```
load("unit");
```

---

### Post by Endolith on 2008-05-30
Oh!  I didn't realize GNU units could do all of these things.  That's what happens with command line tools, I guess.  But you can do all those things:

```

units -1v "100 feet + 5 inches + 3 km" yards
units -1v "100 V / 5 ohms" A
units -1v "furlong per fortnight" cm/minute
units -1v attoparsec/microfortnight inch/sec
units -1v "three hundred + seventy million - pi"
units -1v "5 million pounds" megakilogram
units -1v "1/(2*pi*sqrt(10*microF*100 mH))" Hz
units -1v "sqrt(mu0/epsilon0)" ohm
```

Almost like Google Calculator

---

