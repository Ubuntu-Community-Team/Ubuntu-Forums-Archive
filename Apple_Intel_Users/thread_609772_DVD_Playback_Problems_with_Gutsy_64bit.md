---
title: "DVD Playback Problems with Gutsy 64bit"
date: 2007-11-11
forum: Apple Intel Users
---

### Post by Rog-Mahal on 2007-11-11
I think I have all the correct libraries and programs installed. I have libdvdcss2, libdvdnav4, libdvdread3, libxine1-ffmpeg, vlc, mplayer, ogle, gxine, totem-xine, the whole works! But it appears that the only problem is with libdvdcss. It doesn't seem to initialize. When I run vlc through terminal, I get the following errors:

```
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: HOUSE
libdvdnav: DVD Serial Number: 32d503cd
libdvdnav: DVD Title (Alternative): S1_D1SA_R0
libdvdnav: Unable to find map file '/home/roger/.dvdnav/HOUSE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000134
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000a32d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0000a32d)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000a6e2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000a6e2)!!
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00371e7b
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x00371e7b)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00371e7f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x00371e7f)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0037c37d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0037c381
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x0037c381)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0037e580
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x0037e580)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0037e584
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x0037e584)!!
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 5
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
```
Any thoughts? Was this a result of my rather uninformed decision to use a 64bit system?](*,)

---

### Post by david_edmundson on 2007-11-11
Run this command
/usr/share/doc/libdvdread3/install-css.sh

---

### Post by Rog-Mahal on 2007-11-11
I already have, it downgrades my libdvdcss2 to an earlier version. Right now I have 1.2.9 installed, should I still run it?

---

### Post by maino82 on 2007-11-11
I have the same problem under 64bit gutsy. I can't get any media player to work properly or recognize that I have libdvdcss2 installed (I have tried both the .sh install method and the medibuntu repos, but neither have worked). 32bit gutsy worked fine for me, but after deciding to upgrade to 64 bit suddenly there's a problem.

---

### Post by Rog-Mahal on 2007-11-11
Good to know I'm not alone in this. So far this is the only thing to make me regret the upgrade, everything else works wonderfully.

---

### Post by AndyMcT on 2007-11-13
Same here too, it's a shame as everything else has been perfect since I upgraded.

---

### Post by cyberdork33 on 2007-11-13
> **maino82 said:**
> I have the same problem under 64bit gutsy. I can't get any media player to work properly or recognize that I have libdvdcss2 installed (I have tried both the .sh install method and the medibuntu repos, but neither have worked). 32bit gutsy worked fine for me, but after deciding to upgrade to 64 bit suddenly there's a problem.

I just did this yesterday using the medibuntu repos and it works without a hitch on 64bit gutsy, so I don't think that has anything to do with it.

---

### Post by Rog-Mahal on 2007-11-13
hell, now the problem seems to have changed slightly, I uninstalled everything having to do with dvds and media players, and the 32 bit compatability libraries and reinstalled them, now I get a different error:
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
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x003546d4)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[00000287] main playlist: nothing to play

```
Could the problem lie in the fact that libdvdnav can't find the .map file?

---

### Post by Rog-Mahal on 2007-11-13
Is there any way for me to check if I have "raw access" to my superdrive? I think that may be the problem. If so, is there any way for me to flash the firmware for it from linux/ is there an alternate firmware?

---

### Post by Rog-Mahal on 2007-11-14
so through various wranglings, i think that I have gotten vlc to play dvds. I ended up installing the regionset utility (available in universe for anyone wanting to try it out) and set my dvd drive to region one. Now it appears that the dvd plays, as per the output from running vlc in terminal:

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
[00000287] main playlist: stopping playback
```

But all I get is choppy audio and no video. I have done some further investigation and found that I need to enable DMA access for my superdrive. But, there is a problem:

```
roger@hephaestos:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```
So as a result, here are the buffered time reads that I'm getting:

```
roger@hephaestos:~$ sudo hdparm -t /dev/scd0

/dev/scd0:
 Timing buffered disk reads:    2 MB in  4.44 seconds = 461.11 kB/sec

```

Any thoughts? Where do I go from here? This seems to be a pretty widespread problem, but why don't other people have this problem?

---

### Post by maino82 on 2007-11-14
> **Rog-Mahal said:**
> so through various wranglings, i think that I have gotten vlc to play dvds. I ended up installing the regionset utility (available in universe for anyone wanting to try it out) and set my dvd drive to region one. Now it appears that the dvd plays, as per the output from running vlc in terminal:

Regionset worked for me. It already said it was set at region 1, but I told it to reset it to region 1 anyway and after doing that it worked just fine for me. Maybe the mask that I previously had was incorrect, I'm not sure. The mask I ended up using was 0xFFFFFFFE.

Hope that helps someone.

---

### Post by Rog-Mahal on 2007-11-14
How is your playback quality? Mine is so jerky and slow it's unwatchable, so now I have a new problem to solve.

---

