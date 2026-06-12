---
title: "[SOLVED] Request help in determining filesystem size"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-08-29
After searching the forums, I am still stuck on what is most likely an easy question.

I am running Fiesty, on a box with two hard drives.  The OS and swap partitions are both on drive0, which is 20GB.  Drive1 is a disk I added (a second drive) to be used only for storage of files.

I have changed ownership of the second disk from root to me, and edited my fstab to make it mount at boot time.

I am hoping that this will allow me to use my home directory to store files which will certainly add up to >100 GB.  

Question:  How can I see the total storage available?  Doing right-click>Properties does not seem to help, nor can I find a command in the man pages to show total storage.


Thanks in advance,
m9ke

---

### Post by jrusso2 on 2007-08-29
open a terminal and type df

---

### Post by m9ke on 2007-08-29
Thanks jrusso2.  Output of the command you gave me shows both my hard drives.  Thanks very much and I will make a note of this command.

Cheers,
m9ke

---

