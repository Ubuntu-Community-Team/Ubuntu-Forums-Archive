---
title: "[SOLVED] Just installed, a few things i need to sort out"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by dracovich on 2007-10-22
Hey guys, just installed Ubuntu for the first time (although this is probably my 5th try in switching to Linux, starting back in 98). All in all, things are looking great and i'm very pleased with everything. Definately a big jump since i last tried it (not Ubuntu obviously) in 2003 i believe.

Most of my nagging problems i've found solutions to by some simple googling and asking around, but so far i've had two problems i really need to resolve.

#1 I'm having some issues with .wmv files in Firefox. The videos played fine out of the box, but i am unable to use the slider in some instances (if i try to use the slider the video will freeze up). In addition the slider does not show how much of the download is finished (in Windows the download needs to be completely done before you can use the slider). I read somewhere that you could use VLC to play videos in Firefox, having had nothing but good experience with vlc from windows i tried a command somewhere, and whola vlc is in firefox. But alas it has no slider, and it seems to crash FF quite a lot (especially if i have more then one vid playing). I guess that teaches me not to just copy paste commands and actually know what i'm doing before i sudo anything.

#2 Is more straightforward and not much explenation needed. Basically i have the newest gen of iPod nano and it corrupts my files if i try to load anything new onto it. From what i gathered in googling it's a known issue, but the latest releases of iPod software seems old and i couldn't find a fix (i'm assuming since i'm using 7.10 i have the newest verison of rythmbox, and gtkpods latest release was in june).

Other then that i'm happy :) Get annoyed every time i have to go back to windows (like to reset my ipod lol) and relieved every time i'm back in Linux :)

---

### Post by Pumalite on 2007-10-22
[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by LanDan on 2007-10-22
1 you could give mplayer a try, did you install the w32codecs?

2 don't know

p.s.

welcome back on the other side

---

### Post by Pumalite on 2007-10-22
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by dracovich on 2007-10-22
Alright good stuff, i went through the mediabuntu thing and installed all the media codecs (along with Java since i was doing it). I can't seem to figure out though, how i make VLC stop playing my videos in firefox. I tried under edit-preferences-content-file types-mnage-change action (for wmv) but i'm not entirely sure what to choose there.

---

### Post by dracovich on 2007-10-22
In case it helps any, this is the command i use to make vlc my firefox player:

sudo aptitude install mozilla-plugin-vlc

---

### Post by dracovich on 2007-10-22
Ok, so i managed to uninstall VLC and i'm back using totem, installed MPlayer as suggested, and tried to uninstall totem (from what i gathered all i needed to do was to delete all totem files in the /usr/lib/mozilla/plugins folder, but doing about:plugins still shows totem, and it's still playing videos. At least now it's not crashing on me and i can view videos, but the slider thing is still pretty annoying, so if anyone knows how to completely get rid of totem i'd be very appreciative.

---

### Post by Maestro23 on 2007-10-22
> **dracovich said:**
> Ok, so i managed to uninstall VLC and i'm back using totem, installed MPlayer as suggested, and tried to uninstall totem (from what i gathered all i needed to do was to delete all totem files in the /usr/lib/mozilla/plugins folder, but doing about:plugins still shows totem, and it's still playing videos. At least now it's not crashing on me and i can view videos, but the slider thing is still pretty annoying, so if anyone knows how to completely get rid of totem i'd be very appreciative.

Going into Synaptic, search for totem.  Uninstall

---

### Post by dracovich on 2007-10-22
wow, that was like the most simple thing to do lol, feel pretty stupid for not figuring that one out.

Anyway thanks guys, mplayer is now working fine and the slider there works well enough for my needs. I really appreciate the help.

---

### Post by Maestro23 on 2007-10-22
> **dracovich said:**
> wow, that was like the most simple thing to do lol, feel pretty stupid for not figuring that one out.

Anyway thanks guys, mplayer is now working fine and the slider there works well enough for my needs. I really appreciate the help.

No prob man. Sometimes the answer is right in front of ya.. :)

Please mark this thread SOLVED using the Thread Tools.

Thanks.:)

---

