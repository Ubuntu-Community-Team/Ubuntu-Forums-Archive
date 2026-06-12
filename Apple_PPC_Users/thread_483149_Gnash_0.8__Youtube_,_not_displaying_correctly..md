---
title: "Gnash 0.8 / Youtube , not displaying correctly."
date: 2007-06-24
forum: Apple PPC Users
---

### Post by rectagonal on 2007-06-24
I've installed Ubuntu on an PowerMac G4 AGP, and have been hoping to get gnash 0.8 up and running.

Ive followed the thread here : [http://ubuntuforums.org/showthread.php?t=471169&page=2](http://ubuntuforums.org/showthread.php?t=471169&page=2) but could not get it to work when compiled from source. It would compile and install fine, once I had all the dependencies satisfied, However firefox refused to detect the plugin. I tried putting a link to the library in ~/.mozilla/firefox/[profile]/plugins and /usr/lib/mozilla/plugins but about:config would never list it.

So then I tried backporting the gutsy package using prevu ( also described in the aforementioned thread ) which worked pretty much flawlessly. Except I have some sort of rendering issue. I get a series of horizontal lines covering the left fourth of the video playback.

I have attached a png which illustrates my problem.

Anybody got any suggestions on how to proceed ?

---

### Post by Auria on 2007-06-24
gnash is still far from perfect, you should report bugs to its team (gnashdev.org)

---

### Post by stmiller on 2007-06-24
Gnash can be compiled with several backends to do the rendering. Video and then also audio. So this package in the ubuntu repos may be compiled with other options that may not work so well.

AGG works best for video, according to the gnash mailing list. Unfortunately, this means compiling from source to enable this. 
And for audio, gstreamer backend seems to work good. 

I *think* the default gnash config (and perhaps this ubuntu package) is to use opengl for rendering. So run glxgears and see if that runs okay. That will confirm usable opengl.


--------------------
And I noticed your comment about placing the plugin:

just place the compiled plugin in

/usr/lib/firefox/plugins

type

sudo nautilus 

to do this in a GUI.

---

### Post by rectagonal on 2007-06-24
> **stmiller said:**
> I *think* the default gnash config (and perhaps this ubuntu package) is to use opengl for rendering. So run glxgears and see if that runs okay. That will confirm usable opengl.


Glxgears does run without any of the distortion im getting in gnash.  And GLXInfo claims all is well with glx. 

Despite this I do think the opengl backend is probably at fault. ( the ubuntu package is set to use OpenGL ). I will try recompiling it with AGG and placing the plugin in the aforementioned directory.

---

### Post by rectagonal on 2007-06-24
Well I tried it using the AGG backend and the Cario backend, both gave me no video at all. Audio worked in both cases. ( screen shot attached )

I had been using a pre-packaged .deb someone had created for AGG - [http://ubuntuforums.org/showpost.php?p=2854256&postcount=23](http://ubuntuforums.org/showpost.php?p=2854256&postcount=23) , which is the only thing I can think of as the weak link in this chain. So i'll go download and compile AGG myself and give the AGG backend one more shot.

Is there anyway someone could just generate a binary package of Gnash 0.8 using AGG ? This seems to be a sought after package, so it would seem worth the time...

---

### Post by rectagonal on 2007-06-24
Ah, avoiding that non-standard AGG package worked! I have Gnash up and working. :)

---

### Post by joninkrakow on 2007-06-26
Is it postable? emailable?

-Jon

---

### Post by stmiller on 2007-06-26
Hey Jon: Looks like a gnash package will be available in Feisty-backports soon. So soon you can just apt-get install to get it. I'm too scared to create a .deb for others, personally, b/c if it breaks your system for some reason, I would be to blame. :(

---

### Post by joninkrakow on 2007-06-26
Sounds good--I can wait. But I would never blame anybody for hacks I installed myself. :-) Eyes wide open... 

-Jon

---

### Post by aantn on 2007-06-27
I wish Adobe would open source Flash.

It would save us all so many problems and headaches.

---

### Post by Ububurns on 2007-06-29
Apologies for the broken agg package, rectagonal - I put that up.

---

