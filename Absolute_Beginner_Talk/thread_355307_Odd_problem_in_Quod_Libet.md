---
title: "Odd problem in Quod Libet"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-02-07
So for a little while now, I've been noticing some of my mp3s are making an irritating, low 'warble' sound. Seems to occur mostly in songs by 'lo-fi' bands or older recordings. At first I thought it might be the ancient receiver i have the computer hooked up to, but i hooked headphones directly to the PC, same problem. 

Then I assumed soundcard, but before taking the drastic step of swapping hardware out, I thought "hey, maybe it's the app i'm playing it with"! So I loaded up the mp3s in question in Totem, and hey, what do you know? NO WEIRD NOISE.

Any ideas on how to fix this? I'd like to continue using Quod Libet, but i'd rather my music sounds good.

EDIT: I've now tried one of the mp3s in question in a variety of media players. The problem occurs when I play it in Rhythmbox, Exaile, Quod Libet, and Banshee. It plays PERFECTLY in VLC and Movie Player. 

If a mod could change the thread title to something a little more appropriate, i'd appreciate it.

---

### Post by hugmenot on 2007-02-07
What kind of MP3 decoder do you have installed in GStreamer?
There&#8217;s the old MAD decoder and the newer "legit" decoder by Fluendo. (Run this in a shell: *gst-inspect-0.10 | grep mp3.*decod*)

Do all MP3s have artifacts?

Do other audio format have artifacts?

---

### Post by ComplexNumber on 2007-02-07
**sunexplodes**
so it seems like the video players are playing audio correctly whilst the audio players aren't, yes?
go to the menu -> system -> preferences -> removable systems selector. for the default output plugin for the audio and the video, what does it show as the output?

---

### Post by sunexplodes on 2007-02-07
> **hugmenot said:**
> What kind of MP3 decoder do you have installed in GStreamer?
There’s the old MAD decoder and the newer "legit" decoder by Fluendo. (Run this in a shell: *gst-inspect-0.10 | grep mp3.*decod*)

Do all MP3s have artifacts?

Do other audio format have artifacts?

mad:  mad: mad mp3 decoder
ffmpeg:  ffdec_mp3on4: FFMPEG MP3ON4 decoder
ffmpeg:  ffdec_mp3adu: FFMPEG ADU-formatted MPEG-1 layer 3 audio decoder
ffmpeg:  ffdec_mp3: FFMPEG MPEG-1 layer 3 audio decoder


as i said, only a few mp3s have these artifacts, not the majority.


> **ComplexNumber said:**
> **sunexplodes**
so it seems like the video players are playing audio correctly whilst the audio players aren't, yes?
go to the menu -> system -> preferences -> removable systems selector. for the default output plugin for the audio and the video, what does it show as the output?

I don't have a "removable systems selector" listed under system>preferences. is there a command i could run to bring it up?

---

### Post by ComplexNumber on 2007-02-07
> I don't have a "removable systems selector" listed under system>preferences. is there a command i could run to bring it up?
sorry, i meant multimedia systems selector.

---

### Post by sunexplodes on 2007-02-07
ah, fantastic. 

both audio and video have "autodetect" selected, but here's what options i have listed: under audio i have ALSA, ESD, and OSS, under video there is SDL, X Window System (No Xv), and X Window System (X11/Xshm/Xv)

---

### Post by ComplexNumber on 2007-02-07
> **sunexplodes said:**
> ah, fantastic. 

both audio and video have "autodetect" selected, but here's what options i have listed: under audio i have ALSA, ESD, and OSS, under video there is SDL, X Window System (No Xv), and X Window System (X11/Xshm/Xv)
for audio, select alsa. see if that makes a difference to playback with rhythmbox, banshee, quod libet, etc. if its still the same,  it may well be some alsa component thats missing or not configured properly

---

### Post by sunexplodes on 2007-02-07
Gave it a try on all three options, and it doesn't seem to make much of a difference, sadly.

---

### Post by ComplexNumber on 2007-02-07
ok, here's another theory. i wonder if its something to do with xine and gstreamer. if you haven't already, install the various gstreamer and xine libs via synaptic (just do a search on name only for "xine" and "gstreamer"). 
just to confirm, do you have totem-xine rather than totem-gstreamer installed? totem-xine is the better of the 2.

also, do you have another sound card installed as well as an inbuilt one? if you don't have alsamixer installed, install it now. open alsamixer and look at the control on the far right hand side. is the volume turned up?

---

### Post by Johan! on 2007-02-07
Same problem here.

Some mp3s play ok in quod libet, others have the warbled sound.
Same problem in Exaile.

I use 1 soundcard, a Creative Audigy 1
All relevant gstreamer 0.10 packages are installed (how do you make a list of installed packages?)

---

### Post by sunexplodes on 2007-02-07
I definately have totem-xine installed, and not totem-gstreamer. 

now, in regards to your second question, i've encountered a bit of weirdness. i only have an onboard sound device, no secondary card is physically installed. BUT, under Change Device, I have two options.  VIA 8237 (ALSA Mixer) and the other is RealTek ALC655 rev 0 (OSS Mixer).

---

### Post by ComplexNumber on 2007-02-07
> **sunexplodes said:**
> I definately have totem-xine installed, and not totem-gstreamer. 

now, in regards to your second question, i've encountered a bit of weirdness. i only have an onboard sound device, no secondary card is physically installed. BUT, under Change Device, I have two options.  VIA 8237 (ALSA Mixer) and the other is RealTek ALC655 rev 0 (OSS Mixer).
select VIA 8237. 

also, go into alsamixer(if you haven't installed it yet, then install it. its useful) and look at the control on the very right hand side. if its a volume control (may say something like "AC97"), turn that right down.

---

### Post by sunexplodes on 2007-02-07
The furthest right sliders are 4 sliders by the name VIA DXS, and only one of them makes any difference, and it just lowers and increases volume, having no bearing on the problem, unfortunately. I don't have anything mentioning AC97, but there are quite a variety of sliders here.

---

### Post by ComplexNumber on 2007-02-07
**sunexplodes**
i used to have the same problem as you (i've since solved it0. i have a creative sound blaster live soundcard, but when i openied up the volume control from the voluem control aplet and alsa mixer, it did NOT show me the controls for bass or treble. when i selected the correct sound card/drivers to be used, it would show the bass and treble controls, but changing them made little differnce to the sound. as you say, it sounded warbled and low quality. for example,when the volume was turned up, the bass seemed to vibrate uncomfortably, as though the speakers were straining.

btw if you have an audio application such as solfege, hydrogen, gtick, etc, can you get any sound out of them at all?

---

### Post by sunexplodes on 2007-02-07
yeah, that is exactly what i'm experiencing, although the problem only happens on a small selection of audio files. 

I appreciate your help, by the way, although i'm thinking of just tossing a different sound card in there.

---

### Post by Johan! on 2007-02-07
Well, I think it's a codec problem.

Some mp3s play fine, others don't.
Only in some programs, some mp3s don't play ok.

I don't think it's a harware problem, because like I said, in other programs I don't hear the strange noises.

---

### Post by ComplexNumber on 2007-02-07
if i were in front of your pc, i may well be able to try out all the usual suspects and eventually solve it. but its more difficult trying to solve someones problem like this, having to suggest various possibilities a few at a time. hope you understand.

one thing i did do was to go into the bios and disable the system sound. i'm sure your problem is due to it using the wrong sound drivers.

---

### Post by sunexplodes on 2007-02-07
Of course, man, i completely understand, and I genuinely appreciate your help thus far. 

I'll give that a shot, see if it works.

---

### Post by ComplexNumber on 2007-02-07
ok, well let me know how it goes.

---

### Post by sunexplodes on 2007-02-07
Ok, the only sound-related option in my bios is AC97 Sound [auto/disabled]

Disabling it kills the onboard sound, and thus i have no sound at all.

---

### Post by ComplexNumber on 2007-02-07
> **sunexplodes said:**
> Ok, the only sound-related option in my bios is AC97 Sound [auto/disabled]

Disabling it kills the onboard sound, and thus i have no sound at all.
as it happens, that was what was being used(until i disabled it) when my audio sounded like yours. it seems like the only problem is a not-so-good quality sound card. but then again, you mention that the problem doesn't exist when playing video. i wonder if thats because its using realtek rather than the via sound driver. its either than or its a xine-gstreamer issue.

---

### Post by sunexplodes on 2007-02-07
it's not that the problem doesn't exist when playing video, it's weirder.

an mp3 that sounds crap in Quod Libet sounds great in VLC or Totem. Same file, different app.

---

### Post by Johan! on 2007-02-07
I recorded some music with the sound recorder.
In the attachment you will find 2 files, one is played by quod libet, the other with xmms.

You can hear the difference.

---

### Post by Johan! on 2007-02-07
Installed codecs: (All packages that start with 'ii' are installed)
```

dpkg -l gstreamer0.10*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-============================
ii  gstreamer0.10-alsa                0.10.10-1ubuntu1                  GStreamer plugin for ALSA
un  gstreamer0.10-audiosink           <none>                            (no description available)
un  gstreamer0.10-colorspace          <none>                            (no description available)
ii  gstreamer0.10-esd                 0.10.4-0ubuntu3                   GStreamer plugin for ESD
ii  gstreamer0.10-ffmpeg              0.10.1-2ubuntu1                   FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3         0.10.2.debian-1                   Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-fluendo-mpegdemux   0.10.4-0ubuntu1                   Fluendo GStreamer plugin for MPEG2 demuxing
ii  gstreamer0.10-gl                  0.10.3+cvs20060918-0ubuntu1       GStreamer plugin for OpenGL output
ii  gstreamer0.10-gnomevfs            0.10.10-1ubuntu1                  GStreamer plugin for GnomeVFS
ii  gstreamer0.10-gnonlin             0.10.5-1ubuntu1                   non-linear editing module for GStreamer
un  gstreamer0.10-lame                <none>                            (no description available)
ii  gstreamer0.10-pitfdll             0.10.0+CVS20060731-0ubuntu0seveas Win32 DLL plugin for GStreamer
un  gstreamer0.10-plugins             <none>                            (no description available)
ii  gstreamer0.10-plugins-bad         0.10.3+cvs20060918-0ubuntu1       GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multive 0.10.3+cvs20060918-1              GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base        0.10.10-1ubuntu1                  GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps   0.10.10-1ubuntu1                  GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good        0.10.4-0ubuntu3                   GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly        0.10.4-0ubuntu3                   GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiv 0.10.4-2                          GStreamer plugins from the "ugly" set (Multiverse Variant)
ii  gstreamer0.10-tools               0.10.10-1ubuntu2                  Tools for use with GStreamer
un  gstreamer0.10-videosink           <none>                            (no description available)
ii  gstreamer0.10-x                   0.10.10-1ubuntu1                  GStreamer plugins for X11 and Pango
```

```

dpkg -l totem*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-================================
ii  totem                             2.16.2-0ubuntu3                   A simple media player for the Gnome desktop (dummy package)
pn  totem-gstreamer                   <none>                            (no description available)
un  totem-gstreamer-firefox-plugin    <none>                            (no description available)
ii  totem-mozilla                     2.16.2-0ubuntu3                   Totem Mozilla plugin
ii  totem-xine                        2.16.2-0ubuntu3                   A simple media player for the Gnome desktop based on xine
un  totem-xine-firefox-plugin         <none>                            (no description available)

```

gstreamer:
```

gst-inspect-0.10 |grep mp3
lame:  lame: L.A.M.E. mp3 encoder
mpegaudioparse:  mp3parse: MPEG1 Audio Parser
mad:  mad: mad mp3 decoder
flump3dec:  flump3dec: Fluendo MP3 Decoder
ffmpeg:  ffdec_mp3: FFMPEG MPEG-1 layer 3 audio decoder
ffmpeg:  ffdec_mp3adu: FFMPEG ADU-formatted MPEG-1 layer 3 audio decoder
ffmpeg:  ffdec_mp3on4: FFMPEG MP3ON4 decoder
ffmpeg:  ffdemux_mp3: FFMPEG MPEG audio demuxer
typefindfunctions: audio/mpeg: mp3, mp2, mp1, mpga
typefindfunctions: application/x-id3v1: mp3, mp2, mp1, mpga, ogg, flac, tta
typefindfunctions: application/x-id3v2: mp3, mp2, mp1, mpga, ogg, flac, tta
```

---

### Post by hugmenot on 2007-02-07
Since the artifacts depend on specific files, I think we can rule out the actual output. It must be contingent on the decoding.

Can you provide an example file so we can test it with our setup?

Also what happens if you decode the file to WAV and listen to that? Use "lame --decode example.mp3". Any differences between players?

EDIT: Aha, Johan does have the Fluendo MP3 plugin. Do you also have that one, sunexplodes? My earlier command didn&#8217;t catch that line. Could you try again with a case insensitive grep (**gst-inspect-0.10 | grep -i mp3.*decod**)?

---

### Post by sunexplodes on 2007-02-07
Looks like I have fluendo too.

mad:  mad: mad mp3 decoder
flump3dec:  flump3dec: Fluendo MP3 Decoder
ffmpeg:  ffdec_mp3on4: FFMPEG MP3ON4 decoder
ffmpeg:  ffdec_mp3adu: FFMPEG ADU-formatted MPEG-1 layer 3 audio decoder
ffmpeg:  ffdec_mp3: FFMPEG MPEG-1 layer 3 audio decoder

---

### Post by hugmenot on 2007-02-07
What happens if you remove that temporarily?

---

### Post by sunexplodes on 2007-02-07
> **hugmenot said:**
> What happens if you remove that temporarily?

You're a genius. Problem solved. 

Thank you so much.

---

### Post by Johan! on 2007-02-07
> **sunexplodes said:**
> You're a genius. Problem solved. 

Thank you so much.


Thanks!:KS

---

### Post by hugmenot on 2007-02-08
Cool. That was a shot into the pure blue actually. 
MAD has been the trusted decoder forever and Fluendo implemented one themselves to put Linux users into the clear legally. I thought it likely that the newer one has defective decoding.

---

### Post by sunexplodes on 2007-02-08
How does fluendo put linux in the clear legally in terms of mp3 decoding?

---

### Post by hugmenot on 2007-02-09
They paid the license fee to Thomson/Fraunhofer that entitles them to binary distribution of the decoder. They are generous so they give it away for free.
Earlier encoders and decoders like MAD or LAME were always distributed as sources only to circumvent a direct infringement. But this didn&#8217;t go too well with the GPL.

some bits of info here: [http://thomas.apestaart.org/log/?p=333](http://thomas.apestaart.org/log/?p=333)

---

