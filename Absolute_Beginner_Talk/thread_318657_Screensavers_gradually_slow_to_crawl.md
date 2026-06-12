---
title: "Screensavers gradually slow to crawl"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Scribbleaz on 2006-12-14
Greetings, folks. I'm fairly new both to Ubuntu and Linux. Been having the usual number of frustrating problems, but little by little the clouds have been lifting. 

I've been having a problem in Edgy that is little more than an annoyance, but still...

I love the screensavers, but something weird is happening with the video. When I run any of them, they start out running at a nice clip, but within a few minutes, the frame rate drops dramatically, and they start to crawl. (FYI, I'm running a plain vanilla PC with a Radon 9250 AGP video card.) If the video had started out slow and stayed there, I would simply have attributed the problem to a misconfiguration, the limits of my system, etc., but I'm baffled about why the slowdown would occur a few minutes into the process.

I noticed the problem first in the gnome-screensaver package. I replaced it (following instrux posted throughout the forums) with xscreensaver, but the problem occurs in both.

Apologies if this question has been asked and answered before. I've gone through the forums and seen numerous discussions of video problems, but haven't seen one corresponding to mine.

Anyone have any suggestions for a puzzled newbie? 
Thanks.

---

### Post by mykalreborn on 2006-12-14
it's your 3d acceleration driver for sure. follow this link :[http://ubuntuforums.com/showthread.php?t=287315&highlight=ati+driver+reinstall](http://ubuntuforums.com/showthread.php?t=287315&highlight=ati+driver+reinstall) , and check out post #24. download the attachment and follow the instructions and you should be good. this could damage your display though - i mean you won't be able to see anything, so before you install the driver be sure that you find out how to reconfigure an xserver. search this forum and everything.
i have a 9200 pro ati and after i installed this driver i had to start ubuntu in recovery mode, reconfigure xserver by enabling dri.
still you shouldn't experience these issues. it should work like a charm, but it's good to be on the safe side :D
also. even after you install the driver for 3d acceleration, some of the screensavers run slow. it just ain't such a good video card :p

---

### Post by Scribbleaz on 2006-12-14
Thanks much, but the script in Message 24, when run, warns that the drivers are for dapper only. I'm running Edgy. I appreciate your efforts, though.

---

### Post by mykalreborn on 2006-12-14
oh. my mistake.
then try this link:[http://ubuntuforums.com/showthread.php?t=255929&highlight=ati+3d+driver](http://ubuntuforums.com/showthread.php?t=255929&highlight=ati+3d+driver).
it should help you a bit

---

