---
title: "VLC desktop settings"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by arpinology on 2008-04-11
Im having a major issue with video playback on my computer(xubuntu 7.10)

I installed the vlc package last week, and occasionally could get a video to play entirely...or up to the part of a movie, etc.  What would happen half of the time is the file would open in vlc, the vlc window would pop up, the black screen would be there, i could hear the first second of audiom then vlc would close by itself.  

but it would occasionally work.


now it wont work at all.  I only had one brief success where I got one movie file to load and play perfectly but once i closed vlc, then tried to re open it 5 minutes later to play the same video file, it went back to its old tricks.

The single occurence above happened after i uninstalled and reinstalled vlc and installed the libdevcss2 file from the synaptic library.

oh, also, when i installed and tried mplayer, i received the message "gnome_screensaver_control()" which i researched; my researched concluded that unchecking this box relating to the screensaver.  but that didnt work after that.

anybody have any suggestions?  i have a total of 4 video players on my computer and none of them work.  I know that vlc works, because it has, but now it doesnt.

---

### Post by jw5801 on 2008-04-11
Try running it from the commandline in verbose mode using:
```
vlc -vv
```and it should give you some more debugging information when you try to open the video.

---

### Post by arpinology on 2008-04-11
thanks for the quick reply.

here is what i got with the command you suggested.


eric@eric-desktop:~/movies$ vlc -vv
VLC media player 0.8.6c Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/eric/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 216 modules
[00000001] main private debug: opening config file /home/eric/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000281] main playlist debug: waiting for thread completion
[00000281] main playlist debug: thread 3079789456 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000282] main private debug: waiting for thread completion
[00000282] main private debug: thread 3071396752 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000283] main interface debug: looking for interface module: 1 candidate
[00000283] main interface debug: using interface module "hotkeys"
[00000283] main interface debug: thread 3063004048 (interface) created at priority 0 (interface/interface.c:231)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "screensaver"
[00000285] main interface debug: thread 3054611344 (interface) created at priority 0 (interface/interface.c:231)
[00000287] main interface debug: looking for interface module: 5 candidates
[00000287] main interface debug: using interface module "wxwidgets"
[00000287] main interface debug: thread 3028433808 (manager) created at priority 0 (interface/interface.c:216)
[00000287] wxwidgets interface debug: Using last windows config '(-1,0,0,1280,800)(6,0,0,-1,150)'
[00000287] wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)




this is what i received.  bad allocation looks like the problem.  i was researching the "Bad alloc" message and...i've read things suggesting more ram, re-organizing usage of shared memory for the graphics card, adjusting swap storage...im still looking it all up.

---

### Post by deadgobby on 2008-04-11
Please read this link and go from there.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jw5801 on 2008-04-12
> **arpinology said:**
> thanks for the quick reply.

here is what i got with the command you suggested.


eric@eric-desktop:~/movies$ vlc -vv
VLC media player 0.8.6c Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/eric/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 216 modules
[00000001] main private debug: opening config file /home/eric/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000281] main playlist debug: waiting for thread completion
[00000281] main playlist debug: thread 3079789456 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000282] main private debug: waiting for thread completion
[00000282] main private debug: thread 3071396752 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000283] main interface debug: looking for interface module: 1 candidate
[00000283] main interface debug: using interface module "hotkeys"
[00000283] main interface debug: thread 3063004048 (interface) created at priority 0 (interface/interface.c:231)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "screensaver"
[00000285] main interface debug: thread 3054611344 (interface) created at priority 0 (interface/interface.c:231)
[00000287] main interface debug: looking for interface module: 5 candidates
[00000287] main interface debug: using interface module "wxwidgets"
[00000287] main interface debug: thread 3028433808 (manager) created at priority 0 (interface/interface.c:216)
[00000287] wxwidgets interface debug: Using last windows config '(-1,0,0,1280,800)(6,0,0,-1,150)'
[00000287] wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)




this is what i received.  bad allocation looks like the problem.  i was researching the "Bad alloc" message and...i've read things suggesting more ram, re-organizing usage of shared memory for the graphics card, adjusting swap storage...im still looking it all up.

Those are the normal messages you'll always get when you open it. Try opening the file whilst running in debug mode and you should get lots more output some of which is bound to be useful. All those messages are just related to the interface, nothing to do with loading codecs or anything like that.

---

### Post by arpinology on 2008-04-12
when i first usedvlc -vv, and opened a file, vlc player worked and played the video back normally.  and mplayer worked too.  

once i rebooted, they stopped working and went back to the normal 1-2 second audio and no video playback.  


oh, in a suggestion to an above reply, i installed the "ubuntu restricted extras" even before this problem became intolerable.  i rechecked to be sure and it was fine.  

eric@eric-desktop:~$ vlc -vv
VLC media player 0.8.6c Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/eric/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 216 modules
[00000001] main private debug: opening config file /home/eric/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000281] main playlist debug: waiting for thread completion
[00000281] main playlist debug: thread 3080182672 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000282] main private debug: waiting for thread completion
[00000282] main private debug: thread 3071789968 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000283] main interface debug: looking for interface module: 1 candidate
[00000283] main interface debug: using interface module "hotkeys"
[00000283] main interface debug: thread 3063397264 (interface) created at priority 0 (interface/interface.c:231)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "screensaver"
[00000285] main interface debug: thread 3055004560 (interface) created at priority 0 (interface/interface.c:231)
[00000287] main interface debug: looking for interface module: 5 candidates
[00000287] main interface debug: using interface module "wxwidgets"
[00000287] main interface debug: thread 3028827024 (manager) created at priority 0 (interface/interface.c:216)
[00000287] wxwidgets interface debug: Using last windows config '(-1,0,0,1280,800)(0,234,296,323,79)(6,0,0,-1,150)'
[00000287] wxwidgets interface debug: id=0 p=(234,296) s=(323,79)
[00000287] wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)
[00000281] main playlist debug: adding playlist item `/home/eric/movies/movie.mpeg' ( /home/eric/movies/movie.mpeg )
[00000281] main playlist debug: creating new input thread
[00000290] main input debug: waiting for thread completion
[00000290] main input debug: thread 2987973520 (input) created at priority 0 (input/input.c:265)
[00000290] main input debug: creating statistics handler
[00000290] main input debug: `/home/eric/movies/movie.mpeg' gives access `' demux `' path `/home/eric/movies/movie.mpeg'
[00000290] main input debug: creating demux: access='' demux='' path='/home/eric/movies/movie.mpeg'
[00000292] main demuxer debug: looking for access_demux module: 2 candidates
[00000290] main input debug: creating access '' path='/home/eric/movies/movie.mpeg'
[00000295] main access debug: looking for access2 module: 5 candidates
[00000295] vcd access debug: trying .cue file: /home/eric/movies/movie.cue
[00000295] vcd access debug: could not find .cue file
[00000295] access_file access debug: opening file `/home/eric/movies/movie.mpeg'
[00000295] main access debug: using access2 module "access_file"
[00000301] main private debug: pre-buffering...
[00000301] main private debug: received first data for our buffer
[00000301] main private debug: pre-buffering done 622573 bytes in 0s - 3230 kbytes/s
[00000290] main input debug: creating demux: access='' demux='' path='/home/eric/movies/movie.mpeg'
[00000302] main demuxer debug: looking for demux2 module: 45 candidates
[00000302] main demuxer debug: using demux2 module "ps"
[00000290] main input debug: looking for a subtitle file in /home/eric/movies/
[00000290] main input debug: `/home/eric/movies/movie.mpeg' successfully opened
[00000302] ps demuxer warning: garbage at input, trying to resync...
[00000302] ps demuxer warning: found sync code
[00000302] ps demuxer debug: we found a length of: 30014689
[00000290] main input debug: selecting program id=0
[00000342] main decoder debug: looking for decoder module: 25 candidates
[00000342] main decoder debug: using decoder module "mpeg_audio"
[00000342] main decoder debug: thread 2963110800 (decoder) created at priority 0 (input/decoder.c:159)
[00000356] main decoder debug: looking for decoder module: 25 candidates
[00000356] main decoder debug: using decoder module "libmpeg2"
[00000356] main decoder debug: thread 2953493392 (decoder) created at priority 0 (input/decoder.c:159)
[00000356] libmpeg2 decoder debug: 352x240 (display 352,240), aspect 563200, sar 8:9, 29.971 fps
[00000342] mpeg_audio decoder debug: MPGA channels:2 samplerate:44100 bitrate:192
[00000342] main decoder debug: no aout present, spawning one
[00000357] main audio output debug: looking for audio output module: 3 candidates
[00000356] main decoder debug: no usable vout present, spawning one
[00000357] alsa audio output debug: opening ALSA device `default'
[00000359] main private debug: Registering subpicture channel, ID: 2
[00000359] main private debug: Registering subpicture channel, ID: 3
[00000359] main private debug: Registering subpicture channel, ID: 4
[00000359] main private debug: Registering subpicture channel, ID: 5
[00000357] main audio output debug: thread 2945100688 (aout) created at priority 0 (alsa.c:662)
[00000357] main audio output debug: using audio output module "alsa"
[00000357] main audio output debug: output 's16l' 44100 Hz Stereo frame=1 samples/4 bytes
[00000357] main audio output debug: mixer 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes
[00000357] main audio output debug: filter(s) 'fl32'->'s16l' 44100 Hz->44100 Hz Stereo->Stereo
[00000360] main private debug: looking for audio filter module: 24 candidates
[00000358] main video output debug: window size: 352x270
[00000358] main video output debug: looking for video output module: 6 candidates
[00000360] main private debug: using audio filter module "float32tos16"
[00000357] main audio output debug: found a filter for the whole conversion
[00000357] main audio output debug: looking for audio mixer module: 3 candidates
[00000357] main audio output debug: using audio mixer module "trivial_mixer"
[00000357] main audio output debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1262 bytes
[00000357] main audio output debug: filter(s) 'mpga'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo
[00000384] main private debug: looking for audio filter module: 24 candidates
[00000384] main private debug: using audio filter module "mpgatofixed32"
[00000357] main audio output debug: found a filter for the whole conversion
[00000357] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Stereo->Stereo
[00000385] main private debug: looking for audio filter module: 24 candidates
[00000385] main private debug: using audio filter module "bandlimited_resampler"
[00000357] main audio output debug: found a filter for the whole conversion
[00000357] main audio output warning: PTS is out of range (108056), dropping buffer
[00000357] main audio output warning: PTS is out of range (82347), dropping buffer
[00000357] main audio output warning: PTS is out of range (56454), dropping buffer
[00000357] main audio output warning: PTS is out of range (30552), dropping buffer
[00000357] main audio output warning: PTS is out of range (4647), dropping buffer
[00000357] main audio output warning: PTS is out of range (-21269), dropping buffer
[00000357] main audio output debug: audio output is too slow (47475), trashing 11609us
[00000358] xvideo video output debug: adaptor 0, port 65, format 0x32315659 (YV12) planar
[00000358] xvideo video output debug: Window manager supports NetWM
[00000358] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000358] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000358] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000358] main video output debug: using video output module "xvideo"
[00000358] main video output debug: waiting for thread completion
[00000358] main video output debug: got 8 direct buffer(s)
[00000358] main video output debug: picture in 352x240 (0,0,352x240), chroma I420, ar 176:135, sar 8:9
[00000358] main video output debug: picture user 352x240 (0,0,352x240), chroma I420, ar 176:135, sar 8:9
[00000358] main video output debug: picture out 352x240 (0,0,352x240), chroma I420, ar 176:135, sar 8:9
[00000358] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000358] main video output debug: thread 2933914512 (video output) created at priority 0 (video_output/video_output.c:421)
[00000387] main private warning: dts != current_pts (1745185)
[00000387] main private warning: backward_pts != current_pts (-33367)
[00000358] main video output warning: late picture skipped (1647999)
[00000358] main video output warning: late picture skipped (1047789)
[00000358] main video output warning: late picture skipped (447366)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85
eric@eric-desktop:~$

---

