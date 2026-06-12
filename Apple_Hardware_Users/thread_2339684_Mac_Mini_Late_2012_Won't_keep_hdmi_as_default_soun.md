---
title: "Mac Mini Late 2012 Won't keep hdmi as default sound output"
date: 2016-10-11
forum: Apple Hardware Users
---

### Post by mike_johnson2 on 2016-10-11
I've installed Ubuntu 16.04 on my late 2012 mac mini, in a dual boot configuration.
The easiest Ubuntu install (or any install) I've ever done.
EVERYTHING works great. All drivers are awesome, and it operates way faster than OSx on this machine.

The only minor issue I have, is that the sound output keeps defaulting back to the internal speaker on every reboot.
Is there any way to make it keep a different audio option (HDMI) as default, even after rebooting?

---

### Post by mike_johnson2 on 2016-10-13
I have already tried  "pacmd list sources", and I found my source and set it to default using "pacmd set-default-source <my device>".
It worked for one reboot, then back to the internal speaker.

---

### Post by mike_johnson2 on 2016-10-14
I realized it has to do with the availability of the hdmi as a physical resource.
If I turn off the stereo while the computer is on, the hdmi output is removed as an available output for sound, and it defaults back to audio jacks.
It also defaults back if I allow the screen to turn off in power save mode.
I have to change the sound output back to where I want it a lot.

Is there no way to disable automatic defaulting for something?
I can see how that could suck if it were video out, but should be fine for sound.

---

