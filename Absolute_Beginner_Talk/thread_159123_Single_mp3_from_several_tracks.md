---
title: "Single mp3 from several tracks"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by GeorgeAD on 2006-04-12
Sometimes it'd be good to be able record several tracks on a cd as a single mp3, where sound runs on from one track to the next as on many classical recordings, for example. In windows, audiograbber allows you to specify where a track begins and ends, so you can tell it that the piece you want is a single track; alternatively there is a program that joins mp3s together. Is there anything like that for linux? 

cheers, 
George

---

### Post by Dogmeat on 2006-04-12
I never had to do that, so I really can't tell you which program does it. You can however join the tracks from the command line with cat:

```
cat track1.mp3 track2.mp3 track3.mp3 > joinedtracks.mp3
```

where trackX.mp3 are the tracks you want to join and joinedtracks.mp3 is a single mp3 with all the tracks (it will be in the current directory where you ran cat)

Alternatively you can move every track you want to join into a directory, and type in this directory:

```
cat *.mp3 > joinedtracks.mp3
```

Note that with this method they will be ordered by their name. Someone else will probably tell of you of a good program to join tracks, but for now this should do the trick.

---

### Post by GeorgeAD on 2006-04-13
Thanks Dogmeat, that's exactly what I wanted. One slight problem is that you can hear a small gap where the files are joined. Maybe though that's from the files joined rather than an effect of the joining. I'll try re-recording.

---

### Post by GeorgeAD on 2006-04-14
Still a gap! So does anyone know of an encoding program with an option to record lots of tracks to a single mp3 file? 

cheers, 
George

---

### Post by Dogmeat on 2006-05-04
I found Audacity does what you want, you can copy/paste parts  of tracks in it, so if you're patient you can paste together all the tracks. Or you can cat then together, then edit out the gaps.

---

### Post by aysiu on 2006-05-04
[MP3Wrap is your friend](http://ubuntuforums.org/showpost.php?p=802467&postcount=11).

---

### Post by GeorgeAD on 2006-08-19
Thanks aysiu, I'll try that

---

