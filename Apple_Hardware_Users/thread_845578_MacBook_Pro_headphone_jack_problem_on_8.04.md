---
title: "MacBook Pro headphone jack problem on 8.04"
date: 2008-06-30
forum: Apple Hardware Users
---

### Post by Dacobi on 2008-06-30
Hello all

I have a sound problem with my MBP.
When i plug in my headphones the volume on the internal speakers doesn't mute.
I do however get sound in my headphones as well.

I've tried all sorts of things in alsa-mixer and tried adding model=mbp as an option to the snd-hda-intel module but with no luck.

My MBP is the original Core Duo model with the
HDA Intel SigmaTel STAC9221 A1 audio chip

Anyone got a solution?

/Dacobi

---

### Post by bertvv on 2008-08-04
Sorry, i can only say: "Me too!"

---

### Post by rifak on 2008-08-17
a little late, but just ran across this thread. i had the same problem. here is how i solved:

1) go to system, preferences, sound
2) in the devices tab, change the device to HDA Intel (ALSA mixer)

it worked then. i was able to plug in external speakers and headphones and have the comps speaker shut off.

---

### Post by MaddMatt on 2008-10-12
Good show! 

I don't know why that worked, but it did. 

Cheers!

---

