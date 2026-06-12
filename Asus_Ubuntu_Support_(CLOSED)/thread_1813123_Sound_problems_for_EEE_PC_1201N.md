---
title: "Sound problems for EEE PC 1201N"
date: 2011-07-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by gratefulfrog on 2011-07-27
This solution shows how to set the alsa-mixer for a EEE PC 1201N and how to prevent google chat from playing with the volume levels.

Once implemented, both skype and google chat work properly. All other sound apps seem to work as well!

0. Close all applications, particularly any browsers with voice chat enabled, my problem was gmail chat.
1. Skype must be set to NOT adjust volume controls.
2. using the alsa-mixer, only one capture channel must be enabled. see attached screenshot.
3. close the alsa-mixer.
4. change the permission of the pulse audio config file for device-volumes to read only:
    $ chmod a-w ~/.pulse/*-device-volumes.tdb 
5. This has fixed the problem for non-root applications, like browsers,
6. for gmail chat there is still one thing to do: edit the file:
    ~/.config/google-googletalkplugin/options
so that it contains the following line:
    audio-flags=1

Now you have a proper pusleaudio config and Gmail won't be able to write over it any more!

Hope this helps someone out there!
Ciao,
Bob

---

