---
title: "Help Changing Resolution/SMB Streaming"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by zeroomegazx on 2006-12-13
Hello, I'm semi new to Linux and very new to ubuntu.  Im trying this out as an alternative the beast that is Vista.  I've had great success so far with my older PC's and laptops being fully recognized ahrdware wise but I've run into a wall.


  I only have 1024x768 as my top resolution for my Geforce 5900Ultra that i have on my new test machine.  I have installed teh xorg nvidia drivers from teh add/remove section, and have viewed a few posts on what else to do but i have yet to fix the problem.

Also i have noticed that once a smb share has been connected to VIA ubuntu's menu bar, streaming media such as audio or video, even with the proper codecs installed (as they play when moved to the machine) is not possible and does not give errors.  can anyone help me out on these?

---

### Post by Kobalt on 2006-12-13
Hello,
to add resolutions you must run this command : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then select the resolutions you want as avaliable with the **spacebar**. Hit enter, and restart X with Ctrl+Alt+Backspace. Here you go...
Concerning your VIA smb thing, I don't know about that so I can't help you out. But using the search bar to get answers might give better results :rolleyes: !

---

