---
title: "Totem Player"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2005-12-26
What is up with Totem?

I dont understand it, whenever I try a DVD through it, or infact any kind of video file the actual video and the sound are out of sync.

Now, I'm not sure if this is because of an error in it or because It's a terrible piece of software.
Could someone please clue me in please about what could be wrong or what other piece of software I can use to play DVDs and other popular file formats with please?
(AVI, MPG and WMV are the ones I use the most)


Also, i downloaded Mplayer and whenever i open it it comes up with the error:

New_Face failed. Maybe the front path is wrong.
Please supply the ext font file (~/.mplayer/subfont.ttf)

And when i try and play something:

Fatal Error!
Error opening/initializing the selected video_out (-vo) device.


Any help please?

---

### Post by Perfect Storm on 2005-12-26
Personal preference: drop totem.

how did you install mplayer? sudo apt-get install mplayer-586?


Open Mplayer and go to its preferences. In the video tab change it to xv and see if it helps.

---

### Post by ed_d on 2005-12-26
I find Totem works better for me that does Mplayer. Whenever I try to start a film, I get the following error:
VobSub: Bad magic in IFO header.

Any idea?

---

### Post by The Hedgehog on 2005-12-26
I got the same problem when I used Totem-gstreamer.
When I replaced it with Totem-xine everything was perfect.
Maybe it will do the same for you.

---

### Post by ed_d on 2005-12-26
i should refrase, I get the error when rinnung mplayer, not totem. I also use totm-xine.

---

### Post by Estariel on 2005-12-26
get rid of gstreamer. use totem-xine...

---

### Post by jbmalone on 2005-12-26
I don't mean to hijack, but does anyone know when I open mplayer and try to play a video at fullscreen it doesn't make the video fill the whole screen?  Instead, it just makes the screen black with the video in the center at the size it was.

---

### Post by Dr Von Bon Bon on 2005-12-26
How to you install Totem-xine then please?


Using apt-get would be preferable because of the Lilypond thing I can't use synaptic without it breaking.

---

### Post by Deaf_Head on 2005-12-26
Go into synaptics package manager (system<administrator<synaptics) and do a search.

if you haven't gone and added the repositories you need yet, this is how you do it:
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29%7C%28adding%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29%7C%28adding%29)


Personally, I have found in the 3 weeks i've been using ubuntu that no one media player does everything .. which really sucks. I'm hoping gstreamer .10 (which doesn't seem to be available for ubuntu yet?) fixes this.

---

### Post by Deaf_Head on 2005-12-26
whoops didn't read the very last post fully ... 

```
sudo apt-get install totem-xine

```

---

### Post by jbmalone on 2005-12-28
Does anyone have a fix for my mplayer problem?

---

### Post by SavageBeginner on 2005-12-28
[QUOTE=jbmalone]I don't mean to hijack, but does anyone know when I open mplayer and try to play a video at fullscreen it doesn't make the video fill the whole screen?  Instead, it just makes the screen black with the video in the center at the size it was.[/QUOTE]
In mplayer's preferences, try changing the video driver to xv.

---

### Post by anil_robo on 2005-12-28
I use VLC to play all my movies. Totem does work for me, but I don't like it for some yet-to-be-known reason! ;)

---

### Post by Gray. on 2005-12-28
VLC looks out of place with it's weird UI. Totem-xine works fine for all my video files.

---

### Post by Perfect Storm on 2005-12-28
It's because they have used GTK1 instead GTK2

---

### Post by anil_robo on 2005-12-29
[quote=Artificial Intelligence]It's because they have used GTK1 instead GTK2[/quote]

Is there any way I can configure GTK1 application looks so that VLC does not look ugly anymore? That'll be cool! :)

---

### Post by poofyhairguy on 2005-12-29
Totem-xine is my favorite media player by a mile.

Works better than any other with xcompmgr.

---

### Post by Perfect Storm on 2005-12-29
[QUOTE=anil_robo]Is there any way I can configure GTK1 application looks so that VLC does not look ugly anymore? That'll be cool! :)[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=107135&highlight=gtk](http://ubuntuforums.org/showthread.php?t=107135&highlight=gtk)

Or compile your own VLC with gtk2 enable

---

### Post by Franko30 on 2006-01-14
[QUOTE=jbmalone]I don't mean to hijack, but does anyone know when I open mplayer and try to play a video at fullscreen it doesn't make the video fill the whole screen?  Instead, it just makes the screen black with the video in the center at the size it was.[/QUOTE]

EDIT: Forgot to look at the second page of the thread before posting the answer - sorry.

Change the video to xv in mplayer. That might do the trick.

Franko30

---

