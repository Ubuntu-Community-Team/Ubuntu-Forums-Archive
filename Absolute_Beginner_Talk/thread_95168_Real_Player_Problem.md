---
title: "Real Player Problem"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by nierz on 2005-11-25
I installed the codecs using automatrix, but I am still getting an error when I try to play a .avi movie in real player.

It says the player does not have the capabilities to play back this content.

I've also tried totem player, and mplayer, and it wont work in them either, mplayer just freezes up, and totem gives me errors.

---

### Post by Darrin on 2005-11-25
Whats the specific error you are getting? Is the avi your trying to access on the web? If so post the link.

---

### Post by nierz on 2005-11-25
no, its not on the web, it was a movie in .avi format, it will let me play mpg, but not .avi, any fix for this?

---

### Post by nierz on 2005-11-25
When i try to do it in totem it says it needs a plugin to play the .avi format? Know of any?

---

### Post by canuck45 on 2005-11-25
I couldn't find the necessary plugins for totem either but someone said VLC Media Player will play them.  I downloaded it and it works for me.  I also recall downloading w32 codecs but can't remember what forum listed where to get them and what to do but totem DOES work for avi now also...but still not for mpg....the exact opposite of your problem...

---

### Post by nierz on 2005-11-25
meh, i tried that VLC thing, and it still wont play it, I Just want to watch an avi movie, lol. And I definately have the w32 plugins installed, whats the problem here?

---

### Post by gingermark on 2005-11-25
The .avi format is in fact a container, and so could contain a film encoded with xvid, DivX or several other codecs. To be honest though, it's likely to be one of those two, so make sure you have those codecs installed.

xvid should be in the repositories as it's open source. If you can't find the divX codec add one of the Penguin Liberation Front's repositories to your sources list (located at /etc/apt/sources.list) as detailed [here](http://wiki.ubuntu-fr.org/doc/plf), then apt-get update and use the apt-get install command or Synaptic to install the codec.

Be aware of the legal situation with several of the packages located in that repository though - several are illegal in the states I believe.

Dunno if that'll help Real Player out (I only use that program for Real Media stuff) but it should hopefully sort the other players you mentioned.

---

### Post by bionnaki on 2005-11-25
I think you should uninstall whatever you've installed (codecs & players) and just follow these instructions that I posted this this thread: [http://www.ubuntuforums.org/showthread.php?t=90514](http://www.ubuntuforums.org/showthread.php?t=90514)

guaranteed to work.

---

### Post by nierz on 2005-11-25
i've already done that tutorial, and it doesn't play .avi files.
why would you download the .deb files from the website when you can get them from synaptic?

---

### Post by gingermark on 2005-11-25
[QUOTE=nierz]why would you download the .deb files from the website when you can get them from synaptic?[/QUOTE]

Normally you'd do this for a program if it isn't in the repositories (for example, Opera). If you do though make sure the deb is for Ubuntu. You can break your system if you install other debs willy nilly.

Have you tried installing divx4linux from the PLF repository?

---

### Post by nierz on 2005-11-25
yeah, i added the PLF into my sources.list, and I did the sudo apt install, but I have all those codecs already installed, so I don't know what the problem is.

---

### Post by bionnaki on 2005-11-26
[QUOTE=nierz]i've already done that tutorial, and it doesn't play .avi files.
why would you download the .deb files from the website when you can get them from synaptic?[/QUOTE]

the .deb files will not be found in synaptic.

---

### Post by gingermark on 2005-11-26
OK, you might want to try opening the avi file in Totem, then clicking Movie-->Properties.

This should tell you, among other things, what codec the film was encoded with. Then we'll know if the problem is simply down to a missing codec, or something else.

---

### Post by nierz on 2005-11-26
Okay, it says 

Codec:

ISO MPEG-4 (XviD, ffmpeg)

---

### Post by gingermark on 2005-11-26
Great, do you have the ffmpeg and gstreamer0.8-ffmpeg packages installed? (I believe they are both located in the Universe repository). If so, it doesn't appear to be a video codec problem. One would think that xvid should play anyways though.

Assuming it isn't a codec problem, I'm not too sure what's up. I take it you're certain this avi isn't corrupt at all? Have you managed to get it playing on other systems? If you have any other avi files (particularly those encoded with xvid) do you get the same errors or do they play ok?

I'm really sorry I can't be more help at the moment, hopefully someone else will come along with the answer. If I think of anything else I will post it here, but my main advice is to concentrate on getting it to play in totem, then worry about Real Player afterwards.

---

