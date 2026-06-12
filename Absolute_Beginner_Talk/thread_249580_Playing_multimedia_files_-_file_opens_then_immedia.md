---
title: "Playing multimedia files - file opens then immediately closes"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Seryozha on 2006-09-02
I have fresh install of Ubuntu 6.06 LTS and whenever i try to play any type of sound or video file movie viewer opens then closes imediately.  i installed amarok and i was abble to get an ogg to play once and now i dont hear the sound from it.  I have no other problems with hearing sounds.  I hear the startup and logout sounds and sounds when using gaim.  any help?

---

### Post by taurus on 2006-09-02
You need the codecs, my friend...  You can use BUMP to do that.

[http://www.ubuntuforums.org/showthread.php?t=181248](http://www.ubuntuforums.org/showthread.php?t=181248)

---

### Post by Seryozha on 2006-09-02
> **taurus said:**
> You need the codecs, my friend...  You can use BUMP to do that.

[http://www.ubuntuforums.org/showthread.php?t=181248](http://www.ubuntuforums.org/showthread.php?t=181248)

I installed BUMPs and still having the same trouble :(

---

### Post by taurus on 2006-09-02
Did you use BUMPS to install all the codecs on your machine?

---

### Post by Seryozha on 2006-09-02
ok this just started working all the suddon.  i dunno how...

even mp3's are working if i double click on them.  They wont work in Amarok though.  it says "Amarok currently cannot play MP3 files"  there is a button to click to install MP3 support but when i do that nothing happens.  any ideas?  or is there a way to make a library in totem?

---

### Post by royg1234 on 2006-09-12
I'm having the same problem.  I tried "apt-get remove amarok amarok-xine --purge", then deleting ~/.kde/share/apps/amarok/, and re-installing amarok.

The other media apps (VLC, BMP, Banshee, etc.) play mp3 fine.  Amarok can play ogg and mp4 fine, but not mp3.  What gives?

---

### Post by royg1234 on 2006-09-12
I "fixed" it.  I'm not sure which one did it, but this is what I did:

[LIST]
[*]sudo apt-get remove --purge amarok amarok-xine libxine-extracodecs
[*]sudo apt-get install --reinstall amarok amarok-xine libxine-extracodecs
[*]deleted ~/.kde/share/apps/amarok/ folder
[*]deleted ~/.libxine/ folder
[/LIST]

---

