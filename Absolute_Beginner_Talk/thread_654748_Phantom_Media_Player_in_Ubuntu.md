---
title: "Phantom Media Player in Ubuntu"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2007-12-31
Hey,

I'm rather new to Ubuntu so I don't know all the tricks and programs and such.

I just had a question, I ripped a CD using ubuntu's rip feature (right click >> copy) and they all came out as .ogg files - now I don't know what in the blue hell an ogg file is but I don't care - I wanted to make them MP3's.  So I opened up convert-it, set it to MP3, added the folder, the status bar flew by, made 7 (only 7 songs on this album) songs in .mp3 format - NONE OF THEM WORK.  It gives me some ******** error message shown below:

```

The filename "05 - Two Out of Three Ain't Bad.MP3" indicates that this file is of type "MP3 audio". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

```

Then, to top that off, I went into the command prompt, to see if I could "force" a play (due to what I think the error message was trying to tell me), and the MP3 ones didn't work again, so I went to the .ogg's to see if it would work there, so I typed:
```

~$ sudo play 01\ -\ Bat\ Out\ of\ Hell.ogg &

```

WOW - the song started ******* playing, all by itself it started ******* playing, no media player, no audio player, just playing out of konsole!!  Close the knosle - still playing - So I log out - STILL PLAYING - log back in, STILL PLAYING.  What the hell was going on - It's like a 9 minute song, finally it ended...

A similar thing happened earlier - I was watching a movie - I had to close my player b/c I had to leave, closed the media player - video stopped - audio kept right on cranking - no programs open, no nothing.

What the heck is this about?

PS:  Does anybody know why it won't let me open the MP3's created by convertIT from the .ogg's?

---

### Post by Syndacate on 2007-12-31
****, anybody?

---

### Post by pt123 on 2007-12-31
> **Syndacate said:**
> ****, anybody?

Ubuntu doesn't not play mp3 by default install.

Trying double clicking on the mp3 file. It should guide you to getting mp3 support.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Krydahl on 2007-12-31
Assuming that you're running the most recent version (7.10 Gusty) then enabling MP3 is easy. Go to Synaptic (system -> admin) and search for ubuntu-restricted-extras. Install that.

Not sure you've ripped your CD in the best fashion. I'd suggest going into applications -> Sound & Video and starting Sound Juicer. In there you can go into edit -> preferences and set the file format you rip in to be MP3. (Ogg is the default, it's an open source alternative.)

---

### Post by Syndacate on 2007-12-31
> **pt123 said:**
> Ubuntu doesn't not play mp3 by default install.

Trying double clicking on the mp3 file. It should guide you to getting mp3 support.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That doesn't have anything to do with it, bro, I have MP3's on here and they play fine, but these are empty or corrupt or something, it won't let me play it, it's like it thinks the file has malicious intentions.

[quote=Krydahi]ssuming that you're running the most recent version (7.10 Gusty) then enabling MP3 is easy. Go to Synaptic (system -> admin) and search for ubuntu-restricted-extras. Install that.

Not sure you've ripped your CD in the best fashion. I'd suggest going into applications -> Sound & Video and starting Sound Juicer. In there you can go into edit -> preferences and set the file format you rip in to be MP3. (Ogg is the default, it's an open source alternative.)[/quote]

Worked like a charm, thanks a bunch.

---

