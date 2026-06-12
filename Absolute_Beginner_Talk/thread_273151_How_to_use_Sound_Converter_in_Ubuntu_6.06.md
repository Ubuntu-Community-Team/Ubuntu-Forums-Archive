---
title: "How to use Sound Converter in Ubuntu 6.06?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Khayembii Communique on 2006-10-07
I have a lot of CD's on my computer that I imported to use for iTunes (I have dual boot).  These CD's were imported into .m4a format.  I was told that I could convert .m4a into .mp3 using Sound Converter, so I would like to convert all of my CD files into .mp3 files.

The problem I'm having is that I add an .m4a file to Sound Converter, and hit convert.  It loads for a bit then a load bar in the bottom pops up with the writing next to it saying "Conversion done, in x seconds" (x being any arbitrary number from like 2 to 5).  The load bar never changes (it's always at 0) and the files aren't converted since I told Sound Converter to put them on my desktop when they're converted, and they're not there yet.

What am I doing wrong?  How can I get these files converted to .mp3 or .ogg so I can play them with Rhythmbox?

---

### Post by CameronCalver on 2006-12-28
I am trying to convert from .ogg and .mp3 and convert  to .wav but i click convert and it says 
```
converted in 2seconds
``` but in the folder there is nothing](*,)

---

### Post by lukew on 2007-01-20
> **CameronCalver said:**
> I am trying to convert from .ogg and .mp3 and convert  to .wav but i click convert and it says 
```
converted in 2seconds
``` but in the folder there is nothing](*,)

How about something more like.....

```


for i in *.m4a; do
    mplayer -ao pcm "$i" -ao pcm:file="${i%.m4a}.wav"
done


# Convert WAV 2 MP3
 for i in *.wav; do
    lame -h -b 192 "$i" "${i%.wav}.mp3"
done

rm *.wav

```

---

