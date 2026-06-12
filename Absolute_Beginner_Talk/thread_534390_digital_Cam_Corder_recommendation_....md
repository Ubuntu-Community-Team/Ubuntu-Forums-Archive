---
title: "digital Cam Corder recommendation ..."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-08-25
Anyone recommend a reasonably priced digital Cam Corder that will work with Ubuntu?

Primary usage is to make on-line videos - like for YouTube.

Thanks

Carl

---

### Post by FakeOutdoorsman on 2007-08-26
While I can't give you a specific model, I recommend a standard mini-dv camcorder or a webcam that works on Ubuntu.  Avoid anything camcorder that records to an optical disc such as a DVD because they are notoriously hard to capture video from.  If you get a mini-dv camcorder you could use Kino to capture and edit your video.  You can then use ffmpeg or mencoder to convert it to h264 to upload to youtube.  There are also GUI/frontends to ffmpeg and mencoder such as [Vive]("http://vive.sourceforge.net/") or [WinFF]("http://biggmatt.com/winff/downloads/winff-version-0.3.html").  Kino is available in the Ubuntu repository.

I personally have no experience with webcams, but they would be cheaper and possibly easier once you get it to work.  The trick is getting it to work.

Useful site:
[Supported Webcams for Ubuntu]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")
[Easy video creation using only FOSS software]("http://www.linux.com/articles/58458")
[iPod Video Encoding]("https://help.ubuntu.com/community/iPodVideoEncoding") (has more good info and an ffmpeg ipod script that would work great for youtube)

Good Youtube file specs:
Video: h264, 320x240, 29.97 fps, minimum 512k bitrate, two pass
Audio: aac or mp3, mono, 96k

---

### Post by anewguy on 2007-08-26
A "crazy" thing you can also do and keep your costs down to about $30 - $50 is to buy one of the "one time use" digital camcorders at a certain drug store chain (don't know if I'm allowed to mentioned it) and then convert it to be downloadable and reusable.  There are quite a few sites on the net about this, and this includes the software to use in Linux.  I'm planning that as one of my over the winter projects just for the heck of it to see how it works out.:)

---

