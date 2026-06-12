---
title: "[SOLVED] Dvd Playback"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by hoffmannick on 2007-09-08
Hello, 
I installed all the drivers and libraries to enable DVD playback, but I'm getting an issue when I actually try to play the DVD.  Totem, Xine, VLC, etc, they will all open and close immediately right after they are opened.  Or when I try to open a dvd, the player will close shortly thereafter.

Has anyone else had this problem and have any suggested solutions?

Thanks
-Nick

---

### Post by jnorthr on 2007-09-08
similar problem here using vlc. just found this link: [http://ubuntu1501.blogspot.com/2007/06/medibuntu-how-to-install-dvd-codecs.html](http://ubuntu1501.blogspot.com/2007/06/medibuntu-how-to-install-dvd-codecs.html) dunno if it will help you.

---

### Post by Amazona aestiva on 2007-09-08
See the first link in my signature.

---

### Post by hoffmannick on 2007-09-09
I actually went through both tutorials, thank you for suggesting them, but the problem is still there.  I ran vlc from the command line to see if I could grab any output that might be useful, here is what I got.

```

hoffmannick@nickbuntu:~$ VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Open_Water_2
libdvdnav: DVD Serial Number: 358d9f16
libdvdnav: DVD Title (Alternative): Open_Water_2
libdvdnav: Unable to find map file '/home/hoffmannick/.dvdnav/Open_Water_2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000135
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000dc63
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0019fae6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0019fb1f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001c2540
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001c2579
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0020f9fd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0020fa36
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0021015a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00210193
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00211eda
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00211f13
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
[00000335] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86


```

I tried googling there error, but I couldn't come up with much, this is the same error that I get when I run totem, xine, etc.....



Thanks again for helping me with this.
-Nick

---

### Post by n3tfury on 2007-09-09
> **hoffmannick said:**
> Hello, 
I installed all the drivers and libraries to enable DVD playback, but I'm getting an issue when I actually try to play the DVD.  Totem, Xine, VLC, etc, they will all open and close immediately right after they are opened.  Or when I try to open a dvd, the player will close shortly thereafter.

Has anyone else had this problem and have any suggested solutions?

Thanks
-Nick

you say *the* dvd.  is this a retail dvd or a burned one?  does this happen to all of your dvd's?

---

### Post by hoffmannick on 2007-09-09
I've tried with both, retail and burned dvd's.  I understand that some players can fuss about playing burned ones.  The one that I ran the test in the above post was a retail DVD out of the case.  The problem seems to be universal.  The dvd will spin in the drive, and I'll select to play it, from there the player (totem, xine, xmovie, vlc, etc...) will appear and then quickly disappear.

---

### Post by nonewmsgs on 2007-09-09
insufficent resources it says..could this be an out-of-memory error?  it is trying to get memory dynamically (malloc)

---

### Post by Chris S. on 2007-09-09
Are you running Beryl, Compiz-Fusion, or using Desktop Effects?  This can be a problem with a graphics-heavy app using too much video memory, and these three are the most common culprits.

---

### Post by hoffmannick on 2007-09-09
Go figure, that solved it, it was the desktop effects that broke my playback (or just me not having enough memory!)
Thanks Chris, I sould have checked that before!

---

