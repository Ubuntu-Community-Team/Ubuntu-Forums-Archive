---
title: "Unable remove corrupted files input/output error"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by karies on 2007-05-28
Hi all, 
I cannot open or delete corrupted files.
I was moving some media files onto usb hard drive "MediaGate" when electricity shutdown. Now I'm not able to open, move, or change permission of these files on usb drive, all time I get: "Input/output error".  I just want to remove them,  "rm -f", doesn't work.  
Does anyone know how to delete corrupted files? 
Thank you.

---

### Post by sankarv on 2007-05-29
normally i havent faced any problem in deleting corrupted files in linux. do a reboot and try it again. it might work. 

anyway u could try some of the file tools  for recovery/ safe deletion from web or possibly backup ur USB data of rest of the files and format it.

---

### Post by karies on 2007-06-03
Thank you for your advise. 
I've  tried everything. I'm still getting INPUT/OUTPUT ERROR. I'm going to format this drive.

---

### Post by FrooziE on 2008-05-04
My external serves as my backup. After doing a fresh install of Hardy I cannot copy/change/move/edit anything on the drive. Even when I log in as root. Formatting is not an option.

---

### Post by vikasvishnu on 2008-05-05
> **karies said:**
> Thank you for your advise. 
I've  tried everything. I'm still getting INPUT/OUTPUT ERROR. I'm going to format this drive.

Friend, have you tried removing the file using its inode number? This is a bit advanced stuff, but let me try to help you here.

1) First step is to find the file's inode number:

 - take a terminal, navigate to the directory where you have this file
 - find the inode number using the below command:

 > # ls -il filename

 - Suppose you get the output like this:

> 777777 -rw-r--r--  1 vikas vikas    0 2008-01-27 11:19 corrupted_file

Then 777777 is the inode number. 

2) Delete the file using the inode number using the below command:

> find . -inum [inode-number] -exec rm -i {} \;

for example, to delete the file in my example, give this command:

> find . -inum 777777 -exec rm -i {} \;

That should remove it. Please give it a try and let us know the results. 

Vikas

---

### Post by iacobson on 2008-06-08
hi,
i have a similar problem like karies.
on my hard disk is a file that is not removable.
but when i want to get the node,
i get this output:

> $ rm file 
rm: cannot remove `file': Input/output error
$ ls -il file 
ls: file: Input/output error


is there another way to get this information?
thanks in advance
iacobson

---

