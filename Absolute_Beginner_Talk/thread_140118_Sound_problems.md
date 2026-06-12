---
title: "Sound problems"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-03-05
Ok, I installed alsa 1.0.10 drivers w/ this link

[URL="http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy"]http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy
[/URL]

and restored sound in games like supertux with this:


sudo apt-get install libsdl1.2debian-all

which deleted some files and also got sound to work in those games.

So I have sound via totem and in games...but no sound in Gaim, or flash.

Anyone know what the problem might be?

I appreciate it!
 Donald

---

### Post by Moebius on 2006-03-06
You may need to seed your Multimedia preferences to use ALSA.

Go to System -> Preferences -> Multimedia System Selector

Check if ALSA is selected.

As for flash, you can do a search here in ubuntuforums for an easy way to fix flash, it's in the "Customization Tips & Tricks" section.

---

