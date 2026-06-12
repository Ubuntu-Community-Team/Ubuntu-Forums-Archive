---
title: "memory stick locks files unexpectedly"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by riohondo on 2007-12-21
Hello all. 

I am asking for help here, because I'm not sure which catagory is for errant thumbdrives and Ubuntu.
I have had a 1 GB LG-brand USB memory stick for a couple of years, with no troubles. 
Today, I loaded 3 .avi movies on it, so that I could test a DivX certified DVD player that has a USB port.  After the player successfully found and executed the .avi files, I 'unmounted' the memory stick, making sure to stop playback before removing, and placed it back into my Ubuntu machine. This is when the fun began. 

After showing the contents of the memory stick, I tried to delete the video files I had copied over from the pc only 10 minutes earlier. Suddenly, every file on the stick puts up an icon of a padlock.. Checking the properties of each file shows that I still have permission to create, read and write to the memory stick, and that 'administrator' owns the device. 

Unfortunately, when I attempt to delete any file on this memory stick, it says that the stick is a 'read only' device.  This is strange considering that it operating normally only a few minutes before. 

Could the DVD Player, with its USB port, have changed something about the stick? At this point, I am not sure what to do next, or how to get delete permission restored. 

Thank you.

---

### Post by blueridgedog on 2007-12-21
Perhaps it is being mounted read only?  Can you post your /etc/fstab?

---

### Post by spiderbatdad on 2007-12-21
mmm. if being mounted with the user option if /etc/fstab...

---

### Post by Mud.Knee.Havoc on 2007-12-21
How about deleting the files as root?

---

### Post by riohondo on 2007-12-23
I think the stick is damaged, because it won't let go of any files, irregardless whether the computer is Linux, Macintosh, or windows. That DVD player did something, thankfully there was no critical data on it. 
Thank you for taking the time to suggest a course of action, but my feeling is the stick is no longer a viable mass storage device.

---

