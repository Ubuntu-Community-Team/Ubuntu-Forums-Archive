---
title: "lost video"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by liquoredolce on 2008-02-12
I posted this in another section about a week ago and no one responded so I thought I'd try here too...


So I'm fairly new to Ubuntu and this seems like something rather rediculous. I was trying to re-install my Alsamixer after running updates (PS has anyone figured out which update screws up the alsamixer so I can avoid it next time?) which I've done before, and didn't have much of a problem last time, but this time it seems to be giving me trouble. Rebuilding the lib, then the driver, then the util didn't work. 

but my biggest problem right now is that when I restarted after a couple updates I wasn't presented with the normal login screen with the UBUNTU background and all that good stuff. I was sent straight to a terminal. There was no video, just text, I could log in and everything, but it was still all text guiding me through my folders and all that. Do any of you have any ideas what went wrong and how I can fix it without actually getting into ubuntu???? 

I appreciate any step by step help you can give me because like said earlier I'm pretty much a novice that's learned a few things myself along the way. Thanks!


(oh btw this is a dual boot windows XP and UBUNTU machine, but they're on different partitions so that shouldn't affect anything..)

---

### Post by oedha on 2008-02-12
but you can login on that text mode right ?
login......then what happen if you type startx
if failed......type :==> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by liquoredolce on 2008-02-15
the startx or whatever failed, and when I typed the sudo reconfigure it went to a package configuration, but I don't know what to do from here.  


I have the options of 

apm ark ati chips cirrus, etc...


I got to this screen before but just had no idea what to do here.  Do you have any ideas?  I don't want to play around with anything and not know what I did to change it back haha


EDIT: when I typed startx I came up with this...

Fatal server error:
no screens found
XIO:    fatal I0 error 104 (connection reset by peer) on X server ":0.0"
           after 0 requests (0 known processed) with 0 events remaining.

---

