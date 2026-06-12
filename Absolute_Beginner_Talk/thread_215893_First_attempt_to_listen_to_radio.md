---
title: "First attempt to listen to radio"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-07-14
AFAIK, I have all the possible codecs, media players, etc installed. But when I go to 
[http://puppylinux.org/wikka/RadioStations](http://puppylinux.org/wikka/RadioStations)

and click on one, the browser asks me if I want to open it in either Totem (Firefox) or Amarok (Konqueror). In either case, nothing happens after I say yes. 

I've never listened to internet radio, so I have no idea what's supposed to happen. Can someone please walk me through this?

---

### Post by Drakkor on 2006-07-14
Install streamtuner, you'll get all the stations you want !! :)

---

### Post by Paerez on 2006-07-14
right click and say "save link as". Then open your media player of choice (I would recommend XMMS, Amarok, or Rhythmbox) and open the PLS file with that.

---

### Post by editrix on 2006-07-14
> **Paerez said:**
> right click and say "save link as". Then open your media player of choice (I would recommend XMMS, Amarok, or Rhythmbox) and open the PLS file with that.

Hi Paerez:

Well, I feel like an idiot. I don't see an "Open" option in Rhythmbox. I managed to add a station with Ctrl-I, but all it says is shoutcast-playlist.pls--which is what everything on that list is called. 

I managed to get RadioFrance playing, but that was in the list already.

Do I actually save the file? Or just copy it to something?

---

### Post by Paerez on 2006-07-14
in rhythmbox you actually say "add radio" and in the radio url, copy and paste the path to the pls on the site.

---

### Post by editrix on 2006-07-15
> **Paerez said:**
> in rhythmbox you actually say "add radio" and in the radio url, copy and paste the path to the pls on the site.

So what I paste should end in .pls?

When I did that, I got:

Couldn't start playback: hZ??????_
Problem occurred without error being set. This is a bug in Rhythmbox or GStreamer.

When I tried it in Amarok, I got:
No demux plugin available; check your installation.

No joy with other sites, either--except RealPlayer works.

Sigh!

---

### Post by Paerez on 2006-07-15
I opened the first file on that list, and this is what was inside:
```
[playlist]
numberofentries=0
Version=2

```

So I think those feeds are broken.

Try this one, and say "open with rhythmbox"
[http://somafm.com/groovesalad.pls](http://somafm.com/groovesalad.pls)

Then go to the radio tab in rhythmbox, and there should be a bunch of entries called "(#X) SomaFM: Groove Salad ...". Double click one of those.

If that works, then radio works but the puppylinux links dont.

---

### Post by editrix on 2006-07-15
> **Paerez said:**
> I opened the first file on that list ... So I think those feeds are broken.

Thanks for that. I have now expunged the site from my bookmarks.

> **Paerez said:**
> 
Try this one, and say "open with rhythmbox"
[http://somafm.com/groovesalad.pls](http://somafm.com/groovesalad.pls)

Hallelulah! It worked! Thanks so much! 

Now to find a whole lot more stations so I can practise :-)

---

### Post by crispy_420 on 2006-07-15
Try shoutcast.

[http://www.shoutcast.com/](http://www.shoutcast.com/)

There are thousands of channels.

I have them setup to auto play when I hit the "tune in". So when I hit "tune in", xmms opens up and I'm listening. To do that I selected "open with" in firefox and then browsed over to /usr/bin and chose xmms.

If you want to use a different player later you can go into firefox's preferences and clear it out and just set it up to a different player.

---

### Post by editrix on 2006-07-15
> **crispy_420 said:**
> Try shoutcast.

[http://www.shoutcast.com/](http://www.shoutcast.com/)

There are thousands of channels.

I have them setup to auto play when I hit the "tune in". So when I hit "tune in", xmms opens up and I'm listening. To do that I selected "open with" in firefox and then browsed over to /usr/bin and chose xmms.

If you want to use a different player later you can go into firefox's preferences and clear it out and just set it up to a different player.

I have to say, I do NOT like either Amarok or Rhythmbox--they're too big and clunky and complicated. I recall xmms from a previous attempt at using Linux. So thanks for the reminder and the instructions. And the URL!

---

### Post by ctucker10 on 2006-07-16
My two cents...streamtuner is the best when it comes to listening to radio streams. As for ryhthmbox I have not had a lot of luck getting most streams to play in it however, "ogg" streams work quite well in rhythmbox.

Ogg vorbis streams are still somewhat of an rarity to much of the streaming community but, I found a site that lists a quiet a few of these streams (public radio, campus radio, jazz, eclectic, house, punk, etc.). Enjoy.

[http://wiki.xiph.org/VorbisStreams](http://wiki.xiph.org/VorbisStreams)

---

### Post by editrix on 2006-07-16
> **ctucker10 said:**
> My two cents...streamtuner is the best when it comes to listening to radio streams. As for ryhthmbox I have not had a lot of luck getting most streams to play in it however, "ogg" streams work quite well in rhythmbox.

I've given up on Rhythmbox. Thank heavens there are so many options in Linux. Actually, quite out of the blue, I discovered Kmplayer, and have been having fun with it for the past couple of hours. Very easy to figure out, the radio stations are bookmarks, and you can select whether to play with gstreamer, mplayer or xine--and maybe more. Haven't explored it all yet. And it's light!

---

### Post by ctucker10 on 2006-07-16
> **editrix said:**
> I've given up on Rhythmbox. Thank heavens there are so many options in Linux. Actually, quite out of the blue, I discovered Kmplayer, and have been having fun with it for the past couple of hours.

I've given up on rhythmbox several times over the past two years (that I have been exploring various linux distributions). I always seem to come back to it . Who knows why?

This morning I was determined to figure out how to _reliably_ stream radio stations in rhythmbox. I'll repeat, ogg streams work very well in rhythmbox. As for kmplayer...I didn't have any luck actually playing a stream. I could probably get it to work if I spent as much time messing with it as I have with rhythmbox. But, that's kind of the point of my first post...streamtuner is pre-loaded with hundreds of streams from various sources. Click on the "tune-in" button and you're there. Everything "just works".

---

### Post by Sef on 2006-07-16
Rhythmbox works great for streaming for me.  

As for a radiostations, I like [http://www.mikesradioworld.com]("http://www.mikesradioworld.com").

To get it to play the station I want, I download the link and opened it with Rhythmbox.  That automatically puts it into Rhythmbox.

---

