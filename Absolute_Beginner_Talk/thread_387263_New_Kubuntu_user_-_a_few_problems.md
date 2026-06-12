---
title: "New Kubuntu user - a few problems"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Cam on 2007-03-18
I recently decided to embrace linux (after a failed first time a few years ago). I recently installed Kubuntu (6.10) on my laptop and I have a few teething problems I need some help with.

1. I have no idea how to set up my wireless, nor have a status/connect to item in the notification area.
2. My widescreen LCD seems to be stuck on 1024x768 (it's native resolution is 1280x800). I am assuming this is a driver issue so I downloaded the linux drivers for my adapter (Intel GMA900), went into terminal and did the whole ./install.sh (I'm not totally stupid ;) ), but that doesn't install as it says it requires the latest kernel modules, which perplexes me.
3. I have no sound. Again I am assuming this is because I have no chipset drivers installed (Intel 915 Express), but cannot find linux drivers for them

I'm sure I'll run into other issues as I go, but those are the big three, and any help I could possibly get would be absolutely fantastic!

Thanks in advance :)

---

### Post by freebird54 on 2007-03-18
All these issues have been dealt with before - and you will not have much trouble getting them dealt with again :)

Just a suggestion though.  You will get much faster resolution of each problem if you separate them, and head the post with something descriptive:

Intel sound problem on Edgy
Low resolution on Intel video
Wireless setup on _______

That said - the install MIGHT have given you a good enough video driver, so if you edit the /etc/X11/xorg.conf file to add in the resolutions you want - that might be all that's needed there - if you're lucky!

Help is on the way, though....

---

### Post by Cam on 2007-03-18
> **freebird54 said:**
> All these issues have been dealt with before - and you will not have much trouble getting them dealt with again :)

Just a suggestion though.  You will get much faster resolution of each problem if you separate them, and head the post with something descriptive:

Intel sound problem on Edgy
Low resolution on Intel video
Wireless setup on _______

That said - the install MIGHT have given you a good enough video driver, so if you edit the /etc/X11/xorg.conf file to add in the resolutions you want - that might be all that's needed there - if you're lucky!

Help is on the way, though....

Thanks for your advice and your solution, however it did not work. The xorg.conf file lists all resolutions as being "1280x800", but in the display settings the only option available to me is 1024x768. The OS also correctly identified the model of the graphics chip I have.

---

### Post by Cam on 2007-03-19
Should I repost this in a different part of the forums?

---

### Post by qyte on 2007-03-19
[http://ubuntuforums.org/showthread.php?t=24923](http://ubuntuforums.org/showthread.php?t=24923)

follow that guide for your video settings...
what happens?

Edit:
Generally if you search these forums for one issue at a time i guess you will solve them all.
This community rules!

---

### Post by freebird54 on 2007-03-19
You are in the right place - but you will faster responses if the subjects are broken up.  There might be 2 people online who know how to fix them all - and 40 who know 1 of them.  If they see something they KNOW they can help with, they will read your thread, and probably help.

Just make new posts with descriptive titles/tags, and stay online a while - I was amazed at how fast I had answers when I started up in here!

---

