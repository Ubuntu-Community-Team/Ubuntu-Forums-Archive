---
title: "[SOLVED] Convert .mid to .ogg"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-12-02
I'd like to convert some of my .mid files to .ogg - I've tried Audacity, which seems to work, but the output files are much smaller and both Banshee and Exaile show them as 0.00 length. I don't get any error messages.

I've looked at SoundConverter  which doesn't support .mid, and Timidity which I'm just not very successful with at all. :)

Any advice on this?

TIA

---

### Post by goodmanbrown on 2007-12-02
I think timidity actually is the best tool for this.  Have you tried this command:

```
timidity -Ov *.mid
```

(The -Ov tells it to output a vorbis file.)

I usually use timidity to output wav files, and then use whatever encoders I want on the wav file.  The command for that is:

```
timidity -Ow *.mid
```

---

