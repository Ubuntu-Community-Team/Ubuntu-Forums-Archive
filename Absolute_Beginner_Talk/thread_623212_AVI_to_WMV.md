---
title: "AVI to WMV???"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by freqk on 2007-11-25
I just want to convert an AVI video to a WMV video...
I tried this:
```
mencoder Koyaanisqatsi.avi -ofps 23.976 -ovc lavc -oac copy -o Koyaanisqatsi.wmv
```
It "worked" but the video was all "dirty" bits of the last frames would stay there. Hard to describe.

Need help ASAP.

---

### Post by High Camp on 2007-11-25
Try [www.media-convert.com](www.media-convert.com)

Quick and nothing to install. If not that then look into winff (it's in the repos I think).

Hope that helps,

---

### Post by LinuxDude... on 2007-11-26
Hi 

Try and use ffmpeg, I use it and it makes the *.WMV output look watchable.

ffmpeg -i "********.avi" -b 1000k -vcodec wmv2 -ar 44100 -acodec wmav2 "*****.wmv" 

But does anyone know how to upgrade this to High Definition WMV output?

:D
Cheers

LinuxDude...

---

### Post by Slakker on 2007-11-26
Why do you guys want .wmv videos, anyway?

---

### Post by LinuxDude... on 2007-11-27
My reason is I would like to watch :popcorn: all film content on my xbox360, makes my life easier, but it does mean i spend a lot of time converting dvd ect to HD WMV, I would like to find another solution, but nothing other then this has worked for me so far...:confused:

---

### Post by mahiyar on 2007-11-27
Try ConverIT, not only will it give almost all the possible file formats conversions, but a thread is on about it where the developer will help in case of any problems.

---

### Post by LinuxDude... on 2007-11-27
Cool thank you :), i will give it a try.

---

### Post by LinuxDude... on 2007-11-27
No ConverIT does not do WMV conversions very well, but i have found the command that makes Mencoder do the best encode of the video file.

FreqK could use this.

mencoder -oac copy -ovc copy *******.avi -o *****.wmv

---

### Post by Creative2 on 2007-11-28
omg your command line doesnt  build a wmv.....it change only the capsule\ container but it isn't a wmv you have copy video and audio stream ....is equal to change the name of the file....

stuff.avi rename stuff.wmv

to build a wmv you must use wmv codec and wma for audioo codec 

the problem is wmv is not supported very well i know ffmpeg can encode into wmv2 at the top and i think it has problem with wma codec because there is only decoder and not ENCODER i think

edit i have checked and in the true ffmpeg can do wmav2 like someone has said  unluckly the quality is low....

so to encode a wmv , FOR NOW, the top is this 


ffmpeg -i INPUT  -b 700k -vcodec wmv2 -ar 44100 -acodec wmav2   OUTPUT.WMV

---

### Post by qqzhenyi on 2007-11-28
Use MediaCoder ([http://mediacoder.sourceforge.net/](http://mediacoder.sourceforge.net/)) if you have Windows, else use it with wine.

---

### Post by LinuxDude... on 2007-11-28
I tried this, and the audio is fine, but the Video is very very graining you can actually see the pixels, I tried two files with the same results.

ffmpeg -i INPUT -b 700k -vcodec wmv2 -ar 44100 -acodec wmav2 OUTPUT.WMV


thanks for helping though.

---

