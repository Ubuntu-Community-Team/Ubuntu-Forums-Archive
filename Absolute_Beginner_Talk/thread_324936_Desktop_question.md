---
title: "Desktop question"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by IamAcoconut on 2006-12-24
Hello, dear fellow-users! Coconut has one dumb question,
How does he remove icons representing particular partitions from his desktop?
Coconut just installed 6.06.

Thanks in advance :-)

---

### Post by MkfIbK7a on 2006-12-24
> partitions icons 
?????

---

### Post by jvc26 on 2006-12-24
I'm guessing these are the icons for partitions that you have mounted? (Like the ones which come up when you put a cd in?) Im not sure why mine dont come up any more, but I used to have one for hdc1 which vanished when I unmounted it and remounted it under /mnt/hdc1. Can you not just remove the icons?

Il

---

### Post by smoker on 2006-12-24
if you mean an icon on the desktop, you can usually right click and select move to trash from the pop-up menu, if this is what you mean.

hope this helps

---

### Post by MkfIbK7a on 2006-12-24
ahh that makes sense

---

### Post by IamAcoconut on 2006-12-24
As said, the icons represent partitions. Coconut can't move  them to trash, there's no such option. Perhaps they would disappear if Coconut umounted them, but Coconut doesn't know how to unmount them via GUI.

Can't the partitions be mounted and not visible on the desktop?

---

### Post by spockrock on 2006-12-24
yes they can, but I believe they show up as icons on the desktop when they are mounted in the /media folder.  just remount them to another folder.....

can I ask why you talk in the third person??

---

### Post by IamAcoconut on 2006-12-24
Thanks for the hint! But how to change mount place via GUI?
> then you will see where to configure your adapter.Coconut feels a little depersonalized, that's why ;-)

---

### Post by IamAcoconut on 2006-12-24
Ok, I found out.
gconf-editor
apps
nautilus
desktop
volumes_visible

---

### Post by IamAcoconut on 2006-12-25
I came to think it would be better to do this, just as you, **Spockrock** wrote - by remounting the partitions to a folder different then /media.
**Edit**: I didn't know one has to reboot after changing such settings. Now it's fine! Thank you all for help, and merry Christmas!

---

