---
title: "ASUS graphics driver"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by kcirtap on 2007-07-06
Hi. I just installed Ubuntu and tried it for the first time today and have to say it's the most user convenient distribution i've tried so far. It's a shame I didn't install this distribution any earlier : )

I have some questions though. I can only set my screen resolution to 1024x768 & 60 Hz, so I suspect that I don't have the graphics drivers installed on Linux. Where can I find drivers for the card: ASUS GF7600GS? And also, are there any drivers available for my motherboard that should be installed as well (ASUS M2V motherboard)? I don't have a clue about how to check if I have the latest drivers or any drivers at all for a certain hardware. This is most likely the worst problem I have right now. I don't want to leave out any drivers.

Now when i'm making a new thread, I'll take the chance to ask some other things that isn't crystal clear right now. I used the package manager trying to look for some programming packages. I did find the python IDLE I was looking for, but there were no packages about c++ at all or no IDE's at all either. Why doesn't it find something common like that, am I doing something wrong?

Thankful for help..

---

### Post by felicity on 2007-07-06
The graphics driver you want is an Nvidia one. You can download [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") which will automatically install the correct propriety nvidia driver for you. 

I don't think Asus makes linux drivers, and as far as I know Nvidia doesn't for make nforce drivers for linux either, but you shouldn't need the motherboard ones or extras like you use on windows installs. 

I don't use the package manager, did you try from a prompt? (apt-cache search <program name>)

Or try [http://www.getdeb.net/]("http://www.getdeb.net/") to browse too.

---

### Post by mikeyphi on 2007-07-06
Have a look under System - Administration - Restricted Drivers Manager, that should give you what you want.

---

### Post by kcirtap on 2007-07-06
Thanks a lot.. I found the driver as well the packages I needed.

---

