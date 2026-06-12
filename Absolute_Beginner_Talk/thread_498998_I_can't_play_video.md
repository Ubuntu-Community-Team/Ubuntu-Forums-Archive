---
title: "I can't play video"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by charge1 on 2007-07-12
I can't play video.

I use totem movie player and VLC media player.

1- I double click on the video file to play 
2- The program start before the media player can play the video it crash.

In both totem and VLC the media player crash before open the video file.

What to do?

---

### Post by DSn0wMan on 2007-07-12
It sounds like a codec problem. What type of video file are you trying to play? Does it give any error message after crashing?

---

### Post by jarrett on 2007-07-12
codecs installed?

from ubuntuguide.org:
*sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll*

and 

*sudo apt-get install w32codecs*

---

### Post by charge1 on 2007-07-12
> **DSn0wMan said:**
> It sounds like a codec problem. What type of video file are you trying to play? Does it give any error message after crashing?

The type of file is ogg.

No I don't get any error message.

Thanks

---

### Post by charge1 on 2007-07-12
> **jarrett said:**
> codecs installed?

from ubuntuguide.org:
*sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll*

and 

*sudo apt-get install w32codecs*

I am trying this. I hope it will work.

Thanks

---

### Post by Hallvor on 2007-07-12
> **charge1 said:**
> The type of file is ogg.

No I don't get any error message.

Thanks

That is an audio file, isn`t it?

---

### Post by charge1 on 2007-07-12
> **Hallvor said:**
> That is an audio file, isn`t it?

No it's vedio

---

### Post by DSn0wMan on 2007-07-12
ogg is not a video file, it's an audo file. Kind of like an mp3 but better.

---

### Post by charge1 on 2007-07-12
> **charge1 said:**
> I am trying this. I hope it will work.

Thanks

I am done but nothing happen

---

### Post by DSn0wMan on 2007-07-12
Just a thought, but maybe the ogg file is bad have you tried playing any others. I am pretty sure VLC can handle ogg.

---

### Post by charge1 on 2007-07-12
still I can't play any kind of video?

---

### Post by charge1 on 2007-07-12
I can play MP3 in VLC but not the ogg.

---

### Post by Inxsible on 2007-07-12
Applications --> Add/Remove Search for GStreamer. Install all of the gstreamer packages. and then try again. 

Hopefully that should do it !

---

### Post by charge1 on 2007-07-12
> **Inxsible said:**
> Applications --> Add/Remove Search for GStreamer. Install all of the gstreamer packages. and then try again. 

Hopefully that should do it !
I search I did not find it

---

### Post by DSn0wMan on 2007-07-12
Doesn't feisty ask to install the gstreamer plugins if you doubble click on a file that needs to use them?

---

### Post by charge1 on 2007-07-12
> **DSn0wMan said:**
> Doesn't feisty ask to install the gstreamer plugins if you doubble click on a file that needs to use them?

I found it install it but still nothing happen

---

### Post by DSn0wMan on 2007-07-12
Did you find a different ogg file to try? Maybe there is something wrong with the file itself.

---

### Post by charge1 on 2007-07-12
> **DSn0wMan said:**
> Did you find a different ogg file to try? Maybe there is something wrong with the file itself.

I play mp4, wmv, 3gp, avi, rmvb and mov on both player VLC and totem but the player get crash as soon as I open the file.

---

### Post by Hallvor on 2007-07-12
> **DSn0wMan said:**
> Just a thought, but maybe the ogg file is bad have you tried playing any others. I am pretty sure VLC can handle ogg.

It does. 
[http://en.wikipedia.org/wiki/Vlc#Readable_formats](http://en.wikipedia.org/wiki/Vlc#Readable_formats)

---

### Post by Hallvor on 2007-07-12
> **charge1 said:**
> I play mp4, wmv, 3gp, avi, rmvb and mov on both player VLC and totem but the player get crash as soon as I open the file.

It is probably just a bad file, then.

---

### Post by charge1 on 2007-07-12
> **Hallvor said:**
> It does. 
[http://en.wikipedia.org/wiki/Vlc#Readable_formats](http://en.wikipedia.org/wiki/Vlc#Readable_formats)

Yes

---

### Post by charge1 on 2007-07-12
anyone can help on this issue

Thanks

---

### Post by Hallvor on 2007-07-12
Have you tested other ogg files yet, to exclude the possibility of a bad file?

---

### Post by charge1 on 2007-07-12
> **Hallvor said:**
> Have you tested other ogg files yet, to exclude the possibility of a bad file?

I am sure it's not bad file

---

### Post by SyberKowboy on 2007-07-13
I am having the same problem on a system I just built today. I could open and play video just fine until I installed beryl and AWN. Now every type of a/v file I open in any player just causes it to crash? I'm reinstalling all the gstreamer file and gonna reboot. No idea what the issue is?  Helps? :p

---

### Post by perfect_circle on 2007-09-06
i have the same problem, i cannot play any kind of video. any help?

---

