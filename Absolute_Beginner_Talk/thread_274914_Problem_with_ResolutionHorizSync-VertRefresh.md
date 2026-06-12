---
title: "Problem with Resolution/HorizSync-VertRefresh"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by bigben on 2006-10-10
Hi
Just installed ubuntu on my lappy and the resolution isnt set right(now at 640x). I've been reading for hours in old threads and came to the point of knowing where to add the missing HorizSync&VertRefresh values.But i dont know the values and I'm not able to find them through google(i dont know my lappy's model),dont have the manual and the "sudo ddcprobe | grep monitorrange" doesnt work..
Anybody knows how to bypass the problem?

My Specs: P4 2.66
          15.1 inch screen with 1024/768 pixel and 60mhz refresh rate
          Intel Graphics chip 82845G  (supposenly a 845G model)
Breezy Badger 5.10

TIA

---

### Post by bigben on 2006-10-10
ok, i found the solution myself. I used the knoppix live cd and saw my vertrefresh and horizSync values when it was booting up..(under video settings)
The i just added the values to: sudo gedit /etc/X11/xorg.conf   under the monitor section and voila...its fixed!

hope this will help someone in future..:)

---

