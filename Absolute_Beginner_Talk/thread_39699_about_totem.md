---
title: "about totem"
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by k4rp0r on 2005-06-06
i have this problem with totem mediaplayer. when im trying to play something it says that i dont have decoders to handle the stream in the path home/k4rp0r/Desktop/linux.avi etc. and have to install the corresponding plugins. What should i do to solve this problem?

---

### Post by kozmo on 2005-06-06
[QUOTE=k4rp0r]i have this problem with totem mediaplayer. when im trying to play something it says that i dont have decoders to handle the stream in the path home/k4rp0r/Desktop/linux.avi etc. and have to install the corresponding plugins. What should i do to solve this problem?[/QUOTE]
They removed the Mallarat repository from the [Ubuntu User Guide](http://www.ubuntuguide.org/#extrarepositories) , which is where all those codecs were. 

Eventually, they will port them over to the backports -- hopefully soon. This is becoming a very common request on this board.

---

### Post by az on 2005-06-06
Enable universe and install gstreamer0.8-plugins and gstreamer0.8-ffmpeg


You should be good to go.  The marillat stuff is for the widows codecs and mplayer.  You are using totem with gstreamer.

It is possible to use totem with xine and use the windows codecs, but that is not your question.

---

### Post by kozmo on 2005-06-06
[QUOTE=azz]Enable universe and install gstreamer0.8-plugins and gstreamer0.8-ffmpeg


You should be good to go.  The marillat stuff is for the widows codecs and mplayer.  You are using totem with gstreamer.

It is possible to use totem with xine and use the windows codecs, but that is not your question.[/QUOTE]
I have the universe repository and I get the following message:

```
jimmy@scooter:~$ sudo apt-get install gstreamer0.8-plugins
Password:
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
jimmy@scooter:~$
```

---

### Post by az on 2005-06-06
[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-plugins](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-plugins)

It is is universe.

sudo apt-get update?

---

### Post by Kyral on 2005-06-07
Seriously the fastest way to get almost all common video codecs going is to apt-get xine-ui, totem-xine, and w32codecs.

---

