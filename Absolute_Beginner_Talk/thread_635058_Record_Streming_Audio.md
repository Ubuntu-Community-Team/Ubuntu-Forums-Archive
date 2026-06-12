---
title: "Record Streming Audio"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by bbharatsony on 2007-12-08
How can I record audio that is playing from the internet without using VLC or streamtuner or streamripper?

---

### Post by philinux on 2007-12-08
Audacity can record anything you're listening too.

---

### Post by niteshifter on 2007-12-08
That depends upon what kind of streaming we're talking about. Below is what I use to grab RealAudio streams:
```
mplayer -bandwidth 2000000 -cache 3000 rtsp://somedomain.com/somepath/realfile.rm -ao pcm:waveheader -vc null -vo null

```

Then I use lame to convert the wave file to mp3:
```
lame -h -b 128 audiodump.wav somefile.mp3
```

Then clean up:
```
rm audiodump.wav
```

---
What the above does.

mplayer:
*-bandwidth 2000000* Means get the stream at a 2M bps rate. Without this option the data comes to you much slower - like it is feeding a RealPlayer. This is a very handy feature - without this option you'll still get the stream, but a 1 hour stream takes exactly that: 1 hour. With the bandwidth increased a 1 hour stream can be had in mere minutes. Note that not all servers will permit a bandwidth increase. Note also that **you** have to have the bandwidth capability as well - for example, if one has a 512KBPS DSL connection then asking the server to put out 2MBPS won't work, the server will probably drop you.

Also note that the audiodump.wav can be very large, hundred's of MB. Rough rule of thumb: For a "normal" RA stream (22KBPS encoding) 1 hour generates 300MB. Make sure you've enough disc space!

*-cache 3000* Sets a local cache of 3MB. Sometimes needed with the -bandwidth switch, does no harm to include it.

*rtsp://somedomain.com/somepath/realfile.rm* The URL of the stream you want.

*-ao pcm:waveheader* Is telling mplayer to make a WAVE format file. Default file name is audiodump.wav

*-vc null -vo null* Means no video codec, no video output.

lame:
*-h*  make some quality improvements.

*-b 128*  set the bitrate to 128K bps

*audiodump.wav* Our input file

*somefile.mp3* Our output file

rm:
*audiodump.wav* Delete the file audiodump.wav

---

### Post by nikoPSK on 2007-12-08
yes audacity does it quite well. If you have the time you can record the output of your soundcard with sound recorder....

---

