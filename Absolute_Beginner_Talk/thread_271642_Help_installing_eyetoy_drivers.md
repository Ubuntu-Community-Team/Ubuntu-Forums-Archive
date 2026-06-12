---
title: "Help installing eyetoy drivers"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-10-05
Hi,
I am trying to install the Eyetoy drivers for ubuntu. It is picking it up in device manager, and it is also on "lsusb".
I found this guide:
[http://alpha.ovcam.org/ov511/install.html](http://alpha.ovcam.org/ov511/install.html)
But I can't figure out how to get it to work..
Basically:
```

#  Check that /dev/video0 exists. If it doesn't, you can create it with "mknod /dev/video0 c 81 0 ". If you have another video device, you camera might be on /dev/video1  (change the last argument to mknod to 1 in that case).
# Some applications look for the device at /dev/video . In some operating systems (e.g. RedHat 7.1 or later), /dev/video might be a directory and not a device node or a symbolic link. You will have to manually specify the device as /dev/video0 when you use your video application.
# Give users (besides root) permission to use the camera. This requires read and write access to /dev/video0 . You can grant this permission with "chmod 666 /dev/video0 ". If you don't want everyone on your system to be able to use the camera, use the "chown" command instead to make /dev/video0 belong to you.
# Download an application from http://alpha.dyndns.org/ov511/apps.html and test it. I recommend Xawtv and Vidcat. (Note: vidcat might not work on cameras with OV6620 or OV6630 sensors).
```.

I can't get past step 6, for "mknod /dev/video0 c 81 0" wont work.

Any ideas?
- Josh

---

### Post by pgatrick on 2006-10-05
Did you have root privileges? e.g. 'sudo mknod /dev/video0 c 81 0'

---

### Post by Josh1 on 2006-10-05
> **pgatrick said:**
> Did you have root privileges? e.g. 'sudo mknod /dev/video0 c 81 0'

Yes, i tried that of course.
[http://home.insightbb.com/~foolsh/](http://home.insightbb.com/~foolsh/)
The link wont work anymore.. damnit! :(

---

### Post by frolle on 2006-10-05
I am having the same problem.

I cant make my eyetoy workning. It seems like the drivers is impossible to install.

---

