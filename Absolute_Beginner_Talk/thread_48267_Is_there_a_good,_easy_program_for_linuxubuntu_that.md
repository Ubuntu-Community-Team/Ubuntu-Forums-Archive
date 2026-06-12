---
title: "Is there a good, easy program for linux/ubuntu that can convert avi to mpeg?"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by okey on 2005-07-11
(see topic)

I'm using k3b to try to either burn a DVD-Video or a VCD (whatever will allow me to watch these avi's/mpeg's on my DVD player) and it doesn't support AVI's. What program can I use to convert them?

Keep in mind I have no idea how to use any command line.

Thanks a lot.

---

### Post by tikal26 on 2005-07-11
have you try 
avifile-player
[http://packages.ubuntu.com/breezy/graphics/avifile-player](http://packages.ubuntu.com/breezy/graphics/avifile-player)

---

### Post by bored2k on 2005-07-11
[http://www.ubuntuforums.org/showpost.php?p=77699&postcount=3](http://www.ubuntuforums.org/showpost.php?p=77699&postcount=3)

---

### Post by polo_step on 2005-07-12
Can anyone briefly explain what you would lose (or gain) in terms of size and/or quality by converting .avi files to .mpg files?

Thanks.

---

### Post by sapo on 2005-07-12
[QUOTE=polo_step]Can anyone briefly explain what you would lose (or gain) in terms of size and/or quality by converting .avi files to .mpg files?

Thanks.[/QUOTE]

you can make a mpg with the same quality of an avi file... but.. the size is gonna be a lot bigger  :-P

---

### Post by tristan on 2005-07-12
I know you don't want to use the command line, but unfortunately most of the decent linux stuff which works in ubuntu, requires it. It's really not that diffcult though :)

**mencoder** is a good command line tool which I regularly use to convert divx or xvid avi files to mpeg1 files for burning to vcd. 

For the same filesize, divx / xvid avi will usually have much better quality than mpg. On the other hand, mpg files are easy to stick on a VCD which will play in most DVD players, wheras only a few of the later released DVD players will play divx.

What I usually do is record my stuff as high quality xvid avis. I either watch them on the computer as avi, or convert them to VCD to watch on the telly.

Here's some info from the mplayer homepage which should allow you to transcode your avi files to mpg for VCD:

PAL VCD
  **mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=xvcd -vf scale=352:288,harddup -srate 44100 -af lavcresample=44100 -lavcopts vcodec=mpeg1video:keyint=15:vrc_buf_size=327:vrc_minrate=1152:vbitrate=1152:  vrc_maxrate=1152:acodec=mp2:abitrate=224 -ofps 25  -o movie.mpg movie.avi**

NTSC VCD
  **mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=xvcd -vf scale=352:240,harddup -srate 44100 -af lavcresample=44100 -lavcopts vcodec=mpeg1video:keyint=18:vrc_buf_size=327:vrc_minrate=1152:vbitrate=1152:vrc_maxrate=1152:acodec=mp2:abitrate=224 -ofps 30000/1001  -o movie.mpg movie.avi **

You then convert the mpg to VCD image using vcdimager
**vcdimager movie.mpg**

This creates vidoecd.bin and videocd.cue

Then use cdrdao to write the whole thing to CD

**cdrdao write --device your cd device (eg /dev/hdc) videocd.cue**


Hope this info helps

---

### Post by bored2k on 2005-07-12
[QUOTE=tristan]I know you don't want to use the command line, but unfortunately most of the decent linux stuff which works in ubuntu, requires it. It's really not that diffcult though :)

**mencoder** is a good command line tool which I regularly use to convert divx or xvid avi files to mpeg1 files for burning to vcd. 

For the same filesize, divx / xvid avi will usually have much better quality than mpg. On the other hand, mpg files are easy to stick on a VCD which will play in most DVD players, wheras only a few of the later released DVD players will play divx.

What I usually do is record my stuff as high quality xvid avis. I either watch them on the computer as avi, or convert them to VCD to watch on the telly.

Here's some info from the mplayer homepage which should allow you to transcode your avi files to mpg for VCD:

PAL VCD
  **mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=xvcd -vf scale=352:288,harddup -srate 44100 -af lavcresample=44100 -lavcopts vcodec=mpeg1video:keyint=15:vrc_buf_size=327:vrc_minrate=1152:vbitrate=1152:  vrc_maxrate=1152:acodec=mp2:abitrate=224 -ofps 25  -o movie.mpg movie.avi**

NTSC VCD
  **mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=xvcd -vf scale=352:240,harddup -srate 44100 -af lavcresample=44100 -lavcopts vcodec=mpeg1video:keyint=18:vrc_buf_size=327:vrc_minrate=1152:vbitrate=1152:vrc_maxrate=1152:acodec=mp2:abitrate=224 -ofps 30000/1001  -o movie.mpg movie.avi **

You then convert the mpg to VCD image using vcdimager
**vcdimager movie.mpg**

This creates vidoecd.bin and videocd.cue

Then use cdrdao to write the whole thing to CD

**cdrdao write --device your cd device (eg /dev/hdc) videocd.cue**


Hope this info helps[/QUOTE]
 tristan, what about avi to mpeg for DVDs ? I would be really interested in this.
And, whats the speed on mencoder ?

---

### Post by tristan on 2005-07-12
> tristan, what about avi to mpeg for DVDs ? I would be really interested in this.
And, whats the speed on mencoder ?

I found a bit more info on the mencoder page about encoding DVDs for you Bored2K.

On my box mencoder will transcode 640x480 avi to 352x288 mpeg1 at about 45-50 frames/sec (ie twice realtime). 

I know there are probably many higher quality (and slower) solutions to DVD and VCD encoding around, but the mencoder option is fast, decent quality and you don't need to be a rocket scientist to do it :)


```
This section shows some complete commands for creating VCD/SVCD/DVD compliant videos.
7.13.5.1. PAL DVD

  mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:576,\
  harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:\
  vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:acodec=ac3:\
  abitrate=192:aspect=16/9 -ofps 25 \
  -o movie.mpg movie.avi


7.13.5.2. NTSC DVD

  mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,\
  harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:\
  vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:acodec=ac3:\
  abitrate=192:aspect=16/9 -ofps 30000/1001 \
  -o movie.mpg movie.avi


7.13.5.3. PAL AVI Containing AC3 Audio to DVD

If the source already has AC3 audio, use -oac copy instead of re-encoding it.

  mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:576,\
  harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:\
  vbitrate=5000:keyint=15:aspect=16/9 -ofps 25 \
  -o movie.mpg movie.avi


7.13.5.4. NTSC AVI Containing AC3 Audio to DVD

If the source already has AC3 audio, and is NTSC @ 23.976 fps:

  mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,\
  harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:\
  vbitrate=5000:keyint=15:aspect=16/9 -ofps  24000/1001 \
  -o movie.mpg movie.avi 
```

---

### Post by qrazi on 2005-07-20
i have a symbian phone since a week. i'd like to watch movies or recorded tv on that phone. smartmovie has this option, but that is a windows solution. i'd like to convert movies under l.inux. would mencoder be sufficient and does anyone perhaps the best settings to convert the average xvid/divx to a size that a symbian series 60 phone can use?
the phone i use is a nokia 3230

---

### Post by troughton on 2006-08-05
[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page) i use tovid it is gui fronted and you can also run in termianl it converts any file format to mpg and will even creat the dvd or vcd for you  in pal or ntfc

---

