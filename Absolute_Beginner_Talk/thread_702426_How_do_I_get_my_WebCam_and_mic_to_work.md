---
title: "How do I get my WebCam and mic to work?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by JustLikeFred on 2008-02-20
Dear Ubuntu people! 

I am NEW to Linux, a former OS X user (where everything just works). However, Ubuntu is now my platform, and I'm happy about it - except for two "small" issues. 

a) My built-in mic doesn't work. 
b) My built-in mic doesn't work. 

My pc is an Acer Aspire 5315 laptop. 

I have looked at some other related posts, but it didn't help me - being a NEWbie! 

I hope someone out there can help me solve these issues. Thanks! :) 

Best regards, 
JustLikeFred

---

### Post by OffAxis on 2008-02-20
Here's a good starting point for your camera:
[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

As for the mic, the volume for the sound capture may just be turned all the way down. Check the sound properties for your system (I don't remember where those are offhand) or from the command line try

```
alsamixer
```

Use the Tab key to change the View (from playback to Capture), left/right arrow keys to move, and up/down to adjust the volume. Escape to quit.

---

### Post by TeoBigusGeekus on 2008-02-20
Another nice link if you' re interested in using Skype:
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

