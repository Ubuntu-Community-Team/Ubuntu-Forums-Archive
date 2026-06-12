---
title: "How to turn down the mac startup chime on PPC"
date: 2011-03-06
forum: Apple Hardware Users
---

### Post by rsavage on 2011-03-06
This took me quite a few restarts to figure out so I thought I'd share it with you.  

The loud chime has been bugging me for quite a while now although it was only today that I had a serious look into fixing it.  I'd read quite a few times that this couldn't be done without a Mac OS and even recently on this forum there was the statement the "startup chime can't be controlled from within Linux".  Well after a bit of googling on the subject it turns out that you can turn the volume down from within liunx.  In fact, it is really easy on a PowerPC.

If you only want to turn off the chime occasionally then you can do this by holding down mute (e.g. Fn + F3) when you turn the machine on.

If you want to lower the volume or turn it off permanently then you can use the nvsetvol command which is installed by default (part of the powerpc-utils package).  

The manual page (type "man nvsetvol" at a terminal) says you need to specify a number between 0 and 255.  0 turns off the chime.  Running without a parameter gives the current level.  Sounds easy huh?

So "sudo nvsetvol" gave me the value 27.  Funny number huh?  Typing "sudo nvsetvol 10" and restart gave a lower chime.  Good.  Typing "sudo nvsetvol 5" and a restart gave a loud chime.  Problem. Typing "sudo nvsetvol 0" and a restart did indeed turn off the chime and it was very weird not to have it!

So I wanted the chime, but at the lowest possible level.  Problem was what number would give that?  Clearly it was not a straightforward 0-255 scale.

A bit more googling didn't bring much more information.  Except people had reported that when they use "sudo nvsetvol 0" it gets reset when they boot into Mac OS.  Also if you use a Mac OS utility to mute the chime then "sudo nvsetvol" returns the value 24 not 0 ([http://us.generation-nt.com/answer/re-how-can-i-get-rid-starting-bong-g4-mac-mini-help-170220551.html](http://us.generation-nt.com/answer/re-how-can-i-get-rid-starting-bong-g4-mac-mini-help-170220551.html)).  

So after playing around my theory is this:

Looking at the number as a byte, then it is the 3 least significant bits that set the volume.  The 3 most significant bits probably don't have any effect.  And the two in the middle I can't figure out except they probably should be a '1'.  

So the number range you are looking at is 24 (mute) to 31 (full volume).  25 would be the lowest audible chime.

The range 0 to 7 also works, but the two bits I am unsure of are not set using these values.  My theory is that this is why Mac OS resets the volume when 0 is given (it must do a check and considers the number out of range).

Can somebody with Mac OS confirm that values 24 to 31 are retained and not reset please? Perhaps then we could update the manual for nvsetvol?

---

