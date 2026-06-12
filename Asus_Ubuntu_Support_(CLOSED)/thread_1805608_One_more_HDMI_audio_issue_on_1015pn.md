---
title: "One more HDMI audio issue on 1015pn"
date: 2011-07-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by altoiddealer on 2011-07-16
I had an issue getting HDMI audio to work in the first place ([link]("http://ubuntuforums.org/showthread.php?t=1803885")), which was resolved by toggling all the output settings in Hardware > Sound, under the tab "Output".

Now my problem is that the settings for "Sound output device" switch back to the original settings any time that I reboot!

Many thanks if anyone can help me out with this one~ this is the final piece to my puzzle :)


More details:

In the "Output" tab, I have two things listed:

-High Definition Audio Controller
-High Definition Audio Controller Digital Stereo (HDMI) nr 2

The HDMI audio only works when the second one is selected.

However, every time I reboot, it changes back to the first one and the  HDMI audio does not work again until I change the setting.

* I have already disabled "Internal Audio" under the Hardware tab, but that doesn't seem to matter

---

### Post by altoiddealer on 2011-07-19
I still haven't been able to work out this problem, and would greatly appreciate it if anyone could help.

Thanks!

---

### Post by altoiddealer on 2011-07-21
Still having the problem :(

I need to manually configure HDMI output in Sound > Output every time I boot.

---

### Post by altoiddealer on 2011-07-25
I had to jump through a few hoops but, but I finally got the HDMI audio to work on startup, without having to change the Output setting every time! :guitar:

Well what I did originally to get the HDMI audio to work at all was I updated alsa and nvidia drivers. Then in a terminal typed "gksudo gedit /etc/pulse/default.pa".  I added "load-module module-alsa-sink device=hwplug:1,8" (this was the correct passthrough device for my computer). Then I had to open Preferences > Sound and change my audio output to HDMI and toggle the output profiles until the HDMI audio worked.

This was great! Only problem was that the "Output device" setting needed to be toggled every time I rebooted for the HDMI audio to work.


After reading a zillion different pages and trying all sorts of fixes, this is what worked. I copied a pre-made asound.conf into "/etc/modprobe.d/" which I acquired by copying asound.conf from my XBMC-Live installation (/.xbmc/asound.conf). I figured it would work because it fixed my HDMI audio problems in XBMC-Live.

Then I typed the following in terminal to ensure that it would apply on the next reboot: "sudo update-initramfs -u"


Viola! it worked! My HDMI audio works right away!

There was one more obstacle I needed to tackle, though. I have XBMC set to auto-start and for some reason the HDMI audio would be simply fubar'd when it auto-started. After google-ing a few things I figured that maybe XBMC was loading prior to pulseaudio or alsa or whatever the hell makes the audio work (I don't understand Ubuntu very well). So I changed the startup command to "XBMC -sleep 30", which delayed the startup of the program... and it worked!  The HDMI audio works and XBMC auto-starts.

Hope someone else finds this useful!

---

