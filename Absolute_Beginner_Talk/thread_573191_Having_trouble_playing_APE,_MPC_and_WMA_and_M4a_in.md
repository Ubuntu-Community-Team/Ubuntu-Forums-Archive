---
title: "Having trouble playing APE, MPC and WMA and M4a in Rythmbox"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by graben3 on 2007-10-11
OK, first of all, I searched and tried many music players for linux....

So far XMMS : bad, no library,
Amarok : slow with large music collections
Songbird : would not play my music, just silence !.... didn't struggle enough to make it work thought.
Rythmbox : simple, but have a playlist, a media library and a search functionnality. This is all I need from a music player.

However, my problem is now playing "special" music format files like MPC, APE and M4A and even WMA

On musepack they offer plugins for XMMS and Beep media player....but not for rythmbox :(
[http://www.musepack.net/index.php?pg=lin](http://www.musepack.net/index.php?pg=lin)


What can I do to play these files in Rythmbox 
OR 
What player have a media library, a search functionnality in library and a playlist and can read M4A, mpc, ape and wma files ?

---

### Post by julian67 on 2007-10-11
make sure that in Synaptic you have the multiverse repo enabled. If not then enable it and reload. Install the gstreamer 10 bad, bad-multiverse, ugly and ugly-multiverse plugins. Your gstreamer based apps should now play all formats.

---

### Post by graben3 on 2007-10-11
I did as you told me...

Now MPC files workslike a charm in Rythmbox !

However, no luck so far with .APE files

I also have some errors with MP3 files in Rythmbox :
Many MP3 files generate an import error : 
"The MIME type of the file could not be identified ?"

What causes this error.... in winamp (on XP) those files can play...

---

### Post by julian67 on 2007-10-11
> **graben3 said:**
> I did as you told me...

Now MPC files workslike a charm in Rythmbox !

However, no luck so far with .APE files

I also have some errors with MP3 files in Rythmbox :
Many MP3 files generate an import error : 
"The MIME type of the file could not be identified ?"

What causes this error.... in winamp (on XP) those files can play...

Install gstreamer0.10-ffmep and it should all work normally. Sorry, should have included that in the previous list. 

And a suggestion for later when you're comfortable using Ubuntu. I'd convert those ape files to flac and you'll find they are easily usable in pretty much every open source multimedia app you'll ever come across, whereas ape has very limited support in Linux.

---

### Post by graben3 on 2007-10-12
It is already installed (gstreamer0.10-ffmpeg) ... It doesn't work...

I found this plugin :
[http://gstreamer.freedesktop.org/src/gst-monkeysaudio/](http://gstreamer.freedesktop.org/src/gst-monkeysaudio/)

on this thread : 
[http://forum.ubuntu-fr.org/viewtopic.php?pid=596847](http://forum.ubuntu-fr.org/viewtopic.php?pid=596847)

Downloaded sources and runned
./configure

All goes well until it complains about a missing package :

checking for CreateIAPEDecompressEx in -lmac... no
configure: error: you need mac-port packages installed !

I tried to find those packages... there is none in synaptic. 
Found a link to the package in the source of configure script : 404 error

There is a package named libmac-ipod-gnupod-perl or something like this
Do you know if I should install this (i don't have any ipod and do not plan to get one :) )?

So I'm still stuck...

You are right... i'll convert those songs to flac or any lossless codec as good as or best than ape. May be i should convert them under XP... would be easier for now.... until I find why I can't play APE files.

---

### Post by julian67 on 2007-10-12
That package is for the old gstreamer 8, whereas you are using 10. 

Let's see exactly what gstreamer packages are installed:

```
dpkg -l | grep gstreamer
```

---

### Post by graben3 on 2007-10-12
ii  gstreamer0.10-alsa                         0.10.12-0ubuntu1                       GStreamer plugin for ALSA
ii  gstreamer0.10-esd                          0.10.5-1ubuntu2                        GStreamer plugin for ESD
ii  gstreamer0.10-ffmpeg                       0.10.2-0ubuntu4                        FFmpeg plugin for GStreamer
ii  gstreamer0.10-gnomevfs                     0.10.12-0ubuntu1                       GStreamer plugin for GnomeVFS
ii  gstreamer0.10-plugins-bad                  0.10.4-1ubuntu1                        GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse       0.10.4-3                               GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-base                 0.10.12-0ubuntu1                       GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps            0.10.12-0ubuntu1                       GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good                 0.10.5-1ubuntu2                        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                 0.10.5-0ubuntu2                        GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse      0.10.5-2                               GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-tools                        0.10.12-0ubuntu2                       Tools for use with GStreamer
ii  gstreamer0.10-x                            0.10.12-0ubuntu1                       GStreamer plugins for X11 and Pango
ii  gstreamer0.8-misc                          0.8.12-6ubuntu3                        Collection of various GStreamer plugins
ii  libgstreamer-gconf0.8-0                    0.8.12-6ubuntu3                        GConf support for GStreamer
ii  libgstreamer-plugins-base0.10-0            0.10.12-0ubuntu1                       GStreamer libraries from the "base" set
ii  libgstreamer-plugins0.8-0                  0.8.12-6ubuntu3                        Various GStreamer libraries and library plug
ii  libgstreamer-plugins0.8-dev                0.8.12-6ubuntu3                        Development files for various GStreamer libr
ii  libgstreamer0.10-0                         0.10.12-0ubuntu2                       Core GStreamer libraries and elements
ii  libgstreamer0.8-0                          0.8.12-2                               Core GStreamer libraries, plugins, and utili
ii  libgstreamer0.8-dev                        0.8.12-2                               GStreamer development libraries and headers
ii  totem-gstreamer                            2.18.1-0ubuntu3                        A simple media player for the Gnome desktop


The 0.8 gstreamer plugins were installed when I tried to install the plugin I mentionned before...
It wasn<t working without them and it is not working with them too.
I think It would be better to remove them

By the way....
grep command is a command to filter output based on a criteria and could be used on any other shell command? Am i wrong ? Trying to understand unix shell command syntax... not as simple (and useless) as dos/xp shell commands i was used to... Do you know a good place for xp users to learn the shell commands syntax / basics ? Seems the best way to learn using linux is learning shell comands.

---

### Post by julian67 on 2007-10-12
Yes I'd remove the gstreamer 8 packages.

Sometimes it's a lot easier to use commands. In this case the alternative would be for you to start synaptic and search for gstreamer and then note down or copy/paste the name of each package.... a big yawn. 

from man grep:

>  grep  searches the named input FILEs (or standard input if no files are
       named, or the file name - is given) for lines containing a match to the
       given PATTERN.  By default, grep prints the matching lines.


Meanwhile I'm unsure as to why Rhythmbox is having trouble, you seem to have everything needed. Perhaps the ape plug in merely links to libraries already installed, though I doubt it. You could try adding the morgoth backports and the medibuntu repos and installing libmac2, and also checking if there are updates for your multimedia packages. Sometimes the 3rd party multimedia stuff will work better than the official packages which may be restricted by legal distribution issues.

---

### Post by bluetooth on 2007-11-13
** graben3**, did you get an error saying "configure: error: you need gstreamer development packages installed !" while configuring gst-monkeysaudio. I can't find those dev packages of gstreamer in any of available repositories :(

---

### Post by funkjunkie on 2007-11-16
i am not having luck playing mp3 off my ipood with rythmbox since i upgraded my laptop to gutsy.   must be missing something else?

I am assuming you meant gstreamer0.10-ffmpeg?

apt-get install gstreamer0.10-ffmpeg says i already have latest version. 
dpkg -l | grep gstreamer
ii  gstreamer0.10-alsa                         0.10.14-1ubuntu3                     GStreamer plugin for ALSA
ii  gstreamer0.10-esd                          0.10.6-0ubuntu4                      GStreamer plugin for ESD
ii  gstreamer0.10-ffmpeg                       0.10.2-2ubuntu1                      FFmpeg plugin for GStreamer
ii  gstreamer0.10-gnomevfs                     0.10.14-1ubuntu3                     GStreamer plugin for GnomeVFS
ii  gstreamer0.10-plugins-bad                  0.10.5-4ubuntu1                      GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse       0.10.5-1                             GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-base                 0.10.14-1ubuntu3                     GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps            0.10.14-1ubuntu3                     GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good                 0.10.6-0ubuntu4                      GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                 0.10.6-0ubuntu2                      GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse      0.10.6-0ubuntu1                      GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-tools                        0.10.14-1ubuntu3                     Tools for use with GStreamer
ii  gstreamer0.10-x                            0.10.14-1ubuntu3                     GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0            0.10.14-1ubuntu3                     GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                         0.10.14-1ubuntu3                     Core GStreamer libraries and elements
ii  totem-gstreamer                            2.20.0-0ubuntu3                      A simple media player for the Gnome desktop 


i found a slew of other gstreamer plugins and packages in synaptic, but im not sure which i maight be missing.
any other thoughts?

---

### Post by SunnyRabbiera on 2007-11-16
gstreamer can be a pain, you might want to download automatix and download the win32 codecs pack

---

### Post by funkjunkie on 2007-11-16
after searching synaptic for 'gstreamer mp3' i found a package called:
ubuntu-restricted-extras
installed 22 packages.. and now it works.

---

### Post by mommalomas on 2008-02-15
Is there still no possibility to play APE's in Rhythmbox?
The only way is to converting into FLAC?

---

### Post by ayu on 2008-03-17
> **mommalomas said:**
> Is there still no possibility to play APE's in Rhythmbox?
The only way is to converting into FLAC?

Are there any utilities in the repos to convert ape to flac? Thanks!

---

### Post by Bubba64 on 2008-03-18
Besides all of the mentioned plugins you can install these add ons from Mozilla some of which probably contain the mentioned plugins. With all of these installed and the gstreamer plugins from synaptic and add remove and vlc installed I can can play anything I come across on Totem or mplayer or smplayer. Also sound converter is a good way of converting a file. I also use rhythm player as well.
[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

---

