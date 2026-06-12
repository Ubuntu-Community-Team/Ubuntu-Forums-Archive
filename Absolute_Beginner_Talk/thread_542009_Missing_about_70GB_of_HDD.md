---
title: "Missing about 70GB of HDD"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Satal Keto on 2007-09-03
I have been trying to back up files on my external HDD (to convert it to FAT32 rather than NTFS) onto my laptop, but when I tryed tar.bz2 compressing the files I ran out of space so I assumed that it deleted the unfinished file.
That sees fair enough, but now im noticing that Im missing a large amount of memory missing.
According to QTParted I am using 84.04GB, but after going through / and looking at the properties of each folder (which shows the size of the contains files) I work out I should be using about 13.3GB.

I was wondering whether anyone can suggest what I might do as I really would like to be able to use that 70GB (hell I had to go into recovery mode to boot up earlier as I didn't have enough space for ubuntu to write the login files :lolflag:)

Thanks for any help in advance

Satal



EDIT:

Dont worry, I didn't realise that the files are stored hidden
I used the command > ls -A -h -l to view all the files (including hidden files) and their size and found the offending files

---

### Post by Mirrorball on 2007-09-03
You should empty your trash bin, also have a look at the hidden directories (Ctrl + H in Nautilus will make them visible).

---

