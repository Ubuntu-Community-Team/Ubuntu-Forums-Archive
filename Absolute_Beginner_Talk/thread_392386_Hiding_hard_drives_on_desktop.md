---
title: "Hiding hard drives on desktop"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by dacool25 on 2007-03-24
Hey, i was just wondering is there a way to hide the hard drives, so that they don't show up on your desktop, without unmounting them?  I was thinking that its probably in the coding of the fstab file, but i wouldn't know what to change.  Thanks for your help in advance.

---

### Post by mcduck on 2007-03-24
Press Alt-F2 and run 'gconf-editor' to open the Configuration Editor, then browse to apps/nautilus/desktop and disable 'volumes_visible'. 

The downside is hat this also disables icons for automounted drives like CDs, DVDs and USB sticks. If you don't want that to happen the only way is to mount your hard disks to somewhere else than inside /media, for example in /mnt.

---

### Post by ramzai on 2007-03-24
> **mcduck said:**
> Press Alt-F2 and run 'gconf-editor' to open the Configuration Editor, then browse to apps/nautilus/desktop and disable 'volumes_visible'. 

The downside is hat this also disables icons for automounted drives like CDs, DVDs and USB sticks. If you don't want that to happen the only way is to mount your hard disks to somewhere else than inside /media, for example in /mnt.

Well, the interesting fact that after feisty upgrade these volumes (and only they) disappear from the desktop. CD's, USB flash work ok. I, on the contrary, would like to see them back, but the registry entry mcduck mentioned is already enabled.

---

### Post by dacool25 on 2007-03-24
awesome, thanks for the help.  So how would i go about mounting in /mnt?

---

### Post by IYY on 2007-03-24
It's on ubuntuguide.org

---

### Post by dacool25 on 2007-03-24
sorry to keep this thread going, but i mounted to /mnt..but it still shows up on the desktop.  My ultimate goal here is to get rid of all of my partitions on the desktop, but still be able to see when i put in a cd or usb disk. 

ps. i couldn't remount my primary windows partition to /mnt it says that its not mounted to begin with.

again thanks for your help everyone.

---

### Post by dacool25 on 2007-03-24
nevermind, just had to restart.  Thanks for the help guys.

---

### Post by mcduck on 2007-03-25
> **ramzai said:**
> Well, the interesting fact that after feisty upgrade these volumes (and only they) disappear from the desktop. CD's, USB flash work ok. I, on the contrary, would like to see them back, but the registry entry mcduck mentioned is already enabled.

That's how it used to be in Breezy & Hoary, then at some point in Dapper's development the gconf key to choose if you want to see internal drives on desktop or not disappeared. I don't exactly remember where the key to enable/disable them was, but if I remember right it was somewhere under system/ (could also have been under desktop/gnome), so try looking around in Configuration Editor if you find anything. That's all I can say as I haven't upgraded to Feisty yet.

---

