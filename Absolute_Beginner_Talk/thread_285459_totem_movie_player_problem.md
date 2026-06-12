---
title: "totem movie player problem"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2006-10-26
i get this error when i try and play a movie, im not sure if its like that for all movies but it is for the ones i have tried, this is the error:

"subclass did not specify output size"

---

### Post by Toxicity999 on 2006-10-26
Weird errors like that most likely occur when you don't have the correct codecs installed try:

sudo apt-get install gstreamer0.10*

in a terminal, it will install a few un needed things but this installs every GStreamer Codem there is.

---

### Post by Fittersman on 2006-10-29
i get this

```
cleippi@FamilyComputer:~$ sudo apt-get install gstreamer0.10*
Password:
Reading package lists... Done
Building dependency tree... Done
Note, selecting gstreamer0.10-alsa for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-audiosink for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-bad-doc for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-x for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-base-dbg for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-fluendo-mpegdemux for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-base-doc for regex 'gstreamer0.10*'
Note, selecting libgstreamer0.10-0 for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-ugly for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-colorspace for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse for regex 'gstreamer0.10*'Note, selecting gstreamer0.10-plugins-bad-multiverse for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-good for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-ffmpeg for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-pitfdll for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-videosink for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-ugly-dbg for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-lame for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse instead of gstreamer0.10-lame
Note, selecting gstreamer0.10-plugins-good-dbg for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-ugly-doc for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-good-doc for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-bad for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-doc for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-fluendo-mp3 for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-gl for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-esd for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-base-apps for regex 'gstreamer0.10*'
Note, selecting libgstreamer0.10-dev for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-sdl for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-gnomevfs for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-plugins-base for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-gnonlin for regex 'gstreamer0.10*'
Note, selecting gstreamer0.10-tools for regex 'gstreamer0.10*'
Note, selecting libgstreamer0.10-0-dbg for regex 'gstreamer0.10*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-base-dbg: Depends: gstreamer0.10-alsa (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                  Depends: gstreamer0.10-gnomevfs (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                  Depends: gstreamer0.10-plugins-base (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                  Depends: gstreamer0.10-x (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
                                  Depends: libgstreamer-plugins-base0.10-0 (= 0.10.7-0ubuntu4) but 0.10.7-0ubuntu5 is to be installed
  libgstreamer0.10-dev: Depends: libglib2.0-dev but it is not going to be installed
E: Broken packages
```

---

### Post by jimmygoon on 2006-10-29
Here:

totem is a joke... 100%... so...

"sudo apt-get remove totem-gstreamer totem totem-mozilla"

"sudo apt-get install vlc mozilla-plugin-vlc"

enjoy!

---

### Post by Toxicity999 on 2006-10-29
yea that would be my point too, but VLC completely hates being run with Beryl... Seemingly anyway.

---

### Post by mblinux on 2006-10-29
If you want to keep totem you could try to use Totem-Xine instead of Totem-Gstreamer and see if the error still occurs.

---

### Post by jimmygoon on 2006-10-29
> **Toxicity999 said:**
> yea that would be my point too, but VLC completely hates being run with Beryl... Seemingly anyway.


I know... I just turn it off :( Its such a shame...

---

### Post by Fittersman on 2006-10-30
so what are you guys sayin for me to do then? (specific directions please :D)

---

