---
title: "How can I convert flv to h.264?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by curiousnoob on 2007-12-15
Is there any way to convert flv files into h.264?

---

### Post by TheLions on 2007-12-15
try this on-line converter:
[URL="http://vixy.net/"]
http://vixy.net/[/URL]

---

### Post by curiousnoob on 2007-12-15
Any idea on how to get it to recognize the main window on this page?
[http://www.charlierose.com/shows/2006/12/08/2/a-conversation-with-comedian-stephen-colbert](http://www.charlierose.com/shows/2006/12/08/2/a-conversation-with-comedian-stephen-colbert)

---

### Post by TheLions on 2007-12-16
sorry but no, that page works only on youtube! :(

---

### Post by JillSwift on 2007-12-16
ffmpeg can do that.

---

### Post by Rhubarb on 2007-12-16
Firstly, you'll need to have mencoder installed:
```
sudo aptitude install mencoder
```

There are a few ways to get the flv video from a web page (firefox extentions, a few appliciations in the repositories like youtube-dl and clive).
In this particular case, watch the video here [http://www.charlierose.com/shows/2006/12/08/2/a-conversation-with-comedian-stephen-colbert](http://www.charlierose.com/shows/2006/12/08/2/a-conversation-with-comedian-stephen-colbert)
let it load up completely, once the full video is buffered in (don't close firefox!), navigate to /tmp/ and you'll see a flv file there, copy it to your home directory as input.flv

Now to convert it into a h264 video:-
In this example your flv file is named "input.flv", it will create the h264 video as "output.avi"
```
mencoder input.flv -o output.avi -ovc x264 -x264encopts bitrate=500 -oac mp3lame -lameopts abr:br=52
```

If you have a dual core system, and want a faster encoding, then use this:
```
mencoder input.flv -o output.avi -ovc x264 -x264encopts threads=3:bitrate=500 -oac mp3lame -lameopts abr:br=52
```

---

### Post by curiousnoob on 2007-12-16
> **Rhubarb said:**
> Firstly, you'll need to have mencoder installed:
```
sudo aptitude install mencoder
```

There are a few ways to get the flv video from a web page (firefox extentions, a few appliciations in the repositories like youtube-dl and clive).
In this particular case, watch the video here [http://www.charlierose.com/shows/2006/12/08/2/a-conversation-with-comedian-stephen-colbert](http://www.charlierose.com/shows/2006/12/08/2/a-conversation-with-comedian-stephen-colbert)
let it load up completely, once the full video is buffered in (don't close firefox!), navigate to /tmp/ and you'll see a flv file there, copy it to your home directory as input.flv

Now to convert it into a h264 video:-
In this example your flv file is named "input.flv", it will create the h264 video as "output.avi"
```
mencoder input.flv -o output.avi -ovc x264 -x264encopts bitrate=500 -oac mp3lame -lameopts abr:br=52
```

If you have a dual core system, and want a faster encoding, then use this:
```
mencoder input.flv -o output.avi -ovc x264 -x264encopts threads=3:bitrate=500 -oac mp3lame -lameopts abr:br=52
```

When I try this I get the following error.
mencoder: error while loading shared libraries: liblzo.so.1: cannot open shared object file: No such file or directory

---

### Post by Rhubarb on 2007-12-17
That's odd, liblzo1 is a dependency of mencoder, so it should have been installed when you installed mencoder.
Check in Synaptic Package Manager if all of mencoder and it's dependencies are installed (you may have to re-install mencoder within synaptic).

---

### Post by stooshbunutu on 2008-02-04
for .flv files there is a realy easy porgram for converting to most other files, I'm pretty sure h.264 is one of them, I use [winff]("http://biggmatt.com/files/winff-0.33-i386.deb") that uses the [ffmpeg]("http://packages.ubuntu.com/gutsy/graphics/ffmpeg") codec to covert the file.

hope this helps you, it works great for me.:)

---

