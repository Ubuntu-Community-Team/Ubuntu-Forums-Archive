---
title: "Problems importing photos from a camera"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Nostromo on 2006-10-30
I'm using Ubuntu Dapper Drake 6.06. I'd like to download (well, transport, import, whatever is the correct word) photos from a digital camera (Sony Cybershot, I suppos DSC-W50 stands for the model).

I've tried to use gThumb Image Viewer. There is also GIMP, but I haven't found a command to do the thing.

When I connect the camera (USB connection), Ubuntu recognises the camera ("*USB PTP Class camera*"), BUT I get this kind of an answer:

*An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.*

As an Absolute Beginner, I have no clue of those things. Could someone clarify this? And feel free to write like writing for an idiot (meaning a beginner).

---

### Post by Jussi Kukkonen on 2006-10-30
This seems to be a common problem (as searching for the error message in this forums will tell you), although there doesn't seem to be just one reason for that error... There are quite a few bugs reported in launchpad.net about something like this.

You could try running the import with root permissions, just to see if there is a problem with that. Run this in terminal:
```
sudo gthumb --import-photos
```

Something else to check: Are you in the plugdev group? (run *groups* in terminal to find out)

---

### Post by Bartender on 2006-10-30
Don't know about the camera problem.  Maybe someone who owns a SOny can help out.  If you have broadband, try F-Spot for handling pictures.  Synaptic will get it.

---

### Post by Nostromo on 2006-10-30
Thanks!

Jussi, I should have understood myself to search with the error message myself. Your advice didn't get me immediately anywhere, but I'll check those searches.

I seem to be in plugdev group, whatever that means.

---

### Post by Jussi Kukkonen on 2006-10-30
Every user who is a member of *plugdev* should be able to access hotpluggable devices (digital cameras, USB drives etc.)

---

### Post by Mud.Knee.Havoc on 2007-10-13
There is a bug fix here that can probably help you: [https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/64146]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/64146")

In order to get my Fuji Z10 importing properly, I had to follow that bug fix up with this one: [https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")

---

