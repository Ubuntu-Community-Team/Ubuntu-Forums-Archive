---
title: "Non Root user can't mount USB drive"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by jbrown2197 on 2007-01-24
I plug in my USB memory device, but it does not mount. When I double click on it, it gives an error message that only the root user can mount this device. How do I allow non root users to mount this device?

---

### Post by x64Jimbo on 2007-01-24
put it in your fstab.

---

### Post by K.Mandla on 2007-01-24
> **x64Jimbo said:**
> put it in your fstab.
:lol: That almost sounded like an insult. x64Jimbo means add the mountpoint for the USB drive to your /etc/fstab file. Here are some ideas for you:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

:D

---

### Post by jbrown2197 on 2007-01-24
Yeah, sorry if that seemed a little too easy. The first time I installed Ubuntu my USB just worked. After mucking around I reinstalled Ubuntu and now it doesn't. I couldn't figure out what I had changed.
Thanks for the help, I'll check out that link.

---

### Post by x64Jimbo on 2007-01-24
> **K.Mandla said:**
> :lol: That almost sounded like an insult. x64Jimbo means add the mountpoint for the USB drive to your /etc/fstab file. Here are some ideas for you:

[http://ubuntuforums.org/showthread.php?t=283131]("https://secure.colostate.edu/,DanaInfo=ubuntuforums.org+showthread.php?t=283131")

:D
HAHA I didn't even think about it that way! LOL! Good catch, and thanks for adding the extra info.

---

