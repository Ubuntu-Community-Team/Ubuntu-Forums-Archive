---
title: "New Nano"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by sbussy89 on 2007-12-13
I have a 3G nano.  When I plug it in the icon appears on my desktop but it says there's no music on it, and if I open banshee it says that its not configured to run with the new ipod... is there a fix for this or another program i can use to work with my new ipod?

---

### Post by sbussy89 on 2007-12-14
found a temporaty fix for this... used idump throuh windows to get the music on my pc and then accessed the windows drive through linux to add the files thru bashee

---

### Post by tgalati4 on 2007-12-14
For 2nd gen Nano, I had to change HFS+ filesystem to HFS (without journaling).  I used Disk Utility on a mac to turn off journaling.  After this, I could use it with most of the iPod-capable music managers in Linux.  Perhaps 3rd gen Nano would work the same.

---

