---
title: "Totem 1.2.1 crashing"
date: 2005-12-16
forum: Bug Reports / Support
---

### Post by mpbretl on 2005-12-16
Totem 1.2.1 from backports crashes whenever I add new files to an existing playlist.

Steps to repeat:
1. Open Totem
2. Click the "+" sign and add a file to the playlist.
3. Click the "+" sign again.

---

### Post by arpunk on 2005-12-16
[QUOTE=mpbretl]Totem 1.2.1 from backports crashes whenever I add new files to an existing playlist.

Steps to repeat:
1. Open Totem
2. Click the "+" sign and add a file to the playlist.
3. Click the "+" sign again.[/QUOTE]
Seems fine to me, it doest crash on my box :/

---

### Post by pertti on 2005-12-16
[QUOTE=mpbretl]Totem 1.2.1 from backports crashes whenever I add new files to an existing playlist.

Steps to repeat:
1. Open Totem
2. Click the "+" sign and add a file to the playlist.
3. Click the "+" sign again.[/QUOTE]

Yup, it crashes on my machine too. Sometimes it just crushes, sometimes I can't select any file (the two normal file filters appear as "Untitled filter").

---

### Post by duffman25 on 2005-12-16
[QUOTE=pertti]Yup, it crashes on my machine too. Sometimes it just crushes, sometimes I can't select any file (the two normal file filters appear as "Untitled filter").[/QUOTE]

I'm having the same problem.

---

### Post by mpbretl on 2005-12-17
Another minor issue that I've noticed (which isn't necessarily new to this version) is the behavior of the "Fit Window to Movie" function.  It never gets the sizing right the first time.  You have to hold the 0, 1, or 2 key down until it finishes adjusting, and sometimes, it ends up choosing a bizarre aspect ratio.

Like I said, it's a minor issue, but I'm curious if others have noticed the same thing.

---

### Post by mike_d on 2005-12-20
yup i get the crashing when adding to the play list too.  happens with both totem-xine and totem-gstreamer.  i've resorted to drag and drop from nautilus to add to the play list.  don't know what's wrong.

---

### Post by Gandalf on 2005-12-20
it crashed for me too :(

---

### Post by emerick7 on 2005-12-22
crashes for me as well...

---

### Post by agl on 2006-01-01
same problem - any solutions coming up? It seems that all sound applications are more unstable than usual... Sound-Juicer, gxine, totem, realplayer, Gtkpod etc... are all having random crashes - but that is perhaps just my computer... and then I have the add two times crash...

hope something comes up.

---

### Post by mpbretl on 2006-01-03
I considered requesting a 1.3.0 backport (it's in Dapper), but ubp-build.py reveals a dependency on libgstreamer-0.10.  0.10 can supposedly be installed in parallel with 0.08, but since it's such a fundamental library, it probably isn't viable.

jdong?  Any resolution to this?  I've forced version 1.2.0 in Synaptic for the time being.

---

### Post by copilot on 2006-01-15
Did any of you use automatix to configure your multimedia before the crashes? This is the second install that crashes after using automatix. Could be completely unrelated.

---

### Post by Gandalf on 2006-01-15
Well yeah i use automatix, but i don't even think it has anything to do with it :o

---

### Post by starscalling on 2006-01-19
i did a by hand install and i get the same crashes....
i dont get this in my debian box
and this is a fairly newish crash issue to me 
i know b/c i use the darn thing all the time
and its not just totem-gstreamer its also totem-xine
if you happen to be reinstalling try it before you do a dist-upgrade


[edit]
adding info here... i compiled the latest one on my compy... dunno how well it might or might not work for ya but if you want to try?? 
1. uninstall totem
2. install this
3. try
:P
compiled from 1.3.1 <<--- instead of 1.2.1

[http://www.geocities.com/nipplesncream2006/](http://www.geocities.com/nipplesncream2006/) 
heh hopefully it works a bit :)
btw takes out totem / ubuntu-desktop meta-packages

---

### Post by jdong on 2006-04-07
[https://launchpad.net/products/breezy-backports/+bug/38346](https://launchpad.net/products/breezy-backports/+bug/38346)

This bug is also filed on Launchpad now, and I'm looking into options right now.

---

