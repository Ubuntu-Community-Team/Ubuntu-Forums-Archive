---
title: "Play MP3 songs"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by jothishankar on 2007-10-08
Hi guys,

I'm a new member here and I would like to know how I can play mp3 songs on my Ubuntu. Note that I don't have an internet connection to get the codecs at my home machine. What's the alternative. Please help.

Thanks in advance.:)

---

### Post by skymera on 2007-10-08
err the codecs :wink:

find a computer with connection and get the codecs :D

no other way i belivee

---

### Post by Terl on 2007-10-08
You will need the codecs, hence an internet connection.  If you can get the connection the following works.

```
sudo apt-get install ubuntu-restriced-extras
```

That command will get you the codecs as well as Flash and java.

---

### Post by Wiebelhaus on 2007-10-08
yea , you'll need a connection but so if someone cruises by this thread looking for support I'm going to post.


 Codecs:





[PHP]sudo apt-get install gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-audiofile gstreamer0.8-cdio gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-misc gstreamer0.10-alsa gstreamer0.10-doc gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-gnonlin gstreamer0.10-gnonlin-dev gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-doc gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-base-doc gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-sdl gstreamer0.10-tools gstreamer0.10-x gstreamer-tools irb1.8 liba52-0.7.4 libbreakpoint-ruby1.8 libcdaudio1 libcmdparse2-ruby1.8 libdaemonize-ruby1.8 libdvdnav4 libdvdread3 libdvdplay0 libfaac0 libfaad2-0 libfreebob0 libgems-ruby1.8 libglib2-ruby libgsm1 libgstreamer0.8-0 libgstreamer0.8-ruby libgstreamer0.10-0 libgstreamer0.10-0-dbg libgstreamer0.10-ruby1.8 libgstreamer-gconf0.8-0 libgstreamer-perl libgstreamer-plugins0.8-0 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-pulse0.10-0 libid3tag0 libjack0.100.0-0 libjinglebase0.3-0 libjinglep2p0.3-0 libjinglexmllite0.3-0 libjinglexmpp0.3-0 liblame0 liblog4r-ruby1.8 libmad0 libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 libmpeg2-4 libncurses-ruby1.8 libopenssl-ruby1.8 libpulse0 libquicktime0 libreadline-ruby1.8 libruby1.8 libruby1.8-dbg libruby1.8-extras libsidplay1 libsoundtouch1c2 libswfdec0.3 libwavpack1 libxvidcore4 libxvidcore4-dev rdoc1.8 ruby1.8 ruby ffmpeg mencoder mplayer xvid4conf libxine-extracodecs libxine1-ffmpeg libxine1
[/PHP]
and install libdvdcss2:
libdvdcss2 1.2.9 - x86
libdvdcss2 1.2.9 - amd64


Just for restricted:

> sudo apt-get install ubuntu-restricted-extras



or just for Amarok MP3 support

> sudo apt-get install gstreamer0.8-mad
sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs

Also media Ubuntu , I don't know much about it but have been told it kickass.

Media Ubuntu:
[http://medibuntu.sos-sts.com/index.php](http://medibuntu.sos-sts.com/index.php)

---

### Post by RomeReactor on 2007-10-08
Hi. A way to get the necessary codecs and their dependencies to enable MP3 playback in Ubuntu without internet is to use Synaptic to generate a package download script, which you can then use on another Ubuntu system with internet connection, or open the script in notepad in windows and use the URLs to get the packages. [Look here]("http://ubuntuforums.org/showpost.php?p=3484273&postcount=2") for a bit more complete instructions. Note that in that post I said to mark the **gstreamer0.10-ffmpeg** and **gstreamer0.10-plugins-ugly**; for MP3 playback using Rhythmbox, you'll only need the gstreamer0.10-plugins-ugly package, so you only need to mark that one for installation and then follow the rest of the instructions.

As a side note, as others have said, the ideal way to do this is to somehow get an internet connection for this Ubuntu machine. However, if you **absolutely can't** get an internet connection on your Ubuntu system, and you **only** want to enable MP3 playback for Rhythmbox, then you only need the gstreamer0.10-plugins-ugly package. That way you minimize the number of dependencies and therefore the number of packages you must download by hand, so to speak.

Hope this helps.

---

