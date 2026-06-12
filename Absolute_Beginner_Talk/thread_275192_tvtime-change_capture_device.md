---
title: "tvtime-change capture device"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by gu014 on 2006-10-11
Hello,
i am attempting to get tvtime configured with a hauppauge 150. when i run 'tvtime' i get the blue screen which reads in the middle, No Signal' and at the bottom left no such file
cannot open capture device /dev/video1.

This error message is obvious since the capture device is at /dev/video0

Tvtime states in the man page that it will default to /dev/video0 and the config file at /etc/tvtime/tvtime.xml reads:
<!-- This sets the default capture device to use. -->
  <option name="V4LDevice" value="/dev/video0"/>

As it should. 

tvtime --device=/dev/video0 -S
Produces the same result with the error message in console 
"videoinput: Card failed to allocate capture buffers: Invalid argument
"

I do not know where to go from here and was hoping i could gain some help.  Any would be appreciated. thank you.

---

