---
title: "S-Video to a video file"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Craftycorner on 2006-12-10
I have a video capture card that shows beautiful video on TV-Time in S-Video format that is fed through my cable box to the computer.  MythTV is not what I want, as I have a cable box to set the channel and all that.  I just want the video put into video files, rather like WindowsXP's Nero video capture utility.](*,)

---

### Post by superm1 on 2006-12-10
Well if you are just looking for capturing to a file from a standard V4L device, cat /dev/video0 > ~/filename.mpg will capture to filename.mpg in your home directory.

Although, if you want to consider myth - you can get an external channel changer to handle doing the channel changing on your cable box.  If your cable box has firewire, you can use that. If it has an activated serial port, you can use that If none of the above, you can obtain an IR blaster.

---

### Post by Jose Catre-Vandis on 2006-12-10
something like this with mencoder/mplayer

To Capture Composite/Svideo Feed
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mencoder -tv norm=PAL:driver=v4l2:width=720:height=576:input=2:fps=25 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -vf crop=690:552:10:10 -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=16/9 -o capture.mpg

Notes:

input: 0=tuner, 1=composite, 2=Svideo

test crop requirements first and then enter figures after -vf crop or trial and error for correct aspect cropping

captures to mpeg2

To test for crop requirements on a file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mplayer test.avi -vf cropdetect

This then settles to give an output like this:

crop=688:448:2:54

enter these values as required

---

### Post by christhemonkey on 2006-12-10
> mencoder -tv norm=PAL:driver=v4l2:width=720:height=576:input=2: fps=25 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -vf crop=690:552:10:10 -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=80 00:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192 :aspect=16/9 -o capture.mpg

Thats a hell of a one liner!!

---

