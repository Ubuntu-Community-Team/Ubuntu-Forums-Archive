---
title: "Program to edit video with?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by pimpaulogy on 2006-08-09
I've seen some different posts, but all have to do with capturing video from a camera.

I would like to edit files that I have downloaded from the internet (wmv, avi, mpeg, mpg, mov, etc.).

What is the best, free, easiest program to use?

Sorry if somebody else has answered this already.  Just post the link if that is the case.

Thanks.

---

### Post by o_fortuna on 2006-08-09
I think "kino" might do what you're looking for. You can find it in Add/Remove Applications, or in Synaptic, or using a terminal, type:
```
sudo aptitude install kino
```

---

### Post by qyot27 on 2006-08-09
The chances of finding something that encompasses all those formats **and** edits is probably pretty small.  It may have support for MPEG-1 and AVIs that use MPEG4, DV, or Uncompressed formats, but your best best for stuff like MOV, WMV, RM, etc. is to find something that can convert those files to a lossless AVI or some such so that your editor can use them.  I think mencoder (or AviDemux) are pretty comprehensive in that regard.  I've had some limited success in getting AviSynth 2.56 and VirtualDubMod 1.5.10.2 to work using WINE, but until those get a true Linux port (I know AviSynth 3.0 is slated to be available on Linux, but I don't think there's much initiative to port VDub/Mod) the native apps will probably work better for you.

After that, the editing software to choose from is: Kino (like was mentioned), ZweiStein (which I've not fiddled with myself), Cinelerra (comparable in layout to Adobe Premiere or Final Cut Pro), and I'm sure there's a few others.

---

### Post by pimpaulogy on 2006-08-10
Thanks so far.

I can understand converting the files.  Had to do that in Windows half the time too.

I have tried Kino, using a WMV file, and it didn't like it.  More importantly, when I tried to open the file, it told me it wasn't a DV file, asked me if I wanted to import it, clicked OK, saw a progress bar for just a second, and then nothing.

With the other programs mentioned, sorry but I am a n00b, and some of those programs, at least Cinelerra, seemed pretty involved in trying to get installed.  I used Automatix to install Kino and was hoping there were other programs that I might have more success with that would be that easy to install and get going.

Definitely, any advice is appreciated.

---

### Post by qyot27 on 2006-08-11
> **pimpaulogy said:**
> With the other programs mentioned, sorry but I am a n00b, and some of those programs, at least Cinelerra, seemed pretty involved in trying to get installed.  I used Automatix to install Kino and was hoping there were other programs that I might have more success with that would be that easy to install and get going.

Definitely, any advice is appreciated.
As far as mencoder and Avidemux are concerned, they are available in the Dapper multiverse repository.  If you've opened up all the repositories you can just search for them using Synaptic and install them through that.

EDIT: [I found this useful](http://www.kiberpipa.org/~gandalf/ubuntu/README).  If this doesn't work, then proceed with the next paragraph.

As for Cinelerra, I have an older version installed that I was sure I put in using alien and an rpm from the official site, but the way it's described [here (under easy way)](http://www.ubuntuforums.org/showthread.php?t=188264&highlight=cinelerra) should work okay and isn't too hard to follow.  The only things I would do differently is that I wouldn't do the *sudo rm* part and use gedit instead of nano (both in step 5), and after steps 5-7.2 I'd install the package by using Gdeb instead.  You'll also need to add libquicktime0 and libquicktime-dev to that long apt-get list - I don't know why it doesn't have them in there already, but as far as I can remember, Cinelerra depends on both of those (and I think that even is mentioned in that HOW-TO thread).

---

### Post by pimpaulogy on 2006-08-11
What I am trying to do is edit a WMV file.  So after looking around and taking advice from others, I figured out that I need to convert the file into another format.  Fair enough.  I then installed mencoder, and got it running, but the conversion into an AVI file is horrible, unless I use the "copy" option which turns a 300mb WMV file into a 5.5gig+ AVI file, so that's not acceptable.  Then, it seems like all other programs are just GUI's for mencoder so those doen't work for what I need.  I am stuck there.

I did try Avidemux, but that program can't handle the WMV file so I am still stuck.

I will try Cinelerra and hopefully it isn't too painful for me to get going.

Keep the advice coming though.  I do appreciate it.

The bad thing is I could do this with my Windows box, but I don't want to.  I am trying to become less reliant on Windows and more on Linux, but there are still these little things that keep me holding onto Windows.  Oh well, fighting the good fight.

---

### Post by pimpaulogy on 2006-08-11
Well, unfortunately, Cinelerra not as easy as hoped.  I tried to go through the instructions posted, and everything seemed to work, except for missing one lib file.  Then, I searched around, and found that file is a package, so I installed it, but lib file depended on another, so I finally found that one, got it installed, with one slight error, but didn't seem too detrimental.  Then installed the previous lib, which worked.  Reinstalled Cinelerra and then ran it, and got a whole new error, differnet from the lib error I originally got.  Looked up that error, nobody else seems to have the same issue.  I am throwing in the towel with Cinelerra, for now. 

Any other ideas?

---

### Post by CarpKing on 2006-08-11
> **pimpaulogy said:**
> the conversion into an AVI file is horrible, unless I use the "copy" option which turns a 300mb WMV file into a 5.5gig+ AVI file,

That's because uncompressed AVI files are huge.  I'm not real familiar with how these programs work, but if you can use mencoder to then reencode that AVI with something like XviD, you can get the size back down to a similar range to the WMV.

---

### Post by qyot27 on 2006-08-11
> **pimpaulogy said:**
> I then installed mencoder, and got it running, but the conversion into an AVI file is horrible, unless I use the "copy" option which turns a 300mb WMV file into a 5.5gig+ AVI file, so that's not acceptable.
I have no clue how many lossless formats other than Uncompressed are able to be used under Linux, but that would be my only suggestion.  I would never recommend trying to edit with anything MPEG-based, since most editing software can't cope with the B-frames that are present in those formats and that can result in wonky behaviour.

On Windows you at least have the option of using AviSynth to 'fake' the video file and therefore not take up all the space normally associated with converting the file manually (for those programs which don't accept AviSynth scripts, it is possible to wrap them in fake AVIs, and that allows them to be used in say, Vegas or WMM).  As I said, AviSynth 3.0 is slated for Linux, and apparently it can compile, but it's still in such an early alpha stage it's not really usable yet.  I don't know how well AviSynth 2.5 could integrate with Linux since it requires WINE, if it would even integrate at all.

---

### Post by bobbybobington on 2006-08-12
From my experiences with kino, the impression that i got was that it was useless. Converting Formats is a mess, and as far as edit features much is left to be desired. Then theres Cinellera which (i havn't tried it yet) seems to be at the extreme opposite. Its for professionals so it's hard or has an extremely high learning curve, but is feature rich. What i think we need is a simple, yet fullyfeatured editor with a nice format conveter. I am a video editing junkie so this kind of thing need some attention IMO.

---

### Post by pimpaulogy on 2006-08-17
Well, I am still stuck with not being able to edit the WMV file I have.  But, I have at least crossed one hurdle.  I can finally run Cinelerra.  What a pain trying to get all the right dependencies.  I had practically gave up, and then I found a link to what to add to the sources.list file that would get all the dependencies I needed.  Here is the link to the instructions:

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

Followed that and I finaly got it to launch and run.  Still can't edit the file, but I am now at least one step closer.

---

### Post by Sukarn on 2006-09-17
Isin't that the same link qyot27 gave earlier?

---

### Post by spur on 2006-09-18
DVD and slideshow creation are the only things I still do on windows. In my humble opinion there are no linux rograms as user friendly as those available for windows. I regularly send e-mail to pinacle /ulead/ etc requesting linux versions. Its crappy we have to use something that is questionably legal in a lot of countries just to watch dvds we have legally purchased to watch. Any way rant finished.

---

