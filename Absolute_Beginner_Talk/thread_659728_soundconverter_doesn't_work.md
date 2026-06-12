---
title: "soundconverter doesn't work"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Shadyjames on 2008-01-06
When i attempt to convert from WMA to MP3 on feisty using soundconverter it does a lot of things it shouldn't:

1. The output file is blank. Nothing even remotely helpful occurred during the process.

2. The output file isn't in the same folder as the input file, despite explicitly ticking the "output into the same folder as input" box. Rather than putting the file in "/media/ACRONIS SZ/Music mp3/music/Jars of Clay/Much Afraid" where it came from, it does the same trick often seen with browsers handling spaces in URLS and placed the output (the blank output, i remind you) in "/media/ACRONIS%20SZ/Music%20mp3/music/Jars%20of%20Clay/Much%20Afraid"

Point two took me a bloody long time to figure out. 
As for anybody who knows what acronis is, i assure you i'm not trying to mount an acronis disk image in ubuntu, "ACRONIS SZ" is simply the name of the partition. 

An optional problem you could solve to render the above moot is figuring out how to play lossless WMA files :P

I await your advice with baited breath! so far apt-get is the only thing in this whole OS to work the way its meant to :P (whoever invented that deserves a medal btw) /rant

---

### Post by blueridgedog on 2008-01-06
Spaces in Linux will break a number of things.  Directory names and file names should not have spaces in them as a rule, just to avoid things like you have found.

This link:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3)

Has a great step by step guide to convert from WMA to MP3, including the creation of a simple script to automate the process.

If you elect to try this approach note the following:
-test it/run it on a **copy** of the files as my read of the script is that it is destructive of the set of files it is run against.  I can help you edit the script if you want have it create a copy of the files versus converting and deleting.
-I can help you debug or tweak it if needed

---

### Post by Shadyjames on 2008-01-07
I ran the script in one of my music folders and it managed to do the whole thing in under 5 seconds, which was probably the first sign that it needed some modifications. The second sign is that they won't play, but they were just test copies, nothings been lost :)
It did spout a number of errors (the meaning of which are beyond me) so i'll post them here that you may help me sort out the problem. 
For the impatient reader, below are the bits that looked like trouble:

```
mv: `01_Overjoyed.wma' and `01_overjoyed.wma' are the same file
-waveheader is deprecated. Use -ao pcm:waveheader instead.
rm: cannot remove `audiodump.wav': No such file or directory

```

For a total dump, as it were, of the process:
```
james@james-ubuntu:/media/ACRONIS SZ/Music mp3/music/Jars of Clay/Much Afraid$ wmamp3
mv: `01_Overjoyed.wma' and `01_overjoyed.wma' are the same file
mv: `03_Tea_and_Sympathy.wma' and `03_tea_and_sympathy.wma' are the same file
mv: `04_Crazy_Times.wma' and `04_crazy_times.wma' are the same file
mv: `05_Frail.wma' and `05_frail.wma' are the same file
mv: `07_Weighed_Down.wma' and `07_weighed_down.wma' are the same file
mv: `09_Truce.wma' and `09_truce.wma' are the same file
mv: `10_Much_Afraid.wma' and `10_much_afraid.wma' are the same file
mv: `11_Hymn.wma' and `11_hymn.wma' are the same file
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-waveheader is deprecated. Use -ao pcm:waveheader instead.
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-waveheader is deprecated. Use -ao pcm:waveheader instead.
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-waveheader is deprecated. Use -ao pcm:waveheader instead.
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-waveheader is deprecated. Use -ao pcm:waveheader instead.
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-waveheader is deprecated. Use -ao pcm:waveheader instead.
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-waveheader is deprecated. Use -ao pcm:waveheader instead.
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-waveheader is deprecated. Use -ao pcm:waveheader instead.
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-waveheader is deprecated. Use -ao pcm:waveheader instead.
rm: cannot remove `audiodump.wav': No such file or directory

```

Thanks for the help so far. I did find that script of my own accord earlier but now that somebodys offered their help in getting it working i'm more likely to take it beyond the "didn't work, next thing plz" stage.

---

### Post by blueridgedog on 2008-01-07
OK, here is a modified version.  Note that I am not happy with this, but am tweaking it from a version found.  I might rewrite it, but for the time being, lets try and get it to work.  Note that the mplayer line needs to be on one line.
```

#!/bin/bash

current_directory=$( pwd )

#remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME BE CERTAIN THIS IS ON ONE LINE
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && lame -m s audiodump.wav -o $i; done

#convert file names
for i in *.wma 
do 
        newname=`basename $i .wma`.mp3
        mv $i $newname 
done

rm audiodump.wav
```

Note that the two rename functions designed to eliminate spaces and capitals will result in:

mv: `01_Overjoyed.wma' and `01_overjoyed.wma' are the same file 

Type of errors if the files do not need to have spaces removed and/or capitals removed.  Also note that I see from the example above, that your system thinks Overjoyed is the same as overjoyed, which implies the files are on a fat32 partition.  This may cause issues. 

Here is a test.  On my system I named the script "convert.sh" just for testing and I downloaded a sample wma file name sample.wma.  Things that start with NOTE are my comments to you.  Try this and if you errors post them, it may be that you needs some codecs.


```
james@ripstop:~/audiotest$ ls
convert.sh  sample.wma
james@ripstop:~/audiotest$ ./convert.sh 
mv: `sample.wma' and `sample.wma' are the same file
NOTE: you can ignore this due to the fact that there is no need to change case
mv: `sample.wma' and `sample.wma' are the same file
NOTE: you can ignore this as there is no reason to remove spaces
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 31, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
NOTE: you can ignore this as I am not trying to use a remote
Failed to open LIRC support. You will not be able to use your remote control.

Playing sample.wma.
ASF file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4003->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
[AO PCM] File: audiodump.wav (WAVE)
PCM: Samplerate: 44100Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   5.9 (05.8) of 5.0 (05.0)  2.5% 

Exiting... (End of file)
LAME 3.97 32bits (http://www.mp3dev.org/)
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE, SSE2
Using polyphase lowpass filter, transition band: 16538 Hz - 17071 Hz
Encoding audiodump.wav to sample.wma
Encoding as 44.1 kHz 128 kbps stereo MPEG-1 Layer III (11x) qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
   167/167   (100%)|    0:00/    0:00|    0:00/    0:00|   14.072x|    0:00 
---------------------------------------------------------------------------------------------------
   kbps        LR  %     long switch short %
  128.0      100.0        97.6   1.2   1.2
Writing LAME Tag...done
ReplayGain: +3.6dB
james@ripstop:~/audiotest$ ll
total 88
drwxr-xr-x  2 james james  4096 2008-01-07 21:13 .
drwxr-xr-x 75 james james  4096 2008-01-07 21:13 ..
-rwx------  1 james james   482 2008-01-07 21:13 convert.sh
-rw-r--r--  1 james james 70216 2008-01-07 21:13 sample.mp3
james@ripstop:~/audiotest$ 
```

As you can see from the final ls, the end result is an mp3 file that plays as expected.

---

### Post by Shadyjames on 2008-02-04
thanks for the help, that worked great. Sorry for the late reply, but about one minute and eight seconds into listening to my newly converted songs and writing my thanks in the forums, my motherboard broke! i only just received and replaced it recently, and when i hit "restore old session" on firefox this thread came up, so yes, thanks.

---

