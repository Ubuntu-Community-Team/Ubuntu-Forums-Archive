---
title: "Finished installing Ubunut, a few questions"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by stephentyler20 on 2007-01-23
First, install on my Windows XP machine was a breeze, I just let the installer deal with the partitioning, and that was fine. I love Ubuntu so far, and am getting more comfortable with it by the minute. I do have a few pertinent questions, however, that I hope someone can answer for me!

1. My laptop's touchpad works fine, except for dragging and scrolling with the touchpad itself. I.e., I can move the mouse, and tap-to-click, but I cannot tap-to-drag or tap-to-scroll like in Windows. Is there a fix for this?

2. In Totem, I cannot play movies over the Network from my desktop Windows XP machine (this was no problem in Windows). There was something about a Samba server fix, but I'm clueless?

3. My WiFi works just fine, except I don't know how to view a list of available networks like in Windows, is this possible?

4. Lastly, and not least important, what's the best way to access files from Windows on the same machine? In other words, I'm currently using the Dual Boot feature, but I can't see any of my windows files (i.e. music, pictures) on Ubuntu. Fix?

Thanks!

---

### Post by riven0 on 2007-01-23
1) Not completely sure about the touchpad. I've got a thinkpad, and in order to get the scrolling feature working I had to install the trackpad utility files. Not sure about your particular laptop, but I would advise searching for you laptop in Synaptic. For example, if you've got an Dell, search for that and see what comes up.

Otherwise, you should be able to configure this through your xorg.conf file, but I've never done it myself, so someone else will have to help.

2) Do you have the dvd codecs installed? Otherwise, you may want to setup NTFS read/write support and see if that does the trick. [Here is the howto]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read+write").

3) With Nautilus open, try going to View >> Go >> Network.

4) Again, if you already have Samba set up correctly, you may still need NTFS read/write support. So look into that first, and if it doesn't work, post here again.

---

