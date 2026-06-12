---
title: "MacBook Pro Core Duo No Sound"
date: 2008-06-07
forum: Apple Hardware Users
---

### Post by infinitusagnitio on 2008-06-07
I've searched the forums, followed wiki's, and nothing seems to work.  I can't get my sound coming out of my internal speakers, let alone my external speakers through my line-in (which is what I really need).

Any ideas?

I'm running a dual-boot (OSX/Linux) 2.16ghz Macbook Pro Core Duo with Hardy 8.04

Options file in modprobe.d:
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2


I also removed this (which I originally added from my options file) and added it to the end of the alsa-base file (also in modprobe.d):
options snd-hda-intel model=macbook-pro-v1 position_fix=2 probe_mask=1

Under Volume Preferences, the device to control is HDA Intel(Alsa Mixer) and PCM is highlighted.

Under Volume Control, my master, PCM, Front, and Surround are at 100%.  For the recording tab, Capture and Capture 1 are set to 95%, and Mux and Mux 1 are set to 50%.

Under the switches tab, the only thing that appears is Line In As Output?  which I have checked.

If you need any more info, please let me know.  Help would be greatly appreciated.

-bt

---

### Post by aws910 on 2008-08-27
I'm in the same boat - same hardware, same config.  My sound died after doing updates.

---

### Post by hloupy on 2008-09-02
i presume you guys tried this solution but i thought i would mention it just in case it works for the macbook pro as well as macbook..

[http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/](http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/)

---

