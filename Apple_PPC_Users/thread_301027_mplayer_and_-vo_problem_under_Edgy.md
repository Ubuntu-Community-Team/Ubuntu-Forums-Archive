---
title: "mplayer and -vo problem under Edgy"
date: 2006-11-16
forum: Apple PPC Users
---

### Post by Biber on 2006-11-16
Hi,

Under my clean install of Edgy mplayer stopped working. Under pain I added all the codecs necessary for watching movies my only problem is to get mplayer to work since it is the only player that has acceptable playback quality on my iBook 500. It worked under Dapper but since Edgy I can't select any video output. I get either segfaults or trouble with some prevo or whatever the name file when I start playing a movie. If needed I can check this and post an exact error message (do I have to use some kind of debug option for that?) I think -vo xv is supposed to work but it doesn't neither do any other -vo options. How do I install the proper video drivers or do I have to compile mplayer myself? totem and xine are working just fine.

Thanks for any help,
biber


PS: I checked the output again, this is what I get:

~$ gmplayer
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
AltiVec not found
CPU: PowerPC



Opening joystick device /dev/input/js0

Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing /home/.....avi.
AVI file format detected.
VIDEO:  [DX50]  704x384  24bpp  25,000 fps  1002,2 kbps (122,3 kbyte/s)
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16be, 128,0 kbit/8,33% (ratio: 16000->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================


MPlayer interrupted by signal 4 in module: preinit_libvo
- MPlayer crashed by an 'Illegal Instruction'.

---

### Post by turnovg on 2006-12-05
Same here. It is a Mac3 laptop. Ubuntu 6.10 works just fine. But the movies. They used to work with the previous version of Ubuntu. Now they do not run, giving the error above. Neither do xine or vlc work :|

   If anyone could suggest an answer... My only option left is compiling from source :|


P.S.
Is it possible the mplayer package included in the Ubuntu repositories for Mac not to have been compiled for Mac?

---

### Post by turnovg on 2006-12-08
I've read around the net and I understand the problem now - there is NO mplayer compiled for ppc in Ubuntu Edgy Eft (6.10). The package we need is called mplayer-powerpc. (Mac g3 laptop.)
   If tried to install it on Ubuntu 6.10 from a Debian unstable repository (the one with "konstanz" in the name) but there were unmet dependencies.
   I remember I've tried to install mplayer-powerpc with the Ubuntu 6.06 too. And it was crashing with the error we describe above. BUT! As I could see, Ubuntu makes a default installation with a wrong kernel - an smp one, which is for dual core machines :) And mine (our) is (are) not :) I haven't tested it with installing the correct kernel, but I'll definitely try it soon.
   What I've done was installing Debian Testing. (But TESTING, not stable, because the mplayer-powerppc package is not there either.)
   Now mplayer works just PERFECT! (At least for .avi movies. Haven't tried it yet for other type of movies or DVDs.)
   The only problem (not really a problem though ;) I can see is, when I try to put subtitles on the black band under the movie. It works, but sluggish on some frames. I've tried many options to correct the problem, but the only usefull one was "framedropping", which in fact changes one problem with another :)
   The other problems I've fixed were video and audio settings - video with "xv" and audio with "alsa" only working and "Software Mixer" enabled.
   Hope this helps.

---

