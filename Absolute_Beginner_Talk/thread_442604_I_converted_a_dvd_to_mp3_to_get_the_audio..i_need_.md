---
title: "I converted a dvd to mp3 to get the audio..i need something to split it"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by dreamwarrior on 2007-05-13
HI...i converted a dvd to mp3 to get the audio..its sounds good,but i would like to trim it into several separate tracks ,to make it audio cd later,...i tried Audacity,but it only cuts automatically,and that doesnt work for me,because  theres no space gaps between the songs,as in any cd ..i need to spit them in any place i choose ...i installed "rezound" which is an audio editor but it doesnt appear in the aplication list..how can i make it appear to use it?i dont know how to run it from the terminal(can anyone tell me how?)....any help so i can use this program or if someone can tell me another one i can use to do this job? thanks in advance....

---

### Post by Paradoxdruid on 2007-05-13
Just wanted to chime in and tell you to give Audacity another shot, because it definitely can cut wherever you want--  I use it to make cellphone ringtones out of mp3s.

---

### Post by dreamwarrior on 2007-05-13
> **Paradoxdruid said:**
> Just wanted to chime in and tell you to give Audacity another shot, because it definitely can cut wherever you want--  I use it to make cellphone ringtones out of mp3s.

hi and thanks for answeing....can you tell me how can i do that with Audacity?cause when i run it,i only found the find th auto trim button available...i see the trim button,but its not enable...any help?

---

### Post by lluisanunez on 2007-05-13
Just click on the wave and select, and then cut, copy, paste...

---

### Post by dreamwarrior on 2007-05-13
thanks  for your help...i appreciate it

---

### Post by SuperMike on 2007-09-02
Have you tried 'ecasound'? That's what I use.

---

### Post by meho_r on 2007-09-29
One more Q: is there some tool that does splitting/joining nondestructively? Because, if you use Audacity and similar apps, you get your mp3 file encoded again and again which results in quality loss. Some time ago I used a little utility, Mp3cutter or something like that (on Win;) and wonder is there some alternative on Linux. I know there are mp3splt and mp3wrap, but it'll be nice to have some GUI :)

---

### Post by lluisanunez on 2007-09-30
To avoid quality loss you should always work on audacity format, I think it's **.au**, and export to mp3 only when you're done editing.

---

### Post by rahimveron on 2007-09-30
Thanks for the format tip

---

### Post by meho_r on 2007-10-01
> **lluisanunez said:**
> To avoid quality loss you should always work on audacity format, I think it's **.au**, and export to mp3 only when you're done editing.

It's OK if you have original audio files. But if don't have them, only mp3? Using Audacity in this case leads to quality loss because of reencoding. 

BTW, I've found yesterday a nice little app, mp3DirectCut which does the job :) It is Win app, but works with Wine just fine.

---

### Post by vanadium on 2007-10-01
Next time, convert your DVD audio to a lossless format such as wav. Then open the WAV in Audacity. Place labels on the places where you want to split the audio. When done, write out the audio to separate WAV's (or directly to ogg or mp3) using Export - Multiple.

Splitting mp3's after the fact will work more or less, except where there is no silence at the split point. Indeed, you will end up with clicks between subsequent tracks, when playing back the mp3's AND when creating an audio CD from the mp3s.

To avoid the slightest click between tracks on an audio CD, make sure you split on CD sector boundaries. This is very easily accomplished in Audacity: make sure the timeline is set to CDDA frames and that "Snap to" is set to "on". This way, your markers will automatically be placed on good CD sector boundaries.

---

