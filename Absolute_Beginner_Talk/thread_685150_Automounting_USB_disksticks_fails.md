---
title: "Automounting USB disk/sticks fails"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by markrad on 2008-02-01
I've googled for hours to try and solve this issue but nothing seems to be quite the same. I have a 1Gb usb stick and an 80Gb usb disk which when plugged in do not automount. I'm pretty sure they used to but that could have been on the previous version of Ubuntu (I'm now running 7.10). Unfortunately I don't use these devices very often.

Being somewhat a newbie at Linux I would appreciate some help in how to debug this issue. When I plug the devices in they appear in the Nautilus 'computer' window and if I double click them they will happily mount in /media/whatever (disk or usbstick). They just won't take that extra step and do it on their own. 

Thanks in advance.

---

### Post by freddyp on 2008-02-01
I thought that when you plug the devices in and they appear in the Nautilus 'computer' window that meant they had automounted.  Not exactly sure what you mean by "and if I double click them they will happily mount in /media/whatever (disk or usbstick). They just won't take that extra step and do it on their own."

I'm running 7.10 so not sure if this applies to your version. And not to insult, but have you checked:

System>Preferences>Storage Tab and made sure the following is checked:

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted <<especially this one maybe?

Don't ask me how I know how easy it is to accidentally uncheck one. This should ensure that the USB drive is being recognized by Ubuntu on insert, but remember if you don't ask the O/S to automount it, then it won't be automounted.

Hope this helps!

---

### Post by markrad on 2008-02-02
No they are not mounted. They have been recognized by udev and assigned a device as in /dev/sda1 but they are not accessible. I seem to recall that normally when one attaches a removable drive it would mount it somewhere in the /media directory and put an icon on the desktop optionally browsing that location. I actually have to double click it in 'computer' for the mount to occur and the icon to be added to the desktop. Alternatively I can manually issue a mount command but then I have to umount it too rather then dismount via the Gnome menu.

I did check the storage tab and they are all turned on. Also this is not the HAL GPartd error either before anybody asks. I already made sure that policy file did not exist.

---

