---
title: "Volume/Mute Hotkeys now change mic volume instead of master volume"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by inzania on 2008-04-06
I don't know how or what did it, but pressing the up/down volume or mute keys changes the volume of my microphone in the "Volume Control," instead of the output volume over my speakers.  I've tried fiddling with lots of Volume Control settings, like right clicking the icon and going to "preferences" and changing the device and track to control, and so on.  Still no dice - kind of frustrating since I'm so dependent upon those keys =P

Thanks for any help.

---

### Post by Gen2ly on 2008-04-06
I believe this can be changed in Sound Preferences???

---

### Post by BandD on 2008-04-07
Go to System-->Preferences-->Sound and in the default mixer tracks choose Master or PCM or something like that.

Alternatively you can right-click on the sound icon in the top panel and select preferences then select whichever track you would like to control.

---

### Post by trux on 2008-05-02
In Gnome, the volume up/volume down hotkeys control the Default Mixer Track. You probably changed its value inadvertently to point to your microphone instead of your speaker. To modify it back:

1) run gnome-sound-properties
2) change the "Default Mixer Track" option to your soundcard/device and track of your choice (e.g. Master speaker output instead of Capture/Microphone input).

Everything should go back to normal

---

### Post by trux on 2008-05-02
ps: you can access gnome-sound-properties in System->Preferences->Sound.

---

