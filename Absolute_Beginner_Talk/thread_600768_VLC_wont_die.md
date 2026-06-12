---
title: "VLC wont die"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-11-02
just been playing music with VLC media player. When I close it it wont stop playing I have to reboot to stop it. How do I stop it without rebooting

---

### Post by bluepowder7 on 2007-11-02
there's a KILL function.  if you go System -> Admin (or Preferences) -> Task Manager or System Manager or something like that, it'll pop up a list just like Windows does.  from there, you can select a process and KILL it.

ya, i'm a bit vague, but my linux laptop isn't working properly now, so i'm going from memory here....

hope this helps!  i've got a whole 2-3 months of linux under my belt, so....

---

### Post by Centx on 2007-11-02
You could always just do a "killall vlc" if you just want to kill _all_ instances of vlc, optionally you could make yourself a xkill-button which will kill whatever window you click on after you've executed "xkill".

---

### Post by rudeboyskunk on 2007-11-02
Or if you prefer command-line, you can type:

```
sudo killall vlc
```

---

### Post by rajan on 2007-11-02
go to the command line and type 

```

ps -ef

```

and look for something involving vlc .... then look for the PID (process ID) and in a terminal type 

```

kill <insertthePIDhere>

```

and if that doesn't work, use

```

kill -KILL <insertthePIDhere>

```

---

### Post by mgmiller on 2007-11-02
My favorite is to open a terminal and type:
```
xkill 
```

Your mouse curson becomes a skull and crossbones.  You then just click on whatever you want to kill and IT WILL DIE!!!  :lolflag:

---

### Post by bigmonmulgrew on 2007-11-02
there is no window open the music just keeps playing.
There was nothing in the processes list that was obviously VLC but I will check again tommorrow

---

### Post by bluepowder7 on 2007-11-02
> **bigmonmulgrew said:**
> there is no window open the music just keeps playing.
There was nothing in the processes list that was obviously VLC but I will check again tommorrow


i was once installing Win98Lite (a hack), and once up and running the first thing i did was make it play a CD.  it was a Smashing Pumpkins disc, not sure which one, but then Win98 decided to CRASH and show me the blue screen of death - while the pumpkins were still graciously playing and just happened to sing the line "bang bang you're dead" when the blue screen came on...

:(

---

### Post by Centx on 2007-11-02
> **bigmonmulgrew said:**
> there is no window open the music just keeps playing.
There was nothing in the processes list that was obviously VLC but I will check again tommorrow

Don't like to say this, but your best(easiest for sure) bet would probably be to just purge vlc, and reinstall... If it doesn't work after that, you could try to get some diagnostic output, and post it here(and read it yourself of course :)) with the command ```
vlc -vv
``` from terminal.

to purge vlc from terminal:```
aptitude purge vlc
```

---

### Post by por100pre1 on 2007-11-02
Check if reseting your vlc settings fixes the problem.

```
pkill vlc
```

```
mv .vlc .vlc_backup
```

---

### Post by surfer69 on 2007-11-02
> **rajan said:**
> go to the command line and type 

```

ps -ef

```

and look for something involving vlc .... then look for the PID (process ID) and in a terminal type 



The best way to do that is:

**ps -ef|grep vlc**

That will show the process number to kill, ignore the one for the **'grep vlc'**  itself, because it's finished already!!!!!!!:)

---

### Post by bigmonmulgrew on 2007-11-03
this time the process stayed in the command list. I closed it and bye bye music.
I'll have to investigate this a bit more later

---

### Post by Declan on 2007-11-03
I have had this same problem. For me the solution was to type "sudo killall wxvlc"
I don't know what wxvlc but I think I found it by doing lsof /dev/dsp or something like that.
Anyway, I've used this technique often, and it always does the job.

Declan

---

### Post by carloslosgrande on 2007-11-03
[FONT="Comic Sans MS"]Hi. A bit late with this, but I use an applet called 'force quit' that is available in the 'add to panel' menu.
I often get apps stuck and refuse to quit and I find this little applet very handy.[/FONT]

---

### Post by bratliff on 2007-11-03
sudo killall vlc does not work. but the xkill does, thanks. kill all returns the msg no process killed.

Robert Ratliff




> **rudeboyskunk said:**
> Or if you prefer command-line, you can type:

```
sudo killall vlc
```

---

### Post by rajan on 2007-11-03
> **bigmonmulgrew said:**
> this time the process stayed in the command list. I closed it and bye bye music.
I'll have to investigate this a bit more later

good to hear ... surfer69 is right btw because there tends to be a lotta junk that a simple pipe into grep will filter.

......but i guess the point of this thread isn't to figure out how to kill it, it's to fix the problem. does reinstallation, like mentioned above, help?

---

### Post by bigmonmulgrew on 2007-11-04
purging and reinstalling does not fix the problem

---

### Post by bigmonmulgrew on 2007-11-04
Right just did vlv -vv and the output is as follows

```

VLC media player 0.8.6c Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/bigmon/.vlc/cache/plugins-04081e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 223 modules
[00000001] main private debug: opening config file /home/bigmon/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE SSE2 FPU 
[00000001] main private debug: looking for memcpy module: 4 candidates
[00000001] main private debug: using memcpy module "memcpymmxext"
[00000287] main playlist debug: waiting for thread completion
[00000287] main playlist debug: thread 1082132816 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000288] main private debug: waiting for thread completion
[00000288] main private debug: thread 1090525520 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000289] main interface debug: looking for interface module: 1 candidate
[00000289] main interface debug: using interface module "hotkeys"
[00000289] main interface debug: thread 1098918224 (interface) created at priority 0 (interface/interface.c:231)
[00000291] main interface debug: looking for interface module: 1 candidate
[00000291] main interface debug: using interface module "screensaver"
[00000291] main interface debug: thread 1107310928 (interface) created at priority 0 (interface/interface.c:231)
[00000293] main interface debug: looking for interface module: 5 candidates
[00000293] main interface debug: using interface module "wxwidgets"
[00000293] main interface debug: thread 1115703632 (manager) created at priority 0 (interface/interface.c:216)
[00000293] wxwidgets interface debug: Using last windows config '(-1,0,0,2560,1024)(0,453,490,425,86)(6,0,0,-1,150)'
[00000293] wxwidgets interface debug: id=0 p=(453,490) s=(425,86)
[00000293] wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)


```

I then add goto view playlist and then add my music folder.
It produces this

```

** (.:7171): CRITICAL **: gtk_pizza_set_size: assertion `pizza != NULL' failed
[00000287] main playlist debug: adding playlist item `/home/bigmon/Music' ( /home/bigmon/Music )


```

then I click play and it lists all the tracks and locations in the playlist followed by

```

[00000306] main private debug: received first data for our buffer
[00000306] main private debug: pre-buffering done 1408981 bytes in 0s - 3509 kbytes/s
[00000296] main input debug: creating demux: access='' demux='directory' path='/home/bigmon/Music'
[00000712] main demuxer debug: looking for demux2 module: 1 candidate
[00000712] main demuxer debug: using demux2 module "access_directory"
[00000296] main input debug: looking for a subtitle file in /home/bigmon/
[00000301] access_directory access warning: unimplemented query in control
[00000296] main input debug: `/home/bigmon/Music' successfully opened
[00000296] main input debug: EOF reached
[00000296] main input debug: closing input
[00000712] main demuxer debug: removing module "access_directory"
[00000301] main access debug: removing module "access_directory"
[00000296] main input debug: thread 1124096336 joined (input/input.c:412)
[00000287] main playlist debug: creating new input thread
[00000763] main input debug: waiting for thread completion
[00000763] main input debug: `/home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/Alannah Myles - 08 - Black Velvet.mp3' gives access `' demux `' path `/home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/Alannah Myles - 08 - Black Velvet.mp3'
[00000763] main input debug: creating demux: access='' demux='' path='/home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/Alannah Myles - 08 - Black Velvet.mp3'
[00000764] main demuxer debug: looking for access_demux module: 2 candidates
[00000763] main input debug: thread 1124096336 (input) created at priority 0 (input/input.c:265)
[00000763] main input debug: creating access '' path='/home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/Alannah Myles - 08 - Black Velvet.mp3'
[00001030] main access debug: looking for access2 module: 5 candidates
[00001030] vcd access debug: trying .cue file: /home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/Alannah Myles - 08 - Black Velvet.cue
[00001030] vcd access debug: could not find .cue file
[00001030] access_file access debug: opening file `/home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/Alannah Myles - 08 - Black Velvet.mp3'
[00001030] main access debug: using access2 module "access_file"
[00001031] main private debug: pre-buffering...
[00001031] main private debug: received first data for our buffer
[00001031] main private debug: pre-buffering done 1408981 bytes in 0s - 46221 kbytes/s
[00000763] main input debug: creating demux: access='' demux='' path='/home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/Alannah Myles - 08 - Black Velvet.mp3'
[00001032] main demuxer debug: ID3v2.3 revision 0 tag found, skipping 336 bytes
[00001032] main demuxer debug: looking for demux2 module: 45 candidates
[00001046] main packetizer debug: looking for packetizer module: 17 candidates
[00001046] main packetizer debug: using packetizer module "mpeg_audio"
[00001032] mpga demuxer debug: did not sync on first block
[00000763] main input debug: selecting program id=0
[00001032] main demuxer debug: looking for id3 module: 1 candidate
[00001032] id3tag demuxer debug: checking for ID3 tag
[00001032] id3tag demuxer debug: found ID3v1 tag
[00001032] id3tag demuxer debug: found ID3v2 tag
[00001032] main demuxer debug: using id3 module "id3tag"
[00001032] main demuxer debug: removing module "id3tag"
[00001032] main demuxer debug: using demux2 module "mpga"
[00000763] main input debug: looking for a subtitle file in /home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/
[00001047] main decoder debug: looking for decoder module: 25 candidates
[00001047] main decoder debug: using decoder module "mpeg_audio"
[00001047] main decoder debug: thread 1132489040 (decoder) created at priority 0 (input/decoder.c:159)
[00000763] main input debug: meta information:
[00000763] main input debug:   - 'Title' = 'Black Velvet'
[00000763] main input debug:   - 'Artist' = 'Alannah Myles'
[00000763] main input debug:   - 'Album/movie/show title' = 'The Very Best Of Power Ballads'
[00000763] main input debug:   - 'Date' = '2005'
[00000763] main input debug:   - 'Track number/position in set' = '8'
[00000763] main input debug:   - 'Genre' = 'Other'
[00000763] main input debug:   - 'Title' = 'Black Velvet'
[00000763] main input debug:   - 'Genre' = 'Pop'
[00000763] main input debug:   - 'Track number/position in set' = '8/16'
[00000763] main input debug:   - 'Software/hardware and settings used for encoding' = 'Audiograbber 1.83.01, LAME dll 3.91, 192 Kbit/s, Joint Stereo, Normal quality'
[00000763] main input debug:   - 'Album/movie/show title' = 'The Very Best Of Power Ballads CD3'
[00000763] main input debug:   - 'Artist' = 'Alannah Myles'
[00000763] main input debug:   - 'Date' = '2005'
[00000763] main input debug: `/home/bigmon/Music/The Very Best Of Power Ballads/The Very Best Of Power Ballads CD3/Alannah Myles - 08 - Black Velvet.mp3' successfully opened
[00001046] mpeg_audio packetizer debug: MPGA channels:2 samplerate:44100 bitrate:192
[00001047] mpeg_audio decoder debug: MPGA channels:2 samplerate:44100 bitrate:192
[00001047] main decoder debug: no aout present, spawning one
[00001052] main audio output debug: looking for audio output module: 3 candidates
[00001052] alsa audio output debug: opening ALSA device `default'
[00001052] main audio output debug: thread 1140881744 (aout) created at priority 0 (alsa.c:662)
[00001052] main audio output debug: using audio output module "alsa"
[00001052] main audio output debug: output 's16l' 44100 Hz Stereo frame=1 samples/4 bytes
[00001052] main audio output debug: mixer 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes
[00001052] main audio output debug: filter(s) 'fl32'->'s16l' 44100 Hz->44100 Hz Stereo->Stereo
[00001053] main private debug: looking for audio filter module: 24 candidates
[00001053] main private debug: using audio filter module "float32tos16"
[00001052] main audio output debug: found a filter for the whole conversion
[00001052] main audio output debug: looking for audio mixer module: 3 candidates
[00001052] main audio output debug: using audio mixer module "float32_mixer"
[00001052] main audio output debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1053 bytes
[00001052] main audio output debug: filter(s) 'mpga'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo
[00001081] main private debug: looking for audio filter module: 24 candidates
[00001081] main private debug: using audio filter module "mpgatofixed32"
[00001052] main audio output debug: found a filter for the whole conversion
[00001052] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Stereo->Stereo
[00001082] main private debug: looking for audio filter module: 24 candidates
[00001082] main private debug: using audio filter module "bandlimited_resampler"
[00001052] main audio output debug: found a filter for the whole conversion
[00001052] main audio output warning: output date isn't PTS date, requesting resampling (40005)
[00001052] main audio output warning: buffer is 40012 late, triggering upsampling
[00001052] main audio output warning: resampling stopped after 9627735 usec (drift: 492)



```

I then click on the X in the corner to close VLC and the music keeps playing. There is no further output.
This says to me thet it is closing the gui but not the process but it means you no longer have control over the process. Opening VLC again opens it in a seperate process and gives you no control over the current one

---

### Post by Declan on 2007-11-04
So, did you try "killall wxvlc"? 

Declan

---

