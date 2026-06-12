---
title: "Error: cannot find GRLDR in al drives"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by dropkickfitz on 2007-05-22
Unable to get past the boot menu.

This text comes up:

Try (hd0,0): FAT16: no GRLDR
Try (hd0,1): NTFS5: 3
Try (0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: cannot find GRLDR in all drive.  CTRL+ALT+DEL to restart.

No idea what a GRLDR is.

Can you help?

Thanks

---

### Post by robbielink on 2007-05-23
Is this a Dell machine? I have this problem, too. Dell puts a recovery partition at hd0,0 and it is a FAT16 partition. It's not the boot partition and apparently invisible to windows but I believe this is what is preventing Ubuntu from loading - it's not finding GRUB there.
Anyone know how to get around this?

---

### Post by dropkickfitz on 2007-05-23
Dude, it's a Dell.  I would love to know how to get around it too.

---

### Post by robbielink on 2007-05-24
Did you install with Wubi?

---

### Post by dropkickfitz on 2007-05-24
Yes, I installed with Wubi.  

I just ordered a CD from Ubuntu.  

I may try to make a Live CD, but my prior attempts have been unreadable for my PC.

I use Lifehacker for most of my how to's so I may try again if I can get up the courage for more failure.

---

### Post by robbielink on 2007-05-24
I just found out the other day that there is a dedicated Wubi section on this board. I think this is a Wubi installation issue. I think you (we) should post there:
   	[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)
(it's under 3rd party applications/Wubi)

On a Google search I read somewhere that there was currently no solution to this issue but I'm hoping someone on these forums will have a suggestion.

Will you repost in the Wubi section?

---

### Post by dropkickfitz on 2007-05-25
Consider it done, thanks.

I thought this was a Wubi post!

---

