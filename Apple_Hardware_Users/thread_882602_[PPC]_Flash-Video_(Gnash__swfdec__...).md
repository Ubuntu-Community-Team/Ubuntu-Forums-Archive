---
title: "[PPC] Flash-Video (Gnash / swfdec / ...)"
date: 2008-08-07
forum: Apple Hardware Users
---

### Post by chimaera on 2008-08-07
Hi, I'm trying to get Flash Video to work (youtoube & co) on my 12" Powerbook G4 with Ubuntu 8.04 installed. 
I tried Gnash, but while small Flash-Applets work, youtube just flickers and then shows me a white pane where the video should be (gnash context-menu is available, though. 
Using swfdec, Youtube works, but the video is very skippy and hardly watchable.
I also tried [1] which should make mplayer available for embedded flv playback, but nothing happens at all. 

For now I'm stuck with clive to download the vids to my HDD and then watch them using VLS or mplayer, but those downloaders are limited to certain pages and I'm looking for a more generic approach.  

Has anyone had success with the methods mentioned above? Any other suggestions? 

Thanks. 

[1] [http://www.gc-group.dk/youtube/](http://www.gc-group.dk/youtube/)

---

### Post by ubuntubrian on 2008-08-09
Gnash worked on my G4 TiBook several versions back but quit  with the same problems you have. I installed swfdec from the repos and it plays beautifully but no sound. I'm having general sound issues in 8.04 but when I did have sound for all other apps I had none in swfdec.
I use the firefox add-on "download helper" and can get most vids. I haven't tried using mplayer but I might.
swf in ppc is a pain for sure and to have it and then lose it is a bummer to. I'm feeling hopeful with swfdec because it has played all the flash I've come across but again, no audio.

---

### Post by ubuntubrian on 2008-08-09
A good morning. After following the wiki for pulseaudio:[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
I thought of moving my .asoundrc out of the way as it seemed there was a conflict between pulse and alsa. the wiki on pulse had me create or add to that file with some pcm stuff (ahich Sam had said he didn't need to do to get pulseaudio working but we had already tried getting rid of that file at the meeting to no avail).
In any case I moved it, logged out and in and now have sound all over the system. All the players and even swfdec plugin is playing youtube vids WITH sound!
I also had downloaded the latest alsa-drivers from the alsa website and built them with my soundcard, powermac, so that may have helped. I can watch those videos on youtube or google inside firefox!
Sweet!!

---

### Post by chimaera on 2008-08-10
Well, with swfdec, sound works pretty good, it is just the video-playback that is very choppy. 

Thank you for the hint, though. I'll look into it. I remember that some years back mplayer also had choppy video playback due to audio-related settings.

---

### Post by Starlight on 2008-10-11
Hi! Have you managed to fix it? I have exactly the same problem. :( Gnash is just plain white, but with the context menu available, while swfdec plays sound quite well, but not the video...

---

