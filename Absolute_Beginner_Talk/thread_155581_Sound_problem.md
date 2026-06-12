---
title: "Sound problem"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by stravinsky on 2006-04-05
Dear Ubuntusers!

My Ubuntu cannot make the sound work properly on my computer... I have an external Sound Blaster MP3+ USB sound card, which is recognized, but when I put a cd, the sound has got problems at regular intervals of 1-2 seconds. When I put a DVD, the problem occurs as well, but with shorter intervals! When trying an MP3, it worked, but when I would do something else, it would also "jump" or have problems... Is this due to the Totem player or is it something else?

I've already tried the "Gnome Sound Fix" with Automatix...

Thanks.

---

### Post by Mustard on 2006-04-05
Hmm..first I have ever heard of an external sound card. :)

I wonder whether its an issue with not having DMA enabled (assuming your hardware supports DMA).

Have a read over this page and see if it sounds like it might be something you could try...
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by stravinsky on 2006-04-05
Thanks a lot. It could indeed be the problem... I will have a look at it as soon as I can.
Have a nice day!

---

### Post by stravinsky on 2006-04-05
I've tried the DMA thing ([https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)) and it has solved my problem! Thank you again very much for your help!

---

### Post by Mustard on 2006-04-05
[QUOTE=stravinsky]I've tried the DMA thing ([https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)) and it has solved my problem! Thank you again very much for your help![/QUOTE]

Ah..thats good.  I'm glad you managed to fix the issue. :)

---

### Post by stravinsky on 2006-04-06
Now I seem to have a new problem: when I try to listen to MP3s files, the sound starts through my USB sound card (which is good), but then it stops and starts again using my laptop's sound card (and thus my laptop's speakers). The strange thing is that this issue doesn't appear when reading music from normal CDs, or music/audio from DVDs. It only appears when reading MP3s or WAV (and maybe other files). How do I make Ubuntu use all the time my USB sound card?

Thanks in advance.

---

### Post by Mustard on 2006-04-06
I have to admit you have me completely stumped on that question. :)  The only thing I can think of it that somehow different codecs might be set up to play with different default settings (somewhere, somehow).  That's my complete unsubstantiated guesswork on this problem.  I think you might like to try googling around for others that have used your soundcard system on linux (in particular Ubuntu) and see if you can discover someone who had a similar experience and documented a solution.

In the meantime, hopefully someone comes along that knows the answer in this forum. :)

---

### Post by stravinsky on 2006-04-07
[QUOTE=Mustard]hopefully someone comes along that knows the answer in this forum. :)[/QUOTE]
Yes indeed :neutral:
Anyway, thank you very much for your help Mustard.

---

### Post by stravinsky on 2006-04-08
I think that this issue is actually linked with the problem with my CD eject button! (see my other post here: [http://www.ubuntuforums.org/showthread.php?t=155778](http://www.ubuntuforums.org/showthread.php?t=155778))
I think so because WAV/MP3 files work fine when they are on my hard disk! The problem that it changes sound card only happens when those files are on a CD...
So now I ask a new question: can I undo things done with Automatix? If so, how? If not, can I reset my configuration to the default? (I didn't do much yet in any case).
Thanks for your help!

---

### Post by Mustard on 2006-04-08
I think uninstalling Automatix is covered in a thread in the Automatix section of the forum.  I don't use it, so I don't have much of an idea how you would go about it.

---

