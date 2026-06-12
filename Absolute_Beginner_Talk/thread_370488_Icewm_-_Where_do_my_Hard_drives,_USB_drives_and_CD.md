---
title: "Icewm - Where do my Hard drives, USB drives and CD-Rom show up?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Scolecite on 2007-02-25
I don't have any desktop icons. When I plug in my USB thumbdrive it dosent show up anywhere so I can't access the information. 

When I insert a music cd, nothing happens and I have no CD icon to click on. 

Thanks for any help.

---

### Post by IYY on 2007-02-25
IceWM doesn't have any functionality like what you describe. I am not sure if the disk would even be auto-mounted for you (if it isn't, I'd suggest adding gnome-settings-daemon to your IceWM startup file). If it is automounted but just not displayed, just navigate to it using your file manager (Nautilus and Thunar would have it autodisplayed in the bookmarks folders, whereas in Rox you'd have to go to /media/cdrom or something like that).

---

