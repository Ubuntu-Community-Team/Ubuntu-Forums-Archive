---
title: "Linux problems"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by ubntu350 on 2008-02-03
New to linux, I love the OS, but I have a few problems. 1 streaming video in firefox only works about 50% of the time, the other either locks up UBUNTU (gotta reboot) or doesn't do anything. Guessing I'm missing a plugin.  The other gripe is hang ups,  linux system seems to be full of them, every day I get hang ups, my hard disk spins for a half hour before I take off the battery and reboot.  Is this a hardware or software problem?

---

### Post by st33med on 2008-02-03
I'm guessing it could be a hardware problem. It could also be Flash crashing Firefox, but Ubuntu? Have you tried hitting Ctrl-Alt-Backspace when that happens?

---

### Post by ubntu350 on 2008-02-03
yea, hdd keeps rolling, no response.  I think I may need a quicktime plug-in perhaps, what is it called in linux?

---

### Post by st33med on 2008-02-03
Well, Quicktime is not available on linux, but you can use the VLC plugin for firefox:
```
sudo apt-get install mozilla-vlc-plugin
```

make sure you have the universe and multiverse repositories enabled.

---

### Post by bruce89 on 2008-02-03
> **st33med said:**
> Well, Quicktime is not available on linux, but you can use the VLC plugin for firefox:
```
sudo apt-get install mozilla-vlc-plugin
```

make sure you have the universe and multiverse repositories enabled.

A more integrated solution would be to install more gstreamer plugins.

```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg
```

---

### Post by ryanVickers on 2008-02-03
Just FYI, instead of just powering off with the button, *first* try holding ```

Alt + PrintScreen + R + S + E + I + U + B
```
It doesn't always work, but I'd say about 90% of the time its able to power off correctly.  Worth a try every time just for the extra risk reduction.

---

