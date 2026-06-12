---
title: "VLC transcoding to mp4, no audio help plz."
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by darkservlist on 2008-03-11
Hi, I've found an easy way to transform my videos to mp4 and other formats with VLC with the stream/transcoding wizard found in VLC player File/Wizard, but even if I can successfully transform to mp4 and play them in my ipod 5th gen (used amarok to get them in my ipod since gtkpod-aac has issues in gutsy), I can't seem to find a way to get a video with audio, just the video, is my VLC missing an audio codec or my input is wrong? 

here's what i did with a .wmv file i transcoded successfully (video only of course):

**Video**

Transcode video: *
Codec: MPEG-4 Video
Bitrate (kb/s): 2048
[B]
Audio[/B]

Transcode audio: *
Codec: MPEG 4 audio
Bitrate: 192

---

### Post by azimuth on 2008-03-12
I had a similar experience transcoding a steaming source (capture card). I didn't figure out what was going on until I had a mic plugged in too. The audio was not set to the stream source, but to the mic input. I don't remember where I had to change it, but maybe this will give you a clue of what to look for.

---

### Post by test4444 on 2008-06-08
I have the same problem.

i use the vlc streaming assistent and no sound as well.

(there is no mic decision issue at this assistent.)

please help us !!

---

### Post by Naugas on 2008-06-24
It seems like vlc for ubuntu isn't compiled with aac encoding support... :( That's my guess anyway. Something that makes me think there's something more to it than a mistake is that aac encoding doesn't seem to work (I can't get it to work anyway...) with ffmpeg from medibuntu either - even though the binary claims it is compiled with libfaac. 

My errors with vlc:

ffmpeg error: cannot find encoder MPEG AAC Audio
stream_out_transcode error: cannot find encoder ((null))
stream_out_transcode error: cannot create audio chain
main error: cannot create packetizer output (mpga)

There's also a bug reported on this:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/242201](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/242201)

I would be very very happy if someone that actually have a clue about what's going on here answers.

---

### Post by tyfius on 2008-06-24
I am using WinFF ([http://www.winff.org/](http://www.winff.org/)) to convert my videos to MP4 so I can play them on my iPod.

Note that this requires the Medibuntu ([http://www.medibuntu.org/](http://www.medibuntu.org/)) ffmpeg packages. The default don't have any AAC support.

Works like a charm.

---

