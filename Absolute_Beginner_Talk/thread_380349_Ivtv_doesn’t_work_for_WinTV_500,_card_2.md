---
title: "Ivtv doesn’t work for WinTV 500, card 2"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by arnabbiswas on 2007-03-09
Hi,

I am trying to install these drivers for WinTV 500, which is a dual tuner card. I am following these instructions:
[https://help.ubuntu.com/community/Install_IVTV_Edgy?highlight=%28ivtv%29](https://help.ubuntu.com/community/Install_IVTV_Edgy?highlight=%28ivtv%29)

After installing the drivers, when I test the first card, I am able to view the video fine. I get no errors during the installation and on verifying the install I see:

ivtv: Initialized WinTV PVR 500, card #0 
ivtv: Initialized WinTV PVR 500, card #1 


But when I try the same test for the second card using the following instructions:
cat /dev/video1 > /tmp/test_capture.mpg 
mplayer /tmp/test_capture.mpg 
Mplayer shows only a black screen. 

I have my wall outlet corrected directly to tuner1 (/dev/video0) on it's coax in port, which works correctly. For the second tuner, which doesn’t work, I have the cable output from my set top box connected to the composite in of this tuner card.

Any insights higly appreciated.

---

### Post by panch0 on 2007-03-09
Post the full output from ivtv and MPlayer.

---

### Post by arnabbiswas on 2007-03-10
Sorry for this entire post. It was a false alarm. Nothing wrong with my ivtv installation. My cable company had a cable outage which I was unaware of. I called them up and they informed me and now I am able to watch TV fine through both the devices. Thank you for your help.

---

