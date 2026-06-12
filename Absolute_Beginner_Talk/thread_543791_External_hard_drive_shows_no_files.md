---
title: "External hard drive shows no files"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by tombom on 2007-09-05
I've just upgraded from 6.06>6.10>7.04. I have an external FAT32 USB hard drive. In both 6.06 and 6.10, this worked fine; there was a link on the desktop to it and I could access the files. However, in 7.04, it doesn't show up on the desktop. It seems to be mounted at /mount/sda1 but there are no files there. I'd appreciate any help.

woops. if i mount it manually i can see all the files. so i suppose the problem is how do i get it to automount? i'm pretty sure this is a really stupid question.

[http://ubuntuforums.org/showthread.php?t=529838&highlight=auto+mount](http://ubuntuforums.org/showthread.php?t=529838&highlight=auto+mount)

and this helped with that

---

### Post by dsauxier on 2007-09-06
Not a stupid question.

A couple of things to try.
1 - see if it's listed in /etc/fstab
If so, comment it out and see if it automounts afterwards.

2 - There was a bug that caused automount to fail (not sure if that's been fixed or not) : when a USB device was plugged in and successfully automounted, then unplugged, then plugged back into a different USB port then automount would fail on that subsequent mount (though manually mounting did work) - sounds like it might be your problem

---

