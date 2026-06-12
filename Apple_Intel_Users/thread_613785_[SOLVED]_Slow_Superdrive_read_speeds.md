---
title: "[SOLVED] Slow Superdrive read speeds"
date: 2007-11-15
forum: Apple Intel Users
---

### Post by Rog-Mahal on 2007-11-15
So after much searching, I have finally become able to play DVDs on my Macbook, but only in VLC. Anyway, I have a new problem. My Superdrive runs ridiculously slow. 
Example:

```
roger@hephaestos:~$ sudo hdparm -t /dev/scd0
[sudo] password for roger:

/dev/scd0:
 Timing buffered disk reads:    2 MB in  5.51 seconds = 371.61 kB/sec

```

Hdparm returns the following:

```
roger@hephaestos:~$ hdparm /dev/scd0

/dev/scd0:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

Anyone have similar problems? Any ideas where I can get the correct ioctl? I can't turn on DMA because of the ioctl error...I've done a bit of research and I'm not even sure newer drives support DMA anymore. This is the last hurdle to jump before I have a perfectly configured Macbook singlebooting Gutsy 64 bit.

---

### Post by cyberdork33 on 2007-11-15
```
cyberdork33@Grover-Ubuntu:~$ hdparm /dev/scd0

/dev/scd0:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

Same error, no slow read times. I think you have a different problem.

---

### Post by Rog-Mahal on 2007-11-15
Hmm, any ideas about what I should search for?

---

### Post by cyberdork33 on 2007-11-15
> **Rog-Mahal said:**
> Hmm, any ideas about what I should search for?

I can really only speculate because there isn't a lot of information about why you are having problems...

Can you tell us what version / flavor of ubuntu you are using?

---

### Post by volanin on 2007-11-15
Try this:
```
 $ sudo hdparm -E24 /dev/scd0
```

---

### Post by Rog-Mahal on 2007-11-15
I'm running 64 bit Gutsy with uname -a returning:

```
Linux hephaestos 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

```

The hdparm -E24 did not help read speed:

```
roger@hephaestos:~$ sudo hdparm -E24 /dev/scd0

/dev/scd0:
setting cdrom speed to 24
roger@hephaestos:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:    2 MB in  4.46 seconds = 459.10 kB/sec

```

Can anyone tell me what kind of speeds I should be looking for? Just idle curiosity.

---

### Post by cyberdork33 on 2007-11-15
```
cyberdork33@Grover-Ubuntu:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:    4 MB in  4.10 seconds = 999.41 kB/sec
cyberdork33@Grover-Ubuntu:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:    6 MB in  3.77 seconds =   1.59 MB/sec
cyberdork33@Grover-Ubuntu:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:    6 MB in  3.79 seconds =   1.58 MB/sec
```
I did it a few times to get the disk spinning. This is a CD though.


Here is a video DVD:
```
cyberdork33@Grover-Ubuntu:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:    8 MB in  3.79 seconds =   2.11 MB/sec
cyberdork33@Grover-Ubuntu:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:    6 MB in  3.24 seconds =   1.85 MB/sec
cyberdork33@Grover-Ubuntu:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:    6 MB in  3.24 seconds =   1.85 MB/sec
```

---

### Post by cyberdork33 on 2007-11-15
Ok, well that disc I just tested was a burned disc of tv shows from my media pc, and it was playing all choppy like, so maybe it is the media?

---

### Post by Rog-Mahal on 2007-11-15
Hell, maybe it's not my DVD drive, here's some results after the disc spins up:

```
roger@hephaestos:~$ sudo hdparm -t /dev/scd0
[sudo] password for roger:

/dev/scd0:
 Timing buffered disk reads:    2 MB in  5.42 seconds = 378.06 kB/sec
roger@hephaestos:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:   12 MB in  3.57 seconds =   3.36 MB/sec
roger@hephaestos:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:   10 MB in  3.03 seconds =   3.30 MB/sec

```
But video quality is awful. Here's the output while I play a DVD on VLC (the only player that actually starts playing the disc):
```
roger@hephaestos:~$ vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: THE_ROYAL_TENENBAUMS_DISC_1
libdvdnav: DVD Serial Number: 2caa9747
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/roger/.dvdnav/THE_ROYAL_TENENBAUMS_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000133
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00015feb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000170df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0035133b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003546d4
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[00000325] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[00000362] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
[00000372] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
No accelerated IMDCT transform found
[00000370] main decoder error: decoder is leaking pictures, resetting the heap
[00000287] main playlist: stopping playback

```

I stopped the playback, but there does seem to be a problem with the decoder. Any thoughts?

---

### Post by cyberdork33 on 2007-11-15
um do me a favor and make sure you try without running any compositing.

---

### Post by Rog-Mahal on 2007-11-16
Pardon my ignorance, but could you explain how to do that?

---

### Post by cyberdork33 on 2007-11-16
> **Rog-Mahal said:**
> Pardon my ignorance, but could you explain how to do that?
Turn off any desktop effects... compiz-fusion, etc. I don't know if you are even using them, but they create issues like this for several things.

System > Preferences > Appearance

---

### Post by Rog-Mahal on 2007-11-17
I turned off desktop effects and had the same video quality result, but I got different output:

```
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: THE_ROYAL_TENENBAUMS_DISC_1
libdvdnav: DVD Serial Number: 2caa9747
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/roger/.dvdnav/THE_ROYAL_TENENBAUMS_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000133
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00015feb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000170df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0035133b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003546d4
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[00000325] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[00000363] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
[00000375] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
No accelerated IMDCT transform found
[00000371] main decoder error: decoder is leaking pictures, resetting the heap
[00000372] main video output error: picture 0x11b8140 refcount is -1
[00000372] main video output error: picture to date 0x11b8298 has invalid status 6
[00000372] main video output error: picture to display 0x11b8298 has invalid status 6
[00000372] main video output error: picture 0x11b8298 refcount is -1
[00000287] main playlist: stopping playback

```

I stopped playback myself.

---

### Post by cyberdork33 on 2007-11-17
Here is my output for comparison.
```
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: FELLOWSHIP
libdvdnav: DVD Serial Number: 2c9e02d7
libdvdnav: DVD Title (Alternative): FELLOWSHIP
libdvdnav: Unable to find map file '/home/cyberdork33/.dvdnav/FELLOWSHIP.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000017d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001d70
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000284cb
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000352] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
[00000287] main playlist: stopping playback
```

Again, it was choppy when using compiz, but turning it off made eveything look OK. 

Try starting gstreamer-properties and, on the video tab, try the different options under "Plugin" for default output. Also check these without compiz enabled.

---

### Post by Rog-Mahal on 2007-11-18
Ok...I'm really embarrassed. I was using a dvd that was too scratched. VLC works wonderfully and I don't have any problems with other discs. Thanks a lot for your help cyberdork :oops:

---

