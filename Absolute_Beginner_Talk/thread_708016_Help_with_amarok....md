---
title: "Help with amarok..."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by SumPersonGuy on 2008-02-25
I'm not sure if this is supposed to go here, but I'm pretty much and absolute beginner in ubuntu, I just installed it yesterday. I have 7.04, why I didn't install 7.1, I don't know.

Now, I'm having some problems with amarok, so if anyone could help me I'd greatly appreciate it. 

Amarok sees my music collection just fine, but when I try to play anything, either nothing happens, or I get a window saying "Playlist Finished," even though I didn't do anything to the playlist.

I'm not sure if this is enough information, but it's the only things I could think of, so I'm hoping you can help me anyway.

---

### Post by jcwmoore on 2008-02-25
what is the format of you music, is it mp3?

if so you will need to install the mp3 decoders to play the music

EDIT:

install the following packages, form Synaptic Package Manager

ubuntu-restricted-extras and libxine-extracodecs

---

### Post by Afkpuz on 2008-02-25
sounds like your video card is not detected,  Goto System>Preferences>Sound

Under "Audio Playback", Do you have a soundcard listed in the drop down box?  Can you hear sound when you push the test button?  Try all the choices and see if any of them give sound.

---

### Post by SumPersonGuy on 2008-02-25
Ok, first of all, thanks for the quick responses.

Second of all, yes, my sound card is detected, so I assume it's the  mp3 codecs, so could you direct me to these codecs?

EDIT: By the way, yes they are mp3's.

EDIT AGAIN: Thanks for the help guys.

---

### Post by jcwmoore on 2008-02-25
let me look for a better explination on how to install them....  Watch for an EDIT:


EDIT:

Try here...

[http://www.ubuntux.org/mp3-support-for-amarok]("http://www.ubuntux.org/mp3-support-for-amarok")

---

### Post by mkoehler on 2008-02-25
Just make sure to get the ffmpeg and libxine packages.

---

### Post by Afkpuz on 2008-02-25
```
sudo apt-get install ubuntu-restrcited-extras
```

Also, goto Applications>Add/Remove Programs and make sure you have "all software" selected.  then search for "gstreamer" Install everything with the word "gstreamer" in it.  It'll save you codec problems later down the road.

---

