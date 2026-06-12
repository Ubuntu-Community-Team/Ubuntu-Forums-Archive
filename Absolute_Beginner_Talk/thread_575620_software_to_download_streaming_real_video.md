---
title: "software to download streaming real video"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-10-14
Hello there

i need a software by which i may download the streaming real video files from internet.

I watch UC Berkeley Webcasts online. But i wish to download them for offline viewing. 

In windows xp i used to use Net Transport to download streaming videos.

I have read on internet to use mplayer to download streaming videos.

i tried this but it didn't work. or may be i am doing it wrong way.

Can somebody please suggest any software to download the streaming videos in Ubuntu ?

---

### Post by Pumalite on 2007-10-14
[http://all-streaming-media.com/record-video-stream/all-streaming-video-recording-software.htm#recmp](http://all-streaming-media.com/record-video-stream/all-streaming-video-recording-software.htm#recmp)

---

### Post by cyneuron on 2007-10-14
as i had said i have tried using this command of mplayer but it doesn't work.

i even have all binary codecs available at mplayer website  copied to /usr/lib/win32. mplayer runs already downloaded real video file well, but neither it downloads, nor it streams.

for example to download a video of this url rtsp://169.229.131.16:554//events/publichealth//ph_20070504.rm?start=&end=

i give this command :

mplayer -dumpstream rtsp://169.229.131.16:554//events/publichealth//ph_20070504.rm?start=&end= /home/Documents/Downloads/first.rm


the output is this :

cyneuron@cyneuron:~$ mplayer -dumpstream rtsp://169.229.131.16:554//events/publichealth//ph_20070504.rm?start=&end= /home/Documents/Downloads/first.rm
[1] 31638
bash: /home/Documents/Downloads/first.rm: No such file or directory
cyneuron@cyneuron:~$ MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.73GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

please somebody help, i badly need a software to do this task....

---

### Post by Pumalite on 2007-10-14
Have you upgraded to the new firefox?. It comes with all these plugins out of the box practically.

---

### Post by Original Brownster on 2007-10-18
> **cyneuron said:**
> 

i give this command :

mplayer -dumpstream rtsp://169.229.131.16:554//events/publichealth//ph_20070504.rm?start=&end= /home/Documents/Downloads/first.rm


the output is this :

cyneuron@cyneuron:~$ mplayer -dumpstream rtsp://169.229.131.16:554//events/publichealth//ph_20070504.rm?start=&end= /home/Documents/Downloads/first.rm
[1] 31638
bash: /home/Documents/Downloads/first.rm: No such file or directory

please somebody help, i badly need a software to do this task....

Hi,
I think you missed part of the command (-dumpfile) you need :

mplayer -dumpstream rtsp://169.229.131.16:554//events/publichealth//ph_20070504.rm?start=&end= -dumpfile  /home/Documents/Downloads/first.rm

You might be interested in a small program I've written called Streambank that downloads real media streams, it's still in development but it does work, you can download it [here]("http://originalbrownster.awardspace.com/")

---

