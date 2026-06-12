---
title: "Cannot burn .aiff files to CD"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-09-12
Sorry to post another thread. I have posted a thread about this already but I thought the title may have been inappropriate. My trouble is actually that none of my burning programs are accepting .aiff files (nor are any of my media players). Below is a summary which may be more useful to understand, but here is the original thread:

[http://www.ubuntuforums.org/showthread.php?t=255359](http://www.ubuntuforums.org/showthread.php?t=255359)

Summary:

I have these players:

MPlayer
Kaffeine
Rythmbox
Banshee
Gxine

and these burners:

Gnomebaker
Serpentine
K3b


When I try to burn .aiff files or listen to them, I get messages like this:
Gnomebaker says "The plugin to handle a file of type audio/x-aiff is not installed."

Serpentine says "The following file was not added:" [the file I was trying's name] "If you're having problems opening certain files make sure you have the GStreamer plugins needed to decode them."

I have not had problems with WAV or mp3.

I have these things installed:

gstreamer0.8-audiofile (0.8.12-1ubuntu2)
gstreamer0.8-misc (0.8.12-1ubuntu2)
gstreamer0.8-swfdec (0.8.12-1ubuntu2)
gstreamer0.8-vorbis (0.8.12-1ubuntu2)
libgstreamer-gconf0.8-0 (0.8.12-1ubuntu2)
libgstreamer-plugins0.8-0 (0.8.12-1ubuntu2)

More gstreamer things which synaptics tells me it upgraded:
gstreamer0.10-alsa (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
gstreamer0.10-gnomevfs (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
gstreamer0.10-plugins-base (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
gstreamer0.10-plugins-base-apps (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
gstreamer0.10-x (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5

and quite a few other gtreamer things but I can't cut and paste their names (eg gstreamer0.10-plugins-bad) from synaptics so won't write them here. If you need their names to understand my problem though I can do it.

I don't know what I am doing not right. I am new to it all. Did I put the "plugins" in the wrong place or something? (I got them with synaptics).

Thanks!
Justin

---

### Post by woodlandjustin on 2006-09-12
Bumping this as I edited above post to contain extensive information.
Justin

---

### Post by jamesstansell on 2006-09-12
Hi Justin,

I don't have any experience with .aiff files, but here are some links that I found by searching for aiff ubuntu.

[http://packages.ubuntulinux.org/dapper/libs/gstreamer0.8-audiofile](http://packages.ubuntulinux.org/dapper/libs/gstreamer0.8-audiofile) (you said you have this already; I'm not sure which application uses it.  Do you know how to check reverse dependencies?)

[http://www.ubuntuforums.org/archive/index.php/t-152255.html](http://www.ubuntuforums.org/archive/index.php/t-152255.html) (talks about the audacity program.  I've used it to convert some file to playable formats.  If you can use it for that then perhaps it can be at least a fallback option for you.)

The gstreamer plugins page [http://gstreamer.freedesktop.org/documentation/plugins.html](http://gstreamer.freedesktop.org/documentation/plugins.html) doesn't list AIFF which surprises me.

OK, I probably shouldn't have but I took the time to lookup the reverse dependencies for gstreamer0.8-audiofile.  (I used the apt-cache command-line tool, but Synaptic can do it too.)  Try seeing if the muine package will play your files.

Regards,

-james.

---

### Post by woodlandjustin on 2006-09-12
> **jamesstansell said:**
> Hi Justin,

I don't have any experience with .aiff files, but here are some links that I found by searching for aiff ubuntu.

[http://www.ubuntuforums.org/archive/index.php/t-152255.html](http://www.ubuntuforums.org/archive/index.php/t-152255.html) (talks about the audacity program.  I've used it to convert some file to playable formats.  If you can use it for that then perhaps it can be at least a fallback option for you.)

Yes that is a possibility, but, with the wonders of modern technology and all, I would rather not have to spend ages and ages loading up about 150 tracks one by one to Audacity and converting them, renaming them, dealing with the Japanese font of their titles etc etc. It is the standard mac non-compressed format as far as I can tell. So it should be possible to do in some normal way.

> 
The gstreamer plugins page [http://gstreamer.freedesktop.org/documentation/plugins.html](http://gstreamer.freedesktop.org/documentation/plugins.html) doesn't list AIFF which surprises me.

But got so so many of those gstreamer things already. Even the one which does describe itself as being for .aiff files!

"gstreamer0.8-audiofile
That is described like this "AudioFile plugin for GStreamer
This GStreamer plugin enables the processing of audio data from formats
supported by libaudiofile including AIFF, AIFF-C, WAVE, NeXT/Sun,
BICS, and raw 

I have no idea what I didn't do right for that not to do it. Isn't it meant to do it? Or am I mistaken? (Seriously I don't know.)

> OK, I probably shouldn't have but I took the time to lookup the reverse dependencies for gstreamer0.8-audiofile.  (I used the apt-cache command-line tool, but Synaptic can do it too.)  Try seeing if the muine package will play your files.


Okay so I just installed muine (yet another media player!!!) But no, that doesn't work either (mp3 fine, .aiff not.) Anyway even if it had, I still need to make audio CDs from these. Have I done the plugins wrong?

Thanks
Justin

---

### Post by 3rdalbum on 2006-09-12
```
sudo apt-get install sox
```

then:

```
sox infile.aif outfile.wav
```

where *infile.aif* is an existing AIFF file, and *outfile.wav* is the WAV file you want to create. Because it's a completely command-line program, you can simply write a shell script or Python script to run sox for every file. (if you specify multiple infiles, it concatenates them, so you have to invoke sox once for each file).

---

### Post by woodlandjustin on 2006-09-12
> **3rdalbum said:**
> ```
sudo apt-get install sox
```

then:

```
sox infile.aif outfile.wav
```

where *infile.aif* is an existing AIFF file, and *outfile.wav* is the WAV file you want to create. Because it's a completely command-line program, you can simply write a shell script or Python script to run sox for every file. (if you specify multiple infiles, it concatenates them, so you have to invoke sox once for each file).

Yes, I have sox (got it a few hours ago!) So far that looks like the only option. That is quite frustrating as it seems to be unable to handle file names in Japanese:

> justin@justin-laptop:~/Desktop$ sox &#39080;&#26519;.aiff sox &#39080;&#26519;.wav
sox: Can't open input file 'sox': No such file or directory

(Don't know on your screen but anyway in my terminal it displays the Japanese characters fine.)
If I rename the same file "muf", then it works fine. However that means I have to re-name, convert then un-re-name between 150 and 200 tracks!!!
If anyone knows how I can just use a burning program to use these .aiff files directly to make an audio CD, I would be very grateful!
Thanks
Justin

---

### Post by Delkster on 2006-09-12
I don't know if such special characters generally work well in shell commands (the terminal shows them ok, though). As for your specific command, however, you should only have one 'sox' per command line, like so:
```
sox &#39080;&#26519;.aiff &#39080;&#26519;.wav
```
What happened in your example was that since you had 'sox' also between the filenames, the tool assumed that both '&#39080;&#26519;.aiff' and 'sox' were names of input files (and that '&#39080;&#26519;.wav' was the output file), so it was trying to find a file named 'sox' for processing, which didn't work.

---

### Post by 3rdalbum on 2006-09-13
If you have problems with filenames in Japanese, or if the paths to the files contain spaces, enclose them with quotes, e.g:

sox "/home/justin/01 Come On And Party.aif" "/home/justin/01 Come On And Party.wav"

---

### Post by woodlandjustin on 2006-09-13
> **Delkster said:**
> I don't know if such special characters generally work well in shell commands (the terminal shows them ok, though). As for your specific command, however, you should only have one 'sox' per command line, like so:
```
sox &#39080;&#26519;.aiff &#39080;&#26519;.wav
```
What happened in your example was that since you had 'sox' also between the filenames, the tool assumed that both '&#39080;&#26519;.aiff' and 'sox' were names of input files (and that '&#39080;&#26519;.wav' was the output file), so it was trying to find a file named 'sox' for processing, which didn't work.

Yeah damn that was a pretty silly mistake! Thanks! Great so now I don't have to rename them totally - but I do have to remove the spaces in the file name, otherwise it really doesn't work! The actual name was "1-1 &#39080;&#26519;", and the space threw it totally, making it look for a file named only "1-1".
Thank you for pointing out my error though - saved me a lot of time!
:)
Justin

---

