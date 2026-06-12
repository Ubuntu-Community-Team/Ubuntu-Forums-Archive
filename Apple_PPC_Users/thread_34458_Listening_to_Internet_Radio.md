---
title: "Listening to Internet Radio"
date: 2005-05-15
forum: Apple PPC Users
---

### Post by ipixel on 2005-05-15
BEGINNER'S QUESTION:
Is there a default application in Kubuntu for listening to internet radio streams? - something like iTunes, which already has a list of browsable stations built-in?

Many thanks for any suggestions!

---

### Post by SGC on 2005-05-15
Amarok (Kmenu > Multimedia) comes with 22 radio stations.

Go to the playlists tab (the one with green note) in amarok and choose "Cool-Streams"

---

### Post by slux on 2005-05-15
On the GNOME side, Rhythmbox works as well but doesn't have so many stations by default. If you want live generated lists from sites like live365, Streamtuner works pretty well, you can also get it to record streams by installing streamripper.

---

### Post by ipixel on 2005-05-16
Thanks both SGC and slux for the tips!

Do Streamtuner and streamripper have a GUI - or do I have to brave the command line?...

---

### Post by slux on 2005-05-16
Streamtuner is a GUI application, streamripper isn't but Streamtuner acts as a frontend for it too. I'm not sure if it will appear in the Kubuntu menu by default as it is primarily a KDE app so you may have to look for it. (I wish unified, clean menus were a reality already...)

---

### Post by SGC on 2005-05-16
This howto explains how to use streamripper with stream tuner:
[http://www.ubuntuforums.org/showthread.php?t=28356&highlight=streamripper](http://www.ubuntuforums.org/showthread.php?t=28356&highlight=streamripper)

---

### Post by everettattebury on 2005-05-19
[QUOTE=slux]On the GNOME side, Rhythmbox works as well but doesn't have so many stations by default. If you want live generated lists from sites like live365, Streamtuner works pretty well, you can also get it to record streams by installing streamripper.[/QUOTE]
 The Live365 plug-in for Streamtuner is broken.

---

### Post by ipixel on 2005-05-19
Tried AMAROK, but it does not seem to want to work for me. Here is the situation:

My network works- no problem. My sound works (I hear the startup jingle, the systems bells, etc., etc.). Nevertheless, if I launch Amarok, and try to connect to any of the internet stations listed there, it simply FREEZES on me. The window won't even close - eventually I get a system message, saying that the window is not responding, and asking me whether I want to force-quit it.

Is there anything obvious that I'm missing? Is there another player that I could try?

---

### Post by kris kincaid on 2005-05-27
xmms works on everything I have ever installed Linux on. Right now I am listening to [www.radioabf.net](www.radioabf.net) on my Powerbook.  ;-)

Oh yeah, search for station on [http://shoutcast.com/](http://shoutcast.com/) :)

---

### Post by chrigl on 2005-05-30
For me Rhythmbox works most well. It's a little bit like iTunes.

BUT for running MP3 stream you have to install the gstreamer0.8-mad package via SYNAPTIC. gstreamer0.8-mad is a "universe" Package. So first you have to add the "universe" Package Source Lists.

Enyoj
Chris

---

### Post by tkiesel on 2005-06-02
[QUOTE=everettattebury]The Live365 plug-in for Streamtuner is broken.[/QUOTE]

Yep. Fortunately, there's a patch at the [streamtuner website](http://www.nongnu.org/streamtuner/). Since I wasn't familiar with patching source, it took about an hour, some googling and some trial and error, but streamtuner with the patch is running on my machine now. apt-build is a pretty neat app.

Wonder if the patch can get backported? ;)

edit:  It has been! Lovely!

---

### Post by baraider on 2005-06-03
[QUOTE=tkiesel]Yep. Fortunately, there's a patch at the [streamtuner website](http://www.nongnu.org/streamtuner/). Since I wasn't familiar with patching source, it took about an hour, some googling and some trial and error, but streamtuner with the patch is running on my machine now. apt-build is a pretty neat app.

Wonder if the patch can get backported? ;)

edit:  It has been! Lovely![/QUOTE]
 i use the list of the stations from shoutcast.com to listen to music....but wonder if anyone knows how to save the address of those station into beep-media -player (default player to open those playlist)....

Also, can you share the live365 plugin and how to install it?

---

### Post by everettattebury on 2005-06-06
[QUOTE=tkiesel]Yep. Fortunately, there's a patch at the [streamtuner website](http://www.nongnu.org/streamtuner/). Since I wasn't familiar with patching source, it took about an hour, some googling and some trial and error, but streamtuner with the patch is running on my machine now. apt-build is a pretty neat app.

Wonder if the patch can get backported? ;)

edit:  It has been! Lovely![/QUOTE]

I wonder what I need to add to my sources.list to find the powerpc version of this...

---

### Post by dresnu on 2005-06-06
[QUOTE=ipixel]Tried AMAROK, but it does not seem to want to work for me. Here is the situation:

My network works- no problem. My sound works (I hear the startup jingle, the systems bells, etc., etc.). Nevertheless, if I launch Amarok, and try to connect to any of the internet stations listed there, it simply FREEZES on me. The window won't even close - eventually I get a system message, saying that the window is not responding, and asking me whether I want to force-quit it.

Is there anything obvious that I'm missing? Is there another player that I could try?[/QUOTE]

I had the same problem with amarok. I partialy solved by changing the engine from arts to xine. I say partialy because amarok hangs randomly anyway, but at least you can listen to radio stations as long as it lets you, haha.

---

### Post by bryan986 on 2005-06-10
Thanks for mentioning the xine engine, I had the same streaming problem and it solved it for me

---

### Post by rowanbot on 2005-12-26
Hi kids

My first post, y'all. 

I want music player to be my deafault radio player. I prefer it. I like XMMS for alarms and equalisers etc, but not for the aesthetically difficult interface. How do I do this? I've tried giving the exact location of stream (which doesn't seem to work) so I'm clearly missing something obvious. Most infuriatingly, it seemed to work without my clear instructions a while ago, but it began being difficult after I changed to badger and then back again, to hedgehog (I need openoffice for my work, big time, and it's too unstable with badger). 

You'll see I'm a newbie, so don't be too harsh. 

the location is this [http://80.71.1.30:8000/listen.pls](http://80.71.1.30:8000/listen.pls)

I've also just had an epiphany - I checked if it worked with the deafault stations already set up, and it came up with this

Could not open vfs file "http://ogg.smgradio.com/vc32.ogg" for reading.

What does this mean? 

Now, I also have the ugly feeling that I'm posting to the wrong thread....

---

### Post by SkyNet2029 on 2007-06-19
Thanks for the info. I was busy reading through page after page of radio station source coding for a usable URI.. oh well.. 

Thanks Again..

---

