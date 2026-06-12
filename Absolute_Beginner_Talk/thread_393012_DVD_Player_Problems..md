---
title: "DVD Player Problems."
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by RizingDamp on 2007-03-25
Hi All,

Well I am really new to Ubuntu(Dapper Drake) but Im sticking with it even though at the moment everything seems to be a bit of a struggle for me.  Im basically at the moment popping a DVD in to see if it will play and I wasnt surprised  having read forum posts that it doesnt straight away, it needs some tweaking.

Well from what I understand so far is that when looking at its icon in the Computer window it shows it as a disc so Im thinking its mounted correctly.

I used Synaptic Package Manager and ticked the boxes and then opened a terminal and ran this command.....

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

But then I get this error.....

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.10-pitfdll


Any help guys would be very grateful :) 


Andy,

Ps Im a determined guy so I won`t give up:)

---

### Post by euler_fan on 2007-03-25
I can suggest three options:

1) you mis-spelled the name. But I figure you double checked that, so that probably isn't the problem.
2) you don't have enough repos enabled. Makes sure they're all turned on. Universe, multiverse, everything.

3) Go [here to install VLC]("http://www.videolan.org/vlc/download-ubuntu.html"). It is a great program and I swear by it. I tried to play a protected DVD without libdvdcss2 and it actually played the dvd--scrambled, but still :) VLC will should handle all your other files as well.

Good luck!

---

### Post by the8thstar on 2007-03-28
Hey there,

I came across a puzzling problem after installing VLC and the Win32 and dvdlibcss2 libs last night. When playing a DVD in VLC, the sound plays fine but I don't get the image most of the time.

If I get the image, whenever I fast forward or skip to a new chapter, the screen goes black again.

Do you have any ideas why?

---

