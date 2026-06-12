---
title: "is HD playback possible in Ubuntu ?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-08-18
i've got a graphics card that will cope with HD playback, and today i've invested in a monitor that has the required resolution to cope as well, so i'm wondering if anyone knows if it's possible ?

i downloaded a small movie trailer in HD to test it out, but when it played, it was double speed and the sound was garbled.

just wondered if that was because of my hardware, or i need a codec or something like that ??

---

### Post by taurus on 2007-08-18
Maybe this helps.

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by jasonwatkins on 2007-08-18
i'm not actually looking at playing HD films or anything like, just the odd movie trailer here and there, because i've only got a regular DVD burner, with no HD playback capability.

---

### Post by stoeptegel on 2007-08-18
Get a video player which supports the mplayer core with w32codecs.

---

### Post by jasonwatkins on 2007-08-18
i've been reading about "xine-hd", which appears to do what I want but I can't seem to find it anywhere - nothing like it in package manager or 'add/remove programs'.

i've even tried 'apt-get xine-hd' but no luck.

---

### Post by jasonwatkins on 2007-08-18
to be ultra annoying, I will probably need pointing in the right direction regarding the actual codec to get for mplayer ..

i'm so used to downloading the K-Lite codec pack :D

---

### Post by mysticmatrix on 2007-08-18
If it is a regular trailer from Apple or somewhere, Totem can easily play it after you install plugins required.(Feisty does this by simply clicking file to play).

However you may notice that video is choppy, in which case you can either try VLC or Mplayer.

---

### Post by jasonwatkins on 2007-08-18
i've got mplayer installed and the latest w32codecs, but the playback is still double speed with garbled sound.

VLC played the file with NO sound and double speed playback ..

---

### Post by JeevesBond on 2007-08-18
You may need to [update your version of FFMPEG](http://ffmpeg.mplayerhq.hu/download.html) (what VLC uses to decode media files) to the development version, rather than what's in the Ubuntu repositories. Sorry if that's a bit of a pain. :(

I wrote an article about doing that if you need help: [Installing the latest ffmpeg on Feisty Fawn](http://www.apaddedcell.com/installing-the-latest-ffmpeg-on-ubuntu-feisty-fawn-7-04). I wrote that because I had to do it once and didn't want to forget the procedure!

---

### Post by jasonwatkins on 2007-08-18
> **JeevesBond said:**
> You may need to [update your version of FFMPEG](http://ffmpeg.mplayerhq.hu/download.html) (what VLC uses to decode media files) to the development version, rather than what's in the Ubuntu repositories. Sorry if that's a bit of a pain. :(

I wrote an article about doing that if you need help: [Installing the latest ffmpeg on Feisty Fawn](http://www.apaddedcell.com/installing-the-latest-ffmpeg-on-ubuntu-feisty-fawn-7-04). I wrote that because I had to do it once and didn't want to forget the procedure!

well this is getting a bit frustrating now as i'm now venturing in to areas i know nothing about again :)

I ran this command "./configure --enable-gpl --enable-shared --enable-libvorbis --enable-libogg --enable-pp --enable-libtheora" 

but I had to remove libvorbis, libogg and libtheora as they apparently weren't downloaded when I used 'svn' to get the latest version of ffmpeg.

VLC still plays the clip at double speed with no sound - if you're wondering what the clip is, it's the HD trailer of "rules of attraction" download from the microsoft website.

---

### Post by jasonwatkins on 2007-08-18
i added the /usr/local/bin to the start of the config file as well and "ffmpeg" ran from the command line with no errors, but still the same playback

---

### Post by mysticmatrix on 2007-08-18
jasonwatkins, I downloaded the same trailer from Microsoft's website and extracted the movie by wine.

Initially I wasn't able to hear sound(No video problems) but they vanished after installing w32codecs package from the medibuntu repositaries. 

PS: The first part of trailer is in fast motion; guess that doesn't makes you think that Totem is showing it in double speed :)

EDIT: VLC Player was still not able to produce sound

---

### Post by jasonwatkins on 2007-08-18
i've got the latest w32codecs already installed.

and when I try playing the trailer in totem - it crashes it ...

---

### Post by jasonwatkins on 2007-08-18
actually that's just actually sunk in .. durrrrrrrr

the trailer speed is fine .. it's just the audio that is garbled ..

---

### Post by jasonwatkins on 2007-08-18
i've just downloaded the 1080p and 720p trailers for T2 and both play fine, at normal speed with no jumps or glitches - in kmplayer i might add - but both have zero sound.

---

### Post by Kitsun on 2007-08-18
Have you noticed any other applications (that have a purpose other than playing video) having problems with sound?

Linux sound is still a bit screwy, try closing down every program, and than try the video?

---

### Post by jasonwatkins on 2007-08-19
have no problems with sound in any other application.

i use XMMS as my mp3 player and it works fine.

---

### Post by mysticmatrix on 2007-08-19
Jason, the w32codecs can be used only by mplayer and its derivatives like KMplayer only by default. To enable it in Totem, you would need pitfdll pacage(I don't remember the exact name).

As a personal choice, I prefer SMplayer for my playbacks.

Also make sure that you have compositing turned off i.e. Beryl or other eyecandy while playback.(It causes problems sometime)

---

### Post by jasonwatkins on 2007-08-20
> **mysticmatrix said:**
> As a personal choice, I prefer SMplayer for my playbacks.

Also make sure that you have compositing turned off i.e. Beryl or other eyecandy while playback.(It causes problems sometime)

i might try SMPlayer out of interest, but there's nothing else running that could affect the sound output when I try and play these clips.

The sound on the "Rules of Attraction" clip is garbled, so it surely must be something to do with decoding it or something like that ??

i assume that since the sound on the "T2" trailer is just silent, it just disables the audio stream since it can't find the right audio processor ?

---

### Post by jasonwatkins on 2007-08-20
> **mysticmatrix said:**
> As a personal choice, I prefer SMplayer for my playbacks.

Sir, you are the dude of dudes :)

SMPlayer played both trailers 100% fine, with full, ungarbled sound.

This is now officially my number one media player ! 

Thanks.

---

### Post by mysticmatrix on 2007-08-20
Great!!!
And please mark this thread as solved so that other may be helped when they have similar problems. :)

---

