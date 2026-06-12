---
title: "TV-Out (nvidia)"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Kiri on 2008-03-25
Hi, Can someone tell me what I need to do to get TV-out working so that I can view full screen video on my tv automatically when playing video files?

I have a dell xps m1210 laptop with nvidia Geforce Go 7400 card.
Running Ubuntu 8.04 beta. 
I have enabled the nvidia restricted drivers and got compiz running already.

thanks

---

### Post by LowSky on 2008-03-25
did you install nvidia tv out, its under add/remove

---

### Post by Kiri on 2008-03-25
Thanks for the reply.
I couldnt find it in there, but I saw nvtv in synaptic... But isnt the new (nvidia-glx-new) including support for tv out already?

How can I configure it?

---

### Post by LowSky on 2008-03-25
type **sudo nvidia-settings** in terminal

---

### Post by Kiri on 2008-03-25
ok. I got the settings up now, and I could choose twin view or separate X (separate X didnt seem to work for me).
Twin view worked, but it didnt work well. Opening new windows seemed to open them randomly on 1st display, 2nd display or between them. And when playing videos they didnt display full screen on the tv. If I try and go full screen with the video it plays between the 2 displays.

Is there something Im missing?
Can I get it to just play fullscreen on the tv and leave my laptop display alone?

---

### Post by forestpixie on 2008-03-25
You need to get the seperate x screens going to have them work like that I believe. Whne you tried to do seperate x screen what happened?

---

### Post by Kiri on 2008-03-25
When I tried to enable, the tv showed up, but my laptop display went black :(

---

### Post by *daniel on 2008-04-10
I can't even get my TV-out working with 8.04, but that's an issue for another thread.

One way you can get around the whole X/TwinView/whatever problem is to install and activate Compiz. TwinView essentially just stitches two screens together into one huge one, so X doesn't know where to put things, and when you maximise it of course fills up both screens. Compiz can detect displays (I think this is enabled by default) and maximise to only only the TV. So even if your video starts on one screen, you just drag it over, double-click, and it's full-screen on the TV only. I've had this working for ages, and it works great.

If it doesn't do that by default, install compizconfig-settings-manager and under general preferences select "detect displays". That should do it.

---

