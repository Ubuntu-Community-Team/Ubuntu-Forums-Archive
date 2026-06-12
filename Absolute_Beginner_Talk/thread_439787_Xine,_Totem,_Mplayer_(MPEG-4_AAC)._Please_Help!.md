---
title: "Xine, Totem, Mplayer (MPEG-4 AAC). Please Help!"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-05-11
So I'm trying to play a ShoutCast stream. I've tried Xine, Totem, and Mplayer. With each I have had problems.

Xine:
I get video well, however no audio.

I tried installing libxine-extracodecs. No change.

Mplayer:
Both video and audio work, however crashes after a minute or two.

Tried caching 100mb. No change.

Totem:
No video or audio, get the error message
```

An error occurred

The playback of this movie requires a MPEG-4 AAC
decoder plugin which is not installed.

```

Would like to say I tried installing the MPEG-4 AAC decoder plugin, but I do not know what it is?


I only installed Totem to try to see if it would work. So I am not really interested in using Totem. Mplayer is my first choice, then Xine.


Does anyone please have a solution for me?

Thanks

---

### Post by darkworld on 2007-05-11
Hi ya - I had this a few days back. you are def missing something. Im now racking my brains as to what it is and where I found it. If Iget an output of what I have installed then perhaps you could compare. Sorry I cant do much better at moment. Im a n00b too!

---

### Post by guysmiley25 on 2007-05-11
Thanks so much anyways, it gives me some hope that a solution exist.

That can be a hard part sometime, looking for a solution that does not exist!

---

### Post by guysmiley25 on 2007-05-11
Not that I think it is the best way to go about it, but to get an output of all installed packages

```

aptitude search "~i"

```

To output to file.
```

aptitude search "~i" >> list.txt

```

To search for something your might be after.
```

aptitude search "~i" | grep firefox

```

---

### Post by darkworld on 2007-05-11
somewhere in here it got resolved.

---

### Post by benanzo on 2007-05-11
There are essentially two "versions" of Totem.  One uses the GStreamer framework to play multimedia and one uses the Xine framework.  "Totem" itself is just a GUI.

totem-gstreamer is installed by default in Ubuntu.

In order to play other codecs ie AAC, MP3, WMA and all the plethora of video formats you have to install the GStreamer plugins.

Go to Applications >> Add/Remove
Click Preferences in the lower left corner.
Under the Ubuntu Software tab, make sure that the top 4 check boxes are checked. (you don't need to enable the source code repositories for this.)

It will prompt you to reload your repository information, do it.

Now in the main Add/Remove Applications window open the "Show" drop-down menu in the top right and select "All available applications"

then search for "gstreamer plugins"

put a checkbox next to:
GStreamer extra plugins
GStreamer plugins for aac, xvid, mpeg2, faad
GStreamer plugins for mms, wavpack, quicktime ...
click apply.

it will download and install those plugins.  Restart Totem and try your stream again.

---

### Post by guysmiley25 on 2007-05-11
Ok I found the sucker.

```

aptitude install gstreamer0.10-plugins-bad-multiverse

```

This got totem working with audio but still no video. It gives me visualization effect.

Thanks darkworld for your list, and thanks benanzo I have a better understanding of totem now. I do not have synaptic. I stick to the command line. :)

So I'm still stuck, I did try installing all the GStreamer and still no luck.

This is what I'm trying to stream [http://64.157.15.135:8050;stream.nsv]("http://64.157.15.135:8050;stream.nsv")

I would still rather use Mplayer or Xine.

Any help will be awesome!

---

### Post by benanzo on 2007-05-11
it plays fine for me in Mplayer, not xine or vlc or totem-gstreamer.

make sure w32codecs is installed.

---

### Post by wormser on 2007-05-11
> **benanzo said:**
> it plays fine for me in Mplayer, not xine or vlc or totem-gstreamer.

make sure w32codecs is installed.

Can you check if [www.rushradio.org](www.rushradio.org) works.  I have been having a simular problem playing that.  My signature has the thread I started on the issue.   Thanks.

---

### Post by guysmiley25 on 2007-05-11
Yeah it works find in mplayer for me as well. But after a few minutes it produces errors, and crashes out.

I'll reproduce it here it is...

Ok I could not reproduce the error, and it is working perfectly now. I suspect that it was the type of format that the stream was at the time.

Thanks everyone for the help.

---

### Post by donniebnyc on 2007-05-11
FWIW, I have found that I can't play some video, sound only, with the desktop effects enabled.  Also, sometimes when I get sound only, if I move the window or scroll the page the video appears.  Not a technical solution, but it works.

---

