---
title: "How do I watch BBC News streams?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-04-27
Hi

I'm on a role, just got my ATI card working much better in Ubuntu. Well done all those involved.

Now I would like to watch BBC News. I tried this in Edgy using gxine. It seemed to gradually develop a glare over a few days and then I lost the gui.

So I'm back to see what the latest thinking is. Go gstreamer (just didn't work a few weeks back), go gxine (hopefully more stable now). What do you suggest?

Regards
Bob

---

### Post by whee on 2007-04-27
You could also try Kaffeine , VLC, mPlayer, mPlayer Plugin for Mozilla, Movie Player Totem and Totem Mediaplayer (all are available (in Feisty) under applications>add/remove)
I haven't watched streaming BBC with these apps yet though, but i suppose you can always try.

PS: Kaffeine is for KDE, but it also seems to work in Gnome.

---

### Post by wormser on 2007-04-27
> **bwallum said:**
> Hi

I'm on a role, just got my ATI card working much better in Ubuntu. Well done all those involved.

Now I would like to watch BBC News. I tried this in Edgy using gxine. It seemed to gradually develop a glare over a few days and then I lost the gui.

So I'm back to see what the latest thinking is. Go gstreamer (just didn't work a few weeks back), go gxine (hopefully more stable now). What do you suggest?

Regards
Bob

I have had a lot of success with mplayer.  Post a link of one of the streams and I will check if it works.  To set up mplayer and codecs follow this [guide]("http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html").
You will also have to remove the totem firefox plugin.

```
sudo apt-get remove totem-mozilla
```

---

### Post by bwallum on 2007-04-28
Here is a link. It works at this time. It is probably  temporary.

[http://news.bbc.co.uk/media/avdb/news/uk/video/91000/bb/91587_16x9_bb.asx]("http://news.bbc.co.uk/media/avdb/news/uk/video/91000/bb/91587_16x9_bb.asx")

Thanks for the help,

Regards
Bob

---

### Post by mr bob on 2007-05-03
I was having trouble with firefox plugins. But I finally got it to work with MPlayer plugin, installed with Automatix.

The BBC videos didn't work at first but I right clicked on the window and selected configure. 

It seemed to work once I selected "Use HTTP instead of RTSP".
I also selected X11 video output and alsa audio, although I don't know if that was necessary.

---

