---
title: "mplayer streaming but not visible!"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by BertP on 2007-09-24
I am a Linux noob that has been trying to receive streams of Windows Media format broadcasts,  I used Synaptic to get some extra gstreamer codecs and then installed the mediaplayerconnectivity  add-in to FIreFox and was able to listen to several stations using the totem player  However many other Windows Media Format streams would not play, 

 I then used Synaptic to DL&INST  mplayer,  and  next changed  mediaplayerconnectivity  to direct Windows  Media Format streams  to /usr/bin/X11/mplayer instead of totem....    The result;  mplayer is able to play some of those streams that totem will not  BUT I do not see the resulting mplayer window anywhere on my desktop!

I need to be able to stop and terminate the stream without having to use the System Monitor. Does anyone know why  mplayer plays the stream but does not create a visible  window in this situation?

Note:  mplayer is listed in my menu hierarchy  and does create visible windows when created via menu selection

---

### Post by Kobalt on 2007-09-24
Did you install the w32codecs package ?

---

### Post by BertP on 2007-09-24
Thanks for the help!

No, but I would think I must have installed the component codecs from that package  because the selected WMF stream **does play ** and I do hear it .... it just doesn't create a window that I  will eventually need to stop or terminate the stream

---

### Post by BertP on 2007-09-24
OK  I have found a way to get most of my stations to play using mplayer.....   and thats a very fortunate  thing because something I have done has caused totem not to work anymore with the mediaplayerconnectivity add-in to FireFox...  (now when totem is loaded by mediaplayerconnectivity,  totem begins to buffer the stream and when it is ready to play,  totem's window just dies)

So by experimenting ,  I found that I was directing mediaplayerconnectivity to  the wrong mplayer file;  If instead  I instruct  mediaplayerconnectity to load /usr/bin/x11/gmplayer,   I get an audio window, a video window and an error message window...   then I kill the unneeded windows and listen to the desired stream....  messy but it works,,,,  and I am afraid if I change anything else nothing may work again .](*,)

---

### Post by shirilover on 2007-09-25
Shouldn't that be /usr/bin/mplayer

---

### Post by BertP on 2007-09-25
>>Shouldn't that be /usr/bin/mplayer

I am a noob so I honestly don't know.    When I first installed the mediaplayerconnectivity-add-on,  it pointed to totem in the  /usr/bin/X11/ directory,  so for mplayer, I first tried /usr/bin/X11/mplayer.   Of course  that resulted in the invisible mplayer that
caused me to begin this thread.    Then I found the gmplayer (GUI mplayer?)  in the same directory  so I changed the add-on to point to   /usr/bin/X11/gmplayer.  And it all now works, albeit not gracefully.

Should I change the  add-on to instead point to  /usr/bin/gmplayer?

---

