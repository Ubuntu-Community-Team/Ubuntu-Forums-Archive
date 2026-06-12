---
title: "[SOLVED] URGENT: Weird avi file"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by marufaberlin on 2008-03-10
Hi, I've just encountered a very weird avi file, that can't be played with any media player. it is a video/x-avi-unknown mime file. what dp? Ive got to get this problem solved in the next 1/2 hour.

---

### Post by smurphy_it on 2008-03-10
Did you download the codecs to support divx, xvid ?

That might be your issue.  You have to add in the gstreamer-ugly, gstreamer-bad for sure.... There is probably a script for doing this, but my main machine isn't here, so I can't look it up.

It's something like...

in a terminal type sudo apt-get install gstreamer-plugins-bad gstreamer-plugins-ugly

---

### Post by Stevko on 2008-03-10
If it cannot be played in VLC and it cannot be played in mplayer, then I would suspect, that it is not really avi file. Try to run "file " command on your avi file.
```

file your_avi_file.avi

```
It will show you, what file it really is.
Examples:
For my_avi_file.avi it says:
my_avi_file.avi: RIFF (little-endian) data, AVI, 640 x 480, 25.00 fps, video: DivX 5, audio: MPEG-1 Layer 3 (stereo, 44100 Hz)
or for another.avi it says:
another.avi: RIFF (little-endian) data, AVI, 640 x 272, 23.98 fps, video: XviD, audio: Dolby AC3 (6 channels, 48000 Hz)
for files it does not know it says "data".

You will find out what kind of file it is and then try to use appropriate player. However if it is not really video file, then you hould try to get the file again.

---

### Post by marufaberlin on 2008-03-10
Nah... I don't have it in my repositories. And that machine isn't connected to the outside world, other than through a monitor, a keyboard and a mouse (and a few usb ports)

---

### Post by marufaberlin on 2008-03-10
file gives me RIFF (little-endian) data, AVI, 720 x 576, 25.00 fs, video, uncompressed

---

### Post by solitaire on 2008-03-10
How big is this AVI file?
How long do you think the file should play for? is it a 30 min video or is it a 1-2 min video?

---

### Post by buried on 2008-03-10
Is it truly a AVI file?

---

### Post by marufaberlin on 2008-03-10
Yes it is truly an avi file. But I have three of them. They're all less than a minute.

File one: 95.0 MB
File two: 36.5 MB
File three 61.8 MB

That's pretty big for an avi file.

PS.: nice location, buried

---

### Post by marufaberlin on 2008-03-10
I'm sorry about the urgency, but thing is, I have to hold a presentation in a few hours time and have to have that finished by then. Can someone help, please???

---

### Post by dashnak on 2008-03-10
You could reencode them with avidemux.

---

### Post by solitaire on 2008-03-10
Sounds like the players don't like "Uncompressed" avi's

Onlt thing i can think of is to comress them into a diffrent type of AVI but I don't think you'd have the correct progs installed on the comp...

have you tried opening a movie player then drag one of the files onto the player? that might work insted of just clicking on the file to play it..

---

### Post by marufaberlin on 2008-03-10
No, that doesn't work. I might have the correct progs on my computer, what do I need? I suspect avidemux.

---

### Post by marufaberlin on 2008-03-10
How do I reencode using avidemux?

---

### Post by marufaberlin on 2008-03-10
Ok, I got so far as to downloading all the package files off the internet and installing them - with all the dependencies satisfied -. but what do I do now?

---

### Post by marufaberlin on 2008-03-10
Oh, I see avidemux has a GUI, I dind't know that.

---

### Post by marufaberlin on 2008-03-10
Ok, avidemux doesn't work. But thanks to you all.
 
EDIT:
avidemux _does_ work, I just messed up.

---

### Post by avik on 2008-03-11
> **marufaberlin said:**
> avidemux _does_ work, I just messed up.

I have the same problem.

Can you explain what you did?  I get a green video and even upon re-encoding it, all the frames are green.

---

### Post by marufaberlin on 2008-03-13
Ok, that's not what my problem was. I just didn't get it reencoded. I ran avidemux, opened the video, put my settings in the left panel, and then just saved again.

---

