---
title: "[SOLVED] sda1 contains a file system with errors"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by wallywally on 2007-11-04
My system has completely died and I am having to use the Live CD to write this.  I’ve tried reinstalling Ubuntu from the CD which seems to proceed smoothly enough but when I remove the CD and reboot the following happens.
 
I get the pretty Ubuntu logo and the orange bar manages to complete about one third of it’s journey across the screen then it suddenly stops and the following appears on the screen.
 
(first ten or so lines missing because they scrolled up the screen to quickly for me to read)
* Checking file systems
Fsck 1.40.2 (12-Jul-2007)
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Filesystem contains large files, but lacks LARGE_FILE flag in superblock.
 
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without –a or –p options)
fsck died with exit status 4
[fail]
* File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file manually.
* A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
 
I’ve then got a cursor flashing at root@desktop:~#
 

I've set up sda1 as /home and sda2 as /

What does the line “Filesystem contains large files, but lacks LARGE_FILE flag in superblock” mean and what should I do about it?

Prior to my system completely dying it had been playing up for an hour or so in that it was freezing whenever I used nautilus.  I was in the process of composing a post about that problem when I decided to pop out for lunch so I left everything running but then when I came back it was kaput.  I've only been using Ubuntu for a week or so but despite teething problems it has gone pretty well.  In case it has anything to do with it I should add that in the last twenty-four hours I have downloaded a couple of Java add-ons for  Firefox – neither of which I managed to get to work.

I've already got all my data backed up by the way.

Thanks in advance,

wallywally

---

### Post by Pumalite on 2007-11-04
Maybe you have a dying or dead hard drive. Test with TestDisk:[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by wallywally on 2007-11-04
Thanks for the links Pumalite. I couldn't load the sysreccd website here but I had a look at TestDisk and found that I understood but a fraction of whatever it was on about so left it at that for fear of frazzling what is left of my mind.

In the end I have solved the fsck problem following the tutorial in this post - [http://ubuntuforums.org/showpost.php?p=2200353&postcount=17](http://ubuntuforums.org/showpost.php?p=2200353&postcount=17) - and so everything is back to how it was before.

Unfortunately 'how it was before' still means that nautilus is freezing my system for no apparent reason but I'll just have to avoid touching it for the time being and ferret around for ideas.

---

### Post by Pumalite on 2007-11-04
I looked at your link and it seems that the solution is to isolate parts of your hard drive that are not working right. Or am I wrong?

---

### Post by wallywally on 2007-11-04
> **Pumalite said:**
> I looked at your link and it seems that the solution is to isolate parts of your hard drive that are not working right. Or am I wrong?

I simply resized my sda1 and sda2 partitions ( /home and / respectively.  I didn't know which to do so just did both) and hey presto I can boot from the hard drive again.

As I understand the reason this works is that the Fsck tool won't operate (for some reason) from the maintenance shell but will work if it is running from the Live CD and the partitioning is simply used to kick start the Fsck tool for simpletons like myself who would rather avoid using the terminal.

I (perhaps foolishly) now assume that my hard drive is fine but that there is some software glitch that is screwing with nautilus.

---

