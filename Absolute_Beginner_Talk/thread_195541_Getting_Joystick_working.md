---
title: "Getting Joystick working"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-06-13
I have a MS Sidewinder joystick that runs off the game port on my sound card.  I have tried to get it working, but no luck.  I do not have listing in /dev/input for js0 or anything like that.  Is there a way to get this thing running?

---

### Post by alienexplorers on 2006-06-13
Tried JScalibrate, but because /dev/input/js0 is missing what can I do?

---

### Post by keithjr on 2007-02-11
Try the instructions found here and report back if they work for you.

[http://www.ubuntuforums.org/showthread.php?t=55173](http://www.ubuntuforums.org/showthread.php?t=55173)

Also this sounded like it should have worked:

[http://ubuntuforums.org/showthread.php?p=2071637](http://ubuntuforums.org/showthread.php?p=2071637)

I have the same joystick and neither of these fixes helped me. If it doesn't help you either, I think it's safe to say that the Sidewinder joysticks are not supported in Ubuntu (I'm using 6.10). The kernel modules do not create the device nodes, and if manually created, they do not work. I haven't found anybody on the forum yet who has had this problem solved, and it seems to be fairly common.

---

