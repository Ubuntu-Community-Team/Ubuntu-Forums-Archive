---
title: "7zip can't find archive?"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by mhl12 on 2006-03-04
Hi, I managed to figure out how to use 7zip through the terminal but it can't seem to find the archive. The archive file is located on my desktop but when I type: 7za x archive.zip

it gives me:

Error:
there is no such archive
matt@ubuntuli:~$ archive.zip

7-Zip (A) 4.20  Copyright (c) 1999-2005 Igor Pavlov  2005-05-30
p7zip Version 4.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on)

can anyone help me? Thank you!

p.s. i need to figure out how to use 7zip because i have some other 7zip archives I need to unzip as well.

---

### Post by 5-HT on 2006-03-04
Hi, I haven't used 7zip myself, but from the error you posted it looked like you were trying to unizip the archive from your home directory without specifying the path to the archive in your Desktop folder.

In other words, 7zip was looking for ~/archive.zip instead of the proper ~/Desktop/archive.zip, resulting in the 'archive not found' error.

What about either:

i)changing to your Desktop folder (cd ~/Desktop) and trying it again?

OR

ii)  just including the relative or absolute path to the archive in the command from your home directory (i.e. not just the filename to an archive in a different directory from the one the command is executed)?

Hope this may be of some help.

---

