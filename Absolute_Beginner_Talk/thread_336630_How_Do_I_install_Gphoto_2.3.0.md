---
title: "How Do I install Gphoto 2.3.0 ?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by alpineswampman on 2007-01-11
I am new to Linux, and Ubuntu.  I have a question about how to install Gphoto 2.3.0  It is not listed in the add remove software panel.    I downloaded it to the desktop and tried to follow the install instructions, but am a bit lost there.  It needs to be compiled, and I cant get it to work.  Im not even sure if it will work on Ubuntu.  According to its web page, it supports my digital camera.  I have a Kodak EasyShare C530.  So far, Ubuntu seems to work fine, but if i could get the images out of my camera, it would be great!

Thanks,
AL

---

### Post by PriceChild on 2007-01-14
*moved approved and bumped*

---

### Post by ilya123 on 2007-01-14
Add/remove software allows to manage only a small subset of the system. Try to use the Synaptic package manager, in System - Administration. Most likely it's not the very latest version of gphoto that you get there, but that one you get is normally checked to work with Ubuntu. Compiling will be a pain for a beginner.

Actually, most of cameras those days should be recognized automatically. Did you try just connecting it?

---

### Post by alpineswampman on 2007-01-14
When I connect the camera, a window comes up that says a digital camera has been connected.  It identifies my camera and model but it will not transfer the images.  It gives an error message that it cannot connect to the device and to make sure that I have read and write access to the device.  If I auto detect the camera, it comes up as a PTP device.

Thanks,
AL

---

### Post by alpineswampman on 2007-01-14
Here is the exact error message that I get.

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

AL

---

