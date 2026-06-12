---
title: "Can't watch streaming video."
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by keith11 on 2007-01-23
Hi, I am typing here after going through all the guides and wikis there are out there for playing streaming video on linux. I have not been able to play online video whether it's real or windows media. I have the win32codecs, totem-xine, mozilla-mplayer and all the other packages installed that are mentioned on the Restricted Media format guide in this forum. Whenever I try to play an online video, either in Firefox or Mozilla, there appears nothing on the video screen. In Firefox, the screen just stays gray and the message on the bottom shows "done", but no streaming occurs. In Mozilla, the screen of the video playback at least shows that I need a plugin. Following are the contents of:

1. /usr/lib/mozilla/plugins

libnullplugin.so mplayerplug-in-dvx.so
libtotem-basic-plugin.so mplayerplug-in-dvx.xpt
libtotem-basic-plugin.xpt mplayerplug-in-qt.so
libtotem-complex-plugin.so mplayerplug-in-qt.xpt
libtotem-complex-plugin.xpt mplayerplug-in-rm.so
libtotem-gmp-plugin.so mplayerplug-in-rm.xpt
libtotem-gmp-plugin.xpt mplayerplug-in.so
libtotem-mully-plugin.so mplayerplug-in-wmp.so
libtotem-mully-plugin.xpt mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.so mplayerplug-in.xpt
libtotem-narrowspace-plugin.xpt

2. /usr/lib/mozilla-firefox/plugins

libtotem-basic-plugin.so mplayerplug-in-gmp.so
libtotem-basic-plugin.xpt mplayerplug-in-gmp.xpt
libtotem-complex-plugin.so mplayerplug-in-qt.so
libtotem-complex-plugin.xpt mplayerplug-in-qt.xpt
libtotem-gmp-plugin.so mplayerplug-in-rm.so
libtotem-gmp-plugin.xpt mplayerplug-in-rm.xpt
libtotem-mully-plugin.so mplayerplug-in.so
libtotem-mully-plugin.xpt mplayerplug-in-wmp.so
libtotem-narrowspace-plugin.so mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.xpt mplayerplug-in.xpt
libunixprintplugin.so

I had Mandriva Powerpack 2007 installed earlier but I had the same problem in there too. I am not sure what I need to make this work. I just noticed I am not able to play any video file in Mplayer as a stand alone player too. The error I get while trying to play a video file in Mplayer is "Error opening/initializing the selected video _out (-vo) device". When I try to play an MP3 file it gives an error saying "Requested audio codec family [mp3] (afm=mp3lib) not available. Enable it at compilation." But it still plays the audio file with not so clear quality. Any suggestions please?

I am attaching the screenshot of the error I get in Mozilla as well as in Firefox.

---

### Post by stijn_pol on 2007-01-23
Is it possible that you are trying to watch Flash movies?? Like on youtube...
Some sites use the newest version, Flash 9. You can download it from [www.adobe.com](www.adobe.com)
jip, I took a look at your screenshots, download the flash plugin.

---

### Post by keith11 on 2007-01-23
I think I have flash installed as I can play movies from youtube.com (although I can't maximize the screen for a full screen view). When I right click on the flash movie I can figure out from the menu that flash player 9 is installed. 

My Mplayer itself is not playing any video files. Any further suggestions? Thanks.

---

### Post by stijn_pol on 2007-01-23
I checked the sites and they require wind$ws media player or realplayer.
There should be howto's on how to play such movies in mplayer.

edit: I found howto on to forum to install mplayer with all codecs: [http://www.ubuntuforums.org/showthread.php?t=336706](http://www.ubuntuforums.org/showthread.php?t=336706)
hopefully this will help you out

---

### Post by kevinlyfellow on 2007-01-23
An easier way to do it, if you don't mind watching it in something that isn't in the browser, is to use the MediaPlayerConnectivity extension in firefox.  [https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

---

### Post by keith11 on 2007-01-24
I would greatly appreciate if I can get some more suggestions for helping me overcome this problem. It was the inability to play streaming video/audio in Mandriva Powerpack 2007 which was one of the main reasons for me to switch to Ubuntu 6.10 and now I am facing the same problem. I have installed all the codecs for totem too, as I can verify when I type "about:plugins" in Firefox address box. There are windows as well as real plugins installed for totem, so even if mplayer was not able to open the file, totem should. I went through a 1 hours long compilation process of the mplayer by following the "howto" as Stijn_pol suggested and then installed mplayer. The result is the same as I mentioned in my first post in this thread. I can't play online streams through any media player, so what could be wrong?

I even have VLC plugins for mozilla, but nothing, absolutely nothing plays the online media files, which is kind of frustrating me a lot now as I already switched from Mandriva after a painful reformatting of the linux parititions. I will greatly value any help regarding this, whether it is about making mplayer work without the video output error or even using totem for streaming video. 

Kevinlyfellow: Thanks for that suggestion, I tried it, but it's not what I think I will be very comfortable with.

UPDATE: Great news!:) Well, not very great, but yeah I was finally able to play the video with Totem Movie player. The only thing I changed was the installation of linux-restricted-modules and nvidia glx (I had the generic nvidia installed). The systesm asked me to restart and I restarted. I saw two more options added in the grub bootloader, which were Ubuntu kernel .... 386 and Ubuntu recovery  kernel ... 386. Previously I had only Ubuntu kernel... generic and Ubuntu recovery kernel ... generic. I don't know if it is because of the nvidia glx or the restricted linux modules, but I can play the video. The small complain is that I can't see the video in full screen. I still wish I can make mplayer work so that I can get the flexibility of changing the resolution for the streaming media. I still need help.

---

### Post by Canis familiaris on 2007-01-24
The best would be to download codecs using Automatix
Download and install Automatix with the instructions given in [getautomatix.com]("http://www.getautomatix.com/")
Now install all appropriate codecs in using the Automatix GUI.

---

### Post by keith11 on 2007-01-24
Yet another update, but on the negative side. When I posted the update I had played a video from cbsnews.com which requires a real player codec (in windows, it allows the option to play either in real or windows media) and the video played fine, of course without the option of full screen. BUt just now I tried playing streaming audio from a website which requires real audio plugin but the error message was:

 "Totem could not play 'file:///home/veeral/.mozilla/firefox/k1m41khu.default/Cache/59D91DD6d01'." There is no plugin to handle this movie.

On yet another website (I tried this in mozilla player, not firefox) I tried playing windows media video and it gave me an error saying it needed a plugin to play the file. I just now tried playing the same movie in Firefox and there is just a gray screen, not even an error or a requirement of plugin message, nothing. Back to square one again.:) Need help.

Anurag: I did install the codecs required for streaming media or non-streaming media from the howto mentioned earlier in this thread. I think it covered all the codecs. I am not sure what extra codecs automatix would have and if they could fix a plugin problem. I will try though. Thanks.

But yeah, as I mentioned, as of now, things seem to be back to square one. Any suggestions please?

---

