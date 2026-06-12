---
title: "New laptop, new problems"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Ionamay on 2008-01-05
Right, I've installed Ubuntu on my desktop before and I got everything working and started to get used to it. I recently got a dell inspiron 1520 laptop and tried to install Ubuntu on it, with a couple of problems so far.
First of all I can't connect to the internet wirelessly. I am using the wired connection now and was looking for something to find my network but the add/remove application won't let me download anything at all because it says the list is out of date, i've tried refreshing it and looking for updates but it says there are no updates, which I don't believe because i only just installed ubuntu. Can anyone help me get that to work and maybe suggest something I can do to connect wirelessly please?
Also the sound doesn't work and just says 'No volume control GStreamer plugins and/or devices found.' Obviously I can't download any because it won't let me. Please help me?

---

### Post by adam.tropics on 2008-01-05
Make sure you have the required sources added. Go to settings-->repos in synaptic, and see whats ticked.

---

### Post by SOULRiDER on 2008-01-05
Firstly, runt hese two commands on a terminal
```
sudo aptitude update
sudo aptitude dist-upgrade
```

For audio:
[http://ubuntuforums.org/showthread.php?t=632748](http://ubuntuforums.org/showthread.php?t=632748)

For wireless read:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by Digger78 on 2008-01-05
your repositories where probably commented out.

open adept

click on the adept menu > manage repositories

select the necessary repo's then fetch updates

---

