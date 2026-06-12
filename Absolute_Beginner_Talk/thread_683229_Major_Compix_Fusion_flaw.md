---
title: "Major Compix Fusion flaw"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-30
I don't know if any one else has noticed this, but with Beryl, using the Cube or, a more noticeable fault, using the water effect, it would take nearly no processing power, and I believe this is because it ran the effects solely on the video card.  As far as I can tell, Compiz Fusion is using the CPU for effects such as fire, water, and most other things.  This is absolutely stupid, and I think someone should work on setting it back the way it was!  My technical reasoning follows:

**With the Beryl "All-on-Video Card-concept":**[LIST]
[*]CPU is left untouched by effects leaving it free to do things it actually needs to.
[*]The video card was designed for this, and is thus very good at doing it easily.  The CPU was not, and therefor requires 1000x more cycles to run the effects, hindering their performance and also that of everything else![/LIST][B]With the Compiz Fusion"All-on-CPU-concept":
[/B][LIST]
[*]It is a waste of CPU cycles to run effects that the video card can do easily!  Everything has a purpose, and something it's good at - the video card was made for stuff like this, and the CPU was made for processing and running the OS and apps, not 3D![/LIST]So basically my point is that Beryl did things right by using the video card for the effects, and Compiz Fusion is doing things *wrong* by using the CPU.

---

### Post by Joeb454 on 2008-01-30
Surely this would have been better posted in the Compiz-Fusion forums?

Send them an email asking why they don't do it that way if you feel that strongly about it :)

---

### Post by jordanmthomas on 2008-01-30
I think this is more likely a problem with your graphics card / drivers than with compiz.  Are you using different drivers now than you were when you used beryl?  

Blur used to work for me right when it came out, but eventually it used shaders that my graphics card didn't support, so it went to using the CPU (making it unusable for me).  I don't think compiz runs just on CPU now.

Beryl is basically the "fusion" part (the plugins).

---

### Post by oedha on 2008-01-30
people here : [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)
will help you...they're nice too

~E~

---

### Post by ryanVickers on 2008-01-30
ok, I should be able to solve it now I guess...

---

