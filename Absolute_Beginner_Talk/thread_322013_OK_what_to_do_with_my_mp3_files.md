---
title: "OK what to do with my mp3 files?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by EZEN on 2006-12-19
5 days and I haven't used my Windows but for more than 5 minutes! :-D 
One of my last remaining issues is: What to do about my MP3 files.

1. .Is there a good easy conversion to OGG?
2. Or are there good codecs to use the mp3?
3. Is there a good "retail" "ready to go" mp3 player in say the 20 to 40 dollar range?

Any ideas or opinions would be helpful.
If I can work this out, and one more problem for another thread,.
I can then video tape myself shooting my windows CDs and never looking back:twisted: 
Thanks for any suggestions or ideas.
B)

---

### Post by aysiu on 2006-12-19
You can use your MP3s in Ubuntu. Just install the necessary codecs. This link should help you out with that:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And most MP3 players should be fine. My Sandisk works like a removable drive. I just drag and drop MP3s to it, and that works for me.

If you really want to convert MP3 to Ogg, [this thread](http://ubuntuforums.org/showthread.php?p=1520655#post1520655) should help.

---

### Post by macogw on 2006-12-19
The only mp3 players I know that are that cheap are the flash drive / mp3 player ones.  They're nice because you can store data files too and they're tiny.  Those will work with just copy and paste.

---

### Post by EZEN on 2006-12-19
By Player i really meant...like a winamp type of software player... that already has the mp3 liscense
I have thumb drives all over he place:)

I need these files for my weekend work (local musician) so they are important to me.
But OH can I ever feel the "coversion "to Linux..It's soooo close, .I can Taste it...hahaha!

---

### Post by EZEN on 2006-12-19
Thanks!
I'll look into those.
Many Thanks!
B)

---

### Post by aysiu on 2006-12-19
Install the codecs, and you can use whatever player you want--Rhythmbox, AmaroK, Listen, XMMS...

---

### Post by macogw on 2006-12-19
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```
courtesy of ubuntuguide.org

For an iTunes-style (I guess?  library, playlists on left, songs on right) mp3 player, try banshee (just "sudo apt-get install banshee").  For a WinAmp-style one, try xmms

---

### Post by rodney3 on 2006-12-19
And I'm presuming you need internet connection to install these codecs?

---

### Post by aysiu on 2006-12-19
> **rodney3 said:**
> And I'm presuming you need internet connection to install these codecs?
Yup. Software installation in Ubuntu without an internet connection is going to be painful.

---

### Post by rodney3 on 2006-12-19
Ugh.... I really need to configure that. lmao

Thanks

---

### Post by meng on 2006-12-19
There are free open-source software players, e.g. xmms, mplayer. xmms may be most winamp-like. As for the legality of using a free-open-source-mp3-decoder, this is from wikipedia:
> Additionally, patent holders declined to enforce license fees on open source decoders, allowing many free MP3 decoders to develop. Furthermore, while attempts have been made to discourage distribution of encoder binaries, Thomson has stated that individuals using free MP3 encoders are not required to pay fees. Thus while patent fees have been an issue for companies attempting to use MP3, they have not meaningfully impacted users, allowing the format to grow in popularity.

---

### Post by KB3KVQ on 2006-12-19
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

I've been trying to get my mp3's to work since I loaded Dapper on Sunday.  I've run this code in the terminal but now what do I do?  Rythmbox still doesn't like my audio format.

---

### Post by tony2 on 2006-12-19
even i was like you. to listen to mp3 do these things

1. install all repos.

2. install xmms from the repos. it plays mp3 for me.

---

### Post by macogw on 2006-12-19
> **KB3KVQ said:**
> ```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

I've been trying to get my mp3's to work since I loaded Dapper on Sunday.  I've run this code in the terminal but now what do I do?  Rythmbox still doesn't like my audio format.

Can you play mp3's in any other players like Banshee or XMMS?

---

### Post by EZEN on 2006-12-19
You people are all Excellent!
The Linux widow told me to try it tomorrow...lol
Thank you sooo much!
Happy Holidays to all!
B)

---

### Post by EZEN on 2006-12-19
> **tony2 said:**
> even i was like you. to listen to mp3 do these things

1. install all repos.

2. install xmms from the repos. it plays mp3 for me.


All repositories as in full upgrade?
Hmmm...why not!
I'll post the results of that venture asap
B)

---

### Post by KB3KVQ on 2006-12-19
Cool, They're playing in XMMS now. Is there some sort of library incorporated into XMMS like Rythmbox has?  I normally just play my entire directory on random anyway but since I don't have the directory subdivided in any sense the graphical libraries help me a lot.

thanks folk.

---

### Post by meng on 2006-12-19
No, xmms is a minimalist player, not a library manager.

---

### Post by KB3KVQ on 2006-12-19
Is there a logical reason why Rythmbox wouldn't work when XMMS does?  I've gotten really used to the library in Winamp so any player that has something similar is preferable to me.

---

### Post by TooRight on 2006-12-19
I used to use winamp, and like using Amarok on Ubuntu, so you might want to try that, I don't find much difference between the two, but i'm just a music listener, lol.

Anyone having trouble with audio and video codecs should install Automatix, it will automatically install the programs you choose from its list...flash and java too :D

---

### Post by KB3KVQ on 2006-12-20
Well I like the look of Amarok but it doesn't like my mp3s.  Atleast I found the playlist for XMMS. That's good enough for me now.  Thanks for your help.

73

---

### Post by macogw on 2006-12-20
> **TooRight said:**
> I used to use winamp, and like using Amarok on Ubuntu, so you might want to try that, I don't find much difference between the two, but i'm just a music listener, lol.

Anyone having trouble with audio and video codecs should install Automatix, it will automatically install the programs you choose from its list...flash and java too :D

Automatix, Automatix2, and EasyUbuntu have been known to mess things up.  They also store your password in cleartext which is bad for security.  Generally, manual is the best way to install this stuff if you have the patience.  I think some programs look for codecs in different places or with different names.  I can't get Totem to play any .avi, but it plays .wmv.  I can't get VLC to play .wmv but it plays .avi.  VLC plays practically everything else, though.

---

### Post by seijuro on 2006-12-20
I've sampled a lot of audio players over the years and so far I like amaroK the best. In fact IF I am remembering correctly amaroK played mp3s out of the box when I installed Kubuntu.

---

### Post by EZEN on 2006-12-20
> **seijuro said:**
> I've sampled a lot of audio players over the years and so far I like amaroK the best. In fact IF I am remembering correctly amaroK played mp3s out of the box when I installed Kubuntu.

8) 
AmaroK did it! YAY!
Install it, Drag an mp3 to the desktop, open Amarok, drag mp3 in, hit play, Amarok will ask to enable mp3 support...say...Yes..duh....:) BANG! done!

I'm sooo happy! The dust just got thicker on my gates laptop....:KS 
Now to hook up those speakers...

Thanks everyone!

Happy Holidays

---

### Post by OMRebel on 2006-12-20
amaroK is an awesome application, you'll love using it.  I think it's the best music player out of any of the platforms.

---

### Post by arnieboy on 2006-12-21
> **macogw said:**
> Automatix, Automatix2 <snip> have been known to mess things up.  They also store your password in cleartext which is bad for security.
Really? Could you kindly provide some real proof apart from rants on personal blogs and launchpad?

---

