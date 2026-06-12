---
title: "Sound Juicer output format problem"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2008-04-10
I'm trying to rip a CD to mp3. I've installed all the requirements and there is an entry in the edit profiles section as seen in the first picture below. However, this profile does no exist in the list "output format" even though it is ticked as "active" seen in the second picture. I have tried restarting my computer, restarting sound juicer and patience. None of this has worked.
[IMG]http://lh5.ggpht.com/albertblack/R_3YlzC0gjI/AAAAAAAAAJA/GNG7ZiELiL0/s800/Screenshot-1.png[/IMG]
[IMG]http://lh4.ggpht.com/albertblack/R_3YljC0giI/AAAAAAAAAI4/qmx7X0vfLRo/s800/Screenshot.png[/IMG]

---

### Post by jw5801 on 2008-04-10
I'd be inclined to give GRip a try ```
sudo apt-get install grip
```

Then you can use the how-to [here](http://ubuntuforums.org/showthread.php?t=183125) to set up decent mp3 encoding. I'm a bit picky but I don't like using anything that doesn't give me any options as to the bitrate I'm encoding at :p

---

### Post by scramasax on 2008-04-10
> **jw5801 said:**
> I'm a bit picky but I don't like using anything that doesn't give me any options as to the bitrate I'm encoding at :p

But you can do that in Sound Juicer -- that's what the "Editing profile" dialogue is for.

Anyway, you don't want to be setting an explicit bitrate for LAME MP3.  It's best used in a VBR mode with with a quality setting, just the same as with Vorbis.

---

### Post by scramasax on 2008-04-10
> **farueulogy said:**
> I'm trying to rip a CD to mp3. I've installed all the requirements 

Does that include everything mentioned here?

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

That's from 2005, but there are some fairly recent links pointing to it.

---

### Post by jw5801 on 2008-04-10
> **scramasax said:**
> But you can do that in Sound Juicer -- that's what the "Editing profile" dialogue is for.

Anyway, you don't want to be setting an explicit bitrate for LAME MP3.  It's best used in a VBR mode with with a quality setting, just the same as with Vorbis.

Ah ok, haven't used Sound Juicer much so I thought I'd recommend something I know will work properly. ```
lame -V 2 --vbr-new
```is the preset I normally go with. Although I believe the --vbr-new is redundant in the more recent versions of lame.

---

### Post by SlappyPappy on 2008-04-10
> **scramasax said:**
> But you can do that in Sound Juicer -- that's what the "Editing profile" dialogue is for.

Anyway, you don't want to be setting an explicit bitrate for LAME MP3.  It's best used in a VBR mode with with a quality setting, just the same as with Vorbis.

I don't think that works in SoundJuicier. I tried.

---

