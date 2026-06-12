---
title: "Accidentally overwrote my /home/myusername/ folder"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Galt on 2007-08-26
I think I screwed up pretty bad...

I was attempting to mount an ISO image this morning. I successfully mounted the image, but accidentally mounted it to /home/myusername/. It overwrote all of the files I had in that folder. So, now I cannot seem to get programs to work (like Firefox), cannot get a terminal window open, and cannot check the trash bin to see if (hopefully) my original /home/myusername/ folder is in there. There appears to be two items in the trash at the moment.

I suppose worst case scenario, I will chalk this up to "lesson learned" and start over. Fortunately, this was a relatively new install (about three weeks ago) and most of my files I keep on a separate partition. So I didn't lose anything critical, but it will be a PITA to get everything installed again and back to how I like it. Unfortunately, I hadn't gotten around to learning rsync yet and I have no backups of my /home/ directory.

Anything I can do to recover?

Or, if I am screwed, can I just reinstall Ubuntu to the partition I have set up? I assume that won't affect the other partitions I have set up, or change anything in GRUB. I currently am using a dual boot configuration (Windows XP / Ubuntu) with a swap partition and a shared partition used by both OSes.

EDIT: Forgot to mention that I have left my Ubuntu computer as is...I haven't rebooted for fear of making the problem worse. I'm writing this post from a different computer.

Thanks for any assistance.
Galt

---

### Post by Outrunner on 2007-08-26
Did you try unmount the .iso file? Should be something like this

```
sudo umount /path/to/filename.iso
```

---

### Post by schorsch on 2007-08-26
Your files have not been deleted. They are just invisible as you mounted the ISO file over your $HOME. Just umount the ISO with 
```
umount /home/your_user_name
```
and you will get everything back. I you have not edited your /etc/fstab a reboot will also do the trick.

---

### Post by Galt on 2007-08-26
I couldn't get to a terminal window in order to unmount, so I did a reboot. That did the trick! Everything looks fine now. :)

Galt

---

### Post by schorsch on 2007-08-26
Fine! Can you please mark this thread as solved as it may help others, too?

---

