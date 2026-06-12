---
title: "[SOLVED] Radio"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-12-07
Would like to return to this problem again in Ubuntu 7.10
I am able to get _**one local radio station**_ but when I try to connect to the BBC or another of my local stations I get:

”Could not find an appropriate hxplay or realplay in the system path to use as an embedded player” !!

Well Realplayer resides in a directory of its own in my HOME directory!!

This must be something very simple, particularly when I am able to connect to one local stations!!
 
Thanks


Bernard

---

### Post by nikoPSK on 2007-12-08
I have fm but you can do internet radio in rythymbox....

---

### Post by atomkarinca on 2007-12-08
If you know the URL of the stations, you can try this:

```
mplayer -playlist <URL of the stream>
```

---

### Post by bern1939 on 2007-12-08
Well thanks for that but no success on either suggestion. I have inserted the appropriate URL's with the following results

1. For stations that _**cannot **_be opened the following error is returned:

“Couldn't start playback
Could not write to resource”

2. For the station that I **_can_** open the following error is returned in Rhythmbox Music Player

“You do not have a decoder installed to handle this file. You might need to
install the necessary plugins”

What can I do to rectify this?

Thanks

Bernard

---

### Post by atomkarinca on 2007-12-08
Can you paste the link so that we can try to open it?

---

### Post by bern1939 on 2007-12-08
I keep getting different errors:

So to reply to your query..... for the following link:

**[http://www.rte.ie/smiltest/lyric_new.smil](http://www.rte.ie/smiltest/lyric_new.smil)**

I get this error now:

Bad Transport (rtsp://streaming.rte.ie/encoder/radio1.rm)

??


Thanks

Bernard

---

### Post by atomkarinca on 2007-12-08
Alright, I can play the file using the link you gave. I looked up and I have these installed: MPlayer Plugin for Mozilla, GStreamer ffmpeg video plugin and Helix Player. You can find all of them in "Add/Remove...".

---

### Post by bern1939 on 2007-12-08
Thanks for your assistance but no success.
All 3 items you mention are already installed.

When I use the link in Rythmbox Player I get:
'Could not start playback ... Could not write to resource'

When I put the link into the Helix Player I get an error as per the attached screen-shot.

Amazing that you can succeed .... ????

Thanks again

Bernard

---

### Post by atomkarinca on 2007-12-08
Wow, I tried with Rythmbox and Helix, I get the same errors as you do. But I got it working inside Firefox. The screenshot is attached. And I must say, I enjoyed this channel :)

---

### Post by bern1939 on 2007-12-08
Well good for you. But for me no success.
This ain't working ni matter what I do ????


Pity but .......

Thanks

Bernard

---

### Post by mgmiller on 2007-12-08
Have you tried the firefox extension called media player connectivity?  

It lets you choose from any of the installed players in your system to play any kind of streaming audio or video in firefox.  

You can switch them around easily and try one till it works on the stream you want.

I just tried your link and media player connectivity used helix player (real player) to open and play the stream.

---

### Post by bern1939 on 2007-12-08
Thanks for your patience.
I did as suggested and will try all the possibilities.

One of the programmes(radio) demand the Real Player. That currently resides in a folder which is in my _**HOME**_ directory. Should that be placed in some other folder to be picked up???

Thanks


Bernard

---

### Post by mister_lister on 2007-12-08
Just to add to the conversation:


My experience with online "live" radio players in Linux is really spotty. Some work and others do not. Sometimes it is an issue with the plugin in Firefox some times the player and other times the feed is formated for only certain versions of players. With so many competing formats and players, some where along the line stuff doesn't work. Keep trying but don't be surprised if you find yourself in my situation, unable to listen to SOME live internet radio broadcasts. I posted twice on this subject alone and although I got many responses, nothing solved the dillema for me.

I am using dapper drake 6.06 LTS and have tried : 

* VLC
* MPlayer
* Rhythym box
* Real Player
* Stream Tuner

I had the most luck with MPlayer but still not all stations worked.

---

### Post by bern1939 on 2007-12-08
Well thank you both for the valuable directions and comments.
Thanks to mgmillar for the last post....it solved the problem for me in Firefox. I can now happily listen to my favourite progs.

There is such a lot to learn but all very worthwhile on this forum.

Many thanks again to you all.


Bernard

---

### Post by mgmiller on 2007-12-08
Glad I could help..):P

---

