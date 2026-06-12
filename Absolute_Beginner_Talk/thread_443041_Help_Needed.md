---
title: "Help Needed"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by catch22 on 2007-05-14
I have a USRobotics USB Skype phone that i am trying to get working on ubuntu 7.04 with skype.
When i open skype > tools > options > sound devices > i choose  USB Device 0x62a:0x9004 for audio in and out but when i go to make a call i get error -- problem with sound device.
Also i have tried changing audio conferencing to USB audio for sound capture and playback but get the following errors:

Sound Playback: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.

Sound Capture:gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.

I am sure that i am being stupid but if someone could please help me set this up i would be most grateful.

---

### Post by lakersforce on 2007-05-14
Some USB microphones are known not to be supported under linux. Might be the case with yours.

---

### Post by L Campbell on 2007-05-14
> **catch22 said:**
> I have a USRobotics USB Skype phone that i am trying to get working on ubuntu 7.04 with skype.
When i open skype > tools > options > sound devices > i choose  USB Device 0x62a:0x9004 for audio in and out but when i go to make a call i get error -- problem with sound device.
Also i have tried changing audio conferencing to USB audio for sound capture and playback but get the following errors:

Sound Playback: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.

Sound Capture:gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.

I am sure that i am being stupid but if someone could please help me set this up i would be most grateful.


Unless you absolutely have to use Skype, you could try your phone with :-

[http://www.gizmoproject.com/](http://www.gizmoproject.com/)

---

### Post by catch22 on 2007-05-14
> **L Campbell said:**
> Unless you absolutely have to use Skype, you could try your phone with :-

[http://www.gizmoproject.com/](http://www.gizmoproject.com/)

I have had a look at that before but all the people that i want to call use skype and i cant get them all to change over, i dont think they like me that much :mrgreen:

---

