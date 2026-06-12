---
title: "Big Rm Problem"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by qbox on 2007-12-24
Hi to all. 
I try to delete some garbage in one folder but I make
sudo rm-r * 
in my main folder.
I delete my school projects and program with 1000 lines of code.
ANY HELP TO BRING IT BACK!!!!!!

---

### Post by Dr Small on 2007-12-24
Rm does exactly what it is supposed to do. It removes the object, and since in this case, it was *, it removed it all. I don't know of any recovery applications off hand, but I'm sure somebody here does.

Dr Small

---

### Post by qbox on 2007-12-24
Come on people .... I must save that files SOMEHOW...

---

### Post by mivo on 2007-12-24
This may help or serve as a starting point: [http://recover.sourceforge.net/linux/](http://recover.sourceforge.net/linux/) . [Searching Google]("http://www.google.de/search?q=recovering+deleted+files+linux") will also yield quite a few potentially helpful links. :)

---

### Post by asmiller-ke6seh on 2007-12-24
First, make no changes to your system!

Next, be patient. It's Christmas eve. Not everyone has the knowledge you are looking for, but someone will be around, by and by.

Third, realx. Don't sweat it. If you make NO CHANGES to the system, whatever data is recoverable now will be recoverable an hour from now, a week, from now, a year from now SO LONG AS YOU MAKE NO CHANGES TO YOUR SYSTEM.

---

### Post by qbox on 2007-12-24
I try this 
grep -a -B2 -A99999 "*" /dev/hda1
ahd some numets and simbols start so shown very fast.
Can someone give me something graphick . IM IN PANIC and Im trying to RELAX......

---

### Post by erginemr on 2007-12-24
Unfortunately, ext3 is not a forgiving system on unintentional file / folder deletions. The following is an excerpt form the site:
[http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

> Q: How can I recover (undelete) deleted files from my ext3 partition?
Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.

Also check out the following links:
[http://jblevins.org/computing/linux/ext3-undelete](http://jblevins.org/computing/linux/ext3-undelete)

[http://www.diskinternals.com/linux-recovery/](http://www.diskinternals.com/linux-recovery/)

The second link is a freeware Windows program, which supposedly will try to find and recover deleted files in your ext3 partition from within Windows.

Good Luck.

---

### Post by erginemr on 2007-12-24
> **qbox said:**
> I try this 
grep -a -B2 -A99999 "*" /dev/hda1
ahd some numets and simbols start so shown very fast.
Can someone give me something graphick . IM IN PANIC and Im trying to RELAX......

Try to remember your program code and replace "*" with a unique part of your program code to catch the location of your deleted file on the hard disk.

Also make sure that your file system is ext3 by checking it out from /etc/fstab, all the while doing no / minimal changes in your Linux system to avoid overwriting your newly deleted files. If by chance, it turns out as ext2, then this will be your lucky day, because it is easier to recover files form an ext2 system.

Also try the suggestion on 
[http://jblevins.org/computing/linux/ext3-undelete](http://jblevins.org/computing/linux/ext3-undelete)
for the grep usage format to recover your program code.

---

### Post by Jerry N on 2007-12-24
Why not just reload your files from your backups?

Jerry

---

### Post by qbox on 2007-12-25
> **Jerry N said:**
> Why not just reload your files from your backups?

Jerry

I dont have backup...... My backup was on USB flash drive but I used flash for something else and templ. I put my backup on my desktop. I try to clean my flash drive and I wrote in console sudo rm -r * but I make a mistake. I WAS IN HOME FOLDER. And all things was deleted in a minute.... :(
So ... i cant get back my files....

---

### Post by bumanie on 2007-12-25
You could try test disk. I have no idea whether it will work in this situation ,but it a data recovery tool. I think (but aren't 100% sure) it only works on hdd's and partitions, not just individual folders within a partition. Having said that, I am don't know the program extensively.

---

### Post by qbox on 2007-12-26
Im going to reinstall computer and Im starting over. Thanks to all for your help. I cant wait. Its better to start with project from the beginning.

---

### Post by erginemr on 2007-12-26
You are welcome, but I hope you have also tried Windows alternatives such as:
[http://www.diskinternals.com/linux-recovery/](http://www.diskinternals.com/linux-recovery/)

This is a freeware Windows program, which supposedly will try to find and recover deleted files in your ext3 partition from within Windows. It really did find some deleted files in my Linux box. There are several more (mostly hareware), which will turn up if you google it.

Good luck in anyway.

---

