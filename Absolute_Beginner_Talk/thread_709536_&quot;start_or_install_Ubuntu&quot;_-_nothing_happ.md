---
title: "&quot;start or install Ubuntu&quot; - nothing happens"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by wasabisohot on 2008-02-27
my system:
dell optiplex 160L
2Ghz Celeron
512 mb ram
40 gb HD
onboard video (Intel 82845G/GL/GE/PE/Gv Graphics Controller)
Lite-On DVDRW LH-20A1H
Samsung CD-ROM SC-148C
USB keyboard/mouse

I have downloaded the desktop version of 7.10 ubuntu and burned the ISO image to a cd using InfraRecorder. I have the PC boot from cd and I get to the following screen with the timer counting down.

[IMG]http://i227.photobucket.com/albums/dd136/wasabisohot/ubuntubootup.jpg[/IMG]

# I hit enter on "Start or install Ubuntu" and my cd-rom speeds up for a bit and slows down to nothing. I don't even get the progress bar. It just stays at this first screen (minus the timer after I hit enter).
# I've booted from both dvdrw and cdrom but the same symptom follows (I know both devices work from other tests)
# I've waited ~25 minutes and nothing happens
# Tried "check cd for defects" but nothing happens
# Tried "Start Ubuntu in safe graphics mode" but nothing happens
# I've created 3 extra partitions using gparted for ubuntu thinking that that would help... nope  :(
# I'm able to explore the ubuntu bootable image in windows explorer and I see multiple files
# Think my search skills aren't that great because I haven't found any threads detailing the same problem

I'm currently downloading the "alternate" package to see if that'll work but would welcome some help in the meantime. Thanks!

---

### Post by Afkpuz on 2008-02-27
Yeah, I think the alternate will fix you right up.  The problem is probably due to your video card.  The alternate disc will install in a dos/text mode.  then, once you're into unbutu, you'll need to find the intel video drivers.  I don't have any experience with that, but I think they are in the repositories.

---

### Post by Duck2006 on 2008-02-27
> **wasabisohot said:**
> my system:
dell optiplex 160L
2Ghz Celeron
512 mb ram
40 gb HD
onboard video (Intel 82845G/GL/GE/PE/Gv Graphics Controller)
Lite-On DVDRW LH-20A1H
Samsung CD-ROM SC-148C
USB keyboard/mouse

I have downloaded the desktop version of 7.10 ubuntu and burned the ISO image to a cd using InfraRecorder. I have the PC boot from cd and I get to the following screen with the timer counting down.

[IMG]http://i227.photobucket.com/albums/dd136/wasabisohot/ubuntubootup.jpg[/IMG]

# I hit enter on "Start or install Ubuntu" and my cd-rom speeds up for a bit and slows down to nothing. I don't even get the progress bar. It just stays at this first screen (minus the timer after I hit enter).
# I've booted from both dvdrw and cdrom but the same symptom follows (I know both devices work from other tests)
# I've waited ~25 minutes and nothing happens
# Tried "check cd for defects" but nothing happens
# Tried "Start Ubuntu in safe graphics mode" but nothing happens
# I've created 3 extra partitions using gparted for ubuntu thinking that that would help... nope  :(
# I'm able to explore the ubuntu bootable image in windows explorer and I see multiple files
# Think my search skills aren't that great because I haven't found any threads detailing the same problem

I'm currently downloading the "alternate" package to see if that'll work but would welcome some help in the meantime. Thanks!

When you burn the CD did you burn it at a slow speed?
 ie:X4

---

### Post by wasabisohot on 2008-02-27
the alternate cd seems to have worked. thanks everyone for the help!

---

