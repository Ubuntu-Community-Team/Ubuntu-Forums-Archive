---
title: "how to register a video"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by jrev on 2007-08-25
Hi all,

I don't have broad band so it's difficult for me to listen to a video on line.

and I don't know how to register a video into my /home 

Maybe you let me know how you do that ...

For example : [http://www.youtube.com/watch?v=EytuaK04llw](http://www.youtube.com/watch?v=EytuaK04llw)

Thanks in advance

---

### Post by henriette_holm on 2007-08-25
Hi. I'm sorry but I can't help you. I have no idea if you can download YouTube videos. Anyone?

/Henriette

---

### Post by Lord Illidan on 2007-08-25
A simple "download + youtube" in google would do wonders. Try this link for starters.

Yes, you can download them. As for playback, I recommend mplayer.

---

### Post by ridgeland on 2007-08-25
I used Linux-Google for "save utube to hard drive"
I followed the link in
[http://mag.mypclinuxos.com/html/Issues/200705/page09.html](http://mag.mypclinuxos.com/html/Issues/200705/page09.html)
I found the file using Nautilus,
it was in 
/home/myusername/.mozilla/firefox/stuff.default/Cache
Unlike the help link there was no .swf extension but the file type was a Flash Video.  I just right click it and say use mplayer and it plays.  I could copy to a safe place to keep for later.

Edit: Interesting.  I viewed a second clip and it did not show in /home but rather in /tmp.  Search at least those two places.

---

### Post by jrev on 2007-08-25
Hello, Thanks for the replies.

I downloaded the file OK, but neither VLC nor Mplayer can read it.

The file is in my /home and named **EytuaK04llw.flv**

---

### Post by jordanmthomas on 2007-08-25
You could try something like this:
```
ffmpeg -i **EytuaK04llw.flv** -ab 56 -ar 22050 -b 500 -s 320×240 NEWFILENAME.mpg
```

and then watch NEWFILENAME.mpg

---

### Post by ridgeland on 2007-08-25
I had tried ffmpeg earlier.  My google-linux search lead to 
[http://youmakemedia.com/2006/10/13/converting-flv-to-mpeg-in-linux/](http://youmakemedia.com/2006/10/13/converting-flv-to-mpeg-in-linux/)
for converting flash video to mpg.  I used the same string
$ ffmpeg -i YouTubeTest -ab 56 -ar 22050 -b 500 -s 320x240 UTube.mpg
Observations:
I saw my YouTubeTest (the flash version) played fine with movie player (Totem) but with mplayer the audio was behind the video by a second or two.  My test video was someone acting/fake singing with a pop song.  It was obvious when the sound and lips were together or off.  Once converted to mpg both mplayer and totem played it fine, with video and audio in synch.  The flash was 7.5MB the mpg 13.2MB.

---

### Post by mcduck on 2007-08-26
I always just copy the file from /tmp to my home, and the run 'ffmpeg2theora filename"  to convert it to ogg video.

The file appears in /tmp only as long as the page with the flash is open in browser, after closing the page you have to search for the right file in browser's cache dir.

---

### Post by Dark Star on 2007-08-26
> **mcduck said:**
> I always just copy the file from /tmp to my home, and the run 'ffmpeg2theora filename"  to convert it to ogg video.

The file appears in /tmp only as long as the page with the flash is open in browser, after closing the page you have to search for the right file in browser's cache dir.

> **jordanmthomas said:**
> You could try something like this:
```
ffmpeg -i **EytuaK04llw.flv** -ab 56 -ar 22050 -b 500 -s 320×240 NEWFILENAME.mpg
```

and then watch NEWFILENAME.mpg

Thanks now I 'll download instead of watching it online :):lolflag:

---

### Post by jrev on 2007-08-26
How about this :

jean@aspire:~$ vlc '/home/jean/Desktop/ticker.stm' 
VLC media player 0.8.6 Janus
[00000301] mod demuxer error: failed to understand the file
[00000280] main playlist: playlist is empty

I am trying to download a file  from : [http://news.bbc.co.uk/](http://news.bbc.co.uk/)

But I got this instead

[http://www.enregistrersous.com/images/3/188751202020070826141325.html](http://www.enregistrersous.com/images/3/188751202020070826141325.html)

What is wrong with my Ubuntu ?

---

### Post by ridgeland on 2007-08-26
Try RealPlayer as the missing plugin.
I just watched a BBC clip about the fire in Greece using RealPlayer.
I think this is streaming content - not a file that that is visible in /tmp.
There are tools to capture streaming content, or rather make a copy of what your screen+audio is playing.
xvidcap might be able to do it.  There are more but I don't remember them.

---

### Post by jrev on 2007-08-26
I just got this one downloaded through Unplug and read via totem

---

### Post by ridgeland on 2007-08-26
"Unplug" is an unfortunate choice of names.  Google points everywhere but a package.  Where did you get it? (a French site is OK).

I did not find it with synaptics or Google.

---

