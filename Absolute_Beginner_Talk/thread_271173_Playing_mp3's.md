---
title: "Playing mp3's"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-04
Cheers,

Just finished installing my first Ubuntu, but when I tried to play an mp3 it gives me an error.

"You do not have the decoder to play this file. You might need to install 
the necessary plugins."

So what do I do now??

---

### Post by Ambimom on 2006-10-04
Try this:
[http://www.ehomeupgrade.com/entry/2663/how-to_get_full](http://www.ehomeupgrade.com/entry/2663/how-to_get_full)

or...

Install Automatix
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

Good luck!

---

### Post by Kateikyoushi on 2006-10-04
You need to install the codecs.

[Info]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by icarus.lnx on 2006-10-04
It's documented in the [RestrictedFormats documentation]("https://help.ubuntu.com/community/RestrictedFormats") scattered all over that page. Easist to just do a search on for mp3 on the page until you find a section that is relevent for you.

Basicly you need to enable the 'non-free' packages to install any mp3 support.

---

### Post by Aberrix on 2006-10-04
I just used Automatix last night, I HIGHLY reccomend it! it makes it so easy you feel like you're cheating ;)

---

### Post by walesmd on 2006-10-04
I agre - Automatix is great, I highly recommend it over Easy Ubuntu.

Easy Ubuntu gave me issues and I had to end up installing things one at a time through that interface. Automatix worked flawlessly.

Although I did only use it for codecs - it takes all the fun out of installing the rest of the software.

---

### Post by snakyjake on 2006-10-05
Can anyone explain or have references to what these libraries, codecs, engines are about?

I keep hearing things about xine vs. gstreamer.  And then there's "arts".  Then there's "extracodecs", and I hear "ugly" or "mad".  Seems that different players need different libraries.

The reason why this is important to me is because I don't want to install a lot of useless "garbage" on my computer that I don't need.  That's one of the reasons why I left Windows.  Plus I'm still running a PII with Fluxbuntu.

Hoping someone can break this all down into simple deductive parts.

Thanks, Jake.
Fluxbox

---

### Post by Old Pink on 2006-10-05
> **snakyjake said:**
> The reason why this is important to me is because I don't want to install a lot of useless "garbage" on my computer that I don't need.  That's one of the reasons why I left Windows.  Plus I'm still running a PII with Fluxbuntu.

Garbage is virtually non existant on Linux. 

Try amaroK if you're having totem problems: ```
sudo apt-get install amarok
```

---

### Post by snakyjake on 2006-10-05
> **Matt.H said:**
> Garbage is virtually non existant on Linux. 

Try amaroK if you're having totem problems: ```
sudo apt-get install amarok
```

Perhaps "garbage" was the wrong word to use.  But in this context, I meant that I don't want to install libraries that I don't use or need.  For example, I don't want to play .avi or quicktime, or wma files.  Therefore I don't want to install a library that dumps unneeded codecs to my OS.  If I just want to play MP3, then that's all I wish to install.

But again, the real question is to what all these libraries, codecs, engines, players, are all about?  I want to have the information available so I can make the right choice of what I want, and don't want.

---

### Post by doobit on 2006-10-05
> **snakyjake said:**
> Can anyone explain or have references to what these libraries, codecs, engines are about?

I keep hearing things about xine vs. gstreamer.  And then there's "arts".  Then there's "extracodecs", and I hear "ugly" or "mad".  Seems that different players need different libraries.

The reason why this is important to me is because I don't want to install a lot of useless "garbage" on my computer that I don't need.  That's one of the reasons why I left Windows.  Plus I'm still running a PII with Fluxbuntu.

Hoping someone can break this all down into simple deductive parts.

Thanks, Jake.
Fluxbox


Libraries are the necessary components of applications. Several Linux programs may use some of the same libraries to get the components they need. Once you have installed them, don't remove them. In most cases they don't take up much space anyway.

CODECs stands for COmpressorDECompressors and are the mathematical ways that programmers have come up with to make the huge amounts of data on video and audio files smaller so your slow computer and internet conection can deal with them. There are lots of these because everybody thinks they can do it better than everybody else, but they are all making the same size/quality compromises in the end.

Engines can mean a number of things, but in terms of multimedia applications they are the things that use the codecs to compress and decompress the video and audio. Engines are spoken of in terms of efficiency and speed, and quality. Pick two.

Players use the engines or part of them, to translate the codecs to the analog stuff that you see and hear on your computer.

---

### Post by snakyjake on 2006-10-05
It sounds like to me then I do this:

--> Pick player --> Pick engine --> Pick codec --> Find library with codec --> install my choices.

Or if I want to start based on engine or codec, then rearrange the above.

So what I need now is to find a matrix of some sort (or make one), that lists the players, what engines they work with, what codecs work with what engines, pros/cons of the codes and engines (or at least some criteria to be able to make an informed choice).

I'd like to understand xine vs. gstreamer.  Then I need to read up on "mad" and "ugly".  Also looks like amarok has its own xine engine, but I thought I read somewhere that you can switch engines to maybe gstreamer.

Sheesh...so many choices :-)

---

### Post by doobit on 2006-10-05
> **snakyjake said:**
> It sounds like to me then I do this:

--> Pick player --> Pick engine --> Pick codec --> Find library with codec --> install my choices.

Or if I want to start based on engine or codec, then rearrange the above.

So what I need now is to find a matrix of some sort (or make one), that lists the players, what engines they work with, what codecs work with what engines, pros/cons of the codes and engines (or at least some criteria to be able to make an informed choice).

I'd like to understand xine vs. gstreamer.  Then I need to read up on "mad" and "ugly".  Also looks like amarok has its own xine engine, but I thought I read somewhere that you can switch engines to maybe gstreamer.

Sheesh...so many choices :-)

Fortunately, it's not as complicated for the end-user as all that. I gave you the basic breakdown because that's what you asked for, but in practice, the developers have made it easier for you by "packaging" them. You download a player using Synaptic, and the dependancies for the libraries, and engines,at least, and some of the codecs, are already worked out for you. The only thing you really need to worry about are the other codecs that they don't include. They are the ones that are not "free". As I stated, the player is an interface and will use whatever codecs the engine in it allows. Almost all of them will use mp3 because it's been around a while, but you may have to install it because it's not free, strictly speaking. XMMS must have a license or something because it does include it in the package. For the others you can download a codec package from the internet that will include mp3 and a whole lot of others. Search for w32codecs, for example.

---

