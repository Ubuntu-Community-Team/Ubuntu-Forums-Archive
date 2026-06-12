---
title: "How to watch Shuttleworth interview?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-08-10
[http://www.channel4.com/more4/news/news-opinion-feature.jsp?id=350](http://www.channel4.com/more4/news/news-opinion-feature.jsp?id=350)

This is the URL for the website, but when I click on **>>Watch the report** some javascript thing shows up, and I don't know how to view the interview.

Firefox and Kubuntu 6.06. I haven't had problems with videos before.

---

### Post by nrayever on 2006-08-10
right now i'm looking the interview without any problem. do you have mplayer installed??

---

### Post by rubikfreak on 2006-08-10
That's odd... I get the same problem. Well, I'm a newbie as well and I would be interested to find out the answer behind this. My thought is that it is an ActiveX control that the site has set up for their video player. Have you used this site for using videos before?

---

### Post by editrix on 2006-08-10
> **nrayever said:**
> right now i'm looking the interview without any problem. do you have mplayer installed??

~$ which mplayer
/usr/bin/mplayer

And I tried to open it in Kmplayer, after everything else failed. Kmplayer failed, too.

What's supposed to  happen? I get that window with a black box, then nothing.

If I click on that thing in the middle that looks like a piece of film, Kaffeine loads and I get this:

The specified file or url was not found. Please check it. (/player/v2/asx/showvideofeature.jsp?id=show:1009:1981)

Whoops: Just found another error window:

No plugin found to handle this resource (/player/v2/asx/showvideofeature.jsp?id=show:1009:1981)

xine: cannot find input plugin for MRL [/player/v2/asx/showvideofeature.jsp?id=show:1009:1981]
xine: input plugin cannot open MRL [/player/v2/asx/showvideofeature.jsp?id=show:1009:1981]
input_file: File not found: >/player/v2/asx/showvideofeature.jsp?id=show:1009:1981<
xine: found input plugin : file input plugin
xine: found demuxer plugin: ASF demux plugin
input_http: content length = 197 bytes
xine: found input plugin : http input plugin

Thought I'd installed it all through Automatix. Sigh! Which one do I need?

---

### Post by indytim on 2006-08-10
I think it's looking for MS Media player.  I just tried to access it from my Windows Firefox (I'm at work)  and it went off into plugin install attempt.  If it is in fact tied to Media Player, would be kinda a "hoot" given the subject of the interview.

IndyTim

---

### Post by editrix on 2006-08-10
> **indytim said:**
> I think it's looking for MS Media player.  I just tried to access it from my Windows Firefox (I'm at work)  and it went off into plugin install attempt.  If it is in fact tied to Media Player, would be kinda a "hoot" given the subject of the interview.

IndyTim

It gets even better. Read the Help file. They don't even support Macintosh.

> **Why can't I play videos on my Macintosh?**

Currently, Channel4.com offers full support only for videos on PC. There are a number of reasons for this. One of the most important reasons is that the native Mac format (Quicktime) does not support Digital Rights Management (DRM). 
Is this ironic or what?

---

### Post by dvarsam on 2006-08-10
Hello!

My Ubuntu is trying to open the video, using "Totem" which (as always) crashes!!!

How can I tell it to open the video with "MPlayer"?

Thanks

---

### Post by Drakkor on 2006-08-10
Google video here: [http://video.google.com/videoplay?docid=-1341210584930823491](http://video.google.com/videoplay?docid=-1341210584930823491)

---

### Post by editrix on 2006-08-11
> **Drakkor said:**
> Google video here: [http://video.google.com/videoplay?docid=-1341210584930823491](http://video.google.com/videoplay?docid=-1341210584930823491)

Oh wow, thanks for this! And here I am always suggesting people google first (blush!)

---

### Post by crispy_420 on 2006-08-11
> **dvarsam said:**
> Hello!

My Ubuntu is trying to open the video, using "Totem" which (as always) crashes!!!

How can I tell it to open the video with "MPlayer"?

Thanks

Do you have mozilla-mplayer installed?

---

### Post by junglepeanut on 2006-08-11
For firefox install i think its a plug in or extension.

MediaPlayerConnectivity

It is just an easy way to configure firefox for media with what you already have installed.

Oh yeah for some sites with weird flash/java etc. You might want videodownloader again a plugin that is helpful.

---

### Post by ELD on 2006-08-11
It makes me want to use ubuntu just because im in love with Mr Shuttleworth haha :)

---

### Post by dvarsam on 2006-08-17
Dear "crispy_420"

Thanks for your reply!

[QUOTE=crispy_420]Do you have mozilla-mplayer installed?[/QUOTE]

Yes, I do!

-------------------------------------------

Dear "junglepeanut",

Thanks for your reply!

> For firefox install i think its a plug in or extension.

MediaPlayerConnectivity

In Synaptic, I could not find such a package - "mediaplayerconnectivity"...

In which Repos is that?

--------------------------------------------

Anyway, I managed to see the Video, thanks to Google format!!!

But I did not hear/see anything new coming out from "Mark Shuttleworth"...

Just the plain old story how he got rich & involved with the Ubuntu project...

Thanks again!

---

### Post by editrix on 2006-08-18
> **dvarsam said:**
> 
In Synaptic, I could not find such a package - "mediaplayerconnectivity"...

In which Repos is that?

It's a Firefox extension. Look in Bookmarks/Firefox and  Mozilla/Extensions. There's a gazillion of them--you may be on the site all day :-)

---

