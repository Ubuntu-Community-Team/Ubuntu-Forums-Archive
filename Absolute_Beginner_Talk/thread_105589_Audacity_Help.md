---
title: "Audacity Help"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-12-18
I have installed and reinstalled Audacity, but I still get this error:

> The was an error initializing the audio i/o layer.  You will not be able to play or record audio.

Error: Host error.
I have attached an image of the error box.  Does anyone know how I can fix this?

Thank you very much.

---

### Post by ibanez88 on 2005-12-18
type:

killall esd

in a terminal before opening Audacity.  Works for me.

---

### Post by amcavoy on 2005-12-19
OK that worked.  Is there a way to have that permanently "killed" rather than doing it each time?

Thanks again.

---

### Post by Mustard on 2005-12-19
Go to System>>Preferences>>Sound and disable the sound server.  That is generally the esd process that is running in the background and causing the issues with other applications using the sound device. The downside of  this is that the sound events will no longer be functioning.

Personally I don't miss the sound events and I'm quite happy without the sound server running.

---

### Post by The Hedgehog on 2005-12-21
Is it possible to just deactivate that warning message, because I can do everything I want do to with it. But I don't want to loose my ESD-sound.

---

