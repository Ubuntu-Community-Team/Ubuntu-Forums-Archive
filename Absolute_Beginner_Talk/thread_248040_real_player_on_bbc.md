---
title: "real player on bbc"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by gmcm1979 on 2006-08-31
i have downloaded and installed real player 10, but it does not appear in my list of applications and does not work when streaming on bbc

---

### Post by b_martinez on 2006-08-31
Just out of curiousity, what does bbc stream? MP3, ogg, flac,......? Whichever one it uses, you need that codec (enCOder/DECoder)
 Streamtuner works well. So does Amarok. Rhythmbox ,too.
How did you start it if it doesn't show in the Applications file? Terminal? I hardly use RP10, so I may not be able to help, but we can try.[http://ubuntuforums.org/images/smilies/icon_wink.gif](http://ubuntuforums.org/images/smilies/icon_wink.gif)

---

### Post by rosiet on 2006-08-31
Hello.  I feel your pain, gmcm.  Although realplayer 10 does appear in my applications, I cannot get it to play any of my mp3s.  Nor will rhythmbox.  Does anyone know why not?  They play fine on my phone. 

Rosie

---

### Post by b_martinez on 2006-08-31
> **rosiet said:**
> Hello.  I feel your pain, gmcm.  Although realplayer 10 does appear in my applications, I cannot get it to play any of my mp3s.  Nor will rhythmbox.  Does anyone know why not?  They play fine on my phone. 

Rosie

You need to have the codecs installed (lame for mp3) and you need to tell the players where to find the codecs.

HARD WAY
This is the output (on my box) of 
sudo slocate lame
/var/cache/apt/archives/emodule0-flame_1%3a0.16.999.032-1_i386.deb
/var/lib/doc-base/info/lame.list
/var/lib/doc-base/info/lame.status
/var/lib/dpkg/info/lame.postinst
/var/lib/dpkg/info/lame.list
/var/lib/dpkg/info/lame.prerm
/var/lib/dpkg/info/lame.md5sums
/var/lib/dpkg/info/liblame0.shlibs
/var/lib/dpkg/info/liblame0.list
/var/lib/dpkg/info/liblame0.postinst
/var/lib/dpkg/info/liblame0.postrm
/var/lib/dpkg/info/liblame0.md5sums
/var/lib/dpkg/info/glame.postinst
/var/lib/dpkg/info/glame.list
/var/lib/dpkg/info/glame.prerm
/var/lib/dpkg/info/glame.postrm
/var/lib/dpkg/info/glame.md5sums
/var/lib/dpkg/info/lame-extras.md5sums
/var/lib/dpkg/info/lame-extras.list
/var/lib/dpkg/info/gstreamer0.8-lame.postinst
/var/lib/dpkg/info/gstreamer0.8-lame.list
/var/lib/dpkg/info/gstreamer0.8-lame.preinst
/var/lib/dpkg/info/gstreamer0.8-lame.postrm
/var/lib/dpkg/info/gstreamer0.8-lame.md5sums
/usr/bin/lame
/usr/bin/glame-convert
/usr/bin/glame
/usr/bin/cglame
/usr/lib/gstreamer-0.10/libgstlame.so
/usr/lib/kde3/libaudiocd_encoder_lame.la
/usr/lib/kde3/libaudiocd_encoder_lame.so
/usr/lib/menu/glame
/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0
/usr/lib/glame
/usr/lib/glame/normalize.so
/usr/lib/glame/debug.so
/usr/lib/glame/tutorial.so
/usr/lib/glame/audio_io_oss.so
/usr/lib/glame/mixer.so
/usr/lib/glame/resample.so
/usr/lib/glame/file_oggvorbis_out.so
/usr/lib/glame/audio_io_alsa.so
/usr/lib/glame/audio_io_esd.so
/usr/lib/glame/fft_plugins.so
/usr/lib/gstreamer-0.8/libgstlame.so
/usr/lib/eroaster/lame.py
/usr/lib/eroaster/lame.pyo
/usr/lib/eroaster/lame.pyc

maniac@the-asylum:~$

In /usr/bin and /usr/lib/ is where the codecs are stored. Find yours and edit the preferences files of rhythmbox and RP to point to them. OR install 'Automatix' and let it run. It supposedly install these, from what I understand. Of course, I could be totally wrong about that.

EASY WAY 
uninstall rhythmbox and/or RP10. Search synaptic for mp3 ogg flac libquicktime, and whatever the RP10 native codecs are. Install these, then install rhythmbox and/or RP10.
OR 
uninstall rhythmbox and/or RP10. And install , XMMS, Amarok, lame, lame-extras ,gstreamer0.8-lame, liblame,xmms-liveice.

---

### Post by rosiet on 2006-08-31
Thanks b_martinez.  I choose EASY WAY 1.  But searching for "mp3" in synaptic gives me a host of files.  Do I need to install them all?  Searching for "mp3 ogg flac libquicktime" gives me nothing... 

It doesn't seem to recognise "codec" either... ???

---

