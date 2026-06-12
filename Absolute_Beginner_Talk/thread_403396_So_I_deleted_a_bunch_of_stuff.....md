---
title: "So I deleted a bunch of stuff...."
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by treehouse on 2007-04-07
I had a permission problem so I couldn't empty the trash. I mistakenly follow this instruction: "sudo rm -fR * ~/.Trash"

So as it's deleting a bunch of stuff (I don't even know what all is gone yet) I realise it and manage to kill the terminal and save some of my home folder. Is there a way to recover the massive amount of missing stuff and actually empty my trash?

---

### Post by dbbolton on 2007-04-07
> **treehouse said:**
> I had a permission problem so I couldn't empty the trash. I mistakenly follow this instruction: "sudo rm -fR * ~/.Trash"

So as it's deleting a bunch of stuff (I don't even know what all is gone yet) I realise it and manage to kill the terminal and save some of my home folder. Is there a way to recover the massive amount of missing stuff and actually empty my trash?

one utility is Midnight Commander (command 'mc'), which can use a virtual filesystem and has a special undelete file system that works with ext2/3 filesystems. 'mc' is actually an interface for the 'ext2fs' library. this is a simplified solution to a complex problem, and not 100% efficient.

in order to use this virtual filesystem, you must run a command like such ```
sudo cd /#undel:hdaX
```where hdaX is the partition you're concerned with (like hda2, hda3, etc). it will take awhile for the deleted items to be displayed. a list of inodes will appear, and you can inspect these with a text editor by pressing F4, then press F12 to 'save as', and rename the file as something appropriate for use. exit with Shift + F10. maybe you can only save pieces of files, or none at all.

i hope this helps.

---

### Post by treehouse on 2007-04-07
Thanks. I found a simpler solution that makes me feel like an idiot. Most of the important files were in archives in the trash, where I couldn't delete them...ironically.

---

