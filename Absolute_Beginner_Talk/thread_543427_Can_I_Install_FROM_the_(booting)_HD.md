---
title: "Can I Install FROM the (booting) HD?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by malangbaba on 2007-09-05
Trying to install Xubuntu on a Compaq Armada M300

The M300 doesnt have a CD or floppy (and i cant do net boot). It also cannot boot off of USB

So I took out the HD, put it in a USB enclosure. I was able to install Puppy this way (since it doesnt install drivers). But Xubuntu adds drivers in installation, which gives me problems when I move the HD back to the laptop....

Is there a way to do a install from off of HD?  Could I make one HD partition bootable with installation files in it?

---

### Post by jw5801 on 2007-09-05
That's... a very interesting question! I'm sure it can be done but I have no idea how. Perhaps use the Puppy partition to mount an iso of the install CD and then use that to install to a second partition? I'm not sure how one would go about that though... I'll be watching the thread with interest!

---

### Post by malangbaba on 2007-09-05
Lets say I do mount an ISO....how would I start the installation process?

Right now Im trying to see if I can make the [USB bootable procedure]("https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html") work on a HD...

Please share any ideas...

---

### Post by velib on 2007-09-05
> **malangbaba said:**
> The M300 doesnt have a CD or floppy (and i cant do net boot). It also cannot boot off of USB

In other words: a blind deaf mute.  Had one too.

Is there a way to do a install from off of HD?  Could I make one HD partition bootable with installation files in it?

jw5801 is right: you can install from an iso on a temporary hard drive partition.  All you need is a bootable linux partition to get you started.

[https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28fromlinux%29](https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28fromlinux%29)

EditL oh, but you need some--ANY--way to get the iso onto the hard drive.  You'll have to plug it into another computer and transfer it that way.

---

