---
title: "Using my detected webcam - how?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by TonyDoc on 2007-07-05
I've got a Quickcam pro 5000, installed the latest driver.  If I click the button on the webcam, then dmesg shows the button click has been detected.  So far so good.  The usbview utility also shows it as a video device, and I've checked that it is a supported device for uvcvideo.

Now, how can I get it to do anything?  Camerama reports it couldn't connect to the video device (/dev/video0) and I don't know what other software might view any input.  Knowing nothing about webcams, I'm at a loss.  I know it works in Windows, since I've set it up there, but I really don't want to keep Windows just for that!

Tony
:confused:

---

### Post by Happy_Man on 2007-07-05
Kopete detects pretty much any webcam out there, you may want to try that..... ```
sudo apt-get install kopete
```

---

