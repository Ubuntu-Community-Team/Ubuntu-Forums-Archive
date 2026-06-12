---
title: "How to run .run files."
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by buildsomethingcrazy on 2007-10-27
I downloaded the new ATI drivers for Linux and they save as .run files.

Now, I have right clicked them and made them executable however they still don't work.

I don't use Ubuntu anymore but, rather Dream Linux but, I still had this problem on Ubuntu. Any ideas on how to solve this?

Also, it won't let me set my resolution higher then 800x600 I think. I usually have mine at like 1080x1240

Something like that but, it won't let me.

Is that because of the drivers? I also did the reconfiguration of XServer and told it to allow higher resolutions and changed the driver from VESA to the ATI drivers it came with. Still no luck

My card is a ATI Radeon 9250 256MB gfx card.

---

### Post by FuturePilot on 2007-10-27
Try cd-ing to the directory where it is. So if it's on your Desktop```
cd /home/USER/Desktop
```
Then run it
```
sudo sh What-ever-its-called.run
```

---

