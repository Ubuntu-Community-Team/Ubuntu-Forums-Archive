---
title: "Convert  full .wav to 30 second .mp3"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by esd2609 on 2006-07-13
Hi,

I need to convert about 1,500 full length .wav files to 30 second .mp3 preview tracks.  I've used LAME before to convert wav to mp3 but I don't think it supports time cropping.

Any suggestions for a program that can either crop the wav or mp3 files?  I'd like to be able to do it with some kind of script or batch mode rather than selecting individual files.  


I appreciate any help you can offer.

---

### Post by Arisna on 2006-07-13
It sounds like sox would do it for you with its "trim" parameter.  You would need to run sox on the .wav files and then pass the trimmed samples to lame.  Sox, like lame, is command-line, so scripting is very possible.

---

### Post by esd2609 on 2006-07-13
Great suggestion.  Sox seems like it's what I'm looking for.

Thanks.

---

