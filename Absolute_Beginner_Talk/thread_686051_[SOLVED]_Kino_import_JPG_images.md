---
title: "[SOLVED] Kino import JPG images"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by CommanderBob on 2008-02-02
I want to make a video with video and still images. Kino is the most stable video editing software I have seen (or have been able to get to work). The only problem is I don't know how to import still images. I have a lot of JPG I want in the video. When I drag them it says they are not DV and asks to convert it. If I say yes it says Importing... and never changes for over a half hour for one image, after that I give up. How do I do this?
Thanks,
Justin
:popcorn:

---

### Post by kidcharles on 2008-02-02
Okay, I found a way to create an mpeg movie of arbitrary length from a single jpeg file. Install the following packages:

```
sudo apt-get install kipi-plugins mjpegtools
```

(I tried to do this originally with just installing kipi-plugins, but it requires commands in mjpegtools and didn't work. Obviously mjpegtools should be a dependency of kipi-plugins but isn't)

The command structure is:

```
images2mpg -d <duration in seconds> -o outputfilename.mpg -i inputfilename.jpg
```

I guess from there you need to convert to DV from mpeg, but that should get you started.

---

### Post by kidcharles on 2008-02-02
It looks like Kino will automatically convert files produced using the method I described, but I've learned you must have the package 'ffmpeg' installed for this to work properly, which is yet another dependency problem in the repositories!

```
sudo apt-get install ffmpeg
```

---

### Post by CommanderBob on 2008-02-07
Sorry for the late reply. 

Thanks a lot,
This is a lot easier than I hoped! Works great.

One more thing, I have 25 JPG images. Is there a way to do more than one at a time? Maybe with a script? (I only know how to make very basic scripts)

Justin

---

### Post by CommanderBob on 2008-02-07
Never mind. I found a nice GUI that allows you to do a lot. It is based on images2mpg.
[http://www.downloadtube.com/Linux/Multimedia/Fuoco-Tools-download.html]("http://www.downloadtube.com/Linux/Multimedia/Fuoco-Tools-download.html")

---

### Post by yaknowwat on 2008-02-07
If your someone who likes to import images into a video
I would suggest Kdenlive
It's easy to use though I'll admit it's sort of glitchy (like it will freeze instead of showing transitions to save processing power though you can see the transition frame by frame if you wanted.) it might  be because I'm using the GNOME Desktop Enviroment and its made for KDE so its using the KDE Core or something similar.

---

### Post by CommanderBob on 2008-02-07
I was using Kdenlive but it would crash too often for me. Also I did finally get something together and when I exported it the audio was off. I am using GNOME too.

---

### Post by Creative2 on 2008-02-08
> **CommanderBob said:**
> Never mind. I found a nice GUI that allows you to do a lot. It is based on images2mpg.
[http://www.downloadtube.com/Linux/Multimedia/Fuoco-Tools-download.html]("http://www.downloadtube.com/Linux/Multimedia/Fuoco-Tools-download.html")

why that link when there is official topic here :
[http://fuocotools.byethost13.com/index.php](http://fuocotools.byethost13.com/index.php)

and here
[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

---

### Post by CommanderBob on 2008-02-08
That is what I found when I looked on Goggle. :)

---

