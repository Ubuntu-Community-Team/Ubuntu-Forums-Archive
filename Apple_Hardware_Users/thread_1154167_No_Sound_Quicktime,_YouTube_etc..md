---
title: "No Sound Quicktime, YouTube etc."
date: 2009-05-09
forum: Apple Hardware Users
---

### Post by AussieHolden on 2009-05-09
I was hoping in this new version of Ubuntu that this problem would have been finally fixed I was wrong and I don't understand why it has been overlooked.

Any quicktime movies, clip and also youtube, flash player either does not display properly and all have no sound.

This is really bad for web surfing and trying to watch movie trailers etc.

:confused:

---

### Post by SilkySean on 2009-05-09
I have the same problem. I'm running an Imac PowerPC G4 with Ubuntu 9.04, but flash does not work at all within Firefox. Is there any way of activating it through gnash or swfdec?? I'm a complete noob at all this and google searches have brought me no closer to an answer. Help.

---

### Post by AussieHolden on 2009-05-09
It's even worse then I thought Ubuntu has no sound at all what the hell is going on ?????

---

### Post by stream303 on 2009-05-10
> **AussieHolden said:**
> I was hoping in this new version of Ubuntu that this problem would have been finally fixed I was wrong and I don't understand why it has been overlooked.

Any quicktime movies, clip and also youtube, flash player either does not display properly and all have no sound.

This is really bad for web surfing and trying to watch movie trailers etc.

:confused:

Don't hold your breath since this is not the fault of Ubuntu, nor ANY other ppc distro.

Until you can convince Apple and Adobe to release their code and specs to the Linux developers, the ppc boxes don't make very good multimedia machines.

Alternatives like gnash and swfdec are maturing, but in reality the ball is in YOUR court to help us all out by asking them politely to release the code and specs to the devs.

You forgot to add that just like above, we have to rely on 2D video drivers in many instances for the same reasons.  Speak to Nvidia and ATI about it.

Until then, one has to put their ppc box running Linux to other uses, ie servers, programming, photo-editing, community-involvement, etc.

As for your sound in general, have you tried making sure that your PCM and speaker levels are not muted?  Bring up ALSAMIXER in a terminal, and use your arrow keys, space keys, and M to toggle muting to bring up those up.  Hit ESC to exit.  Then see if your sound works - although you'll have to use some other sound source than flash videos in some cases.

In the end, a ppc box for the typical video multimedia is just not ideal at this point in time no matter what distro you use.

---

### Post by AussieHolden on 2009-05-10
I don't understand Geek Linux Speak.

In Ubuntu 8 this was all working 100% in Ubuntu 9 not one sound the whole system is silent someone stuffed up.

---

### Post by Benboom on 2009-05-10
I can't speak to the Quicktime and Flash issues but I installed 9.04 two days ago on my old G4 PPC (Sawtooth 450 mhz) and audio is working fine on it. I did have to turn up the line output level in alsamixer as it was set way too low out of the box, but that's the only thing that wasn't working right. It plays mp3s and right now I'm listening to a commercial CD with Rhythmbox.

---

### Post by AussieHolden on 2009-05-10
alsamixer has done nothing all level are at 100% and still no sound at all.

---

### Post by Benboom on 2009-05-10
So which Mac model was it again?

---

