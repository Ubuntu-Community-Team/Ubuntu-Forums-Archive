---
title: "&quot;File size limit exceeded&quot; error copying to USB drive"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by funkadelic on 2006-10-14
I am trying to copy a large file from my internal HD to an external USB drive...

The file copy started fine, but then suddenly stopped -- I had no idea what was going on until I ran the copy from the command line and got this error 
"File size limit exceeded" ...

ulimit -a says file size unlimited!

Please help!

---

### Post by ReaderRat on 2006-10-14
Is it a fat32 partition. I believe it has a 1.5 Gig limit.

---

### Post by Kateikyoushi on 2006-10-14
The file size limit is 4GB on FAT32. [LINK]("http://support.microsoft.com/kb/314463")

---

### Post by ReaderRat on 2006-10-14
Maybe this???....USB External HDD - HowTo Write To
         [http://www.ubuntuforums.org/showthread.php?t=276272](http://www.ubuntuforums.org/showthread.php?t=276272)

---

### Post by funkadelic on 2006-10-14
Many thanks! I feel stupid now. :p 

I switched to ext3, then used chown, and now things are groovy... 

But shouldn't the GUI have given me an error rather than just aborting when the file size hit 4GB? Wy did I only get the "File size limit exceeded" error when I tried from the command line? Should I report this as a bug?

Thanks again!

---

### Post by Kateikyoushi on 2006-10-14
Yes, a warning would be nice if it happens, I think it worth a try to report it.

---

