---
title: "installing restricted formats"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by jackss on 2006-03-24
i want to watch mpg video and when i try
to sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg
i get this error
sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-plugins: Depends: gstreamer0.8-a52dec (>= 0.8.11) but it is not going to be installed

please help me

---

### Post by taurus on 2006-03-24
Try installing the codecs, win32codecs, and you should be able to watch pretty much any video format with mplayer, xine, vlc, etc...

---

### Post by engla on 2006-03-24
Hey

Those plugins come from the package repositories universe and multiverse, som kind of "extras" pools for ubuntu. You need to enable these reps by yourself.

Here is a link to [Enabling repositories howto]("http://www.psychocats.net/linux/sources.php")

---

