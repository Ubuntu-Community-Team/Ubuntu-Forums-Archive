---
title: "The meaning of 'mount'?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-05-08
Can someone please explain to me what does 'mount/unmount' mean.  I always encounter this word in Linux documentation regarding partitions/devices/volumes but the concept is not clear yet.  Thanks for your help.

---

### Post by LaRoza on 2007-05-08
It a Windows concept too.

Mounting a drive means the computer can read and write to the drive, you can mount a drive as read only also.

Unmounting is basically releasing the drive.

Think of Mounting as "being able to use".

---

### Post by Nythain on 2007-05-08
it means to put somewhere... to mount a picture on a wall, to mount your butt onto a horse...
to mount a filesystem inside your operating system so it knows its there

when you mount a partition, you arent really mounting the partition persay, more like symlinking to the filesystem on that partition from your current filesystem

its mainly used so your operating system can see and access hard drives or partitons its not contained on

---

### Post by kebes on 2007-05-08
LaRoza's explanation is good. I'll just add to that by saying that, in Linux, whenever we "mount" a new device (hard drive partition, external hard drive, USB key, network drive), you get to pick *where* to mount it.

So in alot of Linux documents, they will say "mount the partition somewhere" or "the USB drive will be mounted to /media/usb" or whatever. The basic idea of "mounting" is that the device gets added to the filesystem somewhere, and you can decide where to put it.

Unmount, then is just the opposite: releasing the device, so that its files no longer show up on your computer, and so that you can remove the device.

---

### Post by Bachstelze on 2007-05-08
For a more in-depth explanation :

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/disk-organization.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/disk-organization.html)

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/mount-unmount.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/mount-unmount.html)

It's very conceptual so it mostly applies to Linux, too.

---

### Post by candtalan on 2007-05-08
As I understand it, mounting in linux is mounting of the filesystem which is contained within a device (that is in a partition in a device such as a hard drive I think), I intuitively see it as plugging in the 'external' device into the root filesystem at the pre-arranged mount point. 

The root filesystem subsequently is tuned to act with the newly mounted device filesystem.

In a physical image I see it as plugging in a device (say a hairdryer) into a (power) socket or hanging a coat onto a coathook.

All very flakey images I know, but they helped me get started.

hth

---

