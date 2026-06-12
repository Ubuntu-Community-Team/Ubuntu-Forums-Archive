---
title: "Download and transcode RealMedia stream?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by neocookie on 2006-08-11
Hi all

I've recently installed ubuntu on my laptop, and I'm trying to go the whole way and convert from windows.

One thing I'm looking to do under linux is grab a copy of my favourite radio programme's realplayer audio stream (rm) and convert it for use on my ipod video (hopefully in AAC format).

What tools could I use to achieve this? I'm happy using the command line, though I'd prefer a GUI tool or two to get me started.

---

### Post by reclusivemonkey on 2006-08-11
> **neocookie said:**
> Hi all

I've recently installed ubuntu on my laptop, and I'm trying to go the whole way and convert from windows.

One thing I'm looking to do under linux is grab a copy of my favourite radio programme's realplayer audio stream (rm) and convert it for use on my ipod video (hopefully in AAC format).

What tools could I use to achieve this? I'm happy using the command line, though I'd prefer a GUI tool or two to get me started.

Look in the mplayer man pages for "dumpstream"; if the stream you want won't allow that there are other ways.

---

### Post by neocookie on 2006-08-11
thanks reclusivemonkey. i'll give that a go this weekend. i'm guessing that will take care of the stream ripping; any advice for the transcoding, or will dumpstream handle that too?

---

### Post by reclusivemonkey on 2006-08-11
> **neocookie said:**
> thanks reclusivemonkey. i'll give that a go this weekend. i'm guessing that will take care of the stream ripping; any advice for the transcoding, or will dumpstream handle that too?

Nope, you will need something else to convert the stream once its been obtained. Actually, I think you may run into trouble with this option as I seem to remember I tried this on a BBC stream and it wouldn't work. They way I do it is to pipe realplayer through arecord, like this;

```

realplay *URL* | arecord *arecord options*

```

which records it to a wav. I am at work so I can't remember the full line but I will post it when I get home. You then need to use something like sox or lame to convert the resulting wav into whatever format you want it in. I have been meaning to write a script to do this for some time now, but as you can see from my profile picture, I have other distractions... ;-)

---

### Post by neocookie on 2006-08-11
Congrats on the little 'un. :)

Yea, its a BBC stream I'm looking to get also.

With the realplay *URL* option, am I going to have to wait while the whole stream "plays" through realplayer? Its just that the stream is 2hrs long, and I'm impatient. ;)

---

### Post by reclusivemonkey on 2006-08-11
> **neocookie said:**
> 
With the realplay *URL* option, am I going to have to wait while the whole stream "plays" through realplayer? Its just that the stream is 2hrs long, and I'm impatient. ;)

Yes, that's right. This is why it will be much better off scripted. You also have to tell arecord the time to record, or you will only get a partial recording. As there is no way to "speed up" a stream that I am aware of, the only way to record it will be in real time; this would be the case with "dumpstream" as well. This is why its much better scripted; you could then leave it going over night and come back to a nicely ripped mp3. Incidentally; this isn't Sean Rowley's "Joy of Music" is it???

---

### Post by neocookie on 2006-08-11
Nope. Annie Mac's radio1 show (thurs, 9pm). Come on, I'm only 24! ;) lol

I found an app for windows which would pull an rm stream down in a fraction of the time. Can't remember the name of it though, and I've reformatted since then. Took 10 mins to grab 2hrs worth. I'll see if I can dig it out this weekend, if I can get infront of my winxp box.

---

