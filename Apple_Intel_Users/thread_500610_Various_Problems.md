---
title: "Various Problems"
date: 2007-07-14
forum: Apple Intel Users
---

### Post by AnlamK on 2007-07-14
Hey all, 

I am new to Ubuntu and I am having a bunch of problems. I have ordered them from the most pressing to the least urgent. I have a MacBook Pro with Intel Core 2 Duo and ATI graphics card.

(1) I have changed my /etc/X11/xorg.conf file in an attempt to fix my touch pad. However, now the touchpad is not working, I can't actually open a Terminal window to re-fix my xorg.conf file. Is there anyway I can get a terminal window without clicking applications->accessories ->Terminal ?

(2) So, to fix this problem, I tried to boot from the Ubuntu-CD, hoping that would give me a command-line. However, when I boot from the CD and get to the installation screen, the keyboard doesn't work and so I can't choose any options. Any ideas why?

(3) The reason why I was trying to fix my touchpad was that it wasn't as sensitive. No matter what I do, my touchpad ignores some of my finger strokes and as a result, it doesn't feel as fluid as it is in OS X. I have tried lowering "FingerLow" in the xorg.conf and maximizing the sensitivity in (I think) System->Preferences->Mouse.
It still isn't as good as in OS X. Does this mean I should buy a mouse?

(4) I can't get right click to work. I have tried mouseemu and followed the instructions on a popular Ubuntu walkthrough but it didn't do it for me. (F12 doesn't work as the default right click.) I have also installed qsynaptics and ksynaptics - maybe they are causing some problems?

I'd appreciate any input and thanks!

---

### Post by apoth on 2007-07-14
CTRL-ALT-F1 will get you a terminal login without GUI, I'm afraid i can't help with the rest, hopefully someone else can.

---

### Post by cyberdork33 on 2007-07-14
> **apoth said:**
> CTRL-ALT-F1 will get you a terminal login without GUI, I'm afraid i can't help with the rest, hopefully someone else can.

#1 You can also hit ALT+F2 in Gnome to bring up a launch command window. You can enter commands there. (like starting the terminal). CTRL+ALT+Fx will get you to one of the consoles though, and ALT+F7 from there will get you back to xorg.

#2 This is a known bug. It won't work. I have an iMac, and I can get it to work by unplugging and replugging my keyboard. I have been meaning to do some testing on this (maybe any USB device can be used? IDK) If you have an external keyboard to plug in you can try that.

#3 The Synaptics How To has several tweaks and tips (and configs) for setting up your touchpad. I will take this issue there.
[http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

#4 I believe that F11 and F12 are the defaults for middle and right-click. Here is a thread pertaining to your question. Please search the forum for answers are there are several issues that have already been covered.
[http://ubuntuforums.org/showthread.php?t=495088](http://ubuntuforums.org/showthread.php?t=495088)

---

### Post by AnlamK on 2007-07-14
Hello,

Thanks for all the suggestions, even though most wasn't helpful. All the keyboard shortcuts wouldn't work for some reason. (Maybe it has to do with Apple? F2 functions as the brightness key, so maybe that's why ALT+F2 didn't work. I have no idea why CTRL+ALT+FCN and others didn't work.) I eventually worked a miracle hack - I don't even want to explain it.

I am still looking for a way to get a right click though.

Thanks for the Synaptics link! One of the posts there was helpful in solving the sluggishness problem. I will look more into it.

Thanks!

---

### Post by Gen2ly on 2007-07-14
The function key should work then.  FN-CTRL-ALT-F1... FN-ALT-F2 or use FN-ALT-F1 to open the gnome-menu.

---

