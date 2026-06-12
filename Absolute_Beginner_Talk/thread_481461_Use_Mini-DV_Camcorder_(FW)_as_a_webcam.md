---
title: "Use Mini-DV Camcorder (FW) as a webcam"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-06-22
I use Kopete, and would like to video-conference with people over the MSN Protocol. I have a SONY MV930 Mini-DV Firewire camcorder, and was wondering whether I could use it as a webcam? Obviously the bitrate would have to be reduced, but any solutions?

Thanks in advance. :D

---

### Post by eoghanmurray on 2007-06-22
Any solutions?

---

### Post by eoghanmurray on 2007-06-22
desperately need this plz

---

### Post by Matt Yun on 2007-06-22
> **eoghanmurray said:**
> I use Kopete, and would like to video-conference with people over the MSN Protocol. I have a SONY MV930 Mini-DV Firewire camcorder, and was wondering whether I could use it as a webcam? Obviously the bitrate would have to be reduced, but any solutions?

Thanks in advance. :D

I really can't add much, but I have connected a Canon Mini-DV camera to Ekiga via firewire.  Ekiga requires the correct plugins; Kopete probably does as well (try googling it).

In case anyone is interested, this is how I got the Mini-DV camera to work with Ekiga:

First, install the Ekiga plugin libraries:  **sudo apt-get install libpt-plugins***  

Then, modprobe the necessary firewire modules (these will have '1394' in their names eg. ieee1394, ohci1394, raw1394, video1394).

Mini-DV camcorders use the AVC plugin (in the libpt-plugin-avc library).  However, firewire webcams use the DC plugin.  As long as you have the correct plugins, Ekiga should autodetect the camera.

See this page for further information:  [IEEE1394 Cameras and Linux]("http://www.rmatsumoto.org/index-en.php?IEEE%201394%20Cameras%20and%20Linux")

---

