---
title: "Video playing problem"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by bjornkri on 2006-07-03
I can play pretty much any video by now, got all the common codecs installed and all that... except for these: 

[http://malvisundur.hexia.net/roller/page/malvisundur/Weblog/myndskilabod7](http://malvisundur.hexia.net/roller/page/malvisundur/Weblog/myndskilabod7)

I'm not sure what format this is (think it requires Quicktime) and don't know what codec I might be missing, so I thought I'd ask around here. Can anyone get it to play? For me it loads until it hits 90%+ or so, and then stops there. Clicking play does nothing.

These are sent as MMS from my mobile phone, so it might be some sort of a weird format, or some sort of a conversion that makes it go wrong for all I know. I do know it plays OK in both Firefox and IE on Windows. 

Oh and for those of you who can see the video, that's not an actual raid, but a practice raid that took place in my back yard ;) 

Thanks

---

### Post by mlind on 2006-07-03
lol, I was able to see first frame of the video. 

Yes, it's quicktime. You must install w32codecs, and if you use gstreamer then
install pitdfll-plugin too, which is wrapper to use w32codecs. For dapper package is
gstreamer0.10-pitfdll.

Then you need to totem-gstreamer-firefox-plugin to get clips embedded on web
content to play.

See [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") for more info.

---

### Post by bjornkri on 2006-07-03
Thanks, that got me closer. :)

I only get a black screen, though, it doesn't play. Anything else that might be missing? I've got the w32codecs, and now the gstreamer plugin and pitfdll

---

### Post by mlind on 2006-07-03
[QUOTE=bjornkri]Thanks, that got me closer. :)

I only get a black screen, though, it doesn't play. Anything else that might be missing? I've got the w32codecs, and now the gstreamer plugin and pitfdll[/QUOTE]

I don't have further experience about playing streaming content on firefox.
You could try xine backend instead, or mplayer plugin for firefox [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

---

### Post by Anduu on 2006-07-03
Well I think it is an issue with Firefox...

When I use the Videodownloader extension to save the move it plays fine...Real Player seems to be the default player for this media type .3gp

---

### Post by PandorsBox on 2006-07-04
Firefox seems to be messing with me too...

I can't hear streaming audio from Pandora's website [http://www.pandora.com](http://www.pandora.com)

any ideas?

---

### Post by mlind on 2006-07-04
[QUOTE=PandorsBox]Firefox seems to be messing with me too...

I can't hear streaming audio from Pandora's website [http://www.pandora.com](http://www.pandora.com)

any ideas?[/QUOTE]

I'm using totem-firefox-plugin, w32codecs, gstreamer0.10-pitfdll plugin, and
I just tried listening Peeping Tom from that website, played out fine.

If I type about:plugins as firefox URL, I get
```

Totem Mozilla Plugin

    File name: libtotem_mozilla.so
    The Totem 1.4.1 plugin handles video and audio streams.

MIME Type 		Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 		Yes
application/x-mplayer2	AVI video 	avi, wma, wmv 	Yes
video/mpeg 		MPEG video 	mpg, mpeg, mpe	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-ms-wmv		WMV video	wmv		Yes
video/x-wmv		WMV video 	wmv 		Yes
application/ogg 	Ogg multimedia  ogg 		Yes
video/divx 		AVI video 	divx 		Yes
audio/wav 		WAV audio 	wav 		Yes

```

---

### Post by PandorsBox on 2006-07-04
I have everything listed except for totem-firefox plugin... I'll have to hunt for it.

EDIT: I have totem-firefox-gstreamer plugin... is that the same thing?

Here's mine, albeit badly formatted:

Totem Mozilla Plugin

    File name: libtotem_mozilla.so
    The Totem 1.4.1 plugin handles video and audio streams.

MIME Type 	          Description 	  Suffixes 	             Enabled
video/quicktime 	  QT video 	       mov 	              Yes
application/x-mplayer2 	AVI vide             avi, wma, wmv 	Yes
video/mpeg 	           MPEG video 	     mpg, mpeg, mpe 	Yes
video/x-ms-asf-plugin 	ASF video 	    asf, wmv 	          Yes
video/x-ms-wmv 	WMV  video 	            wm                    Yes
video/x-wmv 	WMV    video 	               wmv 	            Yes
application/ogg  	    Ogg multimedia     ogg 	              Yes
video/divx 	              AVI video 	                            Yes
audio/wav 	             WAV audio 	         wav 	               Yes


I spent the last week getting sound to work at all... so... [www.last.fm](www.last.fm) works, good enough I guess.

---

