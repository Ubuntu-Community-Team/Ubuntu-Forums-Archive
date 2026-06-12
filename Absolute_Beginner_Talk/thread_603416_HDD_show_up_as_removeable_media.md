---
title: "HDD show up as removeable media"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by fouadaslam on 2007-11-05
hi
i have problem and need help please.
All my partitions from windows(dual booting  gutsy with Xp) that is C,D,E etc show up as removable media. The icons were on the dektop which i was able to remove from under nautilus after this forums help. the trouble is that the USB flash drive also is a "removable drive" and i cant have an icon on the desktop without having all the partitions showing up on the desktop as well. Gutsy should not have them as removable media as they are not on an external HDD, just NTFS partitions.
Is there a way to solve this? 
thanks
regards
Fouad

---

### Post by Steve1961 on 2007-11-05
I'm not aware of anyway to setup Ubuntu to display certain volumes on the desktop but not others.  However, you can still mount/unmount and access all volumes from the Gnome sidebar, including a usbkey.  You can also use the mount tool applet for the Gnome panel, so it's not really necessary to have any volumes on the desktop.

---

### Post by erginemr on 2007-11-05
> **fouadaslam said:**
> hi
i have problem and need help please.
All my partitions from windows(dual booting  gutsy with Xp) that is C,D,E etc show up as removable media. The icons were on the dektop which i was able to remove from under nautilus after this forums help. the trouble is that the USB flash drive also is a "removable drive" and i cant have an icon on the desktop without having all the partitions showing up on the desktop as well. Gutsy should not have them as removable media as they are not on an external HDD, just NTFS partitions.
Is there a way to solve this? 
thanks
regards
Fouad

Hello,

To your question, no as far as I know. There is a setting in gconf-editor, whence one can enable / disable the icons on removable drives.

But due to the fact that Gnome treats windows drives as removable, or rather, unmountable (because they are really unmountable under Linux), you cannot selectively have drive H: (say for the USB stick), but not drives D: & E:

I have removed them from the desktop too, but do not mind it that much, since you can easily reach all drives including the live USB stick from the Places menu item under the main menu. Besides, a dialog or windows should also show up as soon as you plug in the pen drive. So, IMHO it is really not a big deal.

---

### Post by mozetti on 2007-11-05
I think you'll find the HDD partitions are mounted under the ```
/media
``` directory. IIRC, Ubuntu treats everything mounted under "/media" as removable. So, if you change the mount points of your HDD partitions to something other than within the "/media" directory, it should fix the problem.

Not on my Ubuntu machine atm (damn job getting in the way), but I think this will work.

---

### Post by fouadaslam on 2007-11-05
thanks guys for the replies, 
i will try to change the mount point, if i dare, being a eal rookie and all:)
we'll see how it goes
thanks

---

