---
title: "Intel iMac 7,1 - No Sound in Headphones"
date: 2009-06-07
forum: Apple Hardware Users
---

### Post by mac-wilson on 2009-06-07
Okay, so here's the deal.

When I first installed Ubuntu 8.10 I had no sound.  So I searched around the forums and found a solution that worked.

I added "options snd-hda-intel model=imac24" to the end of /etc/modeprobe.d/alsa-base.  Then when i rebooted, I changed my Sound Device to Realtek ALC889A (OSS Mixer).

That did the trick for the no sound problem, but only for the internal speakers.

Even with my headphones plugged in or unplugged the sound always comes out of the internal speakers, and never from headphones.

How can I fix this?  Any help would be appreciated!

---

### Post by cyberdork33 on 2009-06-07
> **mac-wilson said:**
> Okay, so here's the deal.

When I first installed Ubuntu 8.10 I had no sound.  So I searched around the forums and found a solution that worked.

I added "options snd-hda-intel model=imac24" to the end of /etc/modeprobe.d/alsa-base.  Then when i rebooted, I changed my Sound Device to Realtek ALC889A (OSS Mixer).

That did the trick for the no sound problem, but only for the internal speakers.

Even with my headphones plugged in or unplugged the sound always comes out of the internal speakers, and never from headphones.

How can I fix this?  Any help would be appreciated!
unfortunately, I think this is just a bug in ALSA. Probably should search for / file a bug.

---

### Post by mac-wilson on 2009-06-08
I don't really know how to find these bugs/bad files.  Any advice as to where to begin searching?

---

### Post by cyberdork33 on 2009-06-08
> **mac-wilson said:**
> I don't really know how to find these bugs/bad files.  Any advice as to where to begin searching?
[https://bugtrack.alsa-project.org/](https://bugtrack.alsa-project.org/)
[https://bugs.edge.launchpad.net/ubuntu](https://bugs.edge.launchpad.net/ubuntu)

---

### Post by 311005901 on 2009-06-14
You may want to check out [this post]("http://ubuntuforums.org/showpost.php?p=7454958") to see if that fixes your problem.

---

### Post by fyz on 2009-08-02
I am having the opposite problem. There is no sound coming out from internal speaker, but headphone works fine.
I think I am using the intel iMac One.

---

