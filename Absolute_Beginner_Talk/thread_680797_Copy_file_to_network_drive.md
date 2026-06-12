---
title: "Copy file to network drive"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2008-01-28
This has probably been discussed in this forum, but I couldn't find relevant information.

I wish to use Nautilus to drag and drop a file from my hard drive to a network drive. Ideally I would be able to view the destination network drive in the Tree pane in Nautilus and my local folder & file in the other pane and just drag the local file onto the network drive/folder to make a copy.

Is there a way to have the network dive to show as part of the Tree?

---

### Post by LRT on 2008-01-28
i can see all my networked drives in the tree pane. if i want to click and drag from my local filesystem to the network drive i just navigate to the file on my local file system, then expand the network drive folder on the tree pane (don't open the folder from the tree pane, or else it will show the folder contents on the local filesystem pane), and then just click and drag the file or files to the expanded folder in the tree pane... make sense???

---

### Post by lduplantie on 2008-01-28
It certainly makes sense and that is exactly what I want to achieve. However, I cannot see my network drive in the tree pane. Please explain how you got then to show up in the tree pane.

Thanks

---

### Post by emarkd on 2008-01-28
Click on the Go menu and select Network.  When you find what you're looking for, Bookmark it

---

### Post by lduplantie on 2008-01-28
Thank you for your reply.

I followed your instructions. I can put the bookmark in the bookmark list and clicking on it opens the drive/folder. However, it still is not showing in the tree panel.

---

### Post by LRT on 2008-01-29
can you see your networked drives at all through nautilus, or through a terminal?? are the drives actually mounted?? for me, all my mounted networked drives show up in the tree pane. the networked drives are windows machines so they are amounted via samba. i'm not sure if you have the same setup, but for me these drives automatically showed up in the tree pane when they were mounted.

---

### Post by lduplantie on 2008-01-29
Mounting the drive did the trick. The mounted drive also show up on the desktop, Not exactly what I wanted but I can live with that. I guess that in Windows they are mounted automatically. Maybe I was looking for a "Network Places" look alike in Ubuntu and I was hoping that having the Ubuntu "Network" to show up in the tree pane would do the trick. Unfortunately this doe not appear to be possible.

Thank you

---

### Post by LRT on 2008-01-29
glad it worked out... although it would have been nice to view the entire network:/// through the tree pane...

---

