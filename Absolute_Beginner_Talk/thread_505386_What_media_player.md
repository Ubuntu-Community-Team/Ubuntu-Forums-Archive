---
title: "What media player?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by SPQQKY on 2007-07-20
I tried Amarok, but it keeps locking and crashing.
Also, before it does that it tells me no MP3 support. So I really need a player to play my music. Movie player seems to work okay, but it's limited and actually will not play any .avi files. 
Also, going by the sticky here, none of the gstreamer options are available in add/remove programs as suggested. I would like a player that plays all my music and video files. 
Thanks in advance.

---

### Post by AlexenderReez on 2007-07-20
make sure you **enable all repositories** in software sources...then update....
using terminal

> sudo apt-get install gstream*


i vote for rhythmbox!

---

### Post by Happy_Man on 2007-07-20
You need to enable all your repos in Synaptic --> Settings --> Repositories. Then you will be able to find the gstreamer plugins.

---

### Post by deadgobby on 2007-07-20
See 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 Most people love using VLC player  to play all type of multi M stuff

---

### Post by SPQQKY on 2007-07-20
There is no option to enable all repositories in synaptic.

---

### Post by AlexenderReez on 2007-07-20
> **SPQQKY said:**
> There is no option to enable all repositories in synaptic.

synaptic --> setting --> repositories 

:)

---

### Post by SPQQKY on 2007-07-20
> **AlexenderReez said:**
> synaptic --> setting --> repositories 

:)
Yeah, I went there, but there is no option to enable all repositories.

---

### Post by AlexenderReez on 2007-07-20
> **SPQQKY said:**
> Yeah, I went there, but there is no option to enable all repositories.

first row..make sure you click all line there,,,(please think... :))

---

### Post by doomster on 2007-07-20
just get to System>administration>software sources, and make sure all 4 options are enabled (ticked) 
(main, universe, restricted and multiverse)

---

### Post by SPQQKY on 2007-07-20
They're all checked already.

---

### Post by Outrunner on 2007-07-20
> **SPQQKY said:**
> Yeah, I went there, but there is no option to enable all repositories.

Should look somewhat like in the screenshot below. Tick all the boxes.

---

### Post by AlexenderReez on 2007-07-20
> **SPQQKY said:**
> They're all checked already.

ish:( ...reload -->search for rhythmbox...install:)

---

### Post by Mornedhel on 2007-07-20
I use mplayer for video, with all the gstreamer packages installed (apt-get install gstreamer-0.10*). A simpler alternative is to just get vlc, since it comes bundled with codecs. I noticed that VLC sometimes fails rendering colors correctly, which is why I use mplayer.

For music, I use Exaile!. It's GTK+ though, so if you run KDE, you will want to keep Amarok. (Best jukebox there is out there in my opinion. Exaile! is almost there, but not quite. But it doesn't need KDE libs, and as I need the extra RAM...)

I seem to have been lucky with MP3 support, since I always got it to work by accident. ("Huh ? When did I do that ?")

---

### Post by SPQQKY on 2007-07-20
Okay, thanks. Opening up a video file in movie player told me I needed codecs so I selected them all and now I can play movies. Don't know why it didn't do that before....? Also, I installed rhythmbox and it plays very nice.
But I am not keen on movie player. I don't see VLC which is what I used in Windows and that was nice. How do I get that?

---

### Post by Outrunner on 2007-07-20
```
sudo apt-get install vlc
```

Will install vlc.

---

### Post by SPQQKY on 2007-07-20
LOL, yeah, thanks I used add/remove and selected all available......been working on this too long. Now the simple things are eluding me.....thanks all. Cheers!

---

