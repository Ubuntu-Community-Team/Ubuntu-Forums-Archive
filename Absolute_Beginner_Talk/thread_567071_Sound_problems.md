---
title: "Sound problems"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by whein on 2007-10-04
I've been getting weird problems with the sound levels and mute on my system changing themselves unexpectedly.  Most of the time it seems to be related to Myth, but the it's happened using XMMS too.

In Myth, _sometimes_ if I press the left or right arrow to skip forward or back (or use the remote key to do the same) the PCM channel on my sound mixer will become muted.  Not set to zero mind you, but the little icon below it in the mixer panel will get the red X through it and I have to manually unmute it using the mouse in the mixer panel.  Toggling mute on and off from within Myth has zero effect.  This seems to happen only after a while, and then it will happen every time until I reboot.  After a reboot, I can run Myth frontend a few times, watch a couple recorded shows, and everything works fine.  Then at some point it decides to get grumpy and starts muting when I try to skip ahead.

In XMMS, twice now it has set my volume to zero.  I adjust the volume back up and hit the play button and it immediately resets the volume control to zero.  If I adjust the volume while it is already playing a song, then it will accept it.  Reboot fixes the problem, but it has happened twice now.

I'm running Fiesty with the latest versions of Myth and XMMS in the Ubuntu repositories.  Can't check versions right now cause I'm at work.  'Puter is an AMD64x2 4400+ using motherboard sound, 2x PVR-150MCE, 1x PVR-350.

Anyone else ever heard of this?  Ideas?
-Will

---

### Post by whein on 2007-10-08
Some additional data, still no explanation or solution...
The muting conflict seems to occur if I have both Myth and XMMS open (but not playing) at the same time.  If I close XMMS, Myth still mutes whenever I skip forward or back.  Restarting Myth last night seemed to make the muting problem stop, but the volume levels would still randomly decrease from time to time.
Now, granted I'm used to Windows, but I thought that Linux could mix sounds from multiple programs without issue?  In fact I was pretty sure I've had multiple programs overlapping and they all came through as expected, each with their own volume levels.  Anyone know if this is a Myth or an XMMS or an Ubuntu issue?  Ideas on how to track it down further?
:(
-Will

---

