---
title: "Missing MP3 Codecs"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-22
Okay, I've just resolved an issue thanks to all you wonderful people, regarding my partitions . . .was more of a non-issue, and the problem actually was in Automatix . . .As you know, for proprietary law reasons, Ubuntu does not come complete with certain codecs . . .I would like very much to have these codecs on my computer, but I don't know which ones I need and don't need in order for my MP3s to work, or anything else for that matter. ~LOL~ What won't work at square one, and how do I get them to work without using Automatix? ~LOL~ I know I post a lot, but I'm really trying here, folks. I appreciate the patience.

---

### Post by IYY on 2006-11-22
The best answer is [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

To be more specific,

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

---

### Post by LLRNR on 2006-11-22
Ok, for the media problems check [this](https://help.ubuntu.com/community/RestrictedFormats) out, also, may I do a "[cross-reference](http://ubuntuforums.org/showthread.php?t=304460&page=3#27)" here ? :D

---

### Post by Busch on 2006-11-22
this worked for me to play mp3

just download this file and there you go :)

[click here.]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.2.debian-1_i386.deb")

That ofcouse is the i386 one. if you are using some different sort of artichecture (however you spell that) than there is 


[amd64 here.]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.2.debian-1_amd64.deb")

[powerpc here.]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.2.debian-1_powerpc.deb")


[sparc here.]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.2.debian-1_sparc.deb")

Oh yea and to install it. just use the gdebi package installer. basically just double click on the file once downloaded. or use dpkg -i or however you do it.  Hope this helps:p

---

### Post by CheshireMac on 2006-11-22
:) Again, folks, I appreciate all the help . . .I've finally gotten Automatix to run, and I'm so happy now . . .the only ting left for me to do is get uysed to the language and start turning Ubuntu into Mebuntu. ;) ~LOL~ Thanks again folks. Big help . . ..LLRNR, give me a shout sometime if you see me on here. You seem like a pretty capable guy, and fun tot alk to. ~LOL~ Also, my apologies for any typos in this post . . .all the text is white right now, and I'm just too lazy to fix it. ~LOL~ No sleep after last night's problem solving. . . .PEACE OUT RABBIT!!!

---

### Post by Bachstelze on 2006-11-22
> **CheshireMac said:**
> I've finally gotten Automatix to run, and I'm so happy now

Just give it a few weeks, you'll be far less happy then...

---

