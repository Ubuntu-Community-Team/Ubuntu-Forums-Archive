---
title: "[SOLVED] Ctrl+Alt+Backspace = X Shutting Down"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-12-06
When I was trying to make some drivers for my Wacom Intuos3, which is very hard to do, I had almost (I thought) reached the finish line. However, I was told to restart X through Ctrl+Alt+Backspace, and after my X restarting and freezing on a black screen for a while (it showed a bunch of white print on a black background, then repeated after 30 seconds, then stopped) I decided to turn off my computer manually (since nothing else worked) and tried to get my Ubuntu running again. Unfortunately for me, now my computer will turn on but I do not even get a welcome screen anymore. Does this mean that my X has permanently failed? (When I was trying to make a driver for my tablet, I saved the gedit file that I was editing before that. However, this does not seem to make any difference at all. I was also doing some other gedit files for timeoutd, which I still do not know how to do, as well as running about four other applications. What is going on here?)

---

### Post by Dr Small on 2007-12-06
Sounds like X messed up somehow.
Try reconfiguring X:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by irish_flu on 2007-12-06
Did you by chance configure your new device by editing the xorg config file?  If so, there's probably a mistake or problem in there that is causing the file to fail (which will keep the welcome screen and Gnome from starting).

The command the previous poster listed will set it back to a more "default" configuration, and should get you off and running again.

---

### Post by ShadowMKII on 2007-12-06
I was, in fact, editing the xorg config file. Does this mean that in order for me to get my computer working, I will have to type in the command stated above when my screen is black? I cannot get to terminal because I am not able to get into my account, hence the black screen problem.

---

### Post by Happy_Man on 2007-12-06
Boot into recovery mode and enter the command above. Alternatively, boot normally, and once it's finished and is trying vainly to get itself displaying, press ctrl-alt-f2 and log in, and then enter the same command.

---

### Post by LowSky on 2007-12-06
boot into recovery mode (hit ESC while booting to enter grub), it will stay in terminal mode asking for your name then password. after that enter

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ShadowMKII on 2007-12-07
Well, I just followed your instructions, but I had some difficulty. When I was in recovery mode, I was continually told that I might be overwriting something important and as a result, nothing happened. I typed in "exit," and I was brought to the welcome screen, so I did what I would do normally with some strange display settings and a very poor tablet configuration and eventually navigated far enough to replace the edited version with the back up that I made. I then restarted my computer (not X because I did not want to take that chance again) and things worked fine! Thank you a lot for your help!

---

