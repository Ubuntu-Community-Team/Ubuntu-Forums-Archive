---
title: "Codecs for playing YOUTUBE.com videos"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-06-15
One of my PC's which is  running Ubuntu edgy will not play the videos in "YOU TUBE" and where the video should appear is a blacked out box. I'm able to view dvd's on this computer without problems  so wonder if anyone has some advice what  the missing codec might be and where can I find it please?

---

### Post by Kobalt on 2007-06-15
You miss the [flash plugin]("https://help.ubuntu.com/community/RestrictedFormats/Flash"), not a video codec.

---

### Post by a.v.l on 2007-06-15
> **Kobalt said:**
> You miss the [flash plugin]("https://help.ubuntu.com/community/RestrictedFormats/Flash"), not a video codec.

I've istalled this flash plug in and I can now see the video if I use Firefox, but unfortunatly there is no sound to accompany it.  My prefered browser Opera, will still not play the videos in YouTube.

---

### Post by Jerry N on 2007-06-15
FWIW Firefox gives video and sound on Youtube videos on my machine.  I haven't added any plugins that I know of but I am a complete newby to Linux and probably don't know what is going on anyway.  

Jerry

---

### Post by Anonii on 2007-06-15
> **a.v.l said:**
> I've istalled this flash plug in and I can now see the video if I use Firefox, but unfortunatly there is no sound to accompany it.  My prefered browser Opera, will still not play the videos in YouTube.
Is your audio device busy when you are trying to listen to the flash videos? Like, are you running Amarok, a game, or something (it doesn't matter if it's paused or not.)?

---

### Post by ggaaron on 2007-06-15
You can run multiple audio sources on alsa. Amarok hasn't anything to do with it.

Read this:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

With opera... opera sucks... This is unfortunately true, you can love it, but it can only handle one flash page at a time, when you use multiple tabs with flash videos or something, all of places where flash should be will become white... From what I know opera isn't open sourced, so no one can do anything about bad port to linux. I use firefox now, but for some time I used opera as my primary browser, and opened flash sites in firefox if they were displayed inpropertly in opera.

---

### Post by Anonii on 2007-06-15
> **ggaaron said:**
> You can run multiple audio sources on alsa. Amarok hasn't anything to do with it.

Read this:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

With opera... opera sucks... This is unfortunately true, you can love it, but it can only handle one flash page at a time, when you use multiple tabs with flash videos or something, all of places where flash should be will become white... From what I know opera isn't open sourced, so no one can do anything about bad port to linux. I use firefox now, but for some time I used opera as my primary browser, and opened flash sites in firefox if they were displayed inpropertly in opera.
I'm aware that you can run multiple audio sources, but that requires DMIX and OSS emulation (in most cases), which sometimes is not configured by default (in my case, in Feisty, it wasn't) and a small edit in ~/.asoundrc is needed.

---

### Post by sailor2001 on 2007-06-15
you could try grease monkey in firefox (add-on)

---

