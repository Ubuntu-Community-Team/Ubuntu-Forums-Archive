---
title: "Linux DVR on Ubuntu - how to start?"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by darf681 on 2006-02-09
Running ubuntu BB and used synaptic to install DVR onto my machine.

it downloaded and installed both it and its dependencies.

only thing is...

how do I start the program now?
(i can't find an executable at all)

---

### Post by blair on 2006-02-09
what is the name of the package you downloaded? There is a good chance that the executable name is the same as the name of the package. Open a terminal and use the whereis <executable> command to find the directory in which that file is located, e.g.

blair@kitchen:~$ whereis ping
ping: /bin/ping /usr/share/man/man8/ping.8.gz

There is obviously a ping command in the /bin directory and in the /usr/share/man directory. The former is the executable, the latter the man page for that command.

---

### Post by darf681 on 2006-02-09
the name of the package was "DVR"

tried to use the file search for DVR, but came up empty

---

### Post by Michael Matthews on 2006-03-24
dvr-console config-file

edit /usr/share/doc/dvr/sample_configuration to create your own config file.

Doesn't work any way :( 

> dvr-console dvr.conf
added parameter <max_recording_time> with value '10'
added parameter <video_width> with value '720'
added parameter <video_height> with value '480'
added parameter <video_top_margin> with value '0'
added parameter <video_bottom_margin> with value '0'
added parameter <video_codec_name> with value 'FFMPEG DivX5'
added parameter <video_frame_rate> with value '24'
added parameter <capture_frame_rate> with value '0'
added parameter <video_channel> with value '1'
added parameter <video_norm> with value '1'
added parameter <video_device> with value '/dev/video0'
added parameter <sound_recording_enabled> with value '1'
added parameter <sound_sample_size> with value '16'
added parameter <sound_frequency> with value '44100'
added parameter <sound_channels> with value '1'
added parameter <sound_format> with value '85'
added parameter <sound_byterate> with value '8000'
added parameter <sound_device> with value '/dev/dsp'
added parameter <file_segment_size> with value '0'
added parameter <file_name> with value 'tv.avi'
terminate called after throwing an instance of 'FatalError'
Aborted

mythtv is very difficult to setup and apparently screws up gnome sound system.

---

### Post by andresh on 2006-06-21
Hahaha, I had the same problem.. (i am new on linux...) and I found the solution:

I entered this page to search package contents...

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=dvr&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=dvr&version=dapper&arch=i386)

and there found the executable name to start dvr...

dvr-qtgui

---

### Post by em3raldxiii on 2006-08-17
Strangely, when I attempt to run dvr-qtgui, I get the dialogue asking for a device, and then it just hands.  In console, I get this error message:
```

*** WARNING *** : the driver doesn't provide a correct size for memory mapping. DVR tries to correct this error, but some strange things may happend, you are warned.
Can't map memory for capture : Invalid argument

```

What is happening?  Any suggestions?

---

