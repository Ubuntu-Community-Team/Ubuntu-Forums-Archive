---
title: "S/PDIF Digital out not working on Macbook 8.1"
date: 2013-06-25
forum: Apple Hardware Users
---

### Post by TTTNL on 2013-06-25
I'm running Ubuntu 13.04 on my Macbook pro 8.1. I've installed XBMC Frodo and everything is working, except the digital out. I've searched everywhere and tried everything i could find. I've unmuted the <S/PDIF> in Alsamixer, but still no sound or light coming from S/PDIF output. Any suggestions?

[IMG]http://i.imgur.com/BNL4gs6.png[/IMG]

---

### Post by TheFu on 2013-06-25
I dno't use apple products, but on my systems, the audio is part of the video card and video drivers.  First, make certain you have the correct driver for that specific audio chip loaded.

Next, you want to see which audio output is being used by XBMC.  The aplay -l command will show a list of available devices.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Inside the audio settings (System-playback I think), there is a place to entire a custom audio output device.  On my XBMC system, I wanted analog audio output, so the "custom device" is "hw:1,0".  That is card "1", device "0".  Clear?  If I wanted output from the digital device, then I'd select "hw:1,1" ... which in my case is for audio over HDMI output.

I've never had luck using the "passthru" setting and there is a toggle between digital and analog on that same page.  If analog is toggled, I've never gotten the digital hw:1,1 working and vice versa.

I've also attempted to use the XBMC list of audio devices, but found the trial and error to get something working too difficult and it wasted way too much time. Typing in the hw:x,y always worked 100%. That seems easier to me.  If I had "digital" selected on the XBMC page, I think aplay would show "card 0" with 3 additional option. I'm just sayin'.

Good luck!  BTW, in my world, only the XBMC settings mattered, not the ALSAmixer settings. Don't know why.

---

