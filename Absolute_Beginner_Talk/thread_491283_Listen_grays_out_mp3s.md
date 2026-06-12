---
title: "Listen grays out mp3s"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by bartkl on 2007-07-03
Hi,

I'm using Ubuntu 7.04 Feisty and I just installed Listen Music Player 0.5 via Synaptic Package Manager. Therefore all dependencies should be installed, right?
Anyways, I also installed gstreamer0.8-mad on recommendation and I also installed newer gstreamer libs. 

Mp3 playback is working fine with the standard player, but Listen grays out all mp3s.
I can't click them.

Does anybody know what to do?
Btw. Amarok used the xine engine, Listen doesn't seem to be configurable per engine. What does it use?

Thanks :)

---

### Post by moredhel on 2007-07-03
don't quote me on this, but i think that listen uses gstreamer as a backend.

have you tried installing something else like audicious (is that spelt right?) / exaile / banshee and see what they do?

EDIT: Try opening the mp3 with totem, and it should get you the right codecs to install :)

EDIT2: Totem is 'movie player' in sound and audio BTW ;)

---

### Post by bartkl on 2007-07-03
Totem plays Mp3s.
Is that enough information or would you still recommend me to (also) try one of the other players you mention?

Thanks in advance :)

---

### Post by Inxsible on 2007-07-03
Is there a reason you want to use Listen?
 
Other options include, but are not limited to
Amarok - which you mentioned
RhythmBox - default with Ubuntu
Exaile
Songbird

---

### Post by bartkl on 2007-07-03
Well, I wouldn't object trying other players.
The thing is though that I dislike to use KDE apps inside Gnome because personally I think it's less tasteful :p

Listen is said to be a sort of Amarok anlogue in Gnome. And so it seems when I start it, untill I try to play audio files ;)

I also like last.fm support. But mainly it's because it looks like Amarok.
I will try Rhytmbox and others, but I would still like to know what's wrong.

For your information: my Ubuntu install is quite clean, installed today. There shouldn't be fancy things in the way or something like that.



Thanks again.

---

### Post by moredhel on 2007-07-03
exaile is probably the closest to amarok.

saying that, rhythmbox isn't much further off.

---

### Post by moredhel on 2007-07-03
oh, and make sure you add the repository off the exaile website if you try it, the version off there is much newer :)

---

### Post by bartkl on 2007-07-03
Funny how incredibly much alike Rhythmbox and Listen are.
Perhaps that's why it fails to work? Perhaps I should remove Rhythmbox because of corrupting stuff.

---

### Post by bartkl on 2007-07-03
> **moredhel said:**
> oh, and make sure you add the repository off the exaile website if you try it, the version off there is much newer :)

Thanks, I will. Still I hate the fact of not knowing what's going on :P

---

### Post by Inxsible on 2007-07-03
> **bartkl said:**
> Funny how incredibly much alike Rhythmbox and Listen are.
Perhaps that's why it fails to work? Perhaps I should remove Rhythmbox because of corrupting stuff.
 
I dont think one player would mess with another. I have successfully installed Amarok Exaile and RhythmBox. They all co-existed nicely. Until I finally decided that RhythmBox was the one for me and removed the other two. :)
 
 
How did you install Listen? from the repos? or from some other source?

---

### Post by bartkl on 2007-07-03
> **Inxsible said:**
> I dont think one player would mess with another. I have successfully installed Amarok Exaile and RhythmBox. They all co-existed nicely. Until I finally decided that RhythmBox was the one for me and removed the other two. :)
 
 
How did you install Listen? from the repos? or from some other source?

From Synaptic, so I guess thats repos right?

---

### Post by Inxsible on 2007-07-03
> **bartkl said:**
> From Synaptic, so I guess thats repos right? Yup, unless you added additional repos in the Third Party Software tab. But since you say you Linux install is pretty new, that might not be the case.
 
Try un-installing and re-installing it again. This time try the command line. I prefer the command line over anything else
 
```
sudo aptitude remove listen
``` ```
sudo aptitude install listen
```See if that works out !

---

### Post by bartkl on 2007-07-03
I'm checking out Exaile out right now. First impression is good :).
Does it alter mp3 tags by the way? With playcount and rating information? Or is it saved inside database? Wouldn't like my tags to be messed with.

---

### Post by sab0403 on 2007-07-03
Did you install the MP3 codecs? They're not installed by default when you install Ubuntu, since they're propietary...

---

### Post by bartkl on 2007-07-03
> **sab0403 said:**
> Did you install the MP3 codecs? They're not installed by default when you install Ubuntu, since they're propietary...

I've been told that's Gstreamer and I havei nstalled those. Besides, other apps do work.

---

### Post by Inxsible on 2007-07-03
> **bartkl said:**
> I'm checking out Exaile out right now. First impression is good :).
Does it alter mp3 tags by the way? With playcount and rating information? Or is it saved inside database? Wouldn't like my tags to be messed with.
 
I use EasyTag for all my mp3 tagging. I have had problems with RhythmBox tags not being recognized in Exaile etc. But EasyTag tags are recognized in all my music players.
 
```
sudo aptitude install easytag
``` or you can go to the [EasyTag]("http://easytag.sourceforge.net/") website and download the Debian version of the EasyTag package and simply double click to install the .deb package

---

### Post by bartkl on 2007-07-03
> **Inxsible said:**
> I use EasyTag for all my mp3 tagging. I have had problems with RhythmBox tags not being recognized in Exaile etc. But EasyTag tags are recognized in all my music players.
 
```
sudo aptitude install easytag
```

Thanks. But do you know if Exaile itself alters tags while playing? I mean, playcount and stuff?

---

### Post by Inxsible on 2007-07-03
> **bartkl said:**
> Thanks. But do you know if Exaile itself alters tags while playing? I mean, playcount and stuff?
 
I think it does playcount, rhythmbox too....but I am not 100% certain. Not at my 'Buntu box since I am remotely working from an onsite with XP. :(

---

### Post by bartkl on 2007-07-03
> **Inxsible said:**
> I think it does playcount, rhythmbox too....but I am not 100% certain. Not at my 'Buntu box since I am remotely working from an onsite with XP. :(

It does playcount, I looked it up. But what I don't know is if it saves that info inside ID3 tags or inside a database.

---

### Post by bartkl on 2007-07-03
Nobody has an idea about why Listen doesn't work well?

---

### Post by Inxsible on 2007-07-03
> **bartkl said:**
> Nobody has an idea about why Listen doesn't work well?
 
Did you try uninstalling and then re-installing it again ?

---

### Post by bartkl on 2007-07-03
I have tried it, but will try it again.

Yeah it works now :D
There were said to be suggested packages, didn't notice them :)
Thanks a lot everyone, I'll see which player will win .

Now I can make this competition complete :).
Was missing gstreamer plugins.



Thanks!

---

