---
title: "[SOLVED] .flv to .mp3"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2008-02-24
I downloaded a video (about 60 mins long; it's a concert) off of youtube.  It is currently in .flv format.  I've tried to put it into Sound Converter but the app won't run.  It trys but after a while it says "force quit" before eventually converting the beginning of the file to .ogg.  I want to convert it to .mp3 so I can play it in any stereo, etc. What do you recommend?

Thanks.

---

### Post by InfinityCircuit on 2008-02-24
```
sudo apt-get install ecasound mpg123 lame ffmpeg
```

Restart your computer for ecasound to work correctly.

```

ffmpeg -i *.flv -f mp3 -vn -acodec copy /tmp/temp.mp3
ecasound -i /tmp/temp.mp3 -etf:8 -o ~/mysong.mp3
rm -f /tmp/temp.mp3

```

See [http://ubuntuforums.org/showthread.php?t=328347&page=7](http://ubuntuforums.org/showthread.php?t=328347&page=7)

---

### Post by yabbadabbadont on 2008-02-24
Edit: Too slow.

---

### Post by AnLGP on 2008-02-24
I don't understand the second code in your post, infinity.  I looked at the thread you linked and didn't understand that, either.

---

### Post by mridkash on 2008-02-24
try using this simple command, it works for me,

```
ffmpeg -i /path/to/video.flv /path/to/song.mp3
```

---

### Post by harold4 on 2008-02-24
> **AnLGP said:**
> I don't understand the second code in your post, infinity.  I looked at the thread you linked and didn't understand that, either.

First line gets you the audio
Second line converts the mono audio into simulated stereo
Third line removes temp

Link points out the source of this info

---

### Post by zvacet on 2008-02-24
Try [this.](http://pacpl.sourceforge.net/) It works from terminal,but if you have Amarok installed you will have GUI.

---

### Post by TomDaBomb2u on 2008-06-11
Thanks mridkash, that worked fine for me!

---

### Post by twothird on 2008-06-16
yea, but that way you lose a lot of the quality (the sound is encoded then in 64kbits)

```
ffmpeg -i /path/to/video.flv -ac 2 -ar 44100 -ab 320 /path/to/audio.mp3
```

probably that is not the best way to do it (as im not using the '-acodec *codec*), but i managed to get quite good quality with this.
-ac is number of audio channels
-ar is samplerate
-ab is bitrate

---

### Post by begemot. on 2008-06-27
**InfinityCircuit**

Thank You so much!
I couldn't find any link to download mp3 with soundtrack to film "The Jacket" (Fleeting Smile by Roger Eno), after long search, i found only flv-player with this song.
But, my FireFox 3.0 with DownloadHelper addon did the job to get it on hdd, and your advice did the rest.

Thanks A LOT again!

---

### Post by Jackelope on 2008-06-28
I've had great success with WinFF. I don't think it's in the repositories but you can find it online and get the .deb package. Despite the name, its not just for windows. Both soundconverter and a few scripts gave me trouble, but this app was extremely simple. Worth a download.

---

### Post by edoviak on 2008-06-28
I used the instructions at [**Anand Sengupta's blog**](http://anandsengupta.blogspot.com/2008/04/convert-flash-video-flv-to-mp3-in-linux.html) to create a script which automates the process.


Start with: 
[b]
# apt-get install ffmpeg lame
[/b]
Then create the script below in: **/usr/bin/flv-to-mp3** and make it executable with:
[b]
# chmod a+x /usr/bin/flv-to-mp3
[/b]
Then you'll be able to run the command:
[b]
$ flv-to-mp3 myfile.flv
[/b] 
from any directory to convert a file from FLV to MP3.


```

#!/bin/sh
# this script should convert files from FLV to WAV and then to MP3
echo " "
echo "  Welcome to FLV to MP3 converter!  version 0.1"
echo " "
infile_name="$@"
# exit if the user did not enter anything:
if [ -z "$infile_name" ]; then
    echo " "
    echo "You did not tell me the file name, so I will exit now."
    echo " "
    exit
fi
echo " "
ffmpeg -i "$infile_name" -acodec pcm_s16le -ac 2 -ab 128k -vn -y "${infile_name%.flv}.wav"
lame --preset cd "${infile_name%.flv}.wav" "${infile_name%.flv}.mp3"
rm "${infile_name%.flv}.wav"
echo " "
echo "OK. I'm done! Have fun!"
echo " "
exit

```

---

### Post by franket on 2008-07-05
Thank you edoviak.

today I want to convert .flv to mp3 and I Search found your post.

I try and work for me :)

---

