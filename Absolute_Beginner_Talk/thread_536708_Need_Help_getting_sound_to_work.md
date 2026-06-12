---
title: "Need Help getting sound to work"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by rajvirnijjar on 2007-08-28
Hello,

I was trying to watch videos on youtube, and I noticed that there is no sound. I checked other websites that have videos and they also have no sound. The sound works fine when I play music from the hard drive. Can some one please help me to resolve this issue.

Thanks in advance

---

### Post by r4ik on 2007-08-28
If sound doesn't work in Flash Player (for example on YouTube), then edit the configuration file: 

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

to:

FIREFOX_DSP="aoss"

And save the file.

---

### Post by rajvirnijjar on 2007-08-28
I did what you said but that did not help.

Nevermind I restarted the computer and it works fine now

---

### Post by rajvirnijjar on 2007-09-03
I noticed that the it works sometimes and sometimes it dosent. For example if it makes the sound at the startup screen the sound works fine but when there is no sound clip at the log in screen then it dosent work. The sound works fine when I play anything on my computer but it dosent work online.

---

