---
title: "gstreamer help"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by msv240586 on 2006-06-29
Hey guys i've got gstreamer0.8-lame, now how would i go about insalling it and configuring sound juicer to rip into MP3 format at 192 kbps?

Thanks  ;)

---

### Post by ajgreeny on 2006-06-29
How did you get it, because it's in the repos and you should have installed it that way for ease, (sudo apt-get install gstreamer0.8-lame).

It should then be found easily by sound juicer for ripping to mp3.

---

### Post by msv240586 on 2006-06-29
oh ok but how do i get it on sound juicer, sound juicer asks me for. I

name
gstreamer pipeline  etc...

what do i enter into these fields?

've already installed gstreamer 0.8 using sudo dpkg.

---

### Post by Ptero-4 on 2006-06-29
He probably got it off the repos.

---

### Post by msv240586 on 2006-06-29
so now how do i configure the juicer to rip mp3??

---

### Post by ajgreeny on 2006-06-29
Go to *edit/preferences* and then hit the *Edit Profiles* button.  Click *New* and then call the new profile mp3.  In the gstreamer pipeline box insert:-

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux

Put *mp3* in the box for File extension and tick the *Active* click box.  Then all should be OK.

---

