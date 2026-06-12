---
title: "Using FFMPEG to convert AVIs (changing resolution, bitrate)"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-08-06
So I have an avi file. I want to convert it to

Code:

AVI
320 x 240
30 frames a second
Bitrate can be adjusted.  Default usually 512 kbps
Audio 128 kbps

The AVI file has these properties right now (got from right clicking and using the aud/vid tab
Code:

624x352
Codec: Xvid MPEG-4
24 framers per second
Bitrate N/A (is this right?)

Audio 132 kbps
mpeg-1 layer 3

Hope this is pretty easy

I read a bit of the documentation, but it was kinda...huge. I am still reading, but I figure this would get a more timely response then me using trial and error.

---

### Post by FakeOutdoorsman on 2007-08-08
Try something like this (I am using the SVN version of ffmpeg, so I may get some options wrong since they can differ from a non-SVN version):

```
ffmpeg -i originalvideo.avi -s 320x240 -b 512 -ab 128 -acodec copy -vcodec copy -r 29.97 outputvideo.avi
```

-b is bitrate, but it might not work unless you use -b 512k.  Same with -ab (audio bitrate)  You may get better results by ommitting -b altogether since I added -vcodec copy which tells ffmpeg to use the same codec as the original and should also use the original bitrate and other parameters if we do not change them.

-r is frame rate.  I used 29.97 which is native NTSC, but change it to 30 if you need to.

-sameq is another option to try.  It uses the same quality in the encoder as in the decoder, but you may not need it if you already use -vcodec copy.

---

### Post by FleetAdmiral74 on 2007-08-08
Here is what I get from the terminal```
ed@ed-desktop:~$ ffmpeg -i /media/hda1/home/ed/luckymovie/lucky.avi -s 320x240 -b 512k -ab 128k -acodec copy -vcodec copy -r 29.97 /media/hda1/home/ed/luckymovie/outputvideo.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, avi, from '/media/hda1/home/ed/luckymovie/lucky.avi':
  Duration: 01:45:24.2, start: 0.000000, bitrate: 930 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 588x238, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Output #0, avi, to '/media/hda1/home/ed/luckymovie/outputvideo.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 588x238, q=2-31, 25.00 fps(c)
  Stream #0.1: Audio: 0x0055, 48000 Hz, stereo, 112 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=158106 q=-9119872.1 Lsize=  721004kB time=6324.2 bitrate= 933.9kbits/s    
video:624571kB audio:86464kB global headers:0kB muxing overhead 1.401955%
ed@ed-desktop:~$ 

```

It plays ok...but It does not look like anything actually changed. The bitrate, resolution and what not are all the same. The only difference was the output file was like 3mbs larger. Kinda strange...no?

---

### Post by FakeOutdoorsman on 2007-08-08
I guess if you use -vcodec copy and -acodec copy it won't listen to any custom parameters.  Try this:

```

ffmpeg -i /media/hda1/home/ed/luckymovie/lucky.avi -s 320x240 -b 512k -ab 128k -r 29.97 -acodec libmp3lame /media/hda1/home/ed/luckymovie/outputvideo.avi

```

ffmpeg will use default settings if you do not declare them.  If we omitted "-acodec libmp3lame" it will make your audio mp2 by default (you may have to use "mp3lame" instead since the latest SVN uses "libmp3lame").  Default video codec is mpeg4, but you can change it with -vcodec.

We can also get fancy with a 2 pass encode which will take longer but will look better depending on the video codec you use.

```
ffmpeg -y -i /media/hda1/home/ed/luckymovie/lucky.avi -pass 1 -s 320x240 -r 29.97 -b 512k -an /media/hda1/home/ed/luckymovie/outputvideo.avi && ffmpeg -y -i /media/hda1/home/ed/luckymovie/lucky.avi -pass 2 -s 320x240 -r 29.97 -b 512k -acodec libmp3lame -ab 128k /media/hda1/home/ed/luckymovie/outputvideo.avi

```

---

### Post by FleetAdmiral74 on 2007-08-08
Uh oh...something is wrong with libmp3lame/mp3lame. I tried both, here is what I get

```
ed@ed-desktop:~$ ffmpeg -i /media/hda1/home/ed/luckymovie/lucky.avi -s 320x240 -b 512k -ab 128k -r 29.97 -acodec libmp3lame /media/hda1/home/ed/luckymovie/outputvideo.avi

```
```
Unknown codec 'libmp3lame'
```

Same with mp3lame, - the lib part. I tried an apt-get install with libmp3lame and mp3lame, but no luck. That was all I could think of.

Thanks for your time in this.

And thanks for putting in the directory in the command, so nice of you!

---

### Post by FakeOutdoorsman on 2007-08-08
Your version of ffmpeg has not been compiled with lame support (no --enable-libmp3lame along with all those other compile options in your post #3.)

For legal reasons, the ffmpeg in Ubutnu packages does not contain all libraries that you need.  This can be easily fixed though with Medibuntu.

1. Uninstall your version of ffmpeg.
2. Add Medibuntu repository to your sources.list. [Easy instructions]("http://medibuntu.sos-sts.com/repository.php").
2. sudo aptitude update
3. sudo aptitude install ffmpeg (or install via Synaptic to make sure it is the Medibuntu version)
4. Try the ffmpeg command from above again.
5. It will work this time.
6. I think.

---

### Post by FleetAdmiral74 on 2007-08-08
Froodlenitzkie...got this```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ed@ed-desktop:~$ 

```

I tried using sudo as well, no luck. hehe, one problem after another no? It will all work out in the end though.

edit: soon after the failed command, I saw an update window for the ffmpeg something or other...so anyway after that I ran the command again, and worked. Going to proceed with the other steps now...

gah...did the update command, got```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
ed@ed-desktop:~$ 

```

---

### Post by FakeOutdoorsman on 2007-08-08
I would guess Synaptic, Update Manager, adept, or aptitude are currently open or running.  After one of those programs is closed you should be able to continue.  In terminal type **pstree** and you can see if one is running.

---

### Post by FleetAdmiral74 on 2007-08-08
Now this is getting on my nerve. Followed instructions, when i do a --version I get```
--enable-mp3lame
``` included in there

When I run the above command, however, same output about unknown codec. curses!

Here is everything, just in case.```
ed@ed-desktop:~$ ffmpeg --version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
ffmpeg: missing argument for option '--version'
ed@ed-desktop:~$ ffmpeg -i /media/hda1/home/ed/luckymovie/lucky.avi -s 320x240 -b 512k -ab 128k -r 29.97 -acodec mp3lame /media/hda1/home/ed/luckymovie/outputvideo.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, avi, from '/media/hda1/home/ed/luckymovie/lucky.avi':
  Duration: 01:45:24.2, start: 0.000000, bitrate: 930 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 588x238, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Unknown codec 'mp3lame'

```

---

### Post by FakeOutdoorsman on 2007-08-08
I think everything is ready to work, but this latest error must be one of the option differences between our ffmpeg versions (SVN vs. Medibuntu repository).

You can list the formats available with:
```
ffmpeg -formats
```

Scroll down to the Codecs list and you can see which mp3 codec to use.  Mine shows "libmp3lame", and yours could be anything like "mp3" or something.  You can use this to change your audio codec you want to encode with, as long as the listed coded has an "E" next to it.  For example, to encode aac I would use -acodec libfaac.

---

### Post by FleetAdmiral74 on 2007-08-08
I saw one, just mp3...had the E, so I am giving it a try.

---

### Post by FleetAdmiral74 on 2007-08-08
Converted ok...gosh darnit, it should be playing fine...but it does not. Plays fine ont he comp, just not the player... Gimme some time to think...

In case I missed anything or misinterpreted the specs, this is what the tech guy told me...

AVI
320 x 240
30 frames a second
Bitrate can be adjusted. Default usually 512 kbps
Audio 128 kbps

Again...sorry, I never mean to take this much time out of one person but it always happens that way.

---

### Post by FakeOutdoorsman on 2007-08-09
Your supplied specs conform to the ffmpeg commands you used.  Sounds like the tech guy doesn't know what his player needs.  For example, AVI is just a container format and can contain many types of codecs.  What player are you trying to use?  Is this a software player, or hardware like an iPod?

If you want to keep testing various options without having to encode the whole movie you can use -vframes x.  x being the number of frames, so you can do 10 seconds of video at 30 fps = 300 = -vframes 300.

---

### Post by MrKlean on 2007-08-09
You might want to try WinFF.  Despite the name, there is a linux version.. works good for me since devede is no longer usable for me ; (  Maybe one day it will work again ; )

Hope this helps ; )

---

### Post by FleetAdmiral74 on 2007-08-09
I will post about the container format thingy, and see if I can get any more info...

---

