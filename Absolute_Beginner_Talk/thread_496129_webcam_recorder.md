---
title: "webcam recorder"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by AuroraManson on 2007-07-08
Hello I am looking for a good webcam recorder, and then another program to format and edit them for recording video from my webcam and editing it for youtube.

---

### Post by isaacj87 on 2007-07-08
Hello,

Check out the programs in the repos.

Go to Applications->Add/Remove

Widen the search to "all available applications"
and then choose the sound and video category...I think you might find what you need in there. :)

---

### Post by AuroraManson on 2007-07-08
Sigh

I have

nothing

---

### Post by BCtom on 2007-07-21
Hi AuroraManson,

I'm not much of an expert either on Ubuntu, but I did manage to get my Webcam working after a whole lot of persuasion. I can only capture stills, then edit them into videos afterwards. Regrettably, I too have not being successful in finding a way to stream video from a USB Webcam. (There are rumors that say you can?????)

The method I use for capturing stills into video is using a capture program called Camstream (easy to find and install) and Mainactor for editing them into a video. Mainactor is, by the way, a none GNU program, and as such, it costs about $200.00 to buy--but it's worth because it runs on Linux nicely! If you don't want to spend money, try Stopmotion, does the same thing, transforms stills into a motion file.

I find it funny that during my MS Windows days, I could find Webcam programs by the hundreds that would capture video, but not create stills to be saved on my HD in sequential order, yet in Linux, no problem--just can't get it to stream video? 

I hope you get to your goal!

Tom

---

### Post by BCtom on 2007-07-21
I just did a search for capturing video from a webcam, and found a program called "Streamer" which can be download from Synaptic. Although it found my webcam with no problems, it was only able to capture multiple images. Again, I needed to convert the images into a video because the video option in Streamer would not work for me.

The command line I used:

[html]streamer -t 0:10 -r 15 -o XXX0000.jpeg[/html]The theory here is that: time=t (10 sec) @ r= frame per second (15fps) 0=file# (10 x 15 = 150 images called XXX#.jpeg).

<-------------------------------------------------------------------------------->
I'm adding more to this post:

I just found this.

I managed to capture streaming video with my webcam using mecoder. 

I tried this command line and got some success.

[html] mencoder tv:// -tv driver=v4l:width=352:height=288:device=/dev/video0 -ovc lavc -fps 15 -o webcam.avi[/html]

Try these web sites for more information.

[help.ubuntu.community/Webcam]("https://help.ubuntu.com/community/Webcam")

[help.ubuntu.community/MEncoder]("https://help.ubuntu.com/community/MEncoder")

[mplayer head quarters en/encoding-guide]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html")

---

