---
title: "USB on Ti Powerbook"
date: 2006-02-03
forum: Apple PPC Users
---

### Post by N8K99 on 2006-02-03
I can not get images off my digital camera which uses a USB connection, any ideas on how to start working this out?

---

### Post by linear on 2006-02-03
I can only offer some general troubleshooting suggestions, that might help others to give useful advice:
[LIST]
[*]Tell us, in detail, what you've tried and what happens when you try it.
[*]Does the camera show up as a removable device?
[*]Any error messages?
[*]Do other USB devices work?
[*]Does it work in other OS's?[/LIST]etc., etc.

---

### Post by N8K99 on 2006-02-03
I have only tried the camera as I only have one USB device, and that's the camera. It is a Mini DV that I also use to take stills on. When I plug it in, there is no response that indicates that there is any sort of action occurring. I tried to use Konqi to navigate to devices, and that does not show me anything. I would use Konsole to find it but was unclear where to look for it, because only cdrom and cdrom0 showed up in /media

This camera works fine under OS X and even worked on a PC with Hoary, so I thought I was going to have a good old time today editing photographs. *surprise*

---

### Post by sarcasticfrench on 2006-03-10
Try going into system settings, disks and filesystems, hit the administrator mode button, and then look on the list for your device. When you find it, click on it, hit modify, and then choose the format from the list. I found that the ones that start with "usb" are the ones that worked, but your camera may use something different. Choose a mount point, hit "enable," and then it *should* show up at your mount point. If it doesn't, try looking aroud for various file paths for usb devices. Sometimes that will work even when it doesn't show up in Konquerer under media.

---

