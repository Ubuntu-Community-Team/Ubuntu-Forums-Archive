---
title: "[SOLVED] can't get sound to work with GTick metronome"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-03-17
I am trying to use the GTick metronome but whenever I try to start it it gives me this error

[I]Couldn't start metronome.
Please check if specified sound device
and sample file are accessible.[/I]

I went to the apps website and looked at the FAQ. It says to make sure that the /dev/dsp* folder exists. Mine doesn't!

I am using the ALSA sound drivers.
GTick has an option in its preferences to specify where the device "filename" is.
The default is /dev/dsp


Thanks

---

### Post by penguinpi.com on 2008-03-18
Does that app use midi? try to install timidity

I think you can apt-get timidity-server

and make sure you go to the terminal and type timidity start

see if that does it, if it does then you might want to add the command timidity start to run when your computer boots up

---

### Post by audunpoi on 2008-03-20
I'm a total beginner, so sorry if I miss something here. However I had the same error message and fixed it by changing the line in GTick preferences to " /dev/dsp2 ".
Look in your /dev folder for dsp1, dsp2 etc and try them. Hope this helps.

---

### Post by elchico04 on 2008-03-20
hey that did the trick! thanks a lot.

---

### Post by eiffel on 2008-07-13
[edit] Worked for me with settings Sound -> Default and Sound device filename -> /dev/dsp

---

