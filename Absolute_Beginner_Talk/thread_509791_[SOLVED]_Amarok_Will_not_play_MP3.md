---
title: "[SOLVED] Amarok Will not play MP3"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-07-25
Just wanted to post the answer I found for this problem. Found this answer in [Rich Reuter]("http://www.richreuter.com/posts/54")

> I had some issues with getting Amarok to play MP3's since I upgraded to Ubuntu Feisty. I came across this tip to get it to work. In a terminal window, run the following commands:

sudo apt-get install libxine-extracodecs
sudo apt-get install libxine1-ffmpeg 

Open Amarok and go to the settings. You'll need to set the output plugin to "Autodetect". That should do the trick. Hope that helps someone.

Hope this helps some one

Sabar

Trying to replace Microsoft and save the world :)

---

### Post by Foxmike on 2007-07-27
Great!:)
 
Welcome onboard!:)

---

