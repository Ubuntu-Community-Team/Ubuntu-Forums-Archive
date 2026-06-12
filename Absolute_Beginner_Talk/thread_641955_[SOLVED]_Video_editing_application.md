---
title: "[SOLVED] Video editing application"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-12-16
I'm trying to find some video editing apps that will do what I need.  Avidemux works ok but with my new webcam it is not taking the audio correctly.  I can watch the videos raw and everything is synched up but when I use avidemux to compress it's throwing the sound off by about 1 second.  It also will not load the audio for me to edit so I can't really cut out dead air.

I also have KINO which will not load my raw avi files or convert them.

cinerella looks promising but it's 64 bit and I can't compile it.

any suggestions, right now I'm just uploading my videos to jumpcut to edit them for time and then download them again and then upload them again to youtube.

---

### Post by FakeOutdoorsman on 2007-12-16
What kind of errors do you get with Kino?  Open it through a terminal to see more errors.  It should be able to load just about any type of dv file.

Maybe [LiVES]("http://lives.sourceforge.net/") will work for you.

---

### Post by siciliancasanova on 2007-12-16
This is the response when I run it through the terminal... 

```

> setting video preview size to 384x288
>> Starting Editor
>>> iec61883Writer::iec61883Writer port 0 channel 63
>> Creating undo/redo buffer
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
/usr/share/kino/scripts/import/media.sh: 74: ffmpeg: not found
>> Leaving Editor
>> Left Editor
>> Starting Editor
>>> iec61883Writer::iec61883Writer port 0 channel 63

```

The error that is in the GUI that pops up is:
```
"/home/anthony/Desktop/video.avi" is not a DV file. Do you want to import it?
```

followed by:

```
Failed to load media file "/home/anthony/Desktop/video.avi.dv"
```

Is this little bit here " ffmpeg: not found" telling me that I forgot to install something?

---

### Post by FakeOutdoorsman on 2007-12-16
I think you're on to something.  Try installing ffmpeg.  I would use ffmpeg from the Medibuntu repositroy since it is a newer version and has more functionality.  Check this out: [iPod Video Encoding]("https://help.ubuntu.com/community/iPodVideoEncoding#head-718248d42e047c1bdeda6e7e26665b1103b6b00f") on Ubuntu Wiki.  Tells all about how to install Medibuntu ffmpeg.

---

### Post by siciliancasanova on 2007-12-16
Sounds good, thanks for the help.  I just redid my youtube video so it's under 10 min and uploaded it but I've got an hour long one I need to get under 10 min so I will keep working on this tomorrow.  Thanks for the help.

---

### Post by siciliancasanova on 2007-12-16
Yeah I just compiled ffmpeg and all is good now.  Thanks.

---

