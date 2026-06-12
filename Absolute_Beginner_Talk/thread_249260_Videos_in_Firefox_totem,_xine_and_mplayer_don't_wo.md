---
title: "Videos in Firefox totem, xine and mplayer don't work."
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by LA-Jam on 2006-09-02
Hi everybody,

I'm new to Linux and Ubuntu and tried to watch videos from [www.break.com](www.break.com) . You have to stream them from there. Could anybody who's able to watch these movies tell me which player to use and how to configure it?

I tried otem-gstreamer-firefox-plugin only to find it marked "broken" in the synaptic-tool. It said "broken", although I had made sure the plugin version matched the general totem version. I also installed 

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg,

as described in the "desktopguide.pdf".  
Still there was no video playing at all. 

After that I uninstalled totem and tried xine with the plugin totem-xine-firefox-plugin. The player worked in a way, but just showed a black screen. Maybe I was missing some codecs, but there was no message saying so. My problem actually is I don't know how to get the codecs and how to install them.

After that I uninstalled xine and tried mplayer, which I liked best, because it cashed the video and there's a bar showing the process. It seems to run the movie then, but like with cine it doesn't show anything on the screen.

After two hours of trying I'd really appreciate your help. Thanks in advance, 

LA-Jam

---

### Post by skymt on 2006-09-02
You should probably install libxine-extracodecs to get the totem-xine plugin working. Also, I like mozilla-plugin-vlc.

Depending on what codec break.com uses, you may also need [w32codecs](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by LA-Jam on 2006-09-03
Hi skymt,

thanks for your advice. The xine-plugin was the only one I got to work, but I don't like it, because the bar showing progress does not move, the playbutton  only works once, I cannot watch the movie "full screen" and the settings-button in the contextmenu doesn't work, either. 

From what I've seen so far I'd really like to get mplayer running. When I installed it with the synpatic-paket-manager the buttons worked and there's a bar showing progess, but there's no picture and no sound.

On the mplayer-homepage I read you have to compile the program with certain libraries to be able to stream windows codecs. Will I have to do so or is there a way I can work it out with the ubuntu paket magager?

Thanks very much for your help, LA-Jam

---

