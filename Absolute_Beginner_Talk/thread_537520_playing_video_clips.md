---
title: "playing video clips"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by whatme33 on 2007-08-29
Where can I get a program or programs that will play the video clips I get in emails from those who are using windows based software. I use to use windows but I am happy with ubuntu except for a few things like this. Time is helping me get it running as easy as windows but very stable and no garbage. I forward my email jokes from work to home and work uses XP PRO.

---

### Post by nexu56 on 2007-08-29
In the latest version of ubuntu, when you play a video in an unsupported format you should get a message that prompts you to easily download the right plugin to play the video.

To do this manually you need to [enable universe and multiverse]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096"), then you can just type in a terminal:

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

If you're still having problems, install mplayer, which can handle pretty much any format you throw at it.

---

