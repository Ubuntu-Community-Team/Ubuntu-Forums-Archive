---
title: "Quicktime no worky"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-02-08
no media player will play local *.mov files I've tried totem, mplayer, vlc, and probably others.

totem:
[PHP]You do not have a decoder installed to handle this file. You might need to install the necessary plugins.[/PHP]

mplayer:
no error message, shows file name but does not play audio or video

vlc:
no message, no output, it just ignores me and acts like I didn't just tell it to do something!

xine:
[PHP]-xine engine error-
There is no demuxer plugin available to handle 'filename'. Usually this means that the file format was not recognized[/PHP]

I have tried the suggested actions from here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)
as far as installing almost every codec for the various players.

I have also used synaptic to install all of the various media player plugins that allege to support quicktime in their descriptions.

I'm totally stumped, do I have to tell the media players where the codecs are or something?

---

### Post by shareMenaPeace on 2007-02-08
Hi, maybe youe miss a codec
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Or maybe just a plugin. One way to install missing browser plugins is to get 

[http://getautomatix.com](http://getautomatix.com) which let you install browser plugins automaticly.

---

### Post by rkrug on 2007-02-08
I have the exact same problem, running Edgy Eft.

---

### Post by rkrug on 2007-02-08
...And I should add that NO media files will play for me.

---

### Post by shareMenaPeace on 2007-02-08
Ok get automatix and install media codecs 
Afte ryou installed automatix from the link above it is accessable under Applications -> System Tools -Y Automatix

And try realplayer or media player for quicktime.

---

### Post by TBOL3 on 2007-02-08
get easyubuntu, it will really help.

---

### Post by rkrug on 2007-02-08
How do I disable Synaptic?

Automatix wants me to do so.

---

### Post by jackrobinson on 2007-02-09
> **rkrug said:**
> How do I disable Synaptic?

Automatix wants me to do so.

you need to close synaptic and then run automatix.

---

### Post by -Ghost9- on 2007-02-09
> **TBOL3 said:**
> get easyubuntu, it will really help.

?:confused:

---

### Post by techno-mole on 2007-02-09
you could try what i did, i couldnt get embeded files to play (movie trailers and such like)
what i did was using synaptic to remove totem and all associated files, then using automatix i uninstalled all the other media players, then i installed just real player, and the 2 codec packs, the multimedia ones and the aud ones, now i can play those types of files.
im not saying it will work, just that it worked for me.

---

### Post by Jive Turkey on 2007-02-10
Automatix got it half working, I now get audio and the right half of the video displayed on the left side of the viewer, and blue background on the right side of the viewer (in any media player) from quicktime files.  Ok maybe thats 3/4ths not half. 

 Is there an easy to use converter that will make quicktime *mov files into something else that works and can be edited?

---

### Post by punong_bisyonaryo on 2007-02-16
Is there a way aside from using Automatix or EasyUbuntu? Does anyone know which codec/package/player actually gets quicktime to play?

---

### Post by kornelix on 2007-02-22
I have tried all options mentioned in this thread. Nothing works with .mov files
(except Windows of course). Most of the media players crash, including Real Player 10. Others put out some cryptic message or nothing at all. Mplayer is my favorite - it starts and runs for about 0.1 seconds and then stops. No message.

What a bunch of ...

---

### Post by Ben Sprinkle on 2007-02-22
I play .mov's all the time in totem, just install these codecs.

Search gstreamer in synaptic. Install ffmpeg, the ugly and the bad series. That should be all you need for .mov, .wma, .mp3 and more.

---

### Post by kornelix on 2007-02-23
> **Ben Sprinkle said:**
> I play .mov's all the time in totem, just install these codecs.

Search gstreamer in synaptic. Install ffmpeg, the ugly and the bad series. That should be all you need for .mov, .wma, .mp3 and more.
I have every gstreamer codec installed except those named -dev or -doc. With this quicktime file, Totem starts and stops in a fraction of a second and says nothing. I ran it from a terminal in hopes of seeing a message, but still got nothing. The file plays in Windows with Apple quicktime player.

---

### Post by Maestro23 on 2007-02-23
I play quicktime files(offline & online) thru FF 2.0 and mplayer plug-in.  Have the Win32 codecs installed.  Offline, can play the files in Mplayer, Vlc, and gxine with no problems. Running Edgy 6.10

---

### Post by Ben Sprinkle on 2007-02-23
> **kornelix said:**
> I have every gstreamer codec installed except those named -dev or -doc. With this quicktime file, Totem starts and stops in a fraction of a second and says nothing. I ran it from a terminal in hopes of seeing a message, but still got nothing. The file plays in Windows with Apple quicktime player.

Strange, mine works fine.

---

### Post by FrancoNero on 2007-04-21
in firefox, i can play quicktime with sound, but no picture. offline, i tried opening a quicktime mov 1080 file (HD) and that crashes whatever player i try to open it with..... same with 740 HD, I got 480 HD working... this is annoying....
weird if i click on an apple trailer page and open the 480 HD trailer, it opens totem and it streams okay. the same trailer in small medium or high, it gives me the green mpaa screen and that was it, picture wise.....

---

### Post by heepie on 2007-09-20
To play .mov files like those from quicktime you need to install the xine extra pluggins. The easiest way on doing this is throught the Add/remove programs. Make sure that the option on the right is show: "all available applications" and type xine. For the hardcore people that like to do it through the terminal here a good place to get some instructions:

[http://xinehq.de/index.php/faq#](http://xinehq.de/index.php/faq#)

Good luck!!!

---

