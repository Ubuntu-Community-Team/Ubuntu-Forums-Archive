---
title: "No login using Live CD..."
date: 2006-09-02
forum: Apple PPC Users
---

### Post by BinarySpike on 2006-09-02
I ordered the install disks and Bam! they came :D

I start and the thing disk runs fine (using the C key) and it's all good...

Now what happens is the boot comes up and I type "live"

It goes through the loading screen and the screen turns dark redish, and stays that way... it even goes "to sleep" kinda like I even got a screen saver...

Now when I do "live video=ofonly" it gets through the loading screen and goes blue... and displays a window about the X server not being able to launch... and would I like to diagnose the problem... I do yes and it displays something...  I did see that there was a memory allocation problem...

I have Mac os X 10.2 installed on one partition, and just some backup files stored on the other partition... I even copied the disk to the other partition and changed the yaboot.conf to reconize it (hd:9,\install\yaboot)

That gave warnings about the file system type... at the boot screen, and when I do "live video=ofonly" it goes straight to a... er... console like screen.  It's not the real console... and I do ./init for the loader screen to come up...

---

