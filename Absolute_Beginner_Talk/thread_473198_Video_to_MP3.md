---
title: "Video to MP3"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Kymac on 2007-06-13
Is there a program in ubuntu that will allow me to easily convert video files to mp3s, to be played on an mp3 player.  I know there are some windows programs i can dish out money for, but I don't really 'NEED' it, it would just be nice to have.

---

### Post by avik on 2007-06-14
Are you sure you want to convert a video to an mp3, thereby losing the video and keeping only the sound?  Maybe you want to convert a format playable on something like a video iPod?  That would be the mp4 format.

Either way, I know that vlc has a facility to do this conversion (File->Wizard), though that's not the best option.  Still, I've converted video in thi s way before, so it works.

---

### Post by Kymac on 2007-06-18
Ok, Thank You.

And yes, I do want to convert it, I want to play some audio while I am at a warehouse, and there's a few videos that would be cool to use.

---

### Post by jjf on 2007-06-19
I use ffmpeg for this all the time.  I'll download a music video I like with the Firefox extension VideoDownloader.  It comes in .FLV format.  I just want the song, so I'll convert it to mp3.  

Get to your command prompt, navigate to the directory where your video is stored, then:

```
ffmpeg -i original_file.ext my_song.mp3
```

---

### Post by katringa on 2007-06-22
> **jjf said:**
> I use ffmpeg for this all the time.  I'll download a music video I like with the Firefox extension VideoDownloader.  It comes in .FLV format.  I just want the song, so I'll convert it to mp3.  

Get to your command prompt, navigate to the directory where your video is stored, then:

```
ffmpeg -i original_file.ext my_song.mp3
```

Thank you very much! This worked perfectly for me, now I use it all the time :)

---

