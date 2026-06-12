---
title: "CD Juicer Error"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-23
When I enter a cd into my laptop and try ripping it with soundjuicer, I get the following error
```
Sound Juicer could not extract this CD.
Reason: Could not open vfs file "file:///home/travis/Music/Rob%20Dougan/Furious0X0.00001BFB8C6D8P-1022ngels%20(disc%201)/03%20-%20Will%20You           -0.000000ollow%20Me-0.096777.m4a" for writing: Invalid parameters.
```

Second error
```
Sound Juicer could not extract this CD.
Reason: Error starting ripping pipeline
```

It makes it through the intro track then dies on the next one. The intro track on playback is really choppy. I've tried encoding in FLAC, AAC, and WAV. CD playback works fine in sound juicer, and the rest of my computer. There is no playback at the time of ripping. Any help?

---

### Post by Paulmd on 2008-01-23
> **imaginal said:**
> When I enter a cd into my laptop and try ripping it with soundjuicer, I get the following error
```
Sound Juicer could not extract this CD.
Reason: Could not open vfs file "file:///home/travis/Music/Rob%20Dougan/Furious0X0.00001BFB8C6D8P-1022ngels%20(disc%201)/03%20-%20Will%20You           -0.000000ollow%20Me-0.096777.m4a" for writing: Invalid parameters.
```

Second error
```
Sound Juicer could not extract this CD.
Reason: Error starting ripping pipeline
```

It makes it through the intro track then dies on the next one. The intro track on playback is really choppy. I've tried encoding in FLAC, AAC, and WAV. CD playback works fine in sound juicer, and the rest of my computer. There is no playback at the time of ripping. Any help?


Have you tried just playing the cd? It could be scratched.

---

### Post by imaginal on 2008-01-23
The CD is brand new without a scratch on it. Copyright 2003...there is no problem playing it, but it just won't rip. 
Some CDs look like they rip fine, but they only play a stutter of a sound once a second. So far, no successful rips.

How do I find out what is going on?

---

### Post by stchman on 2008-01-23
> **imaginal said:**
> When I enter a cd into my laptop and try ripping it with soundjuicer, I get the following error
```
Sound Juicer could not extract this CD.
Reason: Could not open vfs file "file:///home/travis/Music/Rob%20Dougan/Furious0X0.00001BFB8C6D8P-1022ngels%20(disc%201)/03%20-%20Will%20You           -0.000000ollow%20Me-0.096777.m4a" for writing: Invalid parameters.
```

Second error
```
Sound Juicer could not extract this CD.
Reason: Error starting ripping pipeline
```

It makes it through the intro track then dies on the next one. The intro track on playback is really choppy. I've tried encoding in FLAC, AAC, and WAV. CD playback works fine in sound juicer, and the rest of my computer. There is no playback at the time of ripping. Any help?

I have a tutorial on CD ripping using juicer.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

This works.

---

### Post by imaginal on 2008-01-23
I was missing a codec, and that is what gave me the issues with the stutter. (I was just missing one gstreamer entry)

However, the second song on this cd will not copy. Sort of. CDjuicer does its thing and gives the error message above. Playing the song, everything is fine except that the track time length is wrong (It is under by about 10 seconds). I have a feeling that this is what is crashing cdj, but I don't know for sure... any ideas?

---

