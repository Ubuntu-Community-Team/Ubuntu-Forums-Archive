---
title: "usb sonica installed, not recognized as sound device"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by negative-ions on 2006-06-07
Hi,
I have only had ubuntu a few days and I have been fighting with this issue for most of those days. I have a usb soundcard called the M-Audio Sonica. I have read many threads on this device but it seems most people know what to do once they get the firmware loader. I don't.
I installed madfuloader version 1.2; it is an application designed to load firmware when the sonica is plugged into USB. I am using the udev version. Had to get make, gcc 4.0, build-essential in order to run the usual ./configure etc. etc..

when I use lsusb I see that "MIDIMAN" is occupying slot 1 in my usb.
However, when I try alsa -l it only shows my motherboard audio (via).

It seems I need to make a link between my usb and the alsa snd-usb-audio. Alsa is already installed. How do I do this?

This is on an EPIA CL6000, 256 mb ram. Dual boot. Everything else works great. Ubuntu can play *.avi's while WinXP hiccups on 'em.

---

