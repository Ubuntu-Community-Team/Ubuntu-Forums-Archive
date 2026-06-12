---
title: "Encoding into Apple Lossless"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by RChickenMan on 2006-12-01
What can I say but "Wow".... Thinks are going GREAT in edgy.  Every single thing I have wanted to do with my computer, I have been able to accomplish, with just a bit of effort.  I have been able to play every single audio and video codec I can come accross, including Apple Lossless.  I haven't tried encoding any audio yet, and I am assuming I will be able to find a way with most codecs.  My only concern is Apple Lossless.  The reason I absolutely need support for this codec is because it is the only lossless codec supported by the Apple iPod.  I am concerned that due to the proprietary nature of this codec, I will be unable to do so.  Does anybody know if there is a way, and if so, how?  This is one of those small, random details that I want to iron out before deleting what I like to affectionatly refer to as my "capitalism partition" (i.e. windows).

---

### Post by christhemonkey on 2006-12-01
Decoding it should be no problem.

Encoding to it however...

---

### Post by RChickenMan on 2006-12-01
Yeah, like I said, I've already been able to successfully decode it.  I still need a solution to encode...

---

### Post by quarkhirad on 2006-12-01
Hey Rchickenman welcome to the wounderfull world of ubuntu. Yes what u have just experienced is what we all have experienced . Buy the way what all codecs have u tried because i cannot play some of the files like avi etc.

---

### Post by christhemonkey on 2006-12-01
According to this:
[http://craz.net/programs/itunes/alac.html](http://craz.net/programs/itunes/alac.html)

> Although an encoder is not provided, by using the decoder as a sort of specification it should be fairly trivial to write an encoder.


I dont think anyone has ever written an encoder (not that my googling skills could locate anyway!)

---

### Post by RChickenMan on 2006-12-01
When I get back to my computer (i am in a cubicle right now) I will post the link to a thread that I bookmarked that will basically set you up to play anything.  I have been able to play every single song in my music collection (AAC, Apple Lossless, MP3, etc.) and a few random .avi movies I have, not sure exactly what codecs they use.

---

### Post by RChickenMan on 2006-12-01
Well, when I get back to my ubuntu machine, I'll have to try running iTunes under WINE.  I know it barely works, from what I've read both the music store and iPod support are not functional.  Perhaps it works well enough just to encode things into apple lossless...

Still, hopefully someone can point us in the direction of a linux apple lossless encoder, if it exists.

---

### Post by christhemonkey on 2006-12-01
You could try runnning this in wine:
[http://forum.dbpoweramp.com/showthread.php?p=50839#post50839](http://forum.dbpoweramp.com/showthread.php?p=50839#post50839)

---

### Post by RChickenMan on 2006-12-01
Heh, I came accross the same exact thing on my pre-post google search.  Good call, though, I just saw it as a dead end... I'll give it a shot when I get home (or tomorrow, most likely).

EDIT: According to the source of all knowledge in the universe (wikipedia), DBPowerAmp (the software that, with the addition of a .dll, can encode apple lossless) is "fully compatible with Windows 95/98/ME NT4/2000, Windows XP and Linux (using WINE)"!!!!! Can't wait to give it a shot!

---

### Post by misterbeetz on 2006-12-02
I too would like to have a way to rip my cds into ALAC (apple lossless) format on Ubuntu.  Using Itunes to encode and sync this format to my ipod is probably the only reason a windows partition still sits on my hard drive.

Its a shame that this isn't already possible because the reverse-engineered ALAC decoding (and encoding) code is out there:
[http://crazney.net/programs/itunes/alac.html](http://crazney.net/programs/itunes/alac.html)

Hopefully someone will integrate this functionality into a music client like Banshee or something down the road.  Let us know if you eventually find a solution of doing this in Ubuntu.

-misterbeetz

---

### Post by RChickenMan on 2006-12-03
YES, I had success running dbPowerAmp under WINE!

---

### Post by misterbeetz on 2006-12-04
Does dbpoweramp rip cds or just convert music that was already ripped?

[B]EDIT: nevermind, looks like it does.
[/B]

One more thing though, let us know if the ALAC files play properly on your ipod.  A couple months ago I tried dbpoweramp a few times to convert FLAC files to ALAC and they didn't play properly on my ipod (photo).

- misterbeetz

---

### Post by RChickenMan on 2006-12-04
Sure, I'll see if I can get around to it when I go home this evening (I'm at the office at the moment).  I know it sounds terrible, but I'm a little apprehensive about adding things to my iPod via non-iTunes software due to a bad experience I have had.  I tried GTKPod (back in my KDE days) and it transferred thiings to the iPod just fine, but then it must of corrupted some kind of files on the iPod because it deleted all my playlists from the iPod, and if I tried to connect to iTunes in Windows, iTunes would crash (yeah, crappy software, poor error handling).  This time I will be trying Amorak, and using more concise sentences.

---

### Post by misterbeetz on 2006-12-05
I guess the question now is which music clients support syncing ALAC files to the ipod?

- misterbeetz

---

### Post by RChickenMan on 2006-12-05
I would actually think any of them which can play it, as long as the codec is installed on your system.

---

### Post by misterbeetz on 2006-12-05
I haven't been home for awhile so I haven't had a chance to try this all out. I'm worried though.  I read that Banshee will convert the less popular and less supported formats to mp3s on the fly when sending them over to the ipod.  I hope that isn't the case.

-misterbeetz

---

### Post by RChickenMan on 2006-12-06
Ironically, my iPod died, so I can't participate in this testing anymore.  However, it now gives me the opportunity to purchase a player which supports open source lossless audio codecs (iAudio X5 is all I can come up with).

---

### Post by misterbeetz on 2006-12-06
Nice i might check that one out myself then once my ipod kicks the bucket someday.

-misterbeetz

---

### Post by bofphile on 2006-12-08
This method (dBpowerAMP+amaroK) works fine with my ipod 5G. The only thing missing is to be able to set the "gapless flag".

---

### Post by misterbeetz on 2006-12-08
Excellent, thats good to hear.  I can't wait to try it out over the holidays.

-misterbeetz

---

