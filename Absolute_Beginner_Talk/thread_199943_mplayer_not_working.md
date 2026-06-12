---
title: "mplayer not working"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by stone80 on 2006-06-19
i installed automatix and everything seems to work fine, except for the mplayer, i get audio, but no video, what is wrong with it?

---

### Post by uzi09 on 2006-06-19
have u already installed all the proper codecs?
pls c this guide (for dapper, they have a link for breezy as well in the beginning):
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

also can you tell us what type of video you're playing and what version of ubuntu you're running?

thanks

---

### Post by not_yet on 2006-06-19
try running it from the terminal and see what error messages it reports

---

### Post by stone80 on 2006-06-19
[QUOTE=not_yet]try running it from the terminal and see what error messages it reports[/QUOTE]

i typed in mplayer in the terminal and i didn't get any error messages.

---

### Post by Perfect Storm on 2006-06-19
```
gmplayer
```

---

### Post by uzi09 on 2006-06-19
did you try to play anything?

try:
gmplayer video_file

where you sub in a video file for "video_file".
if that doesn't work, try just opening up gmplayer, right click on the application (not the window where you view the movie) and go to preferences. go to the video tab and try to change it to x11.

let us know what you come up with.

oh also, how did you install mplayer? through repos? or deb? or compiled?

---

### Post by stone80 on 2006-06-19
try:
gmplayer video_file


ok did that, here's what i got. 

> Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.


---

### Post by uzi09 on 2006-06-19
that's odd. try this:

sudo gmplayer video_file

also, can you please tell us how you installed it? it could have been installed incorrectly and you can reinstall very easily using synaptic saving us a lotta hassle :D

---

### Post by stone80 on 2006-06-19
[QUOTE=uzi09]that's odd. try this:

sudo gmplayer video_file

also, can you please tell us how you installed it? it could have been installed incorrectly and you can reinstall very easily using synaptic saving us a lotta hassle :D[/QUOTE]

i went to the automatix website and downloaded it from there and ran the install.

---

### Post by stone80 on 2006-06-19
[QUOTE=uzi09]that's odd. try this:

sudo gmplayer video_file

also, can you please tell us how you installed it? it could have been installed incorrectly and you can reinstall very easily using synaptic saving us a lotta hassle :D[/QUOTE]


ok tried that and got this...

> 91 audio & 204 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

---

### Post by stone80 on 2006-06-19
can anyone help me out? when i go somewhere like thatvideosite.com i get audio but no video.

---

### Post by uzi09 on 2006-06-19
whoa, k we're still a long way from talking about embeded videos...are regular videos off your system working properly?

can you try an mpeg video?
also try avi's and wmv's if you can.

---

