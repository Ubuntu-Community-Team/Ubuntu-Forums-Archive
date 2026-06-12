---
title: "Skype -MacBook mic not working!"
date: 2008-06-21
forum: Apple Hardware Users
---

### Post by Alex&amp;Linux on 2008-06-21
Hello!
I had skype working just fine with the built in mic, but I reinstalled Gutsy today and cant seem to get it going again!

Any help?

---

### Post by hajk on 2008-06-23
You'll have to run the *alsamixer* command in a terminal (it's in the alsa-utils package), to make sure that Master, PCM, Front, Surround, Capture, Input Source Mic and Mux are properly enabled and set. These settings will be preserved across a reboot, provided that the sound driver snd_hda_intel is loaded early enough in the boot sequence; this can be ensured by adding it to /etc/modules. BTW, you'll need a 2.6.22 kernel or newer for this to work properly.

---

