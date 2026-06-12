---
title: "[SOLVED] Sound Problems Macbook"
date: 2007-09-20
forum: Apple Intel Users
---

### Post by czechman86 on 2007-09-20
i cannot control my sound via the f3 - f5 keys and cannot also lower or raise it with the sound control icon in my panel. the sound is stuck at one constant volume and was wondering if anyone else was having this problem or if any knows how to fix it? i can control my sound from amarok and other applications though, but that only changes the volume on the music and not the system. thanks a million for your help!

---

### Post by cyberdork33 on 2007-09-20
> **czechman86 said:**
> i cannot control my sound via the f3 - f5 keys and cannot also lower or raise it with the sound control icon in my panel. the sound is stuck at one constant volume and was wondering if anyone else was having this problem or if any knows how to fix it? i can control my sound from amarok and other applications though, but that only changes the volume on the music and not the system. thanks a million for your help!

run alsamixer and find the channel that actually adjusts your system volume. On some of these Macs, the Master channel doesn't work (which is what the system adjusts by default), and you have to adjust the Front channel or something similar instead.

---

### Post by czechman86 on 2007-09-20
nice! that worked perfect! my ubuntubook now runs better than it ever did with osx! thanks again!

---

### Post by cyberdork33 on 2007-09-20
Please mark as Solved!

---

### Post by anujseth on 2007-09-26
back on the forums (and ubuntu) after long ... and now i'm stuck 

cannot get the sound to work. its a second gen macbook 2 GHz. just installed the gutsy
nightly build ... no sound at all ... umm any clue ??

---

### Post by cyberdork33 on 2007-09-26
> **anujseth said:**
> back on the forums (and ubuntu) after long ... and now i'm stuck 

cannot get the sound to work. its a second gen macbook 2 GHz. just installed the gutsy
nightly build ... no sound at all ... umm any clue ??

Some additional info might be helpful to determine the source of your problem. (is you sound hardware even recognized by the system?) Also, it may be better to start another thread since your problem has nothing to do with the solved issue you posted under (other that is is related to audio).

---

### Post by anujseth on 2007-09-26
how do i tell if its recognised ? i tried the individual options (oss hda alsa etc)... auto detect ... the alsa mixer settings ... nothing 

new thread posted 
[http://ubuntuforums.org/showthread.php?p=3432167](http://ubuntuforums.org/showthread.php?p=3432167)

---

