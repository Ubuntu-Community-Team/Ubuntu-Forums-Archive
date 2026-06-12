---
title: "AMR MP3 conversion"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Bias on 2007-05-19
Hi,

Been looking for some software that will convert between AMR and MP3 formats (preferably in both directions). So far no luck.

Anyone know of anything that will do this?

Thanks,

Nick.

---

### Post by diatribe on 2007-05-19
google amr mp3 conversion ubuntu

---

### Post by Bias on 2007-05-21
Genius! I hadn't thought of that.

---

### Post by apienk01 on 2007-05-21
ffmpeg. It converts video formats, but also works for audio. Can be installed using apt-get or synaptic.

Just type:

```
ffmpeg -i file.amr file.mp3
```

If it doesn't work, you probably need to recompile ffmpeg from source. Use the guide on [this]("http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu-edgy/") page.

---

### Post by Bias on 2007-05-24
> **apienk01 said:**
> ffmpeg. It converts video formats, but also works for audio. Can be installed using apt-get or synaptic.

Just type:

```
ffmpeg -i file.amr file.mp3
```

If it doesn't work, you probably need to recompile ffmpeg from source. Use the guide on [this]("http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu-edgy/") page.


Thanks for that, didn't actually work and the complie instructions failed (they are not for dapper, should have checked first :)). However the ffmpeg thing did point me in the right direction and I came accross this:-

[http://www.miksoft.net/mmc-lin.tar.gz](http://www.miksoft.net/mmc-lin.tar.gz)

Basically put both files in a directory and run the one called mobile media converter. The other file is a version of ffmpeg, I found the version I had and that auto updates installs didn't work but by having this version in the same directory mmc uses it instead of the recommended one and the recommended one is used by the rest of the system.
The interface is a bit clunky but it does the job so I'm a happy psycho clown :)

Thanks.

Nick.

---

### Post by AVH on 2007-06-30
the link "http://www.miksoft.net/mmc-lin.tar.gz" is dead

---

### Post by whawes on 2007-09-15
> **AVH said:**
> the link "http://www.miksoft.net/mmc-lin.tar.gz" is dead

Yes it is, although the product itself still exists and can be downloaded from [http://www.miksoft.net/](http://www.miksoft.net/). Seems to work well too :-)

---

