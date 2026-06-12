---
title: "[SOLVED] no isight after update to hardy"
date: 2008-10-16
forum: Apple Hardware Users
---

### Post by franki.macha on 2008-10-16
there were a lot of updates to hardy yesterday, one of which stopped my isight camera on my santa rosa 3.1 macbook from working.
i tried reinstalling the firmware and i got the message:

** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully

but still no camera, any suggestions, or should i file a bug report?

---

### Post by eaidoido on 2008-10-16
what application(s) are you using to access the camera?

---

### Post by franki.macha on 2008-10-16
i've tried cheese and skype, cheese gives me blocky colours and static, skype just doesn't recognise that there's anything there..

if i open cheese in the terminal i get this output:


** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/franki/.gnome2/cheese/media/0003.ogg'
Reason: Stream contains no data..

** (cheese:10826): WARNING **: could not load /home/franki/.gnome2/cheese/media/0003.ogg (application/ogg)


if that's any use...

---

### Post by cyberdork33 on 2008-10-16
Try completely shutting down the computer and starting from a cold boot. If it still does not work, please post your dmesg output. You can pipe this to a file like so:
```
dmesg > dmesg_output.txt
```

then you can simply attach the file to your post.

---

### Post by franki.macha on 2008-10-17
erm, that worked :)

i feel very silly now, i mean, i did of course restart after installing, but apparently shutting down was necessary...

well, thanks anyway, i'll try not to waste everyone's time in future :|

---

### Post by cyberdork33 on 2008-10-17
> **franki.macha said:**
> erm, that worked :)

i feel very silly now, i mean, i did of course restart after installing, but apparently shutting down was necessary...
It's OK, it is the first thing we usually check because it is simple and very easily overlooked... The hardware has to reset, and it doesn't reset on a reboot, only when you completely shutdown...

P.S. Please mark this thread as solved from the thread tools menu at the top of the page.

---

