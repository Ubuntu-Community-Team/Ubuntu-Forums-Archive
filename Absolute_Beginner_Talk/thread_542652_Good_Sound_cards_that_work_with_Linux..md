---
title: "Good Sound cards that work with Linux."
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-09-04
I'm getting a new Rig soon ([http://jamesbowden.com/~james/miscellaneous/newpc.txt](http://jamesbowden.com/~james/miscellaneous/newpc.txt)) but I have been told that the sound card I have picked does not work on Linux.

does anyone know of any sounds cards around the same quality as the Creative SoundBlaster X-Fi Xtreme Audio Soundcard that will work well on Linux and Windows.

Thanks
James

---

### Post by Jon@bayleys.org.uk on 2007-09-04
I've got an Audigy 2 ZS Platinum Pro seems to be supported perfectly. I do a lot of music recording, the inputs all seem to work OK, including those on the breakout box.

---

### Post by Jamesbowden on 2007-09-04
> **Jon@bayleys.org.uk said:**
> I've got an Audigy 2 ZS Platinum Pro seems to be supported perfectly. I do a lot of music recording, the inputs all seem to work OK, including those on the breakout box.

Thanks, I'll look around for that card.

---

### Post by daverich on 2007-09-04
if you want better than that the RME HDSP cards work under linux, and are pretty reasonable for the quality.

Kind regards

Dave Rich

---

### Post by bobpur on 2007-09-04
The Diamond Xtreme from Diamond Multimedia in 5.1 or7.1 versions work well in linux and the price is excellent for the sound that coms from them.
What hooked me on these cards is that they com with open source software bundled in.
Oh yeah, the price is about $30-$40 from Staples or Newegg.com. Better than $100+ for an X-Fi card that only works under Windows. 
The sound difference is not worth mentioning except on the extreme top end. Creative is better then.

---

### Post by Jamesbowden on 2007-09-04
> **bobpur said:**
> The Diamond Xtreme from Diamond Multimedia in 5.1 or7.1 versions work well in linux and the price is excellent for the sound that coms from them.
What hooked me on these cards is that they com with open source software bundled in.
Oh yeah, the price is about $30-$40 from Staples or Newegg.com. Better than $100+ for an X-Fi card that only works under Windows. 
The sound difference is not worth mentioning except on the extreme top end. Creative is better then.

thanks for this suggestion, this price tag is a lot more in my price range. :)

---

### Post by Fingolfin on 2007-10-13
It was expected that Creative will come with Linux drivers for the X-Fi Xtreme cards at some point in 2007.
What is the prevalent opinion within Ubuntu community at the moment? 
Is it wise to buy one of the X-Fi Xtreme card and hope that it will work with Ubuntu 7.10 or, as suggested here, Diamond models or older Audigy 2 cards are the safer option?
Any experience with "Pinnacle M-Audio Revolution 5.1" under Ubuntu maybe?

If someone knows, can you please explain for the rest of us, what advantage is there with the Xtreme models over the non-Creative models (in terms of mp3 reproduction and also encoding in particular when one wants to transfer music from original CDs into mp3?).

Another question I would put here (trust it is not considered too much off-topic): when reading the sound cards specs, what will tell that the card has an interface that connects it to the front panel lines-in/out/mic? Or this is not mentioned specifically as all cards are supposed to have some sort of the internal connector (similar to the internal usbs which also connect to the front panel)?

---

### Post by Daveth on 2007-10-13
a beta X-Fi 64 bit driver is here

[http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI)

but is unsupported and quite probably buggy, as well as being 64 bit. But at least it exists, which is a stage on in the right direction

---

### Post by Fingolfin on 2007-10-20
Interesting enough, Audigy 2 cards can not be found available from the retailers nowdays.
But this was very useful link, if 64-bit drivers are there (even in beta version) for Creative Xtreme cards, that should hopefully mean that we might have the fully functional drivers for Linux in very near future.

---

### Post by tonytraductor on 2007-11-20
> **bobpur said:**
> The Diamond Xtreme from Diamond Multimedia in 5.1 or7.1 versions work well in linux and the price is excellent for the sound that coms from them.
What hooked me on these cards is that they com with open source software bundled in.
Oh yeah, the price is about $30-$40 from Staples or Newegg.com. Better than $100+ for an X-Fi card that only works under Windows. 
The sound difference is not worth mentioning except on the extreme top end. Creative is better then.

Did you have to dig up and install a driver, or was that one of the many already bundled in
a default kernel?
I just got the 5.1 and installed it, and it appears to be detected, but I have no sound.
Everything is plugged in, Kmix is all set up, etc., but no sound comes out.

thanks
tony

---

### Post by raashell on 2008-02-29
Actually, I'm having problems getting surround sound detected for the Diamond Xtreme 5.1 also.  I've messed around in Alsamixer and with the volume turning settings on and off without much luck.  So far I can get sound in my front and rear speakers, but not from my center or sub.  I bought this card on the recommendation above, because I was having similar problems with a Creative Labs Audigy SE.  Any help would be appreciated.  Thanks, John

Below is a bit of code that I tried with no discernible results for a .asoundrc 

pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}

---

