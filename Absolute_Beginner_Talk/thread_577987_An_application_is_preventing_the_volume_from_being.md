---
title: "An application is preventing the volume from being unmounted."
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-10-16
the title of this post is an error message that get sometimes when using my flash drive, and now its happened with the floppy drive.

 before i just yanked the usb stick and no ones the wiser.

 but when it happened with a floppy it was the last straw. how do i get i to unmount with out yanking?

---

### Post by drascus on 2007-10-16
you can use in termial: sudo eject '/media/(name of disk)'

hope that works

---

### Post by NT4usB on 2007-10-16
If you're done with it, and closed the anything that might be using it:```
 sudo umount -f /media/whateverdrive
```will force it to let go.

---

### Post by 900donuts on 2007-10-16
the problem is i don't know whats using it
both things said device is busy (the floppy indicator light is not on)

---

### Post by NT4usB on 2007-10-16
You don't have to know what is using it, just be sure anything you've been using on it is closed.
I get this a lot when watching video off external USB HDs.
Even though the OS thinks something is still using the drive, I know I've closed mplayer, so I force umount it.

---

### Post by 900donuts on 2007-10-16
yanking won't work with floppies i need the computer to recognize that the floppy has been yanked

---

### Post by NT4usB on 2007-10-16
So, when you run```
mount
```you see the floppy drive mounted?
And, after ```
sudo umount -f /media/whateverthefloppyiscalled
(or, /dev/whateverthefloppyiscalled... I can never remember which to use)
```it's still there?
...then, I'm out of ideas.

---

