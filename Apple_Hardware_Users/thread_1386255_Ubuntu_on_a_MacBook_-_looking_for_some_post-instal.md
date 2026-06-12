---
title: "Ubuntu on a MacBook - looking for some post-installation advice"
date: 2010-01-20
forum: Apple Hardware Users
---

### Post by WdashS on 2010-01-20
So, I just finished installing Ubuntu 9.10 Desktop on my Macbook (5.1, aluminum, Intel). Aside from a few small issues, it seems to be running pretty smoothly (I'm just running Ubuntu, my Mac OS X installation got messed up a few days ago so I just retrieved my data and didn't bother to reinstall it).

My only issues thus far have been:
- Minor networking issues that can probably be blamed on my school's ResNet.
- When I shut the lid to put the computer to sleep, it never seems to wake back up properly when I open it again.
- It takes a long while to boot.
- Touchpad is a little bit different, but I kinda expected that.

So, does anyone have any suggestions/advice for these four problems? Or, any suggestions of software/configuration changes I should implement to make my MacBook run smoother? I'm using it almost exclusively for note-taking, web-browsing, and logging into my server's shell.

---

### Post by linuxopjemac on 2010-01-21
you can edit the touchpad behavior with gsynaptics

```
sudo apt-get install synaptics
```

switching kernel versions normally seem to fix problems like not suspending from sleep.

---

