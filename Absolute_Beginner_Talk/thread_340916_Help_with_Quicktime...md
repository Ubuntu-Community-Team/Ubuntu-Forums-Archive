---
title: "Help with Quicktime.."
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by kimro on 2007-01-17
I reinstalled Ubuntu Edgy cuz I was upgrading my HDD and I can't play embeded quicktime movies from apple website anymore.

I've installed 
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

AND VLC like last time as specified here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

Codecs and VLC are all newest versions.
All I'm getting is a black screen with (no screen) message. Can anyone help?
Thanks!!

---

### Post by spockrock on 2007-01-17
> **kimro said:**
> I reinstalled Ubuntu Edgy cuz I was upgrading my HDD and I can't play embeded quicktime movies from apple website anymore.

I've installed 
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

AND VLC like last time as specified here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

Codecs and VLC are all newest versions.
All I'm getting is a black screen with (no screen) message. Can anyone help?
Thanks!!

what does the terminal spite out when your do that command sudo apt-get install gstreamer0....etc....??

---

### Post by kimro on 2007-01-18
Will get the output for you guys this evening when I get home. Thank you!

---

### Post by Delkster on 2007-01-18
> **kimro said:**
> I reinstalled Ubuntu Edgy cuz I was upgrading my HDD and I can't play embeded quicktime movies from apple website anymore.

Do you have a browser plugin for a video player, and if yes, which player? VLC? The players don't generally come with browser plugins, you'll need to install a plugin separately. They're available in the repositories, though.

I have totem-xine and the corresponding browser plugin, and I think I was able to play videos on the Apple site when I tried (apart from the fact that my lousy connection isn't enough for the streams, and the Totem plugin offers no way of, say, buffering the entire clip before playing).

---

### Post by kimro on 2007-01-18
What I get for VLC:
```
~$ sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
Note, selecting vlc-plugin-dvb for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-ggi for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-esd for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-mad for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-alsa for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-ogg for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-sdl for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-arts for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-glide for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-xosd for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-svgalib for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-aa for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-dv for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-lirc for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-a52 for regex 'vlc-plugin-*'
mozilla-plugin-vlc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

What I get for codecs:
```
~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
> gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-gl is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
libxine-extracodecs is already the newest version.
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Everything worked using these commands in my last install... help would be appreciated!! Thanks.

---

### Post by RomeReactor on 2007-01-18
Make sure you don't have more than one browser video plugin installed, like totem-mozilla or mozilla-mplayer (though i recommend using the mplayer plugin, haven't had any trouble with it).

---

### Post by kimro on 2007-01-18
Thanks for the tip. Now... how would I uninstall mozilla-vlc plugin?

update: 
I installed mplayer as recommended, used Synaptic Package Manager to uninstall mozilla-vlc, restarted firefox and bam! everything works.

Now I can enjoy apple.com thanks to ubuntuforums users :)

---

### Post by pissedoffdude on 2007-01-18
> **kimro said:**
> Thanks for the tip. Now... how would I uninstall mozilla-vlc plugin?

just search vlc in synaptic and remove the mozilla-vlc plugin

---

### Post by kimro on 2007-01-18
While at it, I have one more question.
When I play 720p HD movies using VLC or Totem, screen gets choppy.
It helps when I turn off Compiz but still choppy...

I'm running
AMD64 Dual Core x3800
1gb DDR400
6600GT 128mb

Any suggestions or inputs?

---

### Post by Delkster on 2007-01-27
> **kimro said:**
> While at it, I have one more question.
When I play 720p HD movies using VLC or Totem, screen gets choppy.
It helps when I turn off Compiz but still choppy...

It may be that the Xv video overlay isn't available or working correctly when using compiz. Xv is used to allow video playback (video scaling etc.) to be accelerated by the graphics hardware, and you generally want Xv support at least for high-resolution videos.

If it's also choppy when you have compiz disabled, have you checked whether your video player is using Xv? For GStreamer applications, such as Totem (if you use the totem-gstreamer package, which is installed by default, instead of totem-xine) this is set in gstreamer-properties (you need to run that from a terminal or something -- it was removed from the menus, I guess on the premise of simplicity). In VLC you can set it in the player preferences, in Video > Output Modules (you'll need to have advanced options visible).

Running the video player from the command line may also yield some useful information. Applications often output informational messages about their operation in the terminal.

---

