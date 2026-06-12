---
title: "[SOLVED] Moving Data Between Versions"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by mmmkile on 2008-02-21
I am interested in installing Ubuntu Studio, but I have a lot of files saved on my current Ubuntu Gutsy release. Is there any way that I can move this data from one version to another without saving the files externally. 
Please help!

---

### Post by aysiu on 2008-02-21
If you don't save your files externally, there is always a risk, albeit a small one (if you know what you're doing) that you could accidentally delete or corrupt the files.

If you feel pretty comfortable with partitioning and the command-line, you can try [creating a separate /home partition](http://www.psychocats.net/ubuntu/separatehome).

I would still back up to an external drive or CD/DVD, though, if your data is important to you.

---

### Post by Origin415 on 2008-02-21
Edit -- thought you were going between two different computers, sorry.

---

### Post by aysiu on 2008-02-21
If you have the Universe repositories enabled (ask me about them if you don't know what they are), you can just install Ubuntu Studio as an addition to your existing Ubuntu: ```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop
```

---

### Post by mmmkile on 2008-03-01
Thank you so much. This is the reason I love Ubuntu. Friendly help.

---

### Post by RedRat on 2008-03-01
> **mmmkile said:**
> I am interested in installing Ubuntu Studio, but I have a lot of files saved on my current Ubuntu Gutsy release. Is there any way that I can move this data from one version to another without saving the files externally. 
Please help!

I tried to install Ubuntu Studio via Synaptic and it screwed up my system. I don't really know why but may have something to do with video drivers. Basically, being a newbie, I couldn't resolve the issue and had to re-install the basic Ubuntu. This is just a warning to emphasize the message that you should back up any valuable data, just in case. I hope that you don't have the same problem that I did. Like to hear how it went.

Actually, you can get all of the photo and video apps from synaptic, pick what you want. I found this out later.

---

### Post by mmmkile on 2008-03-01
I switched over to Ubuntu Studio, but I didn't get any of the programs with it.
Did I do something wrong?

---

