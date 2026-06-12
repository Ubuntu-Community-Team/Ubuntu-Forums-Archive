---
title: "Audio Input?? Integrated Audio, Realtec...."
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by belikralj on 2007-03-20
I can't seem to get my sound recorder to work. I tried what I know (which isn't much) but to no avail. The details about what hardware I have are in my signature bellow and I have my audio output woking, I just listened to some music a minute ago but can't record sound. Are there some libraries I might be missing like you need gstreamer for audio output or what? In (dare I say it) windows the driver was called Realtec HD (suppose High Deffinition) Audio Driver but I don't know how to get it working. After this post I'll try skype which is my ultimate goal but I doubt it would work if my sound recorder woun't.

Thanx

---

### Post by jadda on 2007-03-20
I have been trying to make this work myself, so I can use skype. I made it work (occasionally) by doing: 

sudo alsactl names
sudo alsactl store
sudo reboot

But it is still very unstable. It can work at 8, but at 10 it doesn't even thou I didn't change any settings](*,) 

Does anybody else have any suggestions???

---

