---
title: "LAME command for mp3 encoding please."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by paker on 2008-03-14
I have numerous WAV files (voice recordings) stored in 3 DVDs. I want to convert them to mp3. I have been using Grip for CD ripping, but Grip doesn't recognize WAV files on DVD. I don't mind terminal line commands. Can someone help me how to do mass conversion? Thanks.

In other words, what would be the ubuntu equivalent of the following Windows command?
**lame -V 7 --vbr-new  F:\*.wav C:\MyMusic\*.mp3  **

---

### Post by joshrobinson on 2008-03-14
```
sudo apt-get install ffmpeg
```

then use

```
ffmpeg -i input.wav -ac 2 -ab 64 output.mp3
```

change the 64 to a different bitrate if you want, say 128 or 192

---

### Post by paker on 2008-03-15
ffmpeg is already installed. Please show me how to point at the wave files on DVD in ubuntu. Thanks.

---

### Post by joshrobinson on 2008-03-15
just open a terminal and do this

```
cd /media
```
then 
```
ls
```

it will either have a cdrom or dvd listed
whatever one it is
use cd then the directory name
then do your ffmpeg commands

---

### Post by logos34 on 2008-03-15
But looking at the ffmpgeg man page, doesn't -ab (audio bitrate) give you average bitrate?

I mean, if you want **variable** bitrate vbr-new, you could do:

sudo apt-get install lame

lame -V 7 --vbr-new /media/cdrom0/*.wav

that'll convert all the wavs on the dvd to mp3s with same title

---

### Post by joshrobinson on 2008-03-15
> **logos34 said:**
> But looking at the ffmpgeg man page, doesn't -ab (audio bitrate) give you average bitrate?

I mean, if you want **variable** bitrate vbr-new, you could do:

sudo apt-get install lame

lame -V 7 --vbr-new /media/cdrom0/*.wav

that'll convert all the wavs on the dvd to mp3s with same title

that should work also, the op said they were voice recordings, so i didnt think a variable bitrate was really needed

---

### Post by logos34 on 2008-03-15
> **joshrobinson said:**
> that should work also, the op said they were voice recordings, so i didnt think a variable bitrate was really needed

missed that..yeah, you're right, hardly matters

---

