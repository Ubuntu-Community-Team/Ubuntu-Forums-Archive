---
title: "sound changes cards each switch on"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-11-24
I have a internal motherboard sound and have installed a second card which I would prefer to use. However the system switches cards almost every time I power up. The following are the details. Any ideas?

benbow@benbow-desktop:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media PCI CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: CMI9880 [CMI9880]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
benbow@benbow-desktop:~$

---

### Post by PhatBoy on 2007-11-24
This worked for me (and does not just apply to usb headsets):

[http://www.lockergnome.com/linux/2007/09/23/setting-the-default-sound-card-usb-headset/]("http://www.lockergnome.com/linux/2007/09/23/setting-the-default-sound-card-usb-headset/")

---

### Post by Phurious on 2007-11-24
This post helped me resolve my sounds issues:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound")

I believe the part you will find interesting is "Configuring default soundcards / stopping multiple soundcards from switching", about halfway down the page.

---

