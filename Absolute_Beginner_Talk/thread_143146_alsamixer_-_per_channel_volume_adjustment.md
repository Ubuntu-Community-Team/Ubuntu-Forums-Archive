---
title: "alsamixer - per channel volume adjustment?"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-03-11
Hi,

I searched around and read the help screens and everything, but I can't seem to find a way to adjust a single channel's volume in alsamixer.

The reason I ask is because one of the speakers on my headphones was crushed slightly, so the sound comes out the right side a bit louder. I want to drop the volume on the right side only.

Is there an easier way to do it than through alsamixer ?

---

### Post by Kurt` on 2006-03-12
Nobody else here has a soundcard?

---

### Post by therunnyman on 2006-03-12
Hi Kurt`,

My arrangement is this: two soundcards, one inboard (traditional SB) and one outboard (USB).  To alter the volume, channel-wise:

>double click on the speaker icon up next to the clock, bringing up the Volume Control panel, window, whatever it's called.

>Below "PCM," you'll see the two channels, and, below that, a little graphic chain icon.  Click on that chain.  That unlocks the channels.

>Adjust channels to taste

Hope that helps.

therunnyman

---

### Post by Kurt` on 2006-03-12
Excellent, thank you. I didn't realize you could double click that. :)

For future reference, is there a way to do that from the aslamixer?

---

### Post by therunnyman on 2006-03-12
Hi Kurt`,

Looks to be.  From the alsamixer readme:

--start quote--

You can also control left & right levels for the current channel independently,
according to this chart:

Q  |  W  |  E    <-- UP
-------------
Z  |  X  |  C    <---DOWN

^     ^     ^
|     |     +-- Right
|     |
|     +--- Both
|
Left


If the current mixer channel is not a stereo channel, then all UP keys
will work like W, and all DOWN keys will work like X.

--endquote--

I popped into alsamixer to check it out; it's working here.

Hope that helps.

therunnyman

---

### Post by Kurt` on 2006-03-12
I had looked at the in-program help (? key), and it didn't mention those controls.

Thanks!

---

