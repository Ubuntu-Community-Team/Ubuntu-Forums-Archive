---
title: "Multimedia Problems"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Whiffenpoof on 2007-10-01
I am following the multimedia install guide to the letter and cannot get anything to work. I am not interested in DVD playback, I just want MP3 payback and flash enablement.
For instance, I cannot enable flash in install programs/other as it says it does not support AMD 64 bit. Rather good as I have a Pentium D CPU. As for the VIM text editor, what is that all about? Where do I enter txt? Is it at the top or bottom or in the middle? What do I do when the txt is in there? As for entering gpg key from the repository into the terminal, why doesn't it do anything when return is pressed, do I have to be in superuser mode? Any answers? I am tearing my hair out over this, it does not seem to be as user friendly as SuSE.

---

### Post by Perfect Storm on 2007-10-01
VIM text editor can be hard for newbies, try with nano instead (then you can always experiement VIM).

---

### Post by RomeReactor on 2007-10-01
Hi. I think the reference to AMD 64 bit is regarding the 64-bit version of Ubuntu--which you can run on AMD or Intel 64-bit capable processors, not specifically AMD processors; there's no flash for the 64-bit architecture yet. There is, however, a way to enable flash for these systems. For that, [look here]("http://ubuntuforums.org/showthread.php?t=476924&highlight=flashplayer").

As for playing MP3's, you need some gstreasmer plugins:
```
sudo apt-get install gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

The **ugly** plugins are for Rhythmbox; not sure if you need the fluendo package, but it can't hurt to install it. If you use **totem-xine** instead of **totem-gstreamer**, and you want to be able to play the MP3's in Totem, you need the ffmpeg package:
```
sudo apt-get install libxine1-ffmpeg
```

---

