---
title: "x360 media server help"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by adrock1942 on 2007-11-17
OK. I have gotten the program x360mediaserve-0.0.2 to run on ubuntu and it starts up the server. However, i go to my xbox 360 and search for computers and  cant find my computer. Also, how can i add music for the program to stream?

---

### Post by misconfiguration on 2007-11-21
From my understanding the x360mediaserver isn't all that fancy anymore. I've read that it's superior to some other apps when it comes to mp3 content collection and streaming but I've not really wanted to try it.

The xbox 360 listens for active UPNP connections so essentially what you need is a nice little UPNP applet so you can point some files and have the xbox discover your hosted media, right?

Let me recommend two things:

TwonkyMedia (proprietary but works well)
[http://www.twonkyvision.de/Download/TwonkyMedia/index.html](http://www.twonkyvision.de/Download/TwonkyMedia/index.html)

uShare: (open-source based from geeXboX)
[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

Remember that the xbox 360 can only support certain formats, also in order to have streaming movies noticed by your xbox they first need to be in the proper encoded container and audio format. 

See here;
[http://blogs.msdn.com/xboxteam/archive/2007/05/09/spring-07-video-playback-faq.aspx](http://blogs.msdn.com/xboxteam/archive/2007/05/09/spring-07-video-playback-faq.aspx)

I'm in the process of writing a Perl script to automatically convert all of your video media from .avi to .mp4 with the .mov extension and FAAC audio. 

I will post this when it's complete.

---

### Post by misconfiguration on 2007-11-21
From my understanding the x360mediaserver isn't all that fancy anymore. I've read that it's superior to some other apps when it comes to mp3 content collection and streaming but I've not really wanted to try it.

The xbox 360 listens for active UPNP connections so essentially what you need is a nice little UPNP applet so you can point some files and have the xbox discover your hosted media, right?

Let me recommend two things:

TwonkyMedia (proprietary but works well)
[http://www.twonkyvision.de/Download/TwonkyMedia/index.html](http://www.twonkyvision.de/Download/TwonkyMedia/index.html)

uShare: (open-source based from geeXboX)
[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

Remember that the xbox 360 can only support certain formats, also in order to have streaming movies noticed by your xbox they first need to be in the proper encoded container and audio format. 

See here;
[http://blogs.msdn.com/xboxteam/archive/2007/05/09/spring-07-video-playback-faq.aspx](http://blogs.msdn.com/xboxteam/archive/2007/05/09/spring-07-video-playback-faq.aspx)

I'm in the process of writing a Perl script to automatically convert all of your video media from .avi to .mp4 with the .mov extension and FAAC audio. 

I will post this when it's complete.

---

