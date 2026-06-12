---
title: "[SOLVED] Gutsy total system FREEZE inserting a DVD, and CD Data visible but can't be"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by LeDechaine on 2008-02-18
Well, as you can see, I have a little problem. :)

After the Ubuntu installation, everything worked fine. I've listen to an audio CD, I've listened to a DVD (I think..) and I could see my data on this no-name DVD+RW.

I installed Brasero and decided to format this DVD+RW. The DVD formatted. But after re-inserting the DVD in the drive, I got an "incorrect mount option" error. Since then:
- When I insert an audio CD, I can *see* the **.cda** files, but playing them via VLC or XMMS or Sound Juicer = No sound.
- When I insert this same DVD+RW, it still shows me this "incorrect mount option".
- And the last time i've put a real DVD (bought, video DVD), I got this total system freeze, keyboard useless too I guess, because "ctrl+alt+backspace" was not even working.

Help! :)

---

### Post by LeDechaine on 2008-02-18
Note that i've also received input/output errors in VLC (Messages) while trying to play DVDs before.

---

### Post by agim on 2008-02-18
Sometimes compiz can mess with video playback, depending (I think) on your video card. Try turning it off and see if video works again.
Even if it doesn't work, its something simple to check until somebody more knowledgeable has a better idea.

---

### Post by LeDechaine on 2008-02-18
Err. No. That's not my problem, sorry.
Anyway, compiz is currently disabled.

---

### Post by LeDechaine on 2008-02-22
Ok, looks like the CD playing capabilities have been magically solved for whatever reason...
But the DVDs won't play.

Here's the messages I get from VLC, if anyone can help..
*(Now rebooting in XP to play this DVD.. This is Rammstein - Volkerball by the way ;))*

```
main debug: creating new input thread
main debug: waiting for thread completion
main debug: thread 3002878864 (input) created at priority 0 (input/input.c:265)
main debug: `dvd:///dev/hdc' gives access `dvd' demux `' path `/dev/hdc'
main debug: creating demux: access='dvd' demux='' path='/dev/hdc'
main debug: looking for access_demux module: 2 candidates
dvdnav debug: trying to go to dvd menu
main debug: thread 3013737360 (dvdnav event thread handler) created at priority 0 (dvdnav.c:336)
main debug: using access_demux module "dvdnav"
main debug: meta information:
main debug:   - 'Titre' = 'RAMMSTEIN_DISC1'
main debug: `dvd:///dev/hdc' successfully opened
dvdnav debug: DVDNAV_HOP_CHANNEL
dvdnav debug: DVDNAV_VTS_CHANGE
dvdnav debug:      - vtsN=1
dvdnav debug:      - domain=8
dvdnav debug: DVDNAV_CELL_CHANGE
dvdnav debug:      - cellN=1
dvdnav debug:      - pgN=1
dvdnav debug:      - cell_length=3249000
dvdnav debug:      - pg_length=3249000
dvdnav debug:      - pgc_length=3249000
dvdnav debug:      - cell_start=0
dvdnav debug:      - pg_start=0
dvdnav debug: DVDNAV_SPU_CLUT_CHANGE
dvdnav debug: DVDNAV_SPU_STREAM_CHANGE
dvdnav debug:      - physical_wide=0
dvdnav debug:      - physical_letterbox=1
dvdnav debug:      - physical_pan_scan=0
dvdnav debug: buttonUpdate 1
main debug: selecting program id=0
main debug: looking for decoder module: 25 candidates
main debug: using decoder module "spudec"
main debug: thread 2994486160 (decoder) created at priority 0 (input/decoder.c:159)
dvdnav debug: DVDNAV_AUDIO_STREAM_CHANGE
dvdnav debug:      - physical=0
dvdnav debug: buttonUpdate 1
main debug: looking for decoder module: 25 candidates
main debug: using decoder module "libmpeg2"
main debug: thread 2975329168 (decoder) created at priority 0 (input/decoder.c:159)
dvdnav debug: buttonUpdate 1
libmpeg2 debug: 720x480 (display 720,480), aspect 768000, sar 7680:6480, 29.971 fps
main debug: no usable vout present, spawning one
main debug: crop: 72,164,139,101, palette forced: 1
main debug: window size: 853x480
main debug: looking for video output module: 6 candidates
xvideo debug: adaptor 0, port 73, format 0x32315659 (YV12) planar
main debug: Registering subpicture channel, ID: 2
main debug: Registering subpicture channel, ID: 3
main debug: Registering subpicture channel, ID: 4
main debug: Registering subpicture channel, ID: 5
xvideo debug: Window manager supports NetWM
xvideo debug: Window manager supports _NET_WM_STATE_FULLSCREEN
xvideo debug: Window manager supports _NET_WM_STATE_ABOVE
xvideo debug: Window manager supports _NET_WM_STATE_BELOW
main debug: using video output module "xvideo"
main debug: waiting for thread completion
main debug: got 8 direct buffer(s)
main debug: picture in 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
main debug: picture user 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
main debug: picture out 720x480 (0,0,720x480), chroma I420, ar 16:9, sar 32:27
main debug: direct render, mapping render pictures 0-6 to system pictures 1-7
main debug: thread 2966719376 (video output) created at priority 0 (video_output/video_output.c:421)
main debug: Registering subpicture channel, ID: 6
main debug: idx1=-1(??) idx2=-1(??)
main warning: dts != current_pts (161174)
dvdnav warning: cannot get next block (Error reading from DVD.)
main debug: closing input
main debug: thread 3013737360 joined (dvdnav.c:352)
main debug: removing module "libmpeg2"
main debug: thread 2975329168 joined (input/decoder.c:191)
main debug: killing decoder fourcc `mpgv', 0 PES in FIFO
main debug: removing module "spudec"
main debug: thread 2994486160 joined (input/decoder.c:191)
main debug: killing decoder fourcc `spu ', 0 PES in FIFO
main debug: Program doesn't contain anymore ES
main debug: removing module "dvdnav"
main debug: thread 3002878864 joined (input/input.c:412)
main: nothing to play
main debug: garbage collector destroys 1 vout
main debug: removing module "xvideo"
main debug: thread 2966719376 joined (video_output/video_output.c:461)
```

---

### Post by LeDechaine on 2008-02-22
Nevermind, forgot i've had to install **libdvdcss2**, found it here.
[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)
:)

(Weird crash, but anyway, solved!)
Now for the CD data..

---

### Post by LeDechaine on 2008-02-23
Ok, weird coincidences made me think that the problem was Brasero which had messed up with the CD/DVD drive.

Finally solved:
- The audio problem have been magically solved after a reboot. (?!)
- Saw on an other forum that the "incorrect mount option" was **normal**, because there was *nothing* on the DVD. That was exact. Burned files on the DVD+RW after. :)
- The total system freeze when inserting a DVD is quite interesting, because the problem have been solved by installing **libdvdcss2**. CSS encryption crashing ubuntu? Weird.

Anyway, everything **solved**.

---

