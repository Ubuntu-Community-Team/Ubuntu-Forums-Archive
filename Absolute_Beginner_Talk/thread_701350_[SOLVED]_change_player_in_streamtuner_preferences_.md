---
title: "[SOLVED] change player in streamtuner preferences to amarok"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by meindian523 on 2008-02-19
I would prefer to use amarok or vlc to open streams I'm interested in from streamtuner.But when I changed the preferences to amarok -e which effectively means that amarok should enqueue the stream,all I get is amarok opening up and sitting there.I have no idea about how to use vlc since it's man page gives no idea what I could use to open streams from a general kind of source,be it udp,http,rtsp or whatever.Does anybody have an idea how to do this?

---

### Post by meindian523 on 2008-02-19
bump

---

### Post by Cresho on 2008-02-22
Hello!  FUnny I ran into this thread looking for an answer  But I got it.  At first i was wondering why amarok %q wasnt working.  It just cued the file in the playerlist.  So i did a further research.  Now I got it working just right.

This is how you get streamtuner to work with amarok.

open up your streamtunter and in...

Edit->preferences->applications


under command "listen to a .m3u file" double click on the command section and replace
xmms %q with "amarok %q -p" without the quotes.

do the same for Listen to a stream.

It works.

---

### Post by meindian523 on 2008-02-22
It works!I shall mark the thread solved.

---

### Post by mikethebike on 2008-06-25
Thanks very much this solves the problem of missing xmms HH

---

