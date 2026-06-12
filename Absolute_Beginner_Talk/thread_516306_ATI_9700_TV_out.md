---
title: "ATI 9700 TV out"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by stewils on 2007-08-03
Well, this question seems to have been asked quite a few times, but no answers...
I've been through on tutorial and installed the ati drivers, no problems, and now the tv out ALMOST works.  I get an out put signal but it's running at the wrong freq for my TV, so it scrolls and scrolls and scrolls...you get the idea at least I think thats the prob, it happens in windows, but there i just choose from a drop down menu.....
Have looked in xorg.conf but didn't se anything looking like a line saying tvout=ntsc or that kind of thing.....how do i change the output setting?
Running an ATI 9700 in a Fujitsu Seimens A130 Laptop on an AMD 64 processor.
Thanks for your help.

---

### Post by asmoore82 on 2007-08-04
I set out to make the S-Video out on my ATI 9500 IMB Thinkpad T42 work and ran into a few hiccups ...

then I reverted back to a vanilla xorg.conf and discovered that the dang ATI card would automagically
do a "clone display" for me if and only if the svideo was already connected to the tv
when X starts/restarts
maybe you could give that a shot.

if not, there is a command line tool (either aticonfig or aticontrol) that can add some very
useful lines to xorg.conf for you. check the manpage on that command.

---

### Post by stewils on 2007-08-05
Not the command line, nooooooo
Cheers, I'll check it out.

---

