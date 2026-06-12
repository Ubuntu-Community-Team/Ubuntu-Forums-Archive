---
title: "Nvidia Install Problems"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Andy17MB on 2008-03-19
Hi,

I had a 3D driver running for my NVidia 7300le based MSI graphics card under Fiesty.  I installed this using Envy.  When i upgraded to Gutsy the install had a bit of a fit on the graphics card and I have only managed to get the NV driver running.  

If I run the Restricted Drivers manager I get:
```
E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb: subprocess pre-installation script returned error exit status 2
```
Which doesn't seem to tell me much.  

I have tried to clear up the old restricted drivers install using Envy and that has made no difference. Restricted Drivers Manager seems to recognise that there is a card plugged in and that it needs to use the nvidia-glx-new which seems to square with other advice

All suggestions appreciated as this is proving very frustrating

Andy

---

### Post by bswilson on 2008-03-19
Have you tried installing the newest drivers from the nVidia Web site?  Go here to this page, which in most cases will auto-detect the card you have.  I installed this way with great results.

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

---

### Post by Andy17MB on 2008-03-20
Thanks, I'll give that a go

---

