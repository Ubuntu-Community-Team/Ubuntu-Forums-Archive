---
title: "Digital Camera Problem"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by matthateswindows on 2005-09-29
I have a Kodak CX6200 camera, and I want to load the pictures from its memory card into the computer. When I plug it into the USB port a window opens offering to import the pictures, asking where I want to put them, etc. When I click OK, I get this message: *An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device* Can anyone tell me what this means, and /or how to fix it?

---

### Post by nitricacid on 2005-09-29
Is there anyway you can just search the memory of the camra and pull them off that way instead of using the  window that pops-up?

---

### Post by KingBahamut on 2005-09-29
apt-get install gphoto2 
"Kodak CX6200" is in the list as a supported camera. 
=)

---

### Post by Master Shake on 2005-09-29
Something else I'll need to install...

I'm learning there's very little Ubuntu CAN'T do.

---

### Post by matthateswindows on 2005-09-30
[QUOTE=KingBahamut]apt-get install gphoto2 
"Kodak CX6200" is in the list as a supported camera. 
=)[/QUOTE]
I have gphoto installed, and it seems to recognize that the camera is connected. I even tried opening gphoto before I connected the camera and trying to import the pictures through the interface, but with the same results. I will try accessing the camera as a memory location as suggested above. I'll let you know what happens.

So I fooled with this problem over the weekend, and discovered that there was a conflict between my HP photo printer with built-in card reader and the camera. When I start-up with only one of the two connected, it seems to work perfectly. I guess this explains the "other program or kernel module" message I was getting. Thanks to everyone who posted on this.

---

