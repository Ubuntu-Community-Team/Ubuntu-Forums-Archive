---
title: "Format USB HD"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by captgadget on 2006-11-15
OK, I'm trying to install 6.06 on an external usb hd. During the install I get an error message: "Can't create file system". Then when I reboot it no longer finds the usb hd. So I do the reboot back into windows and the hd can't be seen there so I can not reformat. I've used GParted but it's kind of funky. Why can't you just format the whole hd using gparted? When you do make changes with GParted the hd is still not recognized.

---

### Post by dogon on 2006-11-15
You repartitioned the drive, or more accurately, your installer did this for you.

On every partition there is a flag which states the filesystem type. Linux uses a different flag than windows. And since windows cannot deal with the linux filesystems, it simply ignores them. 

You need to remove this partition manually and replace it with a proper windows partition to be able to use your drive on windows. I suppose this is what you want to do..

In windows, go to "Control Panel -> Administrative tools -> Computer Management" There select disk management on the tree on your left.

You should see your USB drive in the list. Use right click and delete the partition you want removed. From there you can recreate the partition, it will automatically be a windows usable partition. You probably want to format it before usage.

This should do the trick. As always, you're messing with your drives here, you might want to extra carefull not to confuse drives. If you have a backup strategy, then before is better than after :)

Good luck.

---

### Post by captgadget on 2006-11-15
Hey,that worked slick!!! Thanks

---

