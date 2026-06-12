---
title: "posibly a dumb question about video"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by hotty fuzzed on 2007-06-18
Hey all,
First timer with Linux in general but I'm loving Ubuntu so far!
The one issue I'm having now that I can't seem to find any info on is that when ever I play a video file (I've tried with a DVD and an .avi) vlc or mplayer both open the video for a fraction of a second before stopping play back.
No errors are displayed the players just sit there doing nothing.
I've installed the codec packs (as best i could figure how with the several guides on these forums) but I can't seem to find any info on my problem - no doubt because its more than likely really dumb!
If anyone could shed some light on this it'd be awesome!

---

### Post by rich.bradshaw on 2007-06-18
have you

sudo apt-get install restricted-extras

You will likely need libdvdcss2 from medibuntu as well.

Follow instructions here [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php) , then

sudo apt-get update

sudo apt-get install **libdvdcss2**

---

### Post by hotty fuzzed on 2007-06-18
Yup - I've installed the most up to date libdvdcss2 pack and still the same result when opening a random avi.
(I've also got the most up to date mediabuntu repository installed)

---

### Post by RomeReactor on 2007-06-18
Hi. Do you have Beryl? Maybe it's interfering with the playback; if you do have it and it's running while trying to watch videos, try [this thread]("http://ubuntuforums.org/showthread.php?t=459020").

---

### Post by hotty fuzzed on 2007-06-18
Ok I've removed beryl and still no joy:(
I do have libdvdcss2 & w32codecs installed correctly:

root@brian-laptop:~# sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
libdvdcss2 is already the newest version.
w32codecs is already the newest version.
The following packages were automatically installed and are no longer required:
  libberyldecoration0 libberylsettings0-gconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

anyone one else got any ideas

---

### Post by eluzi on 2007-06-18
Try running the video from the console, any errors will be output to the screen...

# mplayer <video_filename>

---

### Post by Phixion on 2007-06-18
Have you tried playing it in VLC?

sudo apt-get install vlc

It's THE best video player imo :)

---

### Post by hotty fuzzed on 2007-06-18
here's the error i get when playing in konsole:


Playing test.avi.
AVI file format detected.
Detected NON-INTERLEAVED AVI file format.
VIDEO:  [cvid]  640x480  24bpp  29.970 fps  14356.1 kbps (1752.4 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Xv: could not grab port 73
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffcvid] vfm: ffmpeg (Cinepak Video (native codec))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 32000 Hz, 2 ch, s16le, 1024.0 kbit/100.00% (ratio: 128000->128000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


And here's what happens with VLC:

VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  87
  Current serial number in output stream:  88

I'm sooooo lost..

---

### Post by hotty fuzzed on 2007-06-18
bump

---

### Post by mpeg2M on 2007-06-18
Try turning off Desktop effects - solved a bunch of video issues for me...

  Rich

---

### Post by hotty fuzzed on 2007-06-18
you legend! that was it!

---

