---
title: "webcam almost works"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by linuxgrrl on 2008-02-18
hi,
I have a logitech usb webcam that is almost working right.  Two problems:
1. when the webcam is plugged in, my TV capture card (/dev/video0) stops working - seems to be some kind of conflct.
2. the webcam feed has a yellow cast to it.

I am using Kopete (Yahoo messenger) ... here is the output of dmesg when the webcam is plugged in:

[275599.336221] usb 2-1: new full speed USB device using uhci_hcd and address 2
[275599.535108] usb 2-1: configuration #1 chosen from 1 choice
[275600.186791] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[275600.195771] usbcore: registered new interface driver gspca
[275600.195919] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

any suggestions on how to troubleshoot.

---

### Post by ejb331 on 2008-03-11
Not sure if I can really help you or not but I can share my experiences. 

I too have a Logitech webcam and a tv tuner card. I use Skype because I have AIM and couldn't find an IM program in linux that supports video chats with AIM. Anyways, I use TV TIme to watch tv and sometimes it will come up and say that it could not connect to /dev/video0 (because the webcam somehow ended up there). I do not know why it does this out of the blue (maybe 1 out of 10 times). However, I have never had the two of them conflict with one another.

The only thing I can suggest is to try to permanently assign one of the devices to /dev/video0 and the other to video1. That way they wont fight over it and conflict

Good luck!

---

### Post by linuxgrrl on 2008-03-24
> **ejb331 said:**
> 

The only thing I can suggest is to try to permanently assign one of the devices to /dev/video0 and the other to video1. That way they wont fight over it and conflict

Good luck!

that sounds like a good idea ... how do I go about doing that?

---

