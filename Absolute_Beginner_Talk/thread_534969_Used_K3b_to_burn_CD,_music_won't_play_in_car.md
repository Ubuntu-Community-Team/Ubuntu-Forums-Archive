---
title: "Used K3b to burn CD, music won't play in car?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-08-25
I recently bought a bunch of CD-Rs, to burn some CDs.  I have some burnt CD-Rs that play fine in the car.  This is the first time that I have tried to burn a CD in ubuntu, and it won't play in the car.  I can burn them and pop them into my computer, but the car's CD player won't recognize them or something.  Any ideas before I waste more blank CDs?

---

### Post by slimdog360 on 2007-08-25
check out wha format the music files are in on the cds that wont play. My guess is that you have burnt them as mp3s.

---

### Post by Specter043 on 2007-08-25
What should I burn them as to play them in the car?

---

### Post by nonewmsgs on 2007-08-25
music or cd audio.  also to verify the format try another cdplayer.

---

### Post by nonewmsgs on 2007-08-25
new audio cd (i just installed it on this laptop now)

---

### Post by TeaSwigger on 2007-08-26
> **Specter043 said:**
> What should I burn them as to play them in the car?

Probably a lot more than you want to know, but hey I'm waiting for an herbal tea to steep so I'm going to ramble. Maybe someone will find it enlightening. It's grossly simplified.

A standard, proper "audio CD" has its own setup I guess you might say, having been established before personal computers started using the CD for data. Different file type, different layout, different this and that. If it's called anything it's referred to as "redbook" (after a casual term for the formal Compact Disc Digital Audio standards). CDs for computer use have a variety of "setups" we'll refer to generically as "data CDs." The old "redbook" standard is less accurate with less provision for error recovery than "data CDs," which is why you might hear differences in burning speeds, media, ripper methods and other recording and playback factors with an "audio CD" but probably not if it had used "data CD" standards, but that's a matter hotly debated in some circles and is anyway neither here nor there.

When you "rip" a CD, it naturally turns the data into a computer file. An example of a file capturing the entire data recovered from the CD (lossless) is .wav. An example of a data-compressed file which captures the entire data (lossless) is .flac. An example of a file which throws out sonic data thought to be less important by increasing degrees according to desired mbps rate (lossy) is .mp3. Obviously, not involving lossy files in the process will make for the most sonically accurate results.

When you create an audio CD you have two principal factors involved: 

- The computer file(s) must be converted into the audio CD form to be recorded on the disc.

- The disc must be "authored" according to "redbook" spec, not any of the "data CD" setups.

In k3b, you have to specifically chose to "make an audio CD." If you have an mp3 or ogg or flac or whatever, k3b should convert the files and author the CD as an audio CD you can play on any audio CD player that will read the media (not all will, but that doesn't seem to be the problem). Try it again with that in mind and if you have any questions or problems, come on back. Right now I gotta go, my tea's ready :)

---

### Post by wormser on 2007-08-26
Burn the CD at the slowest speed.  It can resolve the issue sometimes.  Usually older CD players have trouble with some CDR brands.  That could be the issue.

---

### Post by Specter043 on 2007-09-16
Turned out to be my disk drive.  popped in another one and it worked fine.

---

