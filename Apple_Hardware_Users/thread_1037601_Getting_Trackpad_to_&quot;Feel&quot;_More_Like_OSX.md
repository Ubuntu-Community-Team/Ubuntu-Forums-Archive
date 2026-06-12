---
title: "Getting Trackpad to &quot;Feel&quot; More Like OSX"
date: 2009-01-11
forum: Apple Hardware Users
---

### Post by rshnike on 2009-01-11
Hey everyone.

I've been playing around with the mouse/keyboard bindings in ubuntu to get them to act more like OSX (which I still use as my main OS) on my Macbook 1,1 in Ubuntu 8.10 i386.

I have all the bindings as I'd like them for the most part with two exceptions. Firstly I'd like to know if anyone is familiar with how in OSX, even though Cmd is used inside the GUI, when you drop into a Terminal, the terminal uses Ctrl, and if I could emulate that behavior in ubuntu even though I have swapped my Meta and Ctrl keys inside the GUI (which in the end I think I ended up doing using xmodmap).

Also, more importantly, if anyone has some suggestions on how to make the trackpad feel more like it does in OSX that would be most appreciated. I've tried messing around with the Acceleration and Sensitivity bars in the Mouse pane, but I still don't feel the smooth kind of motion that I get in OSX and suspect that perhaps messing with some pommed options are probably what would correct that. So if anyone has found some settings that work I'd really appreciate it.

Thanks!

Edit: I'm embarrassed.... didn't read the touchpad part of the FAQ carefully... gonna try out those settings.

---

### Post by bryonak on 2009-01-12
[Here's a thread]("http://ubuntuforums.org/showthread.php?t=1012714") on that, and [here's another one]("http://swiss.ubuntuforums.org/showthread.php?t=981474"). Just read the first page of both and you're ready to go.
Note that you can't get it to work *exactly* like the OSX touchpad because of implementation specifics.

Make sure there isn't anything "input device" related in your /etc/X11/xorg.conf

Also pommed is outdated in 8.10, you should use the Mactel repository (more info in the FAQ thread at the top of this forum).

---

