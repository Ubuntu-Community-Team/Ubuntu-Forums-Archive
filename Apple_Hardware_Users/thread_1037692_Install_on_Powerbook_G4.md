---
title: "Install on Powerbook G4"
date: 2009-01-12
forum: Apple Hardware Users
---

### Post by deamon_knight on 2009-01-12
I'm stumped trying to get to the Live CD on 8.10 with a Powerbook G4. I can get to yaboot, and with live-noplash i end up at busybox. From there I cannot proceed. I've tried "modprobe ide-core" or "ide_core" and then exit, however it reports it cannot mount several locations and drops back to busybox.

Any advice?

---

### Post by tiresia on 2009-01-12
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by stream303 on 2009-01-12
That got me a few times forgetting that with Gutsy, it was modprobe ide-core.

With Intrepid 8.10, it is *ide-scsi*

---

