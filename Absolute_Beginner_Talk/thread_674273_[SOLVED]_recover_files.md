---
title: "[SOLVED] recover files?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Jinx-Wolf on 2008-01-21
I just deleted all my files from a Fat32 partition on accident.

I did it from the Terminal, so is there any command to just... bring them back???? :(

---

### Post by Cypher on 2008-01-21
What command did you use?? If something like "rm -rf" or so..then the files are gone and getting them back would be a pain..

If you delete files from within the GUI, you have the safety of the Trash Can (like Windows) unless you choose to SHIFT-Delete a file..

---

### Post by jd65pl on 2008-01-21
If you used 'rm' then nope! Sorry.

---

### Post by Jinx-Wolf on 2008-01-21
> **Cypher said:**
> What command did you use?? If something like "rm -rf" or so..then the files are gone and getting them back would be a pain..

If you delete files from within the GUI, you have the safety of the Trash Can (like Windows) unless you choose to SHIFT-Delete a file..

I just use the rm command (not rm -rf) , but I accidentally put an asterisk in the wrong spot, and wasn't paying attention...

---

### Post by Cypher on 2008-01-21
Well without the "-rf" that just means all "writable" files in the top level directory were erase. The directories should be intact and any "read-only" files should also be safe. But since this a FAT32 partitions, those permissions might not have been set, so you lost all the files in the root folder.

Just FYI, the RM, CP, MV commands have a "-i" option which makes them interactive. If you are going to be doing a lot of these commands, sometimes it's great to have a prompt appear to make you think about what you're doing.

---

### Post by jd65pl on 2008-01-21
If you need the stuff on the drive then try not using it, read [this]("http://www.linuxforums.org/forum/servers/109903-recovering-some-files-rm-rf.html") and then try to recover your stuff.

---

### Post by Jinx-Wolf on 2008-01-21
> **Cypher said:**
> Well without the "-rf" that just means all "writable" files in the top level directory were erase. The directories should be intact and any "read-only" files should also be safe. But since this a FAT32 partitions, those permissions might not have been set, so you lost all the files in the root folder.

Just FYI, the RM, CP, MV commands have a "-i" option which makes them interactive. If you are going to be doing a lot of these commands, sometimes it's great to have a prompt appear to make you think about what you're doing.

Thanks for the tip...

I'm going to go buy a backup HDD right now...
I just lost all the pictures of my family, dogs, dead relatives... heh, just about my entire life =/

Ah, that's what I get for not backup up though... damn this sucks..

---

### Post by jd65pl on 2008-01-21
Check the link I posted one of the posters mentioned recovering pictures!

---

### Post by aysiu on 2008-01-21
The very first thing you should do is unmount the drive--make sure it is not in use.

Then install the package *testdisk*, which will include the program *photorec*.

Run the command ```
photorec
``` and specify which drive you want to recover (the FAT32 one, obviously) and what directory you want to copy the recovered files to.

---

