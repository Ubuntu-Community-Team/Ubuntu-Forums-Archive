---
title: "All purpose audio file converter?"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-09-02
Hi,
Is there a general thing that will allow me to convert various audio formats (mp3, ogg and m4a in particular) to wav?
Ta.

---

### Post by logos34 on 2007-09-02
SoundConverter will work for ogg and mp3, but for m4a/aac you may have to use something like TransKode (it's KDE but it's loaded with options)

---

### Post by Genecks on 2007-09-02
Audacity.

I set that sucker up to turn a record of Bobby Fuller Four into an MP3.

---

### Post by tgalati4 on 2007-09-02
if you like a command-line tool:

>sudo apt-get install sox

sox is the swiss army knife of sound utilities.

---

### Post by PmDematagoda on 2007-09-03
How do you use Sox?

---

### Post by avik on 2007-09-03
```
sox *<infile>* *<outfile>*
```

Typing that in the Terminal should do the trick.  Make sure you're in the directory containing *infile*.

---

### Post by beefcurry on 2007-09-03
theres always Konverter if you use KDE :). but I recommend soundconverter. its the easiest to use if you are using Ubuntu.

---

### Post by avik on 2007-09-03
Funnily enough, I was looking for a sound converter today, and I saw this thread.  I tried sox, but it didn't support flac (I know the OP didn't ask for it, but I needed it).  Eventually, I came upon [this article]("http://www.oreillynet.com/onlamp/blog/2004/11/convert_audio_between_mp3_flac.html") on audio conversion that uses LAME, SOX, FLAC and madplay to convert between various file formats.

Yes, a graphical program *is* easier, but the article shows how to use the command line for common conversions.  Just in case *someone*, not necessarily the OP, needs it.

---

### Post by capink on 2007-09-03
A nice program I use is perl audio converter. I use the command line. But it supposedly can integrate with konqueror and amarok, but I have not tried that. Here is the [deb]("http://linuxappfinder.com/debian/pool/main/p/pacpl/pacpl_3.3.2-1_i386.deb") package.

---

### Post by ramjet_1953 on 2007-09-03
I find that Tab Media Converter does the trick nicely.

Here's a link: [http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder](http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder)

Regards,
Roger :cool:

---

### Post by n3tfury on 2007-09-03
> **Fidelio said:**
> Hi,
Is there a general thing that will allow me to convert various audio formats (mp3, ogg and m4a in particular) to wav?
Ta.

are you doing this so you can burn to cd?   i still have a windows box that i use nero on and it will convert all of the above on the fly when burning to cd.  not sure about an open source equivalent.  i'll put in my vote for audacity also since it's been mentioned.

---

### Post by hilde on 2007-09-03
```
mplayer -ao pcm soundfile
```
Replace soundfile by any sound file. You get a file called audiodump.wav. If you prefer to give it an other name, replace the command by:
```
mplayer -ao pcm:file=soundfile.wav soundfile
```
In this case the output file is called soundfile.wav.
You can also use this method to get the sound from a movie. What this does is just send the AudioOutput (option -ao) to a wav-file instead of the sound card.

For mp3-files you can also use:
```
lame --decode soundfile.mp3
```

By the way, n3tfury, converting to wav shouldn't make the quality worse. This is only the case if you convert it back to a lossy format afterwards.

---

### Post by n3tfury on 2007-09-03
> **hilde said:**
> 

By the way, n3tfury, converting to wav shouldn't make the quality worse. This is only the case if you convert it back to a lossy format afterwards.

you're correct, not even finished with my first cup of coffee this morning :)  although this can be true depending on what's doing the converting, but that's for another thread at hydrogenaudio.  i'll edit my post above.

---

### Post by papajew on 2007-10-28
I am completely new to ubuntu.  I just got a new Dell and I wanted to support opensource but I am lost.  One of the earlier posts said to use sox, and _make sure you are in the right directory that the infile is in_.   How do you tell what directory the infile is in, if it is onthe desktop, and how do I tell sox what directory to go to?

---

### Post by barkej on 2007-10-28
Welcome to the community!
If the file is on your desktop the it will be located at /home/your login name/Desktop/your file name.
To change the directory from the terminal type ```
cd /home/your username/Desktop
``` or ```
cd ~/Desktop
```

Also check out [this site]("http://www.linux-books.us/linux_general.php") and this [e-book]("http://kprimdal.dk/ebooks/135.For.Du...%20Dummies.pdf").
Lots of reference material that can be very handy as you try to learn.

---

### Post by papajew on 2007-10-28
thanks.  I actually found it easier with sound converter.  I just had to get information as to how to use it from another post.  THanks for the info about the directory though.  THat is still confusing to me.

---

