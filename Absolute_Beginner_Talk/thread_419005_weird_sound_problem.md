---
title: "weird sound problem"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by iopo on 2007-04-22
Hi Guys!
I have a fresh Feisty installation and yesterday I was checking what services are starting as default.

I unchecked the bluetooth, I checked the hdparm and the alsa-utils. I'm quite a noob so I rally wanted to experiment a bit. 

Well, what happened is that now I have no sound at all!

The funny thing is that bringing everything back to the default configuration and rebooting doesn't make any difference: still no sound!

Also, the hotkeys "mute" "volume-up" "volume-down" are perfectly working: the bar pops up and it seems I can adjust the volume but again no sound.

I also noticed that when I press these hotkeys now a new type of icon (rather big) appears.

I checked my alsa mixer and everything seems fine.

Any idea!
Thanks

---

### Post by iopo on 2007-04-23
I figured out myself. Basically I followed this thread

[http://tech.kiawin.com/2007/04/issue-no-sound-after-install-thinkpad.html](http://tech.kiawin.com/2007/04/issue-no-sound-after-install-thinkpad.html)

that was describing a similar problem. First I reinstalled alsa-utils with hdparm enabled and still no sound. Then I disabled hdparm, reinstalled alsa-utils and the sound is back!

I have no idea if this makes any sense at all. Does it sound like something should be reported as a bug?

---

### Post by beefcurry on 2007-04-23
Sounds like it should be a bug.

---

