---
title: "Cant copy mp3 songs to mp3 player"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-09-29
I thought this was supposed to be as easy as dragging and dropping but it seems i cant even get that right.
My boy had me downloading mp3 format music for which i have installed all the required codecs and stuff from automatix.

The music all plays fine and when i drag it over from pc to mp3 it all looks fine and even plays if i click from there.......but when he goes to listen on the mp3 player it`s just some file he`s got.:confused: 

What aint i doing right...?
Cheers

---

### Post by Javier_Electrico on 2006-09-29
What player are you using?, and did you try to download the build-essential package?
Also try a $apt-cache search mp3
Hope that would help.

---

### Post by DeadEyes on 2006-09-29
What type of mp3player is it?
Also check the properties of the mp3 files to see if they have their artist/album/title values set.

---

### Post by xpod on 2006-09-29
It seems i got  mp3 related stuff in here.:-k 
It`s only a silly little alba thing but it all works and i can play any of the music from it on the pc quite ok

It`s not something ive ever done before and he uses the windows pc to do it usually...I just aquired all the related stuff i seen in automatix and hoped it would work:mrgreen: 

dad@home1:~$ apt-cache search mp3
avidemux - a small editing software for avi (especially DivX)
gogo - mp3 encoder
gstreamer0.8-lame - LAME encoder plugin for GStreamer
lame - LAME Ain't an MP3 Encoder
lame-extras - LAME Ain't an MP3 Encoder
liblame-dev - LAME Ain't an MP3 Encoder
liblame0 - LAME Ain't an MP3 Encoder
libxine-extracodecs - the xine video/media player library, binary files
libxine1c2 - the xine video/media player library, transitional package
liveice - Live audio streaming application
mencoder - MPlayer's Movie Encoder
mencoder-386 - MPlayer's Movie Encoder (dummy package)
mencoder-586 - MPlayer's Movie Encoder (dummy package)
mencoder-686 - MPlayer's Movie Encoder (dummy package)
mencoder-amd64 - MPlayer's Movie Encoder (dummy package)
mencoder-custom - MPlayer's Movie Encoder (dummy package)
mencoder-g4 - MPlayer's Movie Encoder (dummy package)
mencoder-k6 - MPlayer's Movie Encoder (dummy package)
mencoder-k7 - MPlayer's Movie Encoder (dummy package)
mencoder-powerpc - MPlayer's Movie Encoder (dummy package)
mpg123 - MPEG layer 1/2/3 audio player
mpg123-esd - MPEG layer 1/2/3 audio player with Esound support
mpg123-nas - MPEG layer 1/2/3 audio player with NAS support
mpg123-oss-3dnow - MPEG layer 1/2/3 audio player for 3DNow! machines
mpg123-oss-i486 - MPEG layer 1/2/3 audio player for i486 machines
mythmusic - Music add-on module for MythTV
soundkonverter - KDE frontend to various audio converters
xmms-liveice - XMMS plugin that sends your audio to a shoutcast server
a2mp3 - program to optimize your music for your mp3-player
abcde - A Better CD Encoder
alsaplayer-alsa - PCM player designed for ALSA (ALSA output module)
alsaplayer-common - PCM player designed for ALSA (common files)
alsaplayer-daemon - PCM player designed for ALSA (non-interactive version)
alsaplayer-esd - PCM player designed for ALSA (EsounD output module)
alsaplayer-gtk - PCM player designed for ALSA (GTK version)
alsaplayer-jack - PCM player designed for ALSA (JACK output module)
alsaplayer-nas - PCM player designed for ALSA (NAS output module)
alsaplayer-oss - PCM player designed for ALSA (OSS output module)
alsaplayer-text - PCM player designed for ALSA (text version)
alsaplayer-xosd - PCM player designed for ALSA (osd version)
ample - A simple MP3 server easy to use
arson - KDE frontend for burning CDs
audacity - A fast, cross-platform audio editor
audiolink - makes managing and searching for music easier
avifile-mad-plugin - MAD - MPEG audio plugin for libavifile
beep-media-player - Versatile audio player that supports Winamp skins
bmp-crossfade - Beep-Media-Player Plugin for Crossfading / Continuous Output
burn - Command line Data-CD, Audio-CD, ISO-CD, Copy-CD writing tool
cdcat - media catalog program
cdlabelgen - generates front cards and tray cards for CDs and DVDs
checkmp3 - identify MP3s that do not follow the MP3 format
cplay - A front-end for various audio players
crip - terminal-based ripper/encoder/tagger tool
cue2toc - converts CUE files to cdrdao's TOC format
cwcdr - Chez Wam CD Ripper
cynthiune.app - A free software and romantic music player for GNUstep
darkice - Live audio streamer
digitaldj - An SQL based mp3 player front-end
distmp3 - A Perl client and daemon for distributed audio encoding
dvr - Digital Video Recorder
easytag - viewing, editing and writing ID3 tags
ecawave - graphical audio file editor
eroaster - The ECLiPt CD burning frontend
exfalso - audio tag editor for GTK+
extract - displays meta-data from files of arbitrary type
eyed3 - Display and manipulate id3-tags on the command-line
fapg - Fast Audio Playlist Generator
fatsort - utility for sorting FAT directory structures
gjay - An automatic and learning DJ for xmms
gnomeradio - FM-radio tuner for the GNOME desktop
gnomp3 - An MP3 player for large MP3 collections
gnump3d - A streaming server for MP3 and OGG files
graveman - graphical tool to burn dvd and cd, gtk based
grip - GNOME-based CD-player/ripper/encoder
gstreamer0.10-fluendo-mp3 - Fluendo mp3 decoder GStreamer plugin
gstreamer0.8-mad - MAD MPEG audio decoder plugin for GStreamer
gstreamer0.8-misc - Collection of various GStreamer plugins
gstreamer0.8-musepack - Musepack (MPC) audio decoder plugin for GStreamer
icecast2 - Ogg Vorbis and MP3 streaming media server
id3ed - Another id3 tag editor
id3v2 - A command line id3v2 tag editor
imp3 - Web Based Mail Program
iripdb - Generates the DB files for the iRiver iHP-1xx
irmp3 - A Multimedia Audio Jukebox application
irmp3-ncurses - irmp3 control frontend
jack - Rip and encode CDs with one command
juice - playlist editor / player frontend
kid3 - KDE MP3 ID3 tag editor
knapster2 - A KDE clone of the windows Napster client
kstreamripper - kde frontend for streamripper
kyamo - music organizer for KDE
kzenexplorer - manage tracks and playlists on Creative Labs Nomad Jukeboxes
libagrep-ocaml - Wu-Manber algorithm for string searching with errors
libagrep-ocaml-dev - Wu-Manber algorithm for string searching with errors
libakode2-mpeg - mpeg plugins for akode
libalsaplayer-dev - PCM player designed for ALSA (interface library, development files)
libalsaplayer0 - PCM player designed for ALSA (interface library)
libanydata-perl - simple tied hash interface for files and data structures
libapache-mod-mp3 - turns Apache into a streaming audio server
libapache-mod-musicindex - Browse, stream, download and search through MP3/Ogg files
libapache2-mod-musicindex - Browse, stream, download and search through MP3/Ogg files
libaudiere-1.9.4 - a portable, high-level audio library
libaudiere-1.9.4-dbg - a portable, high-level audio library (debug information)
libaudiere-dev - a portable, high-level audio library (development files)
libaudio-file-perl - Perl audio file abstraction library
libaudio-flac-decoder-perl - Perl module providing an object-oriented FLAC decoder
libextractor1c2a - extracts meta-data from files of arbitrary type (library)
libflac-doc - Free Lossless Audio Codec - library documentation
libmad-ocaml - OCaml bindings for the MAD library
libmad-ocaml-dev - OCaml bindings for the MAD library
libmp3-info-perl - Perl MP3::Info - Manipulate / fetch info from MP3 audio files.
libmp3-tag-perl - Module for reading tags of MP3 audio files
libmp3info-ruby1.8 - a pure ruby library for access to mp3 files
libmp3tag-ruby1.6 - Reading and writing ID3V1.1 tags in MP3 for ruby1.6
libmp3tag-ruby1.8 - Reading and writing ID3V1.1 tags in MP3 for ruby1.8
libmpeg3-1 - MPEG streams decoding library
libnjb-dev - Creative Labs Nomad Jukebox library development files
libnjb-doc - Creative Labs Nomad Jukebox library documentation
libnjb-examples - Creative Labs Nomad Jukebox example binaries
libnjb1 - Creative Labs Nomad Jukebox library
libnjb1-dev - Creative Labs Nomad Jukebox library development files
libnjb1-doc - Creative Labs Nomad Jukebox library documentation
libnjb5 - Creative Labs Nomad Jukebox library
libshout-ocaml - OCaml bindings for the shout library
libshout-ocaml-dev - OCaml bindings for the shout library
libsnack2 - Sound functionality extension to the Tcl/Tk language
libsnack2-dev - Snack development files
libsnack2-doc - Snack documentation
libvlc0-dev - development files for VLC
lltag - Automatic command-line mp3/ogg/flac file tagger
lopster - A Napster client using the GTK UI
madplay - MPEG audio player in fixed point
mc-foo - an advanced, learning, Ogg/MP3 jukebox
mixxx - Digital Disc Jockey Interface
mixxx-data - Digital Disc Jockey Interface -- data files
moc - ncurses based console audio player
mod-musicindex-common - Common files for mod-musicindex
modemp3d - AO-40 (Phase3D) Soundcard Telemetry Decoder
moosic - Daemon/client combo to easily queue music files for playing
mozilla-plugin-vlc - multimedia plugin for Mozilla based on VLC
mp32ogg - Converts MP3 file to Ogg Vorbis
mp3blaster - Full-screen console mp3 and ogg vorbis player
mp3burn - burn audio CDs directly from MP3, Ogg Vorbis, or FLAC files
mp3c - MP3Creator - Creator for MP3/OGG-files
mp3check - Check mp3 files for consistency
mp3gain - Lossless mp3 normalizer with statistical analysis
mp3info - An MP3 technical info viewer and ID3 1.x tag editor
mp3info-gtk - MP3 info viewer and ID3 1.x tag editor -- GTK version
mp3rename - Rename mp3 files based on id3tags
mp3report - Perl script to create an HTML report of MP3 files in a directory.
mp3roaster - A Perl hack for burning audio CDs out of MP3/OGG/FLAC files
mp3splt - Splits MP3 and Ogg Vorbis files without reencoding
mp3wrap - Utility for MP3 wrapping (rolling multiple MP3s into one)
mpd - Music Player Daemon, the name says it all
mpg123-el - a front-end program to mpg123 audio player on Emacsen
mpg321 - A Free command-line mp3 player, compatible with mpg123
mpgtx - toolbox to manipulate MPEG files (video, system, and audio)
mplinuxman - an mp3 player manager for mpman F50/F60
mserv - local centralised multiuser music server
mserv-cgi - CGI scripts for local centralised multiuser music environment
mserv-client - client for centralised multiuser music environment
mserv-dev - local centralised multiuser music environment
music123 - A command-line shell for sound-file players
musiclibrarian - A simple GUI tool to organize collections of music
nautilus-script-audio-convert - A nautilus audio converter script
ncdt - Display directory tree
ncmpc - text based audio player
normalize-audio - adjust the volume of WAV files to a standard volume level
opencubicplayer - UNIX port of Open Cubic Player
opencubicplayer-doc - Documentation for UNIX port of Open Cubic Player
orpheus - Light-weight text mode menu- and window-driven audio player
phpgroupware-dj - phpGroupWare mp3 database interface module
playmp3list - Another front-end to mpg123 with theme support
poc-streamer - An MP3/Ogg multicast/HTTP streamer and MP3 cutting tool
prokyon3 - A mp3 and ogg/vorbis manager and tag editor
python-eyed3 - Python module for id3-tags manipulation
python-id3 - Python module for id3-tags manipulation
python-osd - Python bindings for X On-Screen Display library
python-pymad - Python wrapper to the MPEG Audio Decoder library
python2.3-eyed3 - Python module for id3-tags manipulation
python2.4-eyed3 - Python module for id3-tags manipulation
python2.4-osd - Python bindings for X On-Screen Display library
python2.4-pymad - Python wrapper to the MPEG Audio Decoder library
quelcom - Command line editing tools for MP3 and WAV files
quodlibet - audio library manager and player for GTK+
rezound - Audio file editor
rio - A command line Diamond Rio MP3 player controller
rioutil - Talk to USB based Diamond MM products
ripperx - a GTK-based audio CD ripper/encoder
slimp3 - MPEG Layer III Streaming Server
smpeg-gtv - SMPEG GTK+ MPEG audio/video player
smpeg-plaympeg - SMPEG command line MPEG audio/video player
somaplayer - player audio for the soma suite
sorune - tool to manage the database on the Neuros Audio player
soundconvert - convert compressed sound formats
soundconverter - simple sound converter application for GNOME
sox - A universal sound sample translator
speex - The Speex Speech Codec
streamripper - download online streams into mp3 files
sulu - File Mananger for Samsung Uproar and YEPP
superkaramba - a program based on karamba improving the eyecandy of KDE
sweep - An editor for sound samples
swish-e - Simple Web Indexing System for Humans - Enhanced
tagtool - tool to tag and rename MP3 and Ogg Vorbis files
terminatorx - A realtime audio synthesizer
testdisk - Partition scanner and disk recovery tool
v2strip - Removes ID3v2 tags from MP3 files
vdr-plugin-mp3 - Plugin to vdr for playing mp3's
vlc - multimedia player for all audio and video formats
vlc-plugin-alsa - ALSA audio output plugin for VLC
vlc-plugin-arts - aRts audio output plugin for VLC
vlc-plugin-esd - Esound audio output plugin for VLC
vlc-plugin-ggi - GGI video output plugin for VLC
vlc-plugin-glide - Glide video output plugin for VLC
vlc-plugin-sdl - SDL video and audio output plugin for VLC
vlc-plugin-svgalib - SVGAlib video output plugin for VLC
vux - A rating-based, random ogg and mp3 player
wxvlc - wxWidgets frontend for VLC
xmms-crossfade - XMMS Plugin for Crossfading / Continuous Output
xmms-flac - Free Lossless Audio Codec - XMMS input plugin
xmms-kde - MP3 player integrated into the KDE panel
xmms-kjofol - XMMS remote that uses K-Jofol's skins
xmms-ladspa - power XMMS with the Linux Audio Developer's Simple Plugin API
xmms-mad - mp3 input plugin for xmms based on libmad
yepp - Samsung YEPP MP3 loader
flac - Free Lossless Audio Codec - command line tools
juk - music organizer and player for KDE
kaudiocreator - CD ripper and audio encoder frontend for KDE
kdemultimedia-kfile-plugins - au/avi/m3u/mp3/ogg/wav plugins for kfile
libarts1-mpeglib - mpeglib plugin for aRts, supporting mp3 and mpeg audio/video
libflac++-dev - Free Lossless Audio Codec - C++ development library
libflac++5c2 - Free Lossless Audio Codec - C++ runtime library
libflac-dev - Free Lossless Audio Codec - C development library
libflac7 - Free Lossless Audio Codec - runtime C library
libgmp3-dev - Multiprecision arithmetic library developers tools
libgmp3-doc - Multiprecision arithmetic library documentation and examples
libgmp3c2 - Multiprecision arithmetic library
libmad0 - MPEG audio decoder library
libmad0-dev - MPEG audio decoder development library
libmpcdec-dev - Musepack (MPC) format library [development files]
libmpcdec3 - Musepack (MPC) format library
libmusicbrainz4-dev - Second generation incarnation of the CD Index - development
libmusicbrainz4c2a - Second generation incarnation of the CD Index - library
liboggflac++-dev - Free Lossless Audio Codec - C++ development library (ogg)
liboggflac++2c2 - Free Lossless Audio Codec - C++ runtime library (ogg)
liboggflac-dev - Free Lossless Audio Codec - C development library (ogg)
liboggflac3 - Free Lossless Audio Codec - runtime C library (ogg)
libsdl-mixer1.2 - mixer library for Simple DirectMedia Layer 1.2
libsdl-mixer1.2-dev - development files for SDL1.2 mixer library
libshout3 - MP3/Ogg Vorbis broadcast streaming library
libshout3-dev - MP3/Ogg Vorbis broadcast streaming library (development)
libsmpeg-dev - SDL MPEG Player Library - development files
libsmpeg0 - SDL MPEG Player Library - shared libraries
libspeex-dev - The Speex Speech Codec
libspeex1 - The Speex Speech Codec
mpeglib - mp3 and mpeg I audio and video library
python-id3lib - id3lib wrapper for Python - dummy package
python2.4-id3lib - id3lib wrapper for Python - library
rhythmbox - music player and organizer for GNOME
rhythmbox-dbg - music player and organizer for GNOME
serpentine - an application for mastering audio CD
speex-doc - Documentation for speex
xmms - Versatile X audio player
libtunepimp2-dev - MusicBrainz tagging library -- development files
libtunepimp2c2a - MusicBrainz tagging library and simple tagger application
libxine-dev - the xine video player library, development packages
libxine-main1 - the xine video/media player library, binary files
k3b - A sophisticated KDE CD burning application
libtag1-dev - TagLib Audio Meta-Data Library [development]
libtag1c2a - TagLib Audio Meta-Data Library
libtagc0 - TagLib Audio Meta-Data Library (C bindings)
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]
libtunepimp-bin - libtunepimp simple tagging applications
libtunepimp3 - MusicBrainz tagging library and simple tagger application
libtunepimp3-dev - MusicBrainz tagging library -- development files
libk3b2-mp3 - The KDE cd burning application library - MP3 decoder
libtag1-doc - TagLib Audio Meta-Data Library [documentation]
libtunepimp-perl - libtunepimp perl bindings
libtunepimp3-mp3 - MP3 Plugin for MusicBrainz tagging library
python-tunepimp - libtunepimp python bindings (default package)
python2.4-tunepimp - libtunepimp Python 2.4 bindings
realplay - RealPlayer 10 for Linux is based on the open source Helix player.
dad@home1:~$

EDIT:Sorry about that...

---

### Post by DeadEyes on 2006-09-29
I take it alba is a usb/pen drive type player?
Make sure your umounting properly, as I understand it files only actually get written to usb type drive when the unmount command is issued.

---

### Post by Javier_Electrico on 2006-09-29
Ok, got it, long list...
MPEG company does not provide an open source codec, that's why GNU/Linux doesn't includes any codec by default.  If you read that HUGE list, you'll find something like mp123 codec (or something like that).
Try to download and see what happen.  If you undestand spanish, try to search [here]("http://www.guia-ubuntu.org/dapper/index.php/Portada")

---

### Post by PatrickMay16 on 2006-09-29
Hmm... I have an alba mp3 player too, and it works fine. 
Perhaps you've been copying the files over, but haven't been unmounting it so it writes the data onto it properly? Just a guess.

I suggest you copy the files again, then go to Places > Computer, and right click the icon which represents the mp3 player, and select "Unmount Volume". After it's finished unmounting, disconnect it from the computer and try playing again.

Let me know if this helps.

---

### Post by xpod on 2006-09-29
HAHA.......Seems it is copying over ok now..sods law.:rolleyes: 
I obviously know a little about the mp3 thing as i`d read plenty about it and knew i needed certain bits before i could download mp3 etc.Hence the reason i had installed the automatix stuff 

Seems i had the right bits after all as its "sound as a pound" now;) ;) 
Cheers

---

