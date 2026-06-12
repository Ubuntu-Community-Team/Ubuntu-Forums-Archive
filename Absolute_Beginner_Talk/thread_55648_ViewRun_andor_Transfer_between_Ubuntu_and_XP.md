---
title: "View/Run and/or Transfer between Ubuntu and XP"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2005-08-09
Is there a way I can view/run and transfer files to a hd with Ubuntu under XP and is there a way to view and run files on a ntfs partition with XP under Ubuntu

---

### Post by GavinX on 2005-08-09
Have a look at this [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=Tristan9669]Is there a way I can view/run and transfer files to a hd with Ubuntu under XP and is there a way to view and run files on a ntfs partition with XP under Ubuntu[/QUOTE]

Read and use (not change) nfts drives in Ubuntu:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Read and use Ubuntu drives in XP:

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by Juergen on 2005-08-09
Here are some instructions:
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

For sharing files a long time the only way has been to use a fat-partition, because that's what both OSs can write to.
But lately some ext2 driver for windows have appeared:
[http://sourceforge.net/projects/winext2fsd](http://sourceforge.net/projects/winext2fsd)   (there seem to be others, so maybe google for it)
so you can now also use an ext2-partition.

BTW: what do you mean by 'run' a file?
You can play videos/music etc. but you can't execute windows-binaries in Linux directly.
You have to investigate 'wine' if you want to do this.

---

### Post by Tristan9669 on 2005-08-09
Thanks for the help! :)

---

### Post by Tristan9669 on 2005-08-09
[QUOTE=GavinX]Have a look at this [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)[/QUOTE]
how do I remove the directory after I unmount the partition

---

### Post by Juergen on 2005-08-09
The complement to 'mkdir' is 'rmdir'

So if you followed the guide it's
```
sudo rmdir /media/windows
``` but if you plan to do this again, you just can leave it there.

---

